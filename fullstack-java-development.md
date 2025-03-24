# Full Stack Java Development - The 20% That Delivers 80% Understanding

## 1. Java Backend Fundamentals

### Core Java
```java
// Object-Oriented Programming
public class Employee {
    private String name;
    private double salary;
    
    public Employee(String name, double salary) {
        this.name = name;
        this.salary = salary;
    }
    
    public void giveRaise(double percentage) {
        this.salary += this.salary * (percentage/100);
    }
}

// Collections Framework
List<Employee> employees = new ArrayList<>();
Map<String, Employee> employeeMap = new HashMap<>();

// Functional Programming (Java 8+)
employees.stream()
    .filter(e -> e.getSalary() > 50000)
    .map(Employee::getName)
    .forEach(System.out::println);
```

### Spring Framework
```java
// Spring Boot application
@SpringBootApplication
public class HrApplication {
    public static void main(String[] args) {
        SpringApplication.run(HrApplication.class, args);
    }
}

// REST Controller
@RestController
@RequestMapping("/api/employees")
public class EmployeeController {
    @Autowired
    private EmployeeService employeeService;
    
    @GetMapping
    public List<Employee> getAllEmployees() {
        return employeeService.findAll();
    }
    
    @PostMapping
    public Employee createEmployee(@RequestBody Employee employee) {
        return employeeService.save(employee);
    }
}

// Service Layer
@Service
public class EmployeeService {
    @Autowired
    private EmployeeRepository employeeRepository;
    
    // Business logic here
}

// Repository Layer
@Repository
public interface EmployeeRepository extends JpaRepository<Employee, Long> {
    List<Employee> findByDepartmentId(Long departmentId);
}
```

## 2. Database Integration

### JDBC (Java Database Connectivity)
```java
// Basic JDBC Connection
Connection conn = DriverManager.getConnection(
    "jdbc:mysql://localhost:3306/hr", "username", "password");
    
Statement stmt = conn.createStatement();
ResultSet rs = stmt.executeQuery("SELECT * FROM employees");

while(rs.next()) {
    String name = rs.getString("name");
    double salary = rs.getDouble("salary");
    // Process data
}
```

### JPA (Java Persistence API) & Hibernate
```java
// Entity class
@Entity
@Table(name = "employees")
public class Employee {
    @Id
    @GeneratedValue(strategy = GenerationType.IDENTITY)
    private Long id;
    
    private String name;
    
    private double salary;
    
    @ManyToOne
    @JoinColumn(name = "department_id")
    private Department department;
    
    // Getters and setters
}

// Spring Data JPA Repository
public interface EmployeeRepository extends JpaRepository<Employee, Long> {
    List<Employee> findByDepartmentId(Long departmentId);
    
    @Query("SELECT e FROM Employee e WHERE e.salary > :minSalary")
    List<Employee> findEmployeesWithHighSalary(@Param("minSalary") double minSalary);
}
```

## 3. API Development

### RESTful API Design
```
GET /api/employees           # Get all employees
GET /api/employees/{id}      # Get employee by ID
POST /api/employees          # Create new employee
PUT /api/employees/{id}      # Update employee
DELETE /api/employees/{id}   # Delete employee

GET /api/departments         # Get all departments
GET /api/departments/{id}    # Get department by ID
GET /api/departments/{id}/employees  # Get employees by department
```

### Spring Security
```java
@Configuration
@EnableWebSecurity
public class SecurityConfig {
    
    @Bean
    public SecurityFilterChain filterChain(HttpSecurity http) throws Exception {
        http
            .authorizeHttpRequests((authz) -> authz
                .requestMatchers("/api/public/**").permitAll()
                .requestMatchers("/api/admin/**").hasRole("ADMIN")
                .anyRequest().authenticated()
            )
            .oauth2ResourceServer(oauth2 -> oauth2.jwt())
            .csrf(csrf -> csrf.disable());
        return http.build();
    }
}
```

## 4. Frontend Integration

### HTML/CSS/JavaScript Foundations
```html
<!DOCTYPE html>
<html>
<head>
    <title>Employee Portal</title>
    <link rel="stylesheet" href="styles.css">
</head>
<body>
    <div id="app">
        <h1>Employee Directory</h1>
        <div id="employee-list"></div>
    </div>
    <script src="app.js"></script>
</body>
</html>
```

