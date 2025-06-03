# Beans
A Bean in Spring is just an object that is managed by the Spring Framework.
- Why are Beans important?
Instead of you creating objects manually using new, Spring does it for you.
This helps with loose coupling, dependency injection, and easier testing.
- Analogy: Coffee Shop ☕
Imagine you're running a coffee shop:<br>
You (the developer) are not making every cup manually.
<br>
You just tell the staff (Spring container) what kind of coffee (bean/object) you need.
<br>
The staff creates, prepares, and hands it over to you.
<br>
Spring does the same with your Java classes.

## How to make a class a bean 

3 ways : 
1. `@component`
```
@Component
public class MyService {
    public void doSomething() {
        System.out.println("Working!");
    }
}
```
Spring auto detects this class and creates a bean from it when scanning packages.

2. `@Service`, `@Repository`, `@Controller` <br><br>
These are specialized versions of @Component used for:
- @Service = business logic layer
- @Repository = data access layer
- @Controller = web controller layer
3. `@bean` in `@configuration` class<br><br>
This manually defines a bean in a java config class
```
@Configuration
public class AppConfig {
    
    @Bean
    public MyService myService() {
        return new MyService();
    }
}
```
## How to use Beans (Dependency Injection)
Once a class is a bean, you can inject it into other classes using   `@Autowired ` : 
```
@RestController
public class HelloController {

    @Autowired
    private MyService myService;

    @GetMapping("/test")
    public String test() {
        myService.doSomething();
        return "Done";
    }
}
```
Spring automatically injects the MyService bean into HelloController.
## Behind the scenes
When your app starts:
<br>
- Spring scans for components (classes annotated with @Component, @Service, etc.)
- It creates instances of those classes.
- It injects them wherever needed
