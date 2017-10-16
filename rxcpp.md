### rxcpp

https://github.com/Reactive-Extensions/RxCpp

+++

The Reactive Extensions for C++ (**RxCpp**) is a header-only library of algorithms for values-distributed-in-time.

+++

Essentially it is a combination of the best ideas from
the **Observer** pattern, the **Iterator** pattern, and functional programming.

+++

|       | Single item                | Multiple items           |
|-------|----------------------------|--------------------------|
| Sync  | `T getData()`              | `iterator<T> getData()`  |
| Async | `std::future<T>  getData()`| `observable<T> getData()`|

+++

![](http://reactivex.io/rxjs/manual/asset/marble-diagram-anatomy.svg)

more [interactive diagrams](http://rxmarbles.com/)
