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
