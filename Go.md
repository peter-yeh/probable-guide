# Go





### Pointers
- & operator returns the address of a variable/function
- * operator returns data at an address (dereferencing)

``` Go
var x int = 1
var y int

var ip *int // ip is a pointer of type int

// assign ip to address of integer x
ip = &x // ip now points to x

// assign int variable y to value that pointer ip is pointing to
y = *ip // y is now 1
```

### New
- returns a pointer to the variable
- variable is initialized to zero

```
ptr := new(int) // *ptr is 0
*ptr = 3
```
