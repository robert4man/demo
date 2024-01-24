# OGA admin app

# Description

This page serves as general documentation for the oga admin application 

  

# Component

1.  Angular 6 frontend
2.  NodeJS backend
3.  ou_oga schedma on people soft database 

  

# Features 

1.  Hierarchy management 
    1.  List all users 
    2.  Remove user 
    3.  Add an user 
    4.  Search for an user (This has been implemented on front end)

  

# Implementation nodes 

## 1.a Hierarchy List all users 

Please follow the steps below to accomplish this task 

1.  Step up nodeJS application 
2.  Create a domain object point to the table that stores Hierarchy
    information in ou_oga schema (Use lcomm-resource as example to learn
    MVC architecture, db and logics are always in services)
3.  Expose an endpoint (get) to return all hierarchy data in format of
    json 
4.  Step up angular application
5.  From angular side, make a rest call to the backend to retrieve the
    hierarchy data 
6.  Display the hierarchy data on the view 

Resources you may need or learn, make sure all terms make sense to you
because you will need them. 

Bookshelf ORM

Http methods 

Angular Observable

  

## 1.b Remve user

To be added...

  

  

  

  
