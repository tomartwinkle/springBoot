# Maven
Maven in short is a java project manager that helps build the project and manages dependencies. It is a command line lang. 
<br>You can run maven using commands like : 
```
mvn clean install      # Cleans, builds, and packages your app
mvn spring-boot:run    # Runs your Spring Boot application

```
if u code `./mvnw clean compile` in your vscode command prompt u get a message build successful - mvnw is a maven script present in the root of our project it is the command that runs maven wrapper mvnw. <br>
1. **clean**
Deletes the target/ directory (where compiled code and old builds live).
This ensures a fresh start by removing any previously compiled files, cached data, or artifacts.

2. **compile**
Compiles the source code (from src/main/java) into .class files inside the target/ folder.
<br><br>
## Maven Concepts 
we will be using maven wrapper mvnw cuz we dont wanna download maven for now <br>
`mvnw [options] [<goals>] [<phases>]` (general mvnw syntax) <br>
- [options]	 -> Optional flags (e.g. -q for quiet, -X for debug)
- <goals>	-> Specific tasks Maven should run
- <phases> -> Predefined steps in the Maven build lifecycle
###  Phases 
It is a lifecycle, that contains 1 or more goals. It gives the order in which we want to achieve the goals. Maven has 3 phases :
a. clean - removed temp dir and files
b. default - most useful goals live here (where we do building and testing)
c. site - all the documentations like reports etc. live here
#### clean
mvwn clean has 3 goals : pre-clean , clean , post-clean <br> 
Clean cleans out directories n files.<br>
but only the clean goal does the actual cleaning. Pre-clean is the hook before cleaning and post-clean is the hook after cleaning.<br>
It will basically remove the target dir that includes old dir and stuff
#### default 
mvwn [default]
<br>default has 4 goals : 
a. compile -> compiles the code into bytecode
b. test -> run unit tests
c. package -> create a jar or war file
d. verify -> run checks and integration tests
**note - everything runs in this particular order only inside default phase. example : if u want to run it to package then it will compile then test then package etc.**
```
./mvnw compile 
```