```javascript
// Vanilla JavaScript for API calls
async function getEmployees() {
    const response = await fetch('/api/employees');
    const employees = await response.json();
    
    const employeeList = document.getElementById('employee-list');
    employees.forEach(employee => {
        const div = document.createElement('div');
        div.className = 'employee-card';
        div.innerHTML = `
            <h3>${employee.name}</h3>
            <p>Department: ${employee.department.name}</p>
            <p>Salary: $${employee.salary}</p>
        `;
        employeeList.appendChild(div);
    });
}
```

### Modern JavaScript Frameworks

#### React Integration
```javascript
// React Component
function EmployeeList() {
    const [employees, setEmployees] = useState([]);
    
    useEffect(() => {
        fetch('/api/employees')
            .then(response => response.json())
            .then(data => setEmployees(data));
    }, []);
    
    return (
        <div className="employee-list">
            {employees.map(employee => (
                <div className="employee-card" key={employee.id}>
                    <h3>{employee.name}</h3>
                    <p>Department: {employee.department.name}</p>
                    <p>Salary: ${employee.salary}</p>
                </div>
            ))}
        </div>
    );
}
```

#### Thymeleaf (Server-Side Rendering)
```html
<!DOCTYPE html>
<html xmlns:th="http://www.thymeleaf.org">
<head>
    <title>Employee Portal</title>
</head>
<body>
    <h1>Employee Directory</h1>
    <div class="employee-list">
        <div class="employee-card" th:each="employee : ${employees}">
            <h3 th:text="${employee.name}"></h3>
            <p>Department: <span th:text="${employee.department.name}"></span></p>
            <p>Salary: $<span th:text="${employee.salary}"></span></p>
        </div>
    </div>
</body>
</html>
```

## 5. Build & Deploy

### Maven/Gradle
```xml
<!-- Maven pom.xml -->
<dependencies>
    <dependency>
        <groupId>org.springframework.boot</groupId>
        <artifactId>spring-boot-starter-web</artifactId>
    </dependency>
    <dependency>
        <groupId>org.springframework.boot</groupId>
        <artifactId>spring-boot-starter-data-jpa</artifactId>
    </dependency>
    <dependency>
        <groupId>mysql</groupId>
        <artifactId>mysql-connector-java</artifactId>
    </dependency>
</dependencies>
```

### DevOps & Deployment
```yaml
# Docker Compose
version: '3'
services:
  app:
    build: .
    ports:
      - "8080:8080"
    depends_on:
      - db
    environment:
      - SPRING_DATASOURCE_URL=jdbc:mysql://db:3306/hr
      - SPRING_DATASOURCE_USERNAME=user
      - SPRING_DATASOURCE_PASSWORD=password
      
  db:
    image: mysql:8.0
    environment:
      - MYSQL_DATABASE=hr
      - MYSQL_USER=user
      - MYSQL_PASSWORD=password
      - MYSQL_ROOT_PASSWORD=rootpassword
    volumes:
      - db-data:/var/lib/mysql
      
volumes:
  db-data:
```

## 6. Testing Strategies

### Unit Testing
```java
@SpringBootTest
public class EmployeeServiceTest {
    
    @MockBean
    private EmployeeRepository employeeRepository;
    
    @Autowired
    private EmployeeService employeeService;
    
    @Test
    public void testFindAll() {
        // Arrange
        List<Employee> mockEmployees = Arrays.asList(
            new Employee("John Doe", 50000),
            new Employee("Jane Smith", 60000)
        );
        
        when(employeeRepository.findAll()).thenReturn(mockEmployees);
        
        // Act
        List<Employee> result = employeeService.findAll();
        
        // Assert
        assertEquals(2, result.size());
        assertEquals("John Doe", result.get(0).getName());
    }
}
```

### Integration Testing
```java
@SpringBootTest
@AutoConfigureMockMvc
public class EmployeeControllerIntegrationTest {
    
    @Autowired
    private MockMvc mockMvc;
    
    @Test
    public void testGetAllEmployees() throws Exception {
        mockMvc.perform(get("/api/employees"))
            .andExpect(status().isOk())
            .andExpect(jsonPath("$", hasSize(greaterThan(0))))
            .andExpect(jsonPath("$[0].name", notNullValue()));
    }
}
```

## 7. Microservices Architecture

