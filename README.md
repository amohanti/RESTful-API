# RESTful-API
Design/Specification for Customer REST API
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
