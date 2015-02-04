---
layout: post
title: Comparision between Spring (@Component and @Autowired) and java (@Named and @Inject)
date: '2015-02-04T20:00:00.000+02:00'
tags: dependency-injection
---
So I found this [awesome article](http://blogs.sourceallies.com/2011/08/spring-injection-with-resource-and-autowired/#more-2350) that lists all combinations of usage of dependency injection provided by Spring and Java CDI.

Personally I preffer use CDI annotations when writing libraries that will be used by other, because:
* I don't decide what DI framework will be choosen by end user
* I don't get heavy with Spring dependencies
* I can express DI dependencies in my code enough with usage of Java CDI.
