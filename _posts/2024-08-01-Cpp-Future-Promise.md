---
layout: post
title: Future and Promise in C++ 
subtitle: C++
cover-img: /assets/img/path.jpg
thumbnail-img: /assets/img/thumb.png
share-img: /assets/img/path.jpg
tags: [programming, C++]
author: Bruce Wang
---

# Future and Promise in C++
## Future and Promise
The Future and Promise are two classes in C++ that are used to handle asynchronous operations. The Future class represents a value that will be available in the future, while the Promise class is used to set the value of the Future object. The Future and Promise classes are part of the C++11 standard library and are defined in the `<future>` header file. You can think of the Future and Promise classes as a channel through which two threads can communicate with each other. One thread sets the value of the Future object using the Promise object, while the other thread reads the value of the Future object. 

Here is a simple concept picture of how the Future and Promise classes work:

![image](/assets/img/cpp_future_promise.png)

## Exampple
```cpp
#include <iostream>
#include <future>

int main() {
    std::promise<int> p;
    std::future<int> f = p.get_future();

    std::thread t([&p](){
        p.set_value(42);
    });

    std::cout << "The answer is " << f.get() << std::endl;

    t.join();

    return 0;
}
```