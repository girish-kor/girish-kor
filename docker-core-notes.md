# Docker Core Learnings (20% Knowledge for 80% Understanding)

## 1. What is Docker?
- Containerization platform
- Packages applications with all dependencies
- Ensures consistent environments across development and production
- Lightweight alternative to virtual machines
- Enables microservices architecture

## 2. Core Concepts

### Key Terminology
- **Container**: Lightweight, standalone, executable package
- **Image**: Blueprint for containers
- **Dockerfile**: Text file with instructions to build an image
- **Docker Hub**: Cloud repository for Docker images
- **Docker Compose**: Tool for defining multi-container applications

## 3. Basic Docker Commands

### Installation and Verification
```bash
# Install Docker
# (Follow official Docker documentation for your OS)

# Verify installation
docker --version
docker run hello-world
```

### Image Management
```bash
# Download an image
docker pull <image-name>:<tag>

# List downloaded images
docker images

# Remove an image
docker rmi <image-id>
```

### Container Management
```bash
# Run a container
docker run <image-name>

# Run container in background
docker run -d <image-name>

# List running containers
docker ps

# List all containers
docker ps -a

# Stop a container
docker stop <container-id>

# Remove a container
docker rm <container-id>
```

## 4. Dockerfile Basics
```dockerfile
# Base image
FROM openjdk:11-jre-slim

# Set working directory
WORKDIR /app

# Copy application files
COPY target/myapp.jar /app/myapp.jar

# Expose port
EXPOSE 8080

# Run command
CMD ["java", "-jar", "myapp.jar"]
```

## 5. Building and Running Images
```bash
# Build an image
docker build -t myapp:v1 .

# Run the built image
docker run -p 8080:8080 myapp:v1
```

## 6. Docker Compose
### Sample docker-compose.yml
```yaml
version: '3'
services:
  web:
    image: nginx:latest
    ports:
      - "8080:80"
  
  database:
    image: mysql:5.7
    environment:
      MYSQL_ROOT_PASSWORD: rootpassword
    ports:
      - "3306:3306"
```

### Docker Compose Commands
```bash
# Start services
docker-compose up

# Stop services
docker-compose down

# Build and start services
docker-compose up --build
```

## 7. Volume Management
```bash
# Create a volume
docker volume create myvolume

# Mount volume to container
docker run -v myvolume:/app/data <image-name>

# List volumes
docker volume ls

# Remove volume
docker volume rm myvolume
```

## 8. Network Management
```bash
# List networks
docker network ls

# Create a network
docker network create mynetwork

# Run container on specific network
docker run --network=mynetwork <image-name>
```

## 9. Best Practices
- Keep images small
- Use multi-stage builds
- Avoid running containers as root
- Use .dockerignore file
- Minimize number of layers
- Use official base images
- Implement health checks

## 10. Common Use Cases
- Microservices deployment
- Continuous Integration/Continuous Deployment (CI/CD)
- Development environment standardization
- Application isolation
- Scalable infrastructure

## 11. Dockerfile Optimization
```dockerfile
# Multi-stage build example
FROM maven:3.8.1-openjdk-11-slim AS build
WORKDIR /app
COPY pom.xml .
COPY src ./src
RUN mvn package -DskipTests

FROM openjdk:11-jre-slim
WORKDIR /app
COPY --from=build /app/target/myapp.jar ./app.jar
EXPOSE 8080
CMD ["java", "-jar", "app.jar"]
```

## 12. Security Considerations
- Use official images
- Regularly update images
- Scan images for vulnerabilities
- Limit container capabilities
- Use read-only file systems
- Avoid running as root

## 13. Learning Path
1. Docker basics
2. Dockerfile creation
3. Docker Compose
4. Container orchestration
5. CI/CD integration
6. Advanced networking
7. Production deployment

## 14. Recommended Tools
- Docker Desktop
- Docker Hub
- Portainer (Container management)
- Kubernetes
- Jenkins
- GitLab CI

## 15. Quick Reference Cheat Sheet
- `docker pull`: Download image
- `docker run`: Create and start container
- `docker build`: Build image from Dockerfile
- `docker ps`: List containers
- `docker images`: List images
- `docker stop`: Stop running container
- `docker rm`: Remove container
- `docker rmi`: Remove image
- `docker-compose`: Manage multi-container applications
