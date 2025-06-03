# Starting with Springboot 
visit https://start.spring.io/ <br>
- This initializer's goal is to allow us to configure and download a skeleton springboot project.

To use java we will use : project - maven , language - java. <br>
use the latest stable version and fill in details and select jar as packaging. <br>
For this 1st project, to keep it simple use the dependency  - spring web
generate , download , unzip and open in your IDE (VS Code)
# First SpringBoot Project
## HelloWorld REST API 
- After we open our skeleton for this springboot project using spring web in VS Code, we can find out project file inside src -> main -> java\com\twinkle\projectname
- Create a class in the java\com\twinkle\projectname folder called helloWorldController<br>
- we can see a class called helloWorldController has been made. Just above this class we need to add `@RestController` <br>
- Now inside this class we will add a simple method that returns the string - hello world. 
- To recieve this method in our frontend, we need to add just above the method - `@GetMapping(path="/hello")`
- final code for the helloWorldController class : 
```
package com.twinkle.first;

import org.springframework.web.bind.annotation.GetMapping;
import org.springframework.web.bind.annotation.RestController;

@RestController
public class helloWorldController {
    @GetMapping(path = "/hello")
    public String HelloWorld(){
        return "Hello World";
    }
}
```
Then we can run this in VSCode and in the console we can see the port it is running on. For now its 8080 <br>
<br>In the browser, visit : http://localhost:8080/hello<br>
(8080 is the port name and /hello is the path name)<br>
Output : the brower shows 'hello world' written on a blank page 

# Understanding this project and all the terms 
- we start with the main class file that comes automatically in the skeleton, i named it first.java for now. This file has the main class and it is the basic entrypoint of our whole application.
- @SpringBootApplication is a convenience annotation in Spring Boot that tells Spring:<br>
<br>
“Hey, this is the main class — start the Spring Boot application from here.”

```
package com.twinkle.first;

import org.springframework.boot.SpringApplication;
import org.springframework.boot.autoconfigure.SpringBootApplication;

@SpringBootApplication
public class FirstApplication {

	public static void main(String[] args) {
		SpringApplication.run(FirstApplication.class, args);
	}

}
```

**Notice the @SpringBootApplication command. This is very important and does a lot of tasks but for now consider this as an entrypoint identifier for our application.**
- The test folder in our skeleton that uses the `@SpringBootTest` annotation is a way to test and check if our app starts up. Important thing to check in production.
- pom.xml file :

| Concept    | Explanation                                                            |
| ---------- | ---------------------------------------------------------------------- |
| `pom.xml`  | Core file for managing dependencies and build in Maven                 |
| Needed for | Every Spring Boot (Maven) project                                      |
| Defines    | Project metadata, libraries (e.g., `spring-boot-starter-web`), plugins |
```
project-root/
├── pom.xml
└── src/
    ├── main/
    │   └── java/
    │       └── com/twinkle/first/
    │           └── HelloWorldController.java
    │           └── FirstApplication.java
    └── test/
        └── java/...
```
