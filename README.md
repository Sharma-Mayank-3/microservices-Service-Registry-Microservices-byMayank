# microservices-Service-Registry-Microservices-byMayank

Note : This registry service is to register the different services.
       It will let us know which service is up or down.
       default port number 8761

# Include 2 dependencies in pom
1. cloud bootstrap 
2. eureka server
3. main class add 

       @EnableEurekaServer

# Add Configuration of the eureka 
application.properties file 

       # Eureka server configuration
       server.port=8761

       # Register this service with itself
       eureka.client.register-with-eureka=false
       eureka.client.fetch-registry=false

       eureka.instance.hostname=localhost


      -------------------------------------------------------------------

# Add Eureka Server Client like add User service to eureka server.
# Add 2 dependencies in user-service.
1. cloud Bootstrap 
2. eureka discovery client.

       <dependency>
        <groupId>org.springframework.cloud</groupId>
        <artifactId>spring-cloud-starter</artifactId>
       </dependency>

       <dependency>
        <groupId>org.springframework.cloud</groupId>
        <artifactId>spring-cloud-starter-netflix-eureka-client</artifactId>
       </dependency>

# After Dependencies tag over 
Add

    <dependencyManagement>
     <dependencies>
     <dependency>
      <groupId>org.springframework.cloud</groupId>
      <artifactId>spring-cloud-dependencies</artifactId>
      <version>${spring-cloud.version}</version>
      <type>pom</type>
      <scope>import</scope>
     </dependency>
     </dependencies>
    </dependencyManagement>


# Add spring cloud version to the above properties, what ever is mentioned above.  
    
    <properties>
     <java.version>17</java.version>
     <spring-cloud.version>2022.0.4</spring-cloud.version>
    </properties>


# Now Add configuration in the application.properties file 
     
      eureka.instance.preferIpAddress=true
      eureka.client.register-with-eureka=true
      eureka.client.fetch-registry=true
      eureka.client.service-url.defaultZone=http://localhost:8761/eureka/
      spring.application.name=USER-SERVICE

# Add annotation in main class of user

    @EnableDiscoveryClient
      