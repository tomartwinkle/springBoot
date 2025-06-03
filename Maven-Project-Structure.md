# Maven Project Structure
When you generate a Spring Boot project using Spring Initializr or mvn archetype, it follows this standard directory layout:
```
my-project/
│
├── pom.xml                # 🧠 Project Object Model: dependencies, plugins, project config
│
├── src/
│   ├── main/
│   │   ├── java/          # 💻 Your application source code (Java files)
│   │   │   └── com/
│   │   │       └── example/
│   │   │           └── myproject/
│   │   │               └── HelloWorldController.java
│   │   └── resources/     # 📦 App config & static resources (application.properties, static/)
│   │       ├── application.properties
│   │       └── static/    # For web static files like HTML, CSS, JS
│   │
│   └── test/
│       └── java/          # 🧪 Unit and integration tests
│           └── com/example/myproject/
│               └── HelloWorldControllerTests.java
```

| Term                  | Meaning                           |
| --------------------- | --------------------------------- |
| `pom.xml`             | Core configuration file for Maven |
| `src/main/java`       | Main source code                  |
| `src/main/resources`  | App configs, static files         |
| `mvn compile`         | Compile code                      |
| `mvn package`         | Create `.jar`                     |
| `mvn spring-boot:run` | Start the app                     |
# Workflow
- ./mvwn clean 
- ./mvwn compile (j to check if our code has no complition errors) 
- ./mvwn clean test 
- ./mvwn clean package (creates a jar file) 
- java -jar path_to_jar_file (to check production) 
- check the browser at the port 
- ./mvwn verify 
- commit and push


