---
title: Resource Aquisition is Initialisation - (RAII)
alias: RAII
---

# Definition

From <https://en.wikipedia.org/wiki/Resource_acquisition_is_initialization>,

**Resource acquisition is initialization (RAII)** is a programming idiom used in several object-oriented, statically-typed programming languages to describe a particular language behavior. In RAII, holding a resource is a class invariant, and is **tied to object lifetime**. Resource allocation (or acquisition) is done during object creation (specifically initialization), by the constructor, while resource deallocation (release) is done during object destruction (specifically finalization), by the destructor. In other words, resource acquisition must succeed for initialization to succeed. Thus the resource is guaranteed to be held between when initialization finishes and finalization starts (holding the resources is a class invariant), and to be held only when the object is alive. Thus if there are no object leaks, there are no resource leaks. 

---

From <https://en.cppreference.com/w/cpp/language/raii>

Resource Acquisition Is Initialization or RAII, is a C++ programming technique which binds the life cycle of a resource that must be acquired before use (allocated heap memory, thread of execution, open socket, open file, locked mutex, disk space, database connection—anything that exists in limited supply) to the lifetime of an object. 

RAII can be summarized as follows:

-   encapsulate each resource into a class, where
	-   the constructor acquires the resource and establishes all class invariants or throws an exception if that cannot be done,
	-   the destructor releases the resource and never throws exceptions;
-   always use the resource via an instance of a RAII-class that either
	-   has automatic storage duration or temporary lifetime itself, or
	-   has lifetime that is bounded by the lifetime of an automatic or temporary object

# Explanation

This implies that after resources are aquired, once an object goes out of scope the destructor is called and the resources are freed. 

In C++, any object initialised using `malloc` or  `new` , does not satisfy RAII. This is because the resources acquired are not associated with objects that have automatic storage duration or temporary lifetime.

Examples of RAII classes in C++ is vector, smart pointers and mutex's. 

RAII appears to be particulary important for multi-threading. 

# References

- <https://en.wikipedia.org/wiki/Resource_acquisition_is_initialization>
- <https://en.cppreference.com/w/cpp/language/raii>