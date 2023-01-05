# Notes from microservices with Spring Boot and Spring Cloud

Shows what was configured and not configured automatically
> logging.level.org.springframework=debug
> spring.profiles.active=prod
> 
> management.endpoints.web.exposere.include=*

For Configuration classes need the following:
@ConfigurationProperties(prefix = "prefix-match-config")
@Component

@Controller
@RestController

@Autowired
@RequestMapping("/path-to-map")
@PathVariable

  @InitBinder
  protected void initBinder(WebDataBinder binder) {
    SimpleDateFormat dateFormat = new SimpleDateFormat("dd/MM/yyyy");
    binder.registerCustomEditor(Date.class, new CustomDateEditor(
        dateFormat, false));
  }

```XML
<dependency>
  <groupId>org.springframework.boot</groupId>
  <artifactId>spring-boot-starter-web</artifactId>
</dependency>
<dependency>
  <groupId>org.springframework.boot</groupId>
  <artifactId>spring-boot-starter-actuator</artifactId>
</dependency>
```
