---
layout: post
title: Trick for filtering by array size in MongoDb
date: '2016-09-15T08:00:00.000+02:00'
tags: mongodb
---

If you have a document structure with array in it, for example:
```
{
	"arr":[1, 2, 3]
}
```

and you want to filter for document with arr array size bigger than x, you can use:
```
db.collectionName.find({"arr.x" : {"$exists": true}})
```

you need to substitute x, with the number you want. Logic is that mongo gives you access to array members by index, that is 0 based, so if X position exists, then array is of at least X+1 size.
