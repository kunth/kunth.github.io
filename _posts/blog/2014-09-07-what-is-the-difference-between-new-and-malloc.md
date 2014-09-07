---
layout: post
title: What is the difference between new and malloc()?
description: c++
category: blog
---

I don't know how many times I had search for **the difference between new and malloc** on the Internet, and the former several times I may use the Baidu. I also got lots of different descriptions about what's the difference between new and malloc, I got an answer which may not be complete and I forgot it, then I search for it again and got another answer about it, until I found the question answered by Bjarne Stroustrup,in the **[link](http://www.stroustrup.com/bs_faq2.html#malloc)** as follows:

> malloc() is a function that takes a number (of bytes) as its argument; it returns a void* pointing to unitialized storage. new is an operator that takes a type and (optionally) a set of initializers for that type as its arguments; it returns a pointer to an (optionally) initialized object of its type. The difference is most obvious when you want to allocate an object of a user-defined type with non-trivial initialization semantics. Examples:

``` c++

class Circle : public Shape {
public:
Cicle(Point c, int r);
// no default constructor
// ...
};

class X {
public:
X(); // default constructor
// ...
};

void f(int n)
{
void* p1 = malloc(40);// allocate 40 (uninitialized) bytes

int* p2 = new int[10];// allocate 10 uninitialized ints
int* p3 = new int(10);// allocate 1 int initialized to 10
int* p4 = new int();// allocate 1 int initialized to 0
int* p4 = new int;// allocate 1 uninitialized int

Circle* pc1 = new Circle(Point(0,0),10); // allocate a Circle constructed
        // with the specified argument
Circle* pc2 = new Circle;// error no default constructor

X* px1 = new X;// allocate a default constructed X 
X* px2 = new X();// allocate a default constructed X 
X* px2 = new X[10];// allocate 10 default constructed Xs 
// ...
}
```

> Note that when you specify a initializer using the "(value)" notation, you get initialization with that value. Unfortunately, you cannot specify that for an array. Often, a vector is a better alternative to a free-store-allocated array (e.g., consider exception safety).
Whenever you use malloc() you must consider initialization and convertion of the return pointer to a proper type. You will also have to consider if you got the number of bytes right for your use. There is no performance difference between malloc() and new when you take initialization into account.

> malloc() reports memory exhaustion by returning 0. new reports allocation and initialization errors by throwing exceptions.

> Objects created by new are destroyed by delete. Areas of memory allocated by malloc() are deallocated by free().

I wonder why many people won't share this link to those guys who search for the difference between new and malloc, I suffered a lot from the questions answered in shabby Chinese.
