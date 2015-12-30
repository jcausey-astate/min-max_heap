## Min-Max Heap
Defines functions for maintaining a Min-Max Heap, as described by Adkinson:
<blockquote>
    M. D. Atkinson, J.-R. Sack, N. Santoro, and T. Strothotte. 1986.
    Min-max heaps and generalized priority queues.
    Commun. ACM 29, 10 (October 1986), 996-1000.
    DOI=http://dx.doi.org/10.1145/6617.6621
</blockquote>

The main advantage of the Min-Max Heap is the ability to access both the _minimum_ and _maximum_ values contained in the data structure in constant time.  The trade-off is a slight increase in the complexity constant coefficients with respect to traditional heaps.  The Min-Max heap still maintains the same _order_ of complexity as traditional heaps for all operations.

The heap functions defined in _`mmheap.h`_ are defined as _templates_, so a heap of any type that is _less-than comparable_ and _copy-constructable_ is possible.  The heap functions are designed to work in-place on top of a regular C++ array.

### Namespaces
The file _`mmheap.h`_ defines two namespaces: `mmheap` and `_mmheap`.  All of the functions necessary to use the min-max heap are exposed in the `mmheap` namespace.  It should not be necessary to use the `_mmheap` namespace (those functions are for internal use only).

### Function Reference
Full reference documentation is available in the _"docs"_ project directory.  Only the most commonly used functions are described here.

#### `mmheap:: make_heap()`
`template <typename DataType>`<br />
`void make_heap (DataType∗ heap_array, size_t size);`<br />
Creates the min-max heap from an arbitrary C++ array, given the array and its size as arguments.

#### `mmheap:: heap_insert()`
`template <typename DataType>`<br />
`void heap_insert (const DataType& value, DataType∗ heap_array, size_t& count, size_t max_size);`<br />
Inserts a new value into the heap, given the value, the heap array, the current number of items contained in the heap, and the maximum storage size of the array.  The `count` will be increased by one following the function call.

#### `mmheap:: heap_max()`
`template <typename DataType>`<br />
`DataType heap_max (DataType∗ heap_array, size_t count);`<br />
Returns the maximum value contained in the heap, given the heap array and the current number of items contained in the heap.

#### `mmheap:: heap_min()`
`template <typename DataType>`<br />
`DataType heap_min (DataType∗ heap_array, size_t count);`<br />
Returns the minimum value contained in the heap, given the heap array and the current number of items contained in the heap.

#### `mmheap:: heap_remove_max()`
`template <typename DataType>`<br />
`DataType heap_remove_max (DataType∗ heap_array, size_t& count);`<br />
Removes and returns the maximum value contained in the heap, given the heap array and the current number of items contained in the heap.  The `count` will be decreased by one following the function call.

#### `mmheap:: heap_remove_min()`
`template <typename DataType>`<br />
`DataType heap_remove_min (DataType∗ heap_array, size_t& count);`<br />
Removes and returns the minimum value contained in the heap, given the heap array and the current number of items contained in the heap.  The `count` will be decreased by one following the function call.

#### Additional Functions
The following functions are less likely to be commonly used, but are provided under the `mmheap` namespace as well; for more information, _read the documentation in the `docs` directory_.

```cpp
// add to heap, rotating the maximum value out 
// if the heap is full
template <typename DataType>
std::pair <bool, DataType> heap_insert_circular (
    const DataType& value, 
    DataType∗       heap_array, 
    size_t&         count,
    size_t          max_size);

// replace the value at a specific index in the heap array
// with a new value, and restore the heap property
template <typename DataType>
DataType heap_replace_at_index (
    const DataType& new_value, 
    size_t          index, 
    DataType∗       heap_array, 
    size_t          count);

// remove and return the value at a specified index in the
// heap array, and restore the heap property
template <typename DataType>
DataType heap_remove_at_index (
    size_t          index, 
    DataType∗       heap_array, 
    size_t&         count);
```

### License
This library is released under the MIT License: http://opensource.org/licenses/MIT
<pre>  
Copyright (c) 2015 Jason L Causey, Arkansas State University

Permission is hereby granted, free of charge, to any person obtaining a copy
of this software and associated documentation files (the "Software"), to deal
in the Software without restriction, including without limitation the rights
to use, copy, modify, merge, publish, distribute, sublicense, and/or sell
copies of the Software, and to permit persons to whom the Software is
furnished to do so, subject to the following conditions:
The above copyright notice and this permission notice shall be included in
all copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR
IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY,
FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT.  IN NO EVENT SHALL THE
AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER
LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM,
OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN
THE SOFTWARE.
</pre>

