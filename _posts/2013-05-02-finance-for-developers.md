---
layout: post
category : projects
tagline: 
tags : [OSFramework, project, financial, market, standard, conventions, algorithms]
---
{% include JB/setup %}

Yesterday, Arthur Charpentier ([@freakonometrics](https://twitter.com/#!/freakonometrics)) posted a brief
but noteworthy article on DZone - [Financial Model Complexity](http://architects.dzone.com/articles/financial-model-complexity).
The most significant point in the article is where he comments

> ...we started to discuss about financial model complexity, mentioning that
> sometimes, traders and quants are lost, and it might be good to spend more
> time on basics than on very advanced stuff

The world of finance is dominated by complex products with multiple moving parts, involving an array of
algorithms to calculate risk, term, present value, future value, etc. If traders and quantitative analysts
get lost in their *own* conventions and math, how can software developers (who don't come from a financial
background) be expected to produce the tools and systems they depend upon? Where do we learn how to do all
this stuff?

## Finance, OSS-style

Every day, the open source community produces an abundance of technology information, thought, and code
for free to the world. I believe evidence indicates that financial math and "standard market conventions"
deserve the same level of focus and attention, from the same community. I can't think of a realm more wanting
of the OSS community's knowledge cycle:

**Discover problem -> Prototype -> Publish findings -> Discuss -> Collaborate -> Share -> Adopt -> Next!**

A few contributors have already given us some great and useful projects in this area. Examples include:

* [QuantLib](http://quantlib.org/) *(C++)*
* [jFin](http://jfin.org/) *(Java)*

In addition to the projects above, which are intended for direct inclusion in larger application codebases, we
need projects which slightly shift the focus. Taking on a single financial calculation problem, each project
will:

1. Provide documentation and examples to educate developers
2. Provide well-commented source to help developers understand implemented algorithms

## First steps

As a starting point for this path, I started the [Contract Date](http://github.com/osframework/contract-date)
project. The project is intended to teach developers the logic involved in calculating the various dates required
by derivative contract products. It is in progress, and contributors are welcome.

What financial calculation problem are you interested in? Let's start a project for it!
