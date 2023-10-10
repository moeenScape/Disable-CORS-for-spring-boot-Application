# Disable CORS-for-spring-boot

Error-Access to XMLHttpRequest at 'http://localhost:8080//api/v1/home/test/save' from origin 'http://localhost:4200' has been blocked by CORS policy: Response to preflight request doesn't pass access control check: No 'Access-Control-Allow-Origin' header is present on the requested resource.

Solve: Craete a class name CorsConfig at you root and paste this code

```Java
@Configuration
public class CorsConfig {
    @Bean
    public WebMvcConfigurer corsConfigurer() {
        return new WebMvcConfigurer() {
            @Override
            public void addCorsMappings(CorsRegistry registry) {
                registry.addMapping("/**")
                        .allowedOrigins("*")
                        .allowedMethods("*");
            }
        };
    }
}

```
### Note : This is a temprary hack to handle CORS.There are custome configuration for CORS.Study and find your proper Config.
Thank You
