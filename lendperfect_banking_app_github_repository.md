# LendPerfect Banking App

## Project Overview
LendPerfect Banking App is a microservices-based banking and loan management application developed using Java, Spring Boot, Angular, and MySQL. The system helps banks manage customer accounts, loan processing, EMI tracking, transaction management, and secure authentication.

---

# Tech Stack

## Backend
- Java 8
- Spring Boot
- Spring Security
- Spring Data JPA
- Hibernate
- REST API
- Microservices

## Frontend
- Angular
- TypeScript
- Bootstrap
- HTML/CSS

## Database
- MySQL

## DevOps & Tools
- Git & GitHub
- Jenkins
- Docker
- AWS
- Datadog

---

# Project Structure

```bash
lendperfect-banking-app/
│
├── src/main/java/com/lendperfect
│   ├── controller
│   ├── service
│   ├── repository
│   ├── entity
│   ├── dto
│   └── config
│
├── src/main/resources
│   └── application.properties
│
├── pom.xml
└── README.md
```

---

# pom.xml

```xml
<project xmlns="http://maven.apache.org/POM/4.0.0">
    <modelVersion>4.0.0</modelVersion>

    <groupId>com.lendperfect</groupId>
    <artifactId>lendperfect-banking-app</artifactId>
    <version>1.0.0</version>

    <dependencies>

        <dependency>
            <groupId>org.springframework.boot</groupId>
            <artifactId>spring-boot-starter-web</artifactId>
        </dependency>

        <dependency>
            <groupId>org.springframework.boot</groupId>
            <artifactId>spring-boot-starter-data-jpa</artifactId>
        </dependency>

        <dependency>
            <groupId>org.springframework.boot</groupId>
            <artifactId>spring-boot-starter-security</artifactId>
        </dependency>

        <dependency>
            <groupId>mysql</groupId>
            <artifactId>mysql-connector-java</artifactId>
        </dependency>

    </dependencies>
</project>
```

---

# application.properties

```properties
server.port=8080

spring.datasource.url=jdbc:mysql://localhost:3306/lendperfect
spring.datasource.username=root
spring.datasource.password=root

spring.jpa.hibernate.ddl-auto=update
spring.jpa.show-sql=true
```

---

# Customer Entity

```java
package com.lendperfect.entity;

import jakarta.persistence.*;

@Entity
public class Customer {

    @Id
    @GeneratedValue(strategy = GenerationType.IDENTITY)
    private Long id;

    private String name;
    private String email;
    private String accountNumber;
    private Double balance;

    public Long getId() {
        return id;
    }

    public void setId(Long id) {
        this.id = id;
    }

    public String getName() {
        return name;
    }

    public void setName(String name) {
        this.name = name;
    }

    public String getEmail() {
        return email;
    }

    public void setEmail(String email) {
        this.email = email;
    }

    public String getAccountNumber() {
        return accountNumber;
    }

    public void setAccountNumber(String accountNumber) {
        this.accountNumber = accountNumber;
    }

    public Double getBalance() {
        return balance;
    }

    public void setBalance(Double balance) {
        this.balance = balance;
    }
}
```

---

# Repository Layer

```java
package com.lendperfect.repository;

import com.lendperfect.entity.Customer;
import org.springframework.data.jpa.repository.JpaRepository;

public interface CustomerRepository extends JpaRepository<Customer, Long> {
}
```

---

# Service Layer

```java
package com.lendperfect.service;

import com.lendperfect.entity.Customer;
import com.lendperfect.repository.CustomerRepository;
import org.springframework.beans.factory.annotation.Autowired;
import org.springframework.stereotype.Service;

import java.util.List;

@Service
public class CustomerService {

    @Autowired
    private CustomerRepository repository;

    public Customer saveCustomer(Customer customer) {
        return repository.save(customer);
    }

    public List<Customer> getAllCustomers() {
        return repository.findAll();
    }
}
```

---

# Controller Layer

```java
package com.lendperfect.controller;

import com.lendperfect.entity.Customer;
import com.lendperfect.service.CustomerService;
import org.springframework.beans.factory.annotation.Autowired;
import org.springframework.web.bind.annotation.*;

import java.util.List;

@RestController
@RequestMapping("/customers")
public class CustomerController {

    @Autowired
    private CustomerService service;

    @PostMapping
    public Customer saveCustomer(@RequestBody Customer customer) {
        return service.saveCustomer(customer);
    }

    @GetMapping
    public List<Customer> getAllCustomers() {
        return service.getAllCustomers();
    }
}
```

---

# Main Application

```java
package com.lendperfect;

import org.springframework.boot.SpringApplication;
import org.springframework.boot.autoconfigure.SpringBootApplication;

@SpringBootApplication
public class LendPerfectApplication {

    public static void main(String[] args) {
        SpringApplication.run(LendPerfectApplication.class, args);
    }
}
```

---

# API Endpoints

## Create Customer
```http
POST /customers
```

Request Body:

```json
{
  "name": "Dusmanta",
  "email": "dusmanta@gmail.com",
  "accountNumber": "ACC1001",
  "balance": 50000
}
```

---

## Get All Customers
```http
GET /customers
```

---

# Features
- Customer Management
- Loan Processing
- Transaction Handling
- REST APIs
- Secure Authentication
- Database Integration
- Microservices Ready
- Cloud Deployment Support

---

# Git Commands

```bash
git init
git add .
git commit -m "Initial commit"
git branch -M main
git remote add origin https://github.com/yourusername/lendperfect-banking-app.git
git push -u origin main
```

---

# Short GitHub Description

"LendPerfect Banking App is a Spring Boot microservices-based banking and loan management system with secure REST APIs, customer management, transaction processing, and cloud-ready deployment support."

