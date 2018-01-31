---
layout: post
title: TDD meets Maven
---
Recently I went to a TDD course with the amazing [Sandro Mancuso](https://twitter.com/sandromancuso). One of the things I really like was convention of naming the test classes following the schema XXXShould. This makes for really nice flowing English sentences: XXX should react like this, if this is met.

Enter maven, a little bit archaic, it only supports a certain schema for naming test classes. They need either to start or end with 'Test'. All test classes not named like that, are simply skipped by maven SureFire plugin. Of course this can be overridden by configuration, but as a colleague pointed out, this breaks the convention, and is easy to forget about it, resulting in tests simply not executed.

A little bit of thinking later got me the idea, the new naming schema:

TestThatXXXShould

It has following advantages:
* It starts with test, so SureFire will execute it.
* It ends with magic word Should, so it lends nicely to TDD style.
* And it sounds really nice as English sentence.
