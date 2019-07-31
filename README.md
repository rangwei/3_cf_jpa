# Accesing Data with JPA

[Accesing Data with JPA](https://spring.io/guides/gs/accessing-data-jpa/)

## Backend develop

- pom.xml
```
<!-- accessing jpa data with rest  -->
		<dependency>
			<groupId>org.springframework.boot</groupId>
			<artifactId>spring-boot-starter-data-rest</artifactId>
		</dependency>
<!-- accessing jpa data with postgresql  -->		
		<dependency>
			<groupId>org.postgresql</groupId>
			<artifactId>postgresql</artifactId>
		</dependency>
```

- CustomerRepository.java 
```
@RepositoryRestResource
```

- application.properties
```
# Initialize the database using Hibernate
spring.jpa.hibernate.ddl-auto=create-drop
```

## UI

> TODO

## Test run locally
```
localhost:8080
```

## Create manifest.yml

```
---
applications:
# Application
- name: gs-accessing-data
  instances: 1
  memory: 1024M
  path: target/gs-accessing-data-jpa-0.1.0.jar
```

## Deploy to SAP Cloud Foundry

`cf push`

## Binding to PostgreSQL Database

1. List services:
```
cf marketplace
```

2. Check PostgreSQL
```
cf marketplace -s postgresql
```
3. Create a service instance
```
cf create-service postgresql v9.6-dev postgres
```
4. Binding service to app
```
cf services
cf bind-service gs-accessing-data postgres
```
5. Restage app
```
cf restage gs-accessing-data
```
6. Check service binding
```
cf services
```
