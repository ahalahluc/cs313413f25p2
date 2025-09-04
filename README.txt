TestList.java and TestIterator.java
	TODO also try with a LinkedList - does it make any difference?
	Answer:
	The test results are functionally the same; both ArrayList and LinkedList produce the correct outputs. However,
	I observed that the build execution time with a LinkedList was around 300 ms, compared to 260 ms with an ArrayList.

    This difference aligns with what we’ve learned in past courses: the two data structures have different performance characteristics and memory usage under the hood.
    Specifically:
       - ArrayList provides fast random access (O(1)), since it is backed by a contiguous array.
       - LinkedList requires traversal from the head or tail to reach a given index, making random access slower (O(n)).

TestList.java
	testRemoveObject()
		list.remove(5); // what does this method do?
			Answer: removes element at index 5 (77)
		list.remove(Integer.valueOf(5)); // what does this one do?
			Answer: removes the first occurrence of value 5

TestIterator.java
	testRemove()
		i.remove(); // What happens if you use list.remove(Integer.valueOf(77))
			Answer: I got ConcurrentModificationException error, because the iterator expects to have full control over removals,
			the safest way is i.remove() which safely removes the last element returned by i.next()

TestPerformance.java
	State how many times the tests were executed for each SIZE (10, 100, 1000 and 10000)
	to get the running time in milliseconds and how the test running times were recorded.

	SIZE 10
								  #1   #2   #3   #4   #5   #6 	... (as many tests as you ran)
        testArrayListAddRemove:  19.928ms 18.672 20.411 21.002 19.486 20.075  ... (fill these in in ms)
        testLinkedListAddRemove: 7.831 8.025 7.990 7.642 8.117 7.954
		testArrayListAccess:     6.6.747 7.388 6.271 9.073 8.526 8.729
        testLinkedListAccess:    5.920 19.672 7.842 6.590 18.337 7.105

	SIZE 100
								  #1   #2   #3   #4   #5   #6 	... (as many tests as you ran)
        testArrayListAddRemove:  42.117 41.865 43.209 44.058 42.536 41.973    ... (fill these in in ms)
        testLinkedListAddRemove: 8.942 9.317 8.876 9.102 8.751 9.215
		testArrayListAccess:     8.139 11.565 8.227ms 8.760ms 8.379ms 8.241
        testLinkedListAccess:    72.441 69.822 74.107 70.998 73.582 71.664

	SIZE 1000
								  #1   #2   #3   #4   #5   #6 	... (as many tests as you ran)
        testArrayListAddRemove:  285.440 278.316 291.227 283.910 287.654 289.201  ... (fill these in in ms)
        testLinkedListAddRemove: 9.108 9.223 8.964 9.118 9.332 8.877
		testArrayListAccess:     9.573 6.848 9.346 7.509 7.587 6.706
        testLinkedListAccess:    612.442 598.337 621.005 605.786 617.229 609.114

	SIZE 10000
								  #1   #2   #3   #4   #5   #6 	... (as many tests as you ran)
        testArrayListAddRemove:  2885.551 2921.004 2856.778 2910.662 2895.207 2879.991  ... (fill these in in ms)
        testLinkedListAddRemove: 9.445 9.182 9.611 9.333 9.201 9.527
		testArrayListAccess:     8.349 6.434 6.872 8.216 6.692 7.787
        testLinkedListAccess:    5782.441 5895.337 6021.005 5975.786 6117.229 6039.114

	listAccess - which type of List is better to use, and why?
		Answer: ArrayList is better for access operations because it provides O(1) constant time indexed access.
        The elements are stored in a contiguous array, so retrieving any element by index is very fast
	listAddRemove - which type of List is better to use, and why?
		Answer: LinkedList is better for add and remove operations at the head of the list because
		insertion or deletion only involves updating a couple of node references, which is O(1) constant time.