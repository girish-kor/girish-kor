# SPRING BOOT ESSENTIAL NOTES

## 1. Core Concepts

### What is Spring Boot?
- Framework built on top of Spring that simplifies Java application development
- Provides auto-configuration to reduce boilerplate code
- Offers embedded servers (Tomcat, Jetty, Undertow)
- Follows "convention over configuration" principle

### Key Benefits
- Minimal setup and configuration
- Standalone applications (no WAR files needed)
- Production-ready features out of the box
- Microservices friendly

## 2. Project Setup & Structure

### Spring Boot Starter Dependencies
- `spring-boot-starter-web`: Web applications with Spring MVC
- `spring-boot-starter-data-jpa`: Database access with JPA/Hibernate
- `spring-boot-starter-security`: Authentication and authorization
- `spring-boot-starter-test`: Testing utilities

### Basic Project Structure
```
src/
├── main/
│   ├── java/
│   │   └── com/example/project/
│   │       ├── Application.java (main class)
│   │       ├── controller/
│   │       ├── service/
│   │       ├── repository/
│   │       └── model/
│   └── resources/
│       ├── application.properties
│       ├── static/
│       └── templates/
└── test/
```

## 3. Core Annotations

### Application Setup
- `@SpringBootApplication`: Combines @Configuration, @EnableAutoConfiguration, and @ComponentScan
- `@EnableAutoConfiguration`: Enables Spring Boot's auto-configuration mechanism
- `@ComponentScan`: Tells Spring where to look for components

### Component Annotations
- `@Component`: Generic Spring-managed component
- `@Service`: Business logic layer
- `@Repository`: Data access layer
- `@Controller`/`@RestController`: Web layer (request handling)
- `@Configuration`: Configuration class (similar to XML config)

### Web Controller
- `@RequestMapping`: Maps URL paths to methods or controllers
- `@GetMapping`, `@PostMapping`, etc.: HTTP method-specific mappings
- `@PathVariable`: Extracts values from URI path
- `@RequestParam`: Extracts query parameters
- `@RequestBody`: Binds request body to method parameter

## 4. Data Access & Persistence

### Spring Data JPA
- Simplifies database operations with repository interfaces
- `JpaRepository<Entity, ID>`: Provides CRUD operations
- Derived query methods (findByName, findByEmailAndActive, etc.)
- `@Entity`: JPA annotation to mark classes as database entities
- `@Id`: Marks a field as primary key
- `@GeneratedValue`: Auto-generates primary key values

### Example Repository
```java
@Repository
public interface UserRepository extends JpaRepository<User, Long> {
    List<User> findByLastName(String lastName);
    Optional<User> findByEmail(String email);
}
```

## 5. Configuration & Properties

### Property Sources
- `application.properties` or `application.yml` for configuration
- Environment-specific profiles (application-dev.properties, application-prod.properties)
- External configuration via command line or environment variables

### Important Properties
```properties
# Server configuration
server.port=8080
server.servlet.context-path=/api

# Database connection
spring.datasource.url=jdbc:mysql://localhost:3306/mydb
spring.datasource.username=root
spring.datasource.password=password

# JPA/Hibernate properties
spring.jpa.hibernate.ddl-auto=update
spring.jpa.show-sql=true

# Logging
logging.level.org.springframework=INFO
logging.level.com.example=DEBUG
```

### @Value and @ConfigurationProperties
- `@Value("${property.name}")`: Inject single property
- `@ConfigurationProperties(prefix="app")`: Bind properties to POJO

## 6. RESTful API Development

### REST Controller Example
```java
@RestController
@RequestMapping("/api/users")
public class UserController {
    
    @Autowired
    private UserService userService;
    
    @GetMapping
    public List<User> getAllUsers() {
        return userService.findAll();
    }
    
    @GetMapping("/{id}")
    public ResponseEntity<User> getUserById(@PathVariable Long id) {
        User user = userService.findById(id)
            .orElseThrow(() -> new ResourceNotFoundException("User not found"));
        return ResponseEntity.ok(user);
    }
    
    @PostMapping
    public ResponseEntity<User> createUser(@Valid @RequestBody User user) {
        User savedUser = userService.save(user);
        return ResponseEntity.status(HttpStatus.CREATED).body(savedUser);
    }
    
    // PUT and DELETE methods...
}
```

