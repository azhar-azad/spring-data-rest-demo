# Spring-Data-REST-demo

A simple Spring Boot project that uses Spring-Data-JPA and Spring-Data-REST to implement simple CRUD functionalities.

## Insights on Spring-Data-REST

* Adding spring-data-rest dependency to POM.xml file will give you a REST CRUD implementation for FREE..
* Helps to minimize boiler-plate REST code!!
* No new coding required.

## Advanced Features

* Pagination, sorting and searching.
* Extending and adding custom queries with JPQL.
* Query Domain Specific Language (Query DSL).

### Spring-Data-REST will expose the following endpoints for free!

* POST: /entityNames | Create a new Entity
* GET: /entityNames | Read a list of Entities
* GET: /entityNames/{entityId} | Read a single Entity
* PUT: /entityNames/{entityId} | Update an existing Entity
* DELETE: /entityNames/{entityId} | Delete an existing Entity

### Spring-Data-REST: How does it work?

* Spring Data REST will scan your property for JpaRepository.
* Expose REST APIs for each entity type for your JpaRepository.
* By default, Spring Data REST will create endpoints based on entity type.
* Endpoint path is added as "Simple Pluralized Form".
* For example, if the entity name is "Employee" then to GET all the employee records REST will use "/employees" as path. 

# HATEOAS

* HATEOAS: Hypermedia as the Engine of Application State.
* Spring Data REST endpoints are HATEOAS compliant.
* Hypermedia-driven sites provide information to access REST interface. 
* Think of it as meta-data for REST data. 

## HATEOAS example

* Spring Data REST response using HATEOAS.
* REST(json) response from: GET /employees/3

{

    "firstName": "John",
    "lastName": "Doe",
    "email": "j.doe@something.com",
    "_links": {
        "self": {
            "href": "http://localhost:8080/employees/3"
        },
        "employee": {
            "href": "http://localhost:8080/employees/3"
        }
    }
    
}

* For a collection, meta-data includes page size, total elements, pages etc.
* REST(json) response from: GET /employees

{

    "_embedded": {
        "employee": [
            {
                "firstName": "John1",
                "lastName": "Doe1",
                "email": "j.doe1@something.com"
            },
            {
                "firstName": "John2",
                "lastName": "Doe2",
                "email": "j.doe2@something.com"
            },
            ...
        ]
    },
    "page": {
        "size": 20, 
        "totalElements": 5,
        "totalPages": 1,
        "number": 0
    }

}

* HATEOAS uses Hypertext Application Language (HAL) data format.