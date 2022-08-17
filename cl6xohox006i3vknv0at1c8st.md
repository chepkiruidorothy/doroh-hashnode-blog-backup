## Django ORM in a nutshell

Python's Django framework, would not be complete if it did not include a way to interact with databases. The feature that makes it more powerful is its ORM. 

**What is ORM**

ORM (Object-Relational Mapping) is a technique that uses an object-oriented paradigm to query and manipulate data from a database. Django has used this technique to create its own Object Relational Mapper, also known as Django ORM. It is used to query and retrieve data from various relational databases, such as SQLite, PostgreSQL, and MySQL. Simply put, Django ORM is a database-abstraction API that lets you create, retrieve, update and delete objects. The ORM automates this transmission, so the developer does not need to write any SQL. This speeds up and eliminates errors throughout the development process.  

Django ORM provides an alternative to writing the good old Structured Query Language (SQL). Let's create a simple bank account database to better understand how to query data using Django ORM.  Bank has a customer, while the customer has one or many accounts.  It has two models, Customer and Account.                                                                                                                                                                                                                                                    The Customer model has a user field, while the Account model has four fields; name, balance, customer and timestamp. The customer model has used Django's built-in User model. This tutorial will not go into detail about the User model. To better understand how the User model works, check [User](https://docs.djangoproject.com/en/4.0/topics/auth/default/#user-objects). 
 
Create a *models.py*:

                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                     
```
from django.db import models
from django.contrib.auth.models import User

# Create your models here.


class Customer(models.Model):
    user=models.OneToOneField(User, on_delete=models.CASCADE)

    def __str__(self):
        return self.user.username


class Account(models.Model):
    name = models.CharField(max_length=30, unique=True, default='')
    balance=models.DecimalField( max_digits=12, decimal_places=2)
    customer=models.ForeignKey(Customer, on_delete=models.CASCADE)
    timestamp = models.DateTimeField(auto_now_add = True)

    def __str__(self):
        return self.name

``` 



Django Field types used are:

- ****OneToOneField**** - is used to define a one-to-one relationship, whereby one record in one table corresponds to one and only one record in another table. Here, Customer has a One-To-One relationship with the existing User model.


- ***CharField***- A field where text-based data can be stored. In the Accounts model, the name of the account should have a maximum length of 30 and be unique.

- ***DecimalField*** - It is a fixed-precision decimal number represented by a Decimal object in Python.
Accounts balance has a maximum digit of twelve with two decimal points.

- ***DateTimeField*** -  A field to store date and time,  represented in Python by a *datetime.datetime* instance. *auto_now_add* means that when the object is first created, the field is automatically set to that time.

- ***ForeignKey* **-  It is used to define a *many-to-one* relationship. A customer can have many accounts, but one account cannot be held by more than one customer. *on_delete=models.CASCADE* tells Django that when the referenced item is deleted, all objects with references to it are also deleted. In this case, when a customer is deleted, Django deletes their accounts as well.

After creating a sample database above, run migrations. Migrations are Django’s way of propagating changes you make to your models (adding a field, deleting a model, etc.) into your database schema. 

```
python manage.py migrate
``` 


![Screenshot from 2022-08-05 13-59-47.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1659697214924/wnk-cRwr8.png align="left")

Django shell provides easy access to ORM, allowing you to easily interact with the database. To access the shell, run the following command from the main directory of your Django project.

```
python manage.py shell
``` 

![Screenshot from 2022-08-05 14-01-25.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1659697331308/m4nEmRsd2.png align="left")

Import all models to the interactive console you have just created.
 
```
>>> from bank.models import *
>>> from django.contrib.auth.models import User


``` 
This imports Customer, Accounts and User models.

**Create objects**

  Django employs an easy-to-use mechanism to express database-table data in Python objects: A model class represents a database table, while a model instance in that class represents a specific entry in the database table.
To create an object, use **create()** method which takes keyword arguments. Here, *first_name*, *last_name* and *username* are keyword arguments. Then use the **save()** method to save it in the database.

To create a new user:
```
 d=User.objects.create(first_name='tom',last_name='holland', username='holland')
d.save()

e = User.objects.create(first_name= 'jake', last_name= 'candy', username= 'candy')
e.save()

```
To check that the user objects have been saved: 

```
 User.objects.all()
```

The **all()**method returns a QuerySet of all the objects in the database.
This will return all the user objects created.


![Screenshot from 2022-08-15 12-39-51.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1660556476393/PGNGBRsfk.png align="left")
 
You have created user objects. To create customer objects,  pass the “parent” object as this object’s primary key:

```
cust1 = Customer(user=d)
cust1.save()

cust2 = Customer(user=e)
cust2.save() 

```
To check saved customers, 

```
Customer.objects.all()
```
This gives the list of all the customers that you have created.
![Screenshot from 2022-08-15 12-48-53.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1660556941383/siivExVR5.png align="left")

**Read objects**

To retrieve objects from the database, use **get()** or **filter()** method.

```
d=User.objects.get(username='richie')

``` 
**get()** is used to return a required object. If the item doesn't exist or if there are multiple items that meet your criteria, it throws an error.

  **filter()** returns a queryset object if more than one object matches your query.  If no matching items were found, it returns an empty Queryset without throwing an error. 

Let's say you had users who shared the same first name, Jane.

```
a= User.objects.filter(first_name='jane')

``` 
The result will be a Queryset will all users whose first name is jane.


**Update objects **

You can make changes to a user's data and update them on the database by using **save()** method. If you wanted to change *cust1* username from richie to richard and update the changes:

```
d=User.objects.get(username='richie')
d.username='richard'
d.save()

cust1=Customer.objects.get(user=d)
cust1.save()

``` 
**Delete objects**

Django auto-generates a primary key called *id* by default if you did not specify one. The customer objects can be accessed by using *id*. 

```
b=Customer.objects.get(id=2)

``` 
The output is the corresponding Customer object. 
To delete the above Customer object:
```
b=Customer.objects.get(id=2).delete()

```

![Screenshot from 2022-08-17 11-23-06.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1660724620612/L8EjaY0L_.png align="left")

The changes made in Django shell are available in the Django admin interface.
The following images show users and customers respectively.

![Screenshot from 2022-08-17 16-22-21.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1660743563935/8o_aX1EhO.png align="left")


![Screenshot from 2022-08-17 16-22-27.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1660743575796/k6d7tUlTf.png align="left")

**Conclusion**

You have learned how to create, update, read and delete data in Django using its ORM. This sums up the basic functionalities to get you started querying databases. Happy coding.
 
