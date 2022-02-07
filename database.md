In computing, a [database](https://en.wikipedia.org/wiki/Database) is an organized collection of data stored and accessed electronically. 
Small databases can be stored on a file system, while large databases are hosted on computer clusters or cloud storage.

```
from django.db import models

class Publication(models.Model):
    title = models.CharField(max_length=30)

    class Meta:
        ordering = ['title']

    def __str__(self):
        return self.title

class Article(models.Model):
    headline = models.CharField(max_length=100)
    publications = models.ManyToManyField(Publication)

    class Meta:
        ordering = ['headline']

    def __str__(self):
        return self.headline
```
Create a few Publications:

```
>>> p1 = Publication(title='The Python Journal')
>>> p1.save()
>>> p2 = Publication(title='Science News')
>>> p2.save()
>>> p3 = Publication(title='Science Weekly')
>>> p3.save()
```
Create an Article:

```
>>> a1 = Article(headline='Django lets you build web apps easily')
>>> a1.save()
>>> a1.publications.add(p1)

```


Terminology:

**PIVOT** relational operator converts data from row level to column level. PIVOT rotates a table-valued expression by turning the unique
values from one column in the expression into multiple columns in the output. Using PIVOT operator, we can perform aggregate operation 
where we need them.

**Aggregation** operators perform mathematical operations like Average, Aggregate, Count, Max, Min and Sum, on the numeric property of the 
elements in the collection.

Reference:
- [Hands-on Database: An Introduction to Database Design and Development]()
- [A Practical Guide to Database Design]()
