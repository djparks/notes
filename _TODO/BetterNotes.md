# Things to look at adding to projects to make them better

## Good Config Flags

```YAML
server:
  shutdown: graceful
spring:
  lifecycle:
    timeout-per-shutdown-phase: 30s

## Why it matters: If your controller is async (like with WebClient), and you don’t set a timeout — it can hang forever.
spring.mvc.async.request-timeout: 5s

# Default: Calculated by HikariCP (often too low or too high)
# Why it matters: This is the #1 cause of slow DB queries under load in most Spring Boot apps.
# Pair with connection-timeout and idle-timeout.
spring.datasource.hikari.maximum-pool-size: 30

# Why it matters: Hibernate inserts/upserts each row one-by-one by default.
spring.jpa.properties.hibernate.jdbc.batch_size: 100

# Why it matters: This enables Kubernetes liveness/readiness probes directly through Spring Boot’s /actuator/health.
management.endpoint.health.probes.enabled: true

# Why it matters: If you’re serving static assets (especially in internal tools or dashboards), set caching headers:
# Result: Frontend load time dropped by 300ms for repeat users. Saved our CDN bill, too.
spring.web.resources.cache.cachecontrol:
          max-age: 86400
          cache-public: true

#Default: 2147483647 (!)
#Why it matters: Every time you call @Async, Spring may spin up a new thread — and there's no ceiling by default.
spring.task.execution.pool.max-size: 50
```

## Maven Builds

Parallel Builds with mvn -T 1C This one’s underrated:

mvn clean install -T 1C

### Monitor Maven Builds

```XML
<plugin>
  <groupId>org.apache.maven.plugins</groupId>
  <artifactId>maven-buildtime-extension</artifactId>
  <version>2.3.0</version>
</plugin>
```

Every build now shows:
[INFO] Total time: 06:24
[INFO] Module xyz: 02:31

## Keep Project Configuration Values together

```YAML
# application.yml
server:
  port: ${SERVER_PORT:8080}

app:
  name: ${APP_NAME:MyAwesomeApp}
  email:
    enabled: ${EMAIL_ENABLED:true}
    smtp-host: ${SMTP_HOST:localhost}
    from-address: ${FROM_EMAIL:noreply@example.com}
```

And then create a proper configuration class:

```JAVA
@ConfigurationProperties(prefix = "app")
@Data
@Component
public class AppConfig {
    private String name;
    private Email email = new Email();
    
    @Data
    public static class Email {
        private boolean enabled = true;
        private String smtpHost = "localhost";
        private String fromAddress = "noreply@example.com";
    }
}
```

## Better Exception Handling

```JAVA
@RestControllerAdvice
public class GlobalExceptionHandler {
    
    private static final Logger log = LoggerFactory.getLogger(GlobalExceptionHandler.class);
    
    @ExceptionHandler(UserNotFoundException.class)
    public ResponseEntity<ErrorResponse> handleUserNotFound(UserNotFoundException ex) {
        log.info("User not found: {}", ex.getMessage());
        return ResponseEntity.status(HttpStatus.NOT_FOUND)
            .body(new ErrorResponse("USER_NOT_FOUND", "User not found"));
    }
    
    @ExceptionHandler(ValidationException.class)
    public ResponseEntity<ErrorResponse> handleValidation(ValidationException ex) {
        log.warn("Validation failed: {}", ex.getMessage());
        return ResponseEntity.badRequest()
            .body(new ErrorResponse("VALIDATION_ERROR", ex.getMessage()));
    }
    
    @ExceptionHandler(Exception.class)
    public ResponseEntity<ErrorResponse> handleGeneral(Exception ex) {
        log.error("Unexpected error", ex);
        return ResponseEntity.status(HttpStatus.INTERNAL_SERVER_ERROR)
            .body(new ErrorResponse("INTERNAL_ERROR", "Something went wrong"));
    }
}
```

## Caching

### TODO: Read up on caching annotations

Use caching, but use it wisely:

```JAVA
@Service
public class UserService {
    
    @Cacheable(value = "users", key = "#id")
    public Optional<User> findById(Long id) {
        log.debug("Fetching user {} from database", id);
        return userRepository.findById(id);
    }
    
    @CacheEvict(value = "users", key = "#user.id")
    public User updateUser(User user) {
        return userRepository.save(user);
    }
}
```

## Your README should have

How to run the app locally
How to run tests
What the app actually does
API documentation (use OpenAPI/Swagger)

## Good DOC

```JAVA
@Operation(summary = "Create a new user")
@ApiResponses(value = {
    @ApiResponse(responseCode = "201", description = "User created"),
    @ApiResponse(responseCode = "400", description = "Invalid request")
})
@PostMapping
public ResponseEntity<UserResponse> createUser(@Valid @RequestBody CreateUserRequest request) {
    // Your boring controller logic here
}
```
