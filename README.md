# RESTful-API
Design/Specification for Customers REST API
Resource: Customers
Methods: Get a single/all customers (GET)
         Create a new customer (POST)
         Update a customer (PATCH)
         Delete a customer (DELETE)
Attributes: First Name, Last Name, Address
Relationships: Products, Orders
Use Cases: Periodic 5 minute consumption of API and consumer maintains a copy of all customers obtained from provider
           Mobile App uses API to retrieve and update customer details
           Simple Extension of API to support future resources such as Products and Orders

#%RAML 1.0
---
title: Customers API
baseUri: http://api.customers.com/{version}
version: v1
/Customers:
 get:
  description: Retrieve single, multiple or all customers based on query parameters
  queryParameters:
   id:
    displayName: ID
    type: number
    description: unique customer ID
    example: 1001
    required: false
   firstName:
    displayName: First Name
    type: String
    description: Customer's first name
    example: Mary
    required: false
   lastName:
    displayName: Last Name
    type: String
    description: Customer's last name
    example: Deakins
    required: false
  responses:
   200:
    body:
     application/json:
      example:
       {
        "data": {
         "id": "1001",
         "firstName": Mary,
         "lastName": Deakins,
         "address": 10 Garigal Road, Kellyville,
         "link": "http://api.customers.com/v1/Customers?firstName=Mary,
        },
        "success": true,
        "status": 200
       }
   404:
    body:
     application/json:
      example:
       {
        "data": {
         "description": "Customer(s) not found",
         "link": "http://api.customers.com/v1/Customers?firstName=X12TR,
        },
        "success": false,
        "status": 404
       }
/Customers:
 /{id}
  get:
   description: Retrieve specific customer as per provided Customer ID
  responses:
   200:
    body:
     application/json:
      example:
       {
        "data": {
         "id": "1001",
         "firstName": Mary,
         "lastName": Deakins,
         "address": 10 Garigal Road, Kellyville,
         "link": "http://api.customers.com/v1/Customers/1001,
        },
        "success": true,
        "status": 200
       }
   404:
    body:
     application/json:
      example:
       {
        "data": {
         "description": "Customer(s) not found",
         "link": "http://api.customers.com/v1/Customers/11,
        },
        "success": false,
        "status": 404
       }
 post:
 patch:
 delete:
/Products:
/Orders:
