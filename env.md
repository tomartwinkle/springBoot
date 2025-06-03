# Environment Variables
An environment variable is a key-value pair used to configure settings outside your code — like app secrets, ports, database URLs, etc.
Think of it like a settings file for your operating system or app, where you keep things like passwords, API keys, and configs.
<br><br>
Spring Boot makes working with environment variables easy through the application.properties or application.yml files.
<br>
Example: application.properties
```
server.port=${PORT:8080}
myapp.secret=${JWT_SECRET_KEY}
```
it means : 
- Use the value of PORT env variable (or fallback to 8080)
- Use the value of JWT_SECRET_KEY for myapp.secret
**Use in Spring Boot via ${VAR_NAME} syntax in properties/yml**
  