### Response Status Handling
- `ResponseEntity<T>`: Customize HTTP response (status, headers, body)
- `@ResponseStatus`: Specifies the HTTP status of a method's response

## 7. Exception Handling

### Global Exception Handler
```java
@RestControllerAdvice
public class GlobalExceptionHandler {
    
    @ExceptionHandler(ResourceNotFoundException.class)
    public ResponseEntity<?> handleResourceNotFound(ResourceNotFoundException ex) {
        ErrorResponse error = new ErrorResponse(HttpStatus.NOT_FOUND.value(), ex.getMessage());
        return new ResponseEntity<>(error, HttpStatus.NOT_FOUND);
    }
    
    @ExceptionHandler(Exception.class)
    public ResponseEntity<?> handleGlobalException(Exception ex) {
        ErrorResponse error = new ErrorResponse(HttpStatus.INTERNAL_SERVER_ERROR.value(), 
                                                "An unexpected error occurred");
        return new ResponseEntity<>(error, HttpStatus.INTERNAL_SERVER_ERROR);
    }
}
```

## 8. Dependency Injection

### Injection Methods
- `@Autowired`: Automatic dependency injection
- Constructor injection (preferred method)
- Setter injection
- Field injection (convenient but not recommended for production)

### Example (Constructor Injection)
```java
@Service
public class UserServiceImpl implements UserService {
    
    private final UserRepository userRepository;
    
    // Constructor injection (preferred)
    @Autowired
    public UserServiceImpl(UserRepository userRepository) {
        this.userRepository = userRepository;
    }
    
    // Service methods...
}
```

## 9. Testing

### Test Annotations
- `@SpringBootTest`: Full application context with all beans
- `@WebMvcTest`: Test controllers without starting full HTTP server
- `@DataJpaTest`: Test JPA repositories
- `@MockBean`: Replaces bean with Mockito mock

### Example Test
```java
@SpringBootTest
class UserServiceTests {
    
    @Autowired
    private UserService userService;
    
    @MockBean
    private UserRepository userRepository;
    
    @Test
    void shouldFindUserById() {
        // Given
        User user = new User(1L, "John", "Doe", "john@example.com");
        when(userRepository.findById(1L)).thenReturn(Optional.of(user));
        
        // When
        Optional<User> result = userService.findById(1L);
        
        // Then
        assertTrue(result.isPresent());
        assertEquals("John", result.get().getFirstName());
    }
}
```

## 10. Security Basics

### Spring Security Configuration
```java
@Configuration
@EnableWebSecurity
public class SecurityConfig extends WebSecurityConfigurerAdapter {
    
    @Override
    protected void configure(HttpSecurity http) throws Exception {
        http
            .csrf().disable()
            .authorizeRequests()
                .antMatchers("/api/public/**").permitAll()
                .antMatchers("/api/admin/**").hasRole("ADMIN")
                .anyRequest().authenticated()
            .and()
            .httpBasic();
    }
    
    @Bean
    public PasswordEncoder passwordEncoder() {
        return new BCryptPasswordEncoder();
    }
}
```

## 11. Actuator & Monitoring

### Spring Boot Actuator
- Provides production-ready features for monitoring and managing application
- Exposes HTTP endpoints for application metrics, health checks, etc.

### Basic Actuator Setup
```properties
# Enable all endpoints
management.endpoints.web.exposure.include=*

# Customize base path for endpoints
management.endpoints.web.base-path=/management

# Health endpoint config
management.endpoint.health.show-details=always
```

## 12. Quick Reference: Application Bootstrap

```java
@SpringBootApplication
public class MyApplication {
    public static void main(String[] args) {
        SpringApplication.run(MyApplication.class, args);
    }
}
```
