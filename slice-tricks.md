# Slice is not just a dynamic array

Go's slice is a clever design. It has a look-and-feel of dynamic arrays in most other languages, but the inner working is quite different (Believe me, this confused me as well). 

Slice is designed with three goals:
1. make it behave like a dynamic arrays for memory allocation in most other languages.
2. it provides a view on an array. In most cases, only slices are passed around, unnecessary array copy is thus avoided.
3. By definition, it's a struct with a pointer, length and capacity on top of arrays. It prevents insecure array manipulation like C arrays.

## Slice Creation
**make()** creates a slice and its underlying array. 
```
func make([]T, len, cap) []T
```

A slice can also be created by "slicing" the current array or slice.
```
x := [6]byte{'g', 'o', 'l', 'a', 'n', 'g'}
y := x[:]
```

## Append and bytes.Split()
**bytess.Split()** takes a slice and a separator, splits the slice by the separator, and returns a slice of byte slices. The operation is in-place. This may come unexpected as in other languages, split usually relies on allocate-and-copy semantics at the expense of efficiency at runtime. 

**append()** adds new elements to the end of a slice, thus expanding the slice. The behavior differs in terms of the capacity (the size of the underlying array of the slice counting from the first element in the slice) and length after the append operation.
* ​if the length is smaller than the capacity, the element is appended to the end of the slice and write to existing array.
* if the length is larger than the capacity, a new array is created and the slice is pointed to the new one.