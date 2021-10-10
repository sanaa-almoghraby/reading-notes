# Spring RequestMapping
1. Overview
In this tutorial, we'll focus on one of the main annotations in Spring MVC: @RequestMapping.

Simply put, the annotation is used to map web requests to Spring Controller methods.

2. @RequestMapping Basics
 2.1. @RequestMapping — by Path
 2.2. @RequestMapping — the HTTP Method
3. RequestMapping and HTTP Headers
 3.1. @RequestMapping With the headers Attribute
 3.2. @RequestMapping Consumes and Produces
 Starting with Spring 3.1, the @RequestMapping annotation now has the produces and consumes attributes, specifically for this purpose:

@RequestMapping(
  value = "/ex/foos", 
  method = RequestMethod.GET, 
  produces = "application/json"
)
@ResponseBody
public String getFoosAsJsonFromREST() {
    return "Get some Foos with Header New";
}
4. RequestMapping With Path Variables
Parts of the mapping URI can be bound to variables via the @PathVariable annotation.

 4.1. Single @PathVariable
 4.2. Multiple @PathVariable
 4.3. @PathVariable With Regex
5. RequestMapping With Request Parameters
6. RequestMapping Corner Cases
 6.1. @RequestMapping — Multiple Paths Mapped to the Same Controller Method
 6.2. @RequestMapping — Multiple HTTP Request Methods to the Same Controller Method
 6.3. @RequestMapping — a Fallback for All Requests
 6.4. Ambiguous Mapping Error
 7. New Request Mapping Shortcuts
Spring Framework 4.3 introduced a few new HTTP mapping annotations, all based on @RequestMapping:

* @GetMapping
* @PostMapping
* @PutMapping
* @DeleteMapping
* @PatchMapping
8. Spring Configuration
The Spring MVC Configuration is simple enough, considering that our FooController is defined in the following package:

package org.baeldung.spring.web.controller;

@Controller
public class FooController { ... }

# Accessing Data with JPA
This guide walks you through the process of building an application that uses Spring Data JPA to store and retrieve data in a relational database.

### Starting with Spring Initializr
You can use this pre-initialized project and click Generate to download a ZIP file. This project is configured to fit the examples in this tutorial.

To manually initialize the project:

Navigate to https://start.spring.io. This service pulls in all the dependencies you need for an application and does most of the setup for you.

Choose either Gradle or Maven and the language you want to use. This guide assumes that you chose Java.

Click Dependencies and select Spring Data JPA and then H2 Database.

Click Generate.

Download the resulting ZIP file, which is an archive of a web application that is configured with your choices.

Define a Simple Entity
In this example, you store Customer objects, each annotated as a JPA entity. The following listing shows the Customer class (in src/main/java/com/example/accessingdatajpa/Customer.java):

package com.example.accessingdatajpa;

import javax.persistence.Entity;
import javax.persistence.GeneratedValue;
import javax.persistence.GenerationType;
import javax.persistence.Id;

@Entity
public class Customer {

  @Id
  @GeneratedValue(strategy=GenerationType.AUTO)
  private Long id;
  private String firstName;
  private String lastName;

  protected Customer() {}

  public Customer(String firstName, String lastName) {
    this.firstName = firstName;
    this.lastName = lastName;
  }

  @Override
  public String toString() {
    return String.format(
        "Customer[id=%d, firstName='%s', lastName='%s']",
        id, firstName, lastName);
  }

  public Long getId() {
    return id;
  }

  public String getFirstName() {
    return firstName;
  }

  public String getLastName() {
    return lastName;
  }
}COPY
Here you have a Customer class with three attributes: id, firstName, and lastName. You also have two constructors. The default constructor exists only for the sake of JPA. You do not use it directly, so it is designated as protected. The other constructor is the one you use to create instances of Customer to be saved to the database.

The Customer class is annotated with @Entity, indicating that it is a JPA entity. (Because no @Table annotation exists, it is assumed that this entity is mapped to a table named Customer.)

The Customer object’s id property is annotated with @Id so that JPA recognizes it as the object’s ID. The id property is also annotated with @GeneratedValue to indicate that the ID should be generated automatically.

The other two properties, firstName and lastName, are left unannotated. It is assumed that they are mapped to columns that share the same names as the properties themselves.

The convenient toString() method print outs the customer’s properties.

## CrudRepository, JpaRepository, and PagingAndSortingRepository in Spring Data

 2. Spring Data Repositories
Let's start with the JpaRepository – which extends PagingAndSortingRepository and, in turn, the CrudRepository.

Each of these defines its own functionality:

CrudRepository provides CRUD functions
PagingAndSortingRepository provides methods to do pagination and sort records
JpaRepository provides JPA related methods such as flushing the persistence context and delete records in a batch
3. CrudRepository
Notice the typical CRUD functionality:

save(…) – save an Iterable of entities. Here, we can pass multiple objects to save them in a batch
findOne(…) – get a single entity based on passed primary key value
findAll() – get an Iterable of all available entities in database
count() – return the count of total entities in a table
delete(…) – delete an entity based on the passed object
exists(…) – verify if an entity exists based on the passed primary key value
This interface looks quite generic and simple, but actually, it provides all basic query abstractions needed in an application.

4. PagingAndSortingRepository
5. JpaRepository
6. Downsides of Spring Data Repositories


