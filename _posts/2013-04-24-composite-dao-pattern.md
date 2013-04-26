---
layout: post
category : patterns
tagline: "Abstracting multiple data sources"
tags : [composite, dao, design, pattern, project]
---
{% include JB/setup %}

Let's talk about what a Composite DAO is and why you would consider creating one. I introduce the
pattern, and then I provide a common example where it is a valuable tool. For a demonstration, you
can fork my demo [composite-dao](http://github.com/davejoyce/composite-dao) project.

## Introduction 

### What is Composite DAO?

Composite DAO is an object oriented design pattern. Actually, it is a combination of two design
patterns:

* [Composite pattern](http://www.oodesign.com/composite-pattern.html)
* [Data Access Object pattern](http://en.wikipedia.org/wiki/Data_access_object)

As most JEE and .NET developers are aware, DAO objects perform the platform-specific logic required
to read, write, and delete persistent domain model object state. The DAO interface is typically
associated with a single domain model or entity class. Each implementation of the DAO interface is
then specific to a particular persistence platform. So, given a `Person` domain model class, the
basic design would look something like

![DAO class diagram](http://davejoyce.github.io/images/Class-Dao.png)
 
The Composite DAO pattern is an extension of the Data Access Object pattern, where the composite
object is an implementation of the same DAO interface implemented by the objects of which it is
composed. Employing this pattern, one can assemble nested structures of DAO objects, each of which
may:

1. Encapsulate logic for a specific persistence mechanism (RDBMS, file, directory service, etc.)
2. Be a composite DAO itself!

![Composite DAO class diagram](http://davejoyce.github.io/images/Class-CompositeDao.png)

To better understand the value of this pattern, let's talk through some examples where it is
beneficial.

### Example: Local vs Remote 

In this scenario, the *System of Record* is remote to the application. It may be a mainframe records
system, a centralized data warehouse, or some black box-type system exposing a web service interface.
Regardless, the platform is remote and therefore 'expensive' to connect and interact with. Persistent
operations on `Person` objects in this system are all done inside a `RemoteSystemPersonDAO` object.

To mitigate the expense of going back and forth to the remote system, the application uses a local
database which acts as the *System of Reference*. "Local" may mean the database physically resides on
the same server as the application, or it may simply mean the database is within the same network. The
main point is that the local database is 'cheap' to connect and interact with, relative to the expense
of the remote system of record. Persistent operations on `Person` objects in this system are all done
inside a `LocalDatabasePersonDAO` object. 

For a service-layer object in the application, there will have to be some chunky but possibly
boilerplate logic to determine which DAO object(s) to use for any given operation on a domain model
entity. What happens when the company moves to a new system of reference? What level of refactor would
that incur? What if yet another data storage system gets introduced... meaning another DAO
implementation? Yikes!

To simplify the service-to-DAO interaction, we can use the Composite DAO pattern. Here, we would have
a `PersonCompositeDAO` object that the service uses. It handles 2 things:

* Abstraction of the local and remote DAOs away from the service. The service now deals with 1 DAO.
* Moves the "which place do I go?" decision logic out of the service and into the DAO layer.

## Conclusion

I hope I have shown you the promise and value of the Composite DAO pattern. Again, if you'd like to
see a concrete example, check out the [composite-dao](http://github.com/davejoyce/composite-dao)
project. 