```java
// Employee Service
@SpringBootApplication
public class EmployeeServiceApplication {
    public static void main(String[] args) {
        SpringApplication.run(EmployeeServiceApplication.class, args);
    }
}

// Department Service
@SpringBootApplication
public class DepartmentServiceApplication {
    public static void main(String[] args) {
        SpringApplication.run(DepartmentServiceApplication.class, args);
    }
}

// API Gateway
@SpringBootApplication
@EnableDiscoveryClient
public class ApiGatewayApplication {
    public static void main(String[] args) {
        SpringApplication.run(ApiGatewayApplication.class, args);
    }
}

// Service Registry with Eureka
@SpringBootApplication
@EnableEurekaServer
public class ServiceRegistryApplication {
    public static void main(String[] args) {
        SpringApplication.run(ServiceRegistryApplication.class, args);
    }
}
```

## 8. Best Practices & Design Patterns

### Layered Architecture
```
├── Controller Layer (API endpoints)
├── Service Layer (Business logic)
├── Repository Layer (Data access)
└── Entity Layer (Data models)
```

### Common Design Patterns
```java
// Singleton (Spring beans are singletons by default)
@Service
public class EmployeeService {
    // Methods...
}

// Repository Pattern (via Spring Data)
public interface EmployeeRepository extends JpaRepository<Employee, Long> {
    // Methods...
}

// DTO Pattern
public class EmployeeDTO {
    private Long id;
    private String name;
    private String departmentName;
    // No sensitive data like salary
    
    // Constructor, getters, setters
}

// Builder Pattern
Employee employee = Employee.builder()
    .name("John Doe")
    .department(dept)
    .salary(50000)
    .build();

// Factory Pattern
public class EmployeeFactory {
    public static Employee createEmployee(String type, String name) {
        if ("MANAGER".equals(type)) {
            return new Manager(name, 80000);
        } else if ("DEVELOPER".equals(type)) {
            return new Developer(name, 70000);
        } else {
            return new Employee(name, 50000);
        }
    }
}
```

## 9. Security Best Practices

```java
// Password encoding
@Bean
public PasswordEncoder passwordEncoder() {
    return new BCryptPasswordEncoder();
}

// JWT Authentication
@Component
public class JwtTokenProvider {
    @Value("${app.jwtSecret}")
    private String jwtSecret;
    
    @Value("${app.jwtExpirationInMs}")
    private int jwtExpirationInMs;
    
    public String generateToken(Authentication authentication) {
        UserDetails userDetails = (UserDetails) authentication.getPrincipal();
        
        Date now = new Date();
        Date expiryDate = new Date(now.getTime() + jwtExpirationInMs);
        
        return Jwts.builder()
                .setSubject(userDetails.getUsername())
                .setIssuedAt(new Date())
                .setExpiration(expiryDate)
                .signWith(SignatureAlgorithm.HS512, jwtSecret)
                .compact();
    }
    
    // Methods to validate token, get username from token, etc.
}

// Input validation
@PostMapping
public Employee createEmployee(@Valid @RequestBody EmployeeRequest request) {
    // Implementation
}

public class EmployeeRequest {
    @NotBlank
    @Size(min = 2, max = 100)
    private String name;
    
    @Positive
    private double salary;
    
    @NotNull
    private Long departmentId;
    
    // Getters and setters
}
```

## 10. Performance Optimization

### Caching
```java
@Configuration
@EnableCaching
public class CacheConfig {
    @Bean
    public CacheManager cacheManager() {
        SimpleCacheManager cacheManager = new SimpleCacheManager();
        cacheManager.setCaches(Arrays.asList(
            new ConcurrentMapCache("employees"),
            new ConcurrentMapCache("departments")
        ));
        return cacheManager;
    }
}

@Service
public class EmployeeService {
    @Cacheable("employees")
    public List<Employee> findAll() {
        // This will be cached
        return employeeRepository.findAll();
    }
    
    @CacheEvict(value = "employees", allEntries = true)
    public Employee save(Employee employee) {
        // This will clear the cache when a new employee is added
        return employeeRepository.save(employee);
    }
}
```

### Database Optimization
```java
// Indexing (in JPA Entity)
@Entity
@Table(name = "employees", indexes = {
    @Index(name = "idx_employee_department", columnList = "department_id"),
    @Index(name = "idx_employee_name", columnList = "name")
})
public class Employee {
    // Fields, getters, setters
}

// Pagination
@GetMapping
public Page<Employee> getAllEmployees(
        @RequestParam(defaultValue = "0") int page,
        @RequestParam(defaultValue = "10") int size) {
    
    Pageable pageable = PageRequest.of(page, size);
    return employeeRepository.findAll(pageable);
}
```
