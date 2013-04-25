---
layout: post
category : projects
tagline: "Abstracting multiple data sources"
tags : [composite, dao, design, pattern]
---
{% include JB/setup %}

This introduction will outline what a Composite DAO is and why you would consider creating one.
Following the introduction, we'll walk through implementation considerations, as well as solutions
that may sometimes be an alternative to the Composite DAO pattern.

## Overview 

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

![Composite DAO class diagram](http://davejoyce.github.io/images/Class-CompositeDAO.png)
 
Simply stated, the Composite DAO pattern is an extension of the Data Access Object pattern, where
the composite object is itself an implementation of the same DAO interface implemented by the
objects of which it is composed. If that sounds a little circular, it's because that circularity
is intentional. To better understand the value of this pattern, let's talk through some examples
where it is beneficial.

#### Local vs Remote 

#### Fast vs Slow

## Implementation Considerations

## Alternatives

## Conclusion

I hope this paints a clearer picture of what Jekyll is doing and why it works the way it does.
As noted, our main programming constraint is the fact that our API is limited to what is accessible via Liquid and Liquid only.

Jekyll-bootstrap is intended to provide helper methods and strategies aimed at making it more intuitive and easier to work with Jekyll =)

**Thank you** for reading this far.
