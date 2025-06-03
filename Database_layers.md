# Database Layer 
Spring boot uses relational databases.

| Type                 | Examples                      | Description                                |
| -------------------- | ----------------------------- | ------------------------------------------ |
| **Relational (SQL)** | MySQL, PostgreSQL, H2, Oracle | Data in **tables** with columns & rows     |
| **NoSQL**            | MongoDB, Firebase, Redis      | Data in **documents**, **key-value**, etc. |
```
Controller (API Layer)   <-- handles HTTP requests
       ↓
Service (Business Logic) <-- handles processing rules
       ↓
Repository (Database Layer) <-- talks to the DB
       ↓
Database (SQL/NoSQL)
```
🔸 @Entity: Tells Spring this class maps to a database table <br>
🔸 @Id: Marks the primary key <br>
# Connect to a H2 Database
for this lets initialise another spring skeleton this time with the dependency of Lombok , H2 Database , JDBC API .
Main class code to connect : 
```
package com.example.demo;

import javax.sql.DataSource;

import org.springframework.boot.CommandLineRunner;
import org.springframework.boot.SpringApplication;
import org.springframework.boot.autoconfigure.SpringBootApplication;
import org.springframework.jdbc.core.JdbcTemplate;

import lombok.extern.java.Log;

@SpringBootApplication
@Log
public class DemoApplication implements CommandLineRunner {

	private final DataSource dataSource;
	public DemoApplication(final DataSource dataSource){
		this.dataSource=dataSource;
	}
	public static void main(String[] args) {
		SpringApplication.run(DemoApplication.class, args);
	}

	@Override
	public void run(String... args){
		log.info("Datasource : "+dataSource.toString());
		final JdbcTemplate restTemplate=new JdbcTemplate(dataSource);
		restTemplate.execute("Select 1");
	}

}

```
## Code explainatiom : 
1. `package com.example.demo;` : This is the package for our main class.
2. `import javax.sql.DataSource;` : This package is automatically imported by our skeleton when we download DB dependencies. DataSource is an interface that gives us connection to a database like H2,mySQL.
3. `import org.springframework.boot.CommandLineRunner;` : This interface allows us to run some code after the app starts for testing or checking a DB connection
4. `import org.springframework.boot.SpringApplication;`and`import org.springframework.boot.autoconfigure.SpringBootApplication;` : Standard springboot that start the application and other features as well.
5. `import org.springframework.jdbc.core.JdbcTemplate;` : helper class to run SQL queries easily
6. `import lombok.extern.java.Log;` : It's from lombok to auto generate a logger so we can use log command(similar to console.log in js)

--------------------------------------------------------------------------------------------------------------------------------
1. `@SpringBootApplication` : Important annotation that tells this is a springboot object and starts it , declares the main class , builds and helps in auto config and scanning components.
2. `@log` : helps use the log command
--------------------------------------------------------------------------------------------------------------------------------
1. `public class DemoApplication implements CommandLineRunner` : Main class where the application starts and it implements CommandLineRunner so we can execute some code right after the app starts to test our DB connectivity.
2. ```
   	private final DataSource dataSource;

	public DemoApplication(final DataSource dataSource){
		this.dataSource=dataSource;
    }
    ```
   This creates a DataSource object as a class variable and then we use a parametrized constructor to initialise this dataSource object.
3. ```
   public static void main(String[] args) {
		SpringApplication.run(DemoApplication.class, args);
	}
    ```
   This is where the app starts from, the main class.
4. ```
   	@Override
	public void run(String... args){
		log.info("Datasource : "+dataSource.toString());
		final JdbcTemplate restTemplate=new JdbcTemplate(dataSource);
		restTemplate.execute("Select 1");
	}
    ```
   This is a run method that runs after the app has started due to CommandLineRunner.<br>
   - log.info(...) just prints the datasource info to your terminal/log.

    - Then you create a JdbcTemplate from that datasource.

    - restTemplate.execute("Select 1"); runs a simple SQL query — a test — to make sure the DB is reachable and responding.
  ## Application Properties
  Now by default if we r using H2 DB we dont really need to modify the application.properties but if we are using any other DB (mySQL, PostgreSQL) we need to atleast include these : 
  ```
spring.datasource.url=
spring.datasource.username=
spring.datasource.password=
```
example : 
```
spring.application.name=databaseConnection
spring.dataSource.url=jdbc:h2:mem:testdb
spring.dataSource.driverClassName=org.h2.Driver
spring.dataSource.username=sa
spring.dataSource.password=password
```
**Now if we run we can see that the DB connects and automatically shutsdown as the application ends as well**
