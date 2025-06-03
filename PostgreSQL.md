# Connect to PostgreSQL DB
Intialise a new springboot project skeleton with the dependencies : PostgreSQL Driver , lombok , JDBC API <br><br>
```
package com.twinkle.PostgreSQLConnection;

import javax.sql.DataSource;

import org.springframework.boot.CommandLineRunner;
import org.springframework.boot.SpringApplication;
import org.springframework.boot.autoconfigure.SpringBootApplication;
import org.springframework.jdbc.core.JdbcTemplate;

import lombok.extern.java.Log;

@SpringBootApplication
@Log
public class PostgreSqlConnectionApplication implements CommandLineRunner {
	private final DataSource dataSource;

    public PostgreSqlConnectionApplication(DataSource dataSource) {
        this.dataSource = dataSource;
    }

	
	public static void main(String[] args) {
		SpringApplication.run(PostgreSqlConnectionApplication.class, args);
	}

    @Override
    public void run(String... args) {
		log.info("DataSource : "+dataSource.toString());
		JdbcTemplate restTemplate=new JdbcTemplate(dataSource);
		restTemplate.execute("select 1");

	}
    

}

```

- What you typically do when using Docker with a database like PostgreSQL for a project:<br><br>
Create a Docker container running the PostgreSQL database for your project.
(Usually, one container per database instance.)<br><br>
You can name the container and set environment variables (POSTGRES_DB, POSTGRES_USER, POSTGRES_PASSWORD) to configure it.
<br><br>
docker-compose.yml file is something you write yourself or get from your project templates; Docker Compose does not auto-generate it for you.
This file defines what containers to run (e.g., your app + database) and how they connect.
<br><br>
In your Spring Boot app's application.properties (or application.yml), you configure connection details matching the Docker container:
URL, username, password, driver class.
<br><br>docker-compose.yml : 
```
services:
  db:
    image: postgres:15
    restart: always
    environment:
      POSTGRES_USER: user
      POSTGRES_PASSWORD: password
      POSTGRES_DB: mydatabase  # this should create the database automatically
    ports:
      - "5432:5432"

```
application.properties : 
```
spring.datasource.url=jdbc:postgresql://localhost:5432/postgres
spring.datasource.username=user
spring.datasource.password=password
spring.datasource.driver-class-name=org.postgresql.Driver
spring.jpa.database-platform=org.hibernate.dialect.PostgreSQLDialect
spring.jpa.hibernate.ddl-auto=update
```
To create a new docker databse : 
## Docker workflow 

Typical Docker Workflow for a New Project with PostgreSQL

1. Create a docker-compose.yml file in your project folder:
Example docker-compose.yml:
```
version: '3.1'

services:
  db:
    image: postgres:15
    restart: always
    environment:
      POSTGRES_USER: user
      POSTGRES_PASSWORD: password
      POSTGRES_DB: mydatabase
    ports:
      - "5432:5432"
```
You just create this file once per project, adjusting:

- POSTGRES_USER

- POSTGRES_PASSWORD

- POSTGRES_DB

- ports (optional, usually 5432)

2. Start PostgreSQL container for your project
Open your terminal in your project folder where docker-compose.yml is and run:

```
docker-compose up -d
```
-d runs the container in the background (detached mode).
This command pulls the postgres image if not present, then creates and starts your container.

3. Check if container is running
```
docker ps
```
You should see your Postgres container running, exposing port 5432.
4. Connect your app to PostgreSQL
In your app's config (e.g., application.properties in Spring Boot), use:
```
spring.datasource.url=jdbc:postgresql://localhost:5432/mydatabase
spring.datasource.username=user
spring.datasource.password=password
```
What if you want to stop or remove the container?
Stop the container:
```
docker-compose down
```
This stops and removes containers defined in the compose file but keeps your data volumes intact unless you delete those separately.

