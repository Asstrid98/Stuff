# Java Multi-Environment Configuration

```java
public class EnvironmentConfig {
    
    public enum Environment {
        DEVELOPMENT, STAGING, PRODUCTION
    }
    
    private Environment environment;
    private String apiUrl;
    private String dbUrl;
    
    public EnvironmentConfig(Environment env) {
        this.environment = env;
        configureEnvironment();
    }
    
    private void configureEnvironment() {
        switch(environment) {
            case DEVELOPMENT:
                apiUrl = "http://localhost:8080";
                dbUrl = "jdbc:mysql://localhost:3306/dev_db";
                break;
            case STAGING:
                apiUrl = "https://staging-api.example.com";
                dbUrl = "jdbc:mysql://staging-db:3306/stage_db";
                break;
            case PRODUCTION:
                apiUrl = "https://api.example.com";
                dbUrl = "jdbc:mysql://prod-db:3306/prod_db";
                break;
        }
    }
    
    public String getApiUrl() { return apiUrl; }
    public String getDbUrl() { return dbUrl; }
}
```

**Usage:**
```java
EnvironmentConfig config = new EnvironmentConfig(Environment.PRODUCTION);
System.out.println(config.getApiUrl());
```