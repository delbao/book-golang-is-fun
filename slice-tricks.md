At the first glance,

[https://www.reddit.com/r/golang/comments/84ahjo/confusion\_about\_append\_built\_in/](https://www.reddit.com/r/golang/comments/84ahjo/confusion_about_append_built_in/)  
[https://appliedgo.net/slices/](https://appliedgo.net/slices/)

* Write about view, pointer, length, capacity
* vs. dynamic array 
* append example
* split example

Go's slice is a clever design. It has a look-and-feel of dynamic arrays in most other languages, but the inner working is quite different \(Believe me, this confused me as well\). Here is a list of facts about slices

* By definition, it's a struct with a pointer, length and capacity on top of arrays
* a view on an array
* full control over memory allocation



