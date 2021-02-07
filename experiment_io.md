**Basics**  
Io> a := 1  
==> 1  
Io> getSlot("a")  
==> 1  

Io> OperatorTable
==> OperatorTable_0x7f92ebd38250:
Operators
  0   ? @ @@
  1   **
  2   % * /
  3   + -
.....

Assign Operators
  ::= newSlot
  :=  setSlot
  =   updateSlot

To add a new operator: OperatorTable addOperator("+", 4) and implement the + message.
To add a new assign operator: OperatorTable addAssignOperator("=", "updateSlot") and implement the updateSlot message.

Io> message(2/4)
==> 2 /(4)

**Modifying Prototypes**  
Io> List slotNames  
==> list(second, removeFirst, swapIndices, sortByKey, containsIdenticalTo, pop, containsAny, contains, itemCopy, empty, third, mapFromKey, detect, asMessage, removeSeq, union, rest, reverseReduce, groupBy, removeAll, setSize, asString, appendSeq, indexOf, containsAll, atInsert, justSerialized, with, intersect, at, appendIfAbsent, max, atPut, ListCursor, min, join, foreach, sort, difference, cursor, asMap, first, sum, append, last, reverseInPlace, removeAt, asSimpleString, insertBefore, preallocateToSize, flatten, select, selectInPlace, asEncodedList, unique, size, sortInPlaceBy, sortKey, mapInPlace, isNotEmpty, remove, map, slice, copy, push, reduce, sortBy, insertAt, uniqueCount, reverseForeach, sortInPlace, asJson, sliceInPlace, prepend, exSlice, average, insertAfter, removeLast, capacity, reverse, isEmpty, fromEncodedList)  

Io> List myAverage := method(self average)  
==> method(  
    self average  
)  
Io> l := list(1,2,3,4)  
==> list(1, 2, 3, 4)  
Io> l myAverage  
==> 2.5  

Io> List check := method(self foreach(v, if(v type != "Number", Exception raise("Invalid"))))
==> method(
    self foreach(v, if(v type != "Number", Exception raise("Invalid")))
)
Io> mylist := (1,2)

  Exception: compile error: Assign operator passed multiple arguments, e.g., a := (b, c).
  ---------
  message ':=' in '[unlabeled]' on line 1

Io> exit

Io> List check := method(self foreach(v, if(v type != "Number", Exception raise("Invalid"))))  
==> method(  
    self foreach(v, if(v type != "Number", Exception raise("Invalid")))  
)  
Io> mylist := list(1,2)  
==> list(1, 2)  
Io> mylist check  
==> false  
Io> mylist := list(1,"z")  
==> list(1, z)  
Io> mylist check  

  Exception: Invalid  
  ---------
  Exception raise                      Command Line 1  
  List check                           Command Line 1  

**override**
Io> origDiv := Number getSlot("/")  
==> Number_/()  
Io> 10 origDiv(5) println  
2  
==> 2  
Io> 10 origDev(0) println  

  Exception: Number does not respond to 'origDev'  
  ---------
  Number origDev                       Command Line 1  

Io> Number / := method(i, if(i != 0, self origDiv(i), 0))  
==> method(i, if(i != 0, self origDiv(i), 0))  
Io> (10 / 5)  
==> 2  
Io> (10 / 0)  
==> 0  

**Fibonacci number**

Io> fib := method(i,a,b, if(i<=2, return b, return fib(i-1,b,a+b)))  
==> method(i, a, b,   
    if(i <= 2, return b, return fib(i - 1, b, a + b))  
)  
Io> fib(2,1,1)  
==> 1  
Io> fib(3,1,1)  
==> 2  
Io> fib(4,1,1)  
==> 3  
Io> fib(5,1,1)  
==> 5  
Io> fib(6,1,1)  
==> 8  

**List**  
Io> sum := method(l, for(i,0,(l size)-1,1, if(l at(i) type == "List", t=(for(j,0,(l at(i) size)-1,1, t=(l at (i) at(j))+t, t=(l at(i)+t))))))  
==> method(l, 
    for(i, 0, (l size) - 1, 1, if(l at(i) type == "List", t = for(j, 0, (l at(i) size) - 1, 1, t = (l at(i) at(j)) + t, t = l at(i) + t)))  
)  
Io> v := list(list(1,2),list(3,4))  
==> list(list(1, 2), list(3, 4))  
Io> t := 0  
==> 0  
Io> sum(v)  
==> 10  
