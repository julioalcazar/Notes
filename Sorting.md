# Comparison Sort  
[Wikipedia Sorting algorithm](https://en.wikipedia.org/wiki/Sorting_algorithm)  
  
  
## Insertion Sort  
__Time Complexity:__ O(N^2)  
__Auxiliary Space:__ O(1)  
__Stable:__ Yes  
Insertion sort iterates, consuming one input element each repetition, and growing a sorted output list. Each iteration, insertion sort removes one element from the input data, finds the location it belongs within the sorted list, and inserts it there. It repeats until no input elements remain.  
Advantage  
*  Adaptive (It takes advantage of existing order in its input) O(n) time when nearly sorted  
*  Low overhead (When problem size is small)  
  
  
## Selection Sort
__Time Complexity:__ O(N^2)  
__Auxiliary Space:__ O(1)  
__Stable:__ No  
The algorithm divides the input list into two parts: the sublist of items already sorted, which is built up from left to right at the front (left) of the list, and the sublist of items remaining to be sorted that occupy the rest of the list. Initially, the sorted sublist is empty and the unsorted sublist is the entire input list. The algorithm proceeds by finding the smallest (or largest, depending on sorting order) element in the unsorted sublist, exchanging it with the leftmost unsorted element (putting it in sorted order), and moving the sublist boundaries one element to the right.  
Advantage  
*  It requires only n write operations.  
*  No need for extra memory.  
  
  
## Shell Sort  
__Time Complexity:__ O(N^3/2)  
__Auxiliary Space:__ O(1)  
__Stable:__ No  
Shell sort is based on insertion sort algorithm. This algorithm avoids large shifts as in case of insertion sort if smaller value is very far right and have to move to far left.  
Advantage  
*  Adaptive (It takes advantage of existing order in its input) O(N lg(N)) time when nearly sorted  
  
  
## Shuffle  
__Time Complexity:__ O(N)  
__Auxiliary Space:__ O(1)  
__Stable:__ No  
Rearrange array so that result is a uniformly random permutation.  
  
  
## Merge Sort  
__Time Complexity:__ O(N Log N)  
__Auxiliary Space:__ O(N)  
__Stable:__ Yes  
Recursive algorithms reduce large problems into smaller ones. A recursive approach to sorting involves partitioning the elements into two groups, sorting each of the smaller problems recursively, and then interleaving the two sorted lists to totally order the elements.  
Advantage  
*  Guarantee O(N log N) performance  
*  Highly parallelizable  
  
  
## Bottom Up Merge sort  
__Time Complexity:__ O(N Log N)  
__Auxiliary Space:__ O(N)  
__Stable:__ Yes  
Organize the merges so that we do all the merges of tiny arrays on one pass, then do a second pass to merge those arrays in pairs, and so forth, continuing until we do a merge that encompasses the whole array.  
Advantage 
*  Guarantee O(N log N) performance   
*  Non-recursive implementation 
  
  
## External merge sort  
which sorts chunks that each fit in RAM, then merges the sorted chunks together.For example, for sorting 900 megabytes of data using only 100 megabytes of RAM.  
[Wikipedia External sorting](https://en.wikipedia.org/wiki/External_sorting)  
  
  
## Quick Sort
__Time Complexity:__ Average O(N Log N), Worst O(N^2)  
__Auxiliary Space:__ O(1)  
__Stable:__ No  
Quick Sort execute the work before the recursion.
Quick Sort (Partition-exchange sort) is a sorting algorithm on average, makes O(n log n) comparisons to sort n items. In the worst case, it makes O(n2) comparisons, though this behavior is rare. Quick-sort is often faster in practice than other O(n log n) algorithms. Additionally, quick-sort's sequential and localized memory references work well with a cache. Quick-sort is a comparison sort and, in efficient implementations, is not a stable sort. Quick-sort can be implemented with an in-place partitioning algorithm, so the entire sort can be done with only O(log n) additional space used by the stack during the recursion.  
Such partitioning buys us two things. First, the pivot element p ends up in the exact array position it will reside in the the final sorted order. Second, after partitioning no element flops to the other side in the final sorted order. Thus we can now sort the elements to the left and the right of the pivot independently! This gives us a recursive sorting algorithm, since we can use the partitioning approach to sort each subproblem. The algorithm must be correct since each element ultimately ends up in the proper position.  
  
  
If we are extremely unlucky and our randomly selected elements always are among the largest or smallest element in the array, quick-sort turns into selection sort and runs in O(n2). However, the odds against this are vanishingly small.
The steps are:  
1.  Pick an element, called a pivot, from the array.  
2.  Reorder the array so that all elements with values less than the pivot come before the pivot, while all elements with values greater than the pivot come after it (equal values can go either way). After this partitioning, the pivot is in its final position. This is called the partition operation.  
3.  Recursively apply the above steps to the sub-array of elements with smaller values and separately to the sub-array of elements with greater values.  
  
  
## Heap sort  
__Time Complexity:__ Average O(N Log N), Worst O(N Log N)  
__Auxiliary Space:__ O(1)  
__Stable:__ No  
Merge Sort execute the recursion before the work.  
Heap sort is an in place sorting algorithm with N log N worst-case.  
1.  Build max Heap using bottom-up method (Start with nodes with children, 1 Node heaps are ignored "already already sorted").  
2.  Reapeatedly delete the largest remaining items.  
  
  
Heaps are usually implemented using arrays. This representation is that the positions of the parent and children of the key at position k are readily determined. The left child of k sits in position 2k and the right child in 2k + 1, while the parent of k holds court in position n/2. Thus we can move around the tree without any pointers.  
*  Inner loop longer than quicksort's.  
*  Makes poor use of cache memory.  
*  Not stable.  
  
  
## Bitmap Sort
__Time Complexity:__ O(N) 
__Auxiliary Space:__ O(N)  
__Stable:__ N/A (elements are unique)
This algorithm works on unique integers in a given range, with no data associated with it.

  
## Count Sort
__Time Complexity:__ O(N) 
__Auxiliary Space:__ O(N) 
__Stable:__ Yes (depends on implementation)

## Radix Sort
__Time Complexity:__ O(WN) 
__Auxiliary Space:__ O(W+N) 
__Stable:__ Yes 
Radix sort is a non-comparative integer sorting algorithm that sorts data with integer keys by grouping keys by the individual digits which share the same significant position and value.

