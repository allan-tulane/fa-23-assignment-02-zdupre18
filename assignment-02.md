# CMPS 2200 Assignment 2

**Name:**______zoe dupre ___________________

In this assignment we'll work on applying the methods we've learned to analyze recurrences, and also see their behavior
in practice. As with previous
assignments, some of of your answers will go in `main.py` and `test_main.py`. You
should feel free to edit this file with your answers; for handwritten
work please scan your work and submit a PDF titled `assignment-02.pdf`
and push to your github repository.


1. Derive asymptotic upper bounds of work for each recurrence below.
  * $W(n)=2W(n/3)+1$
.  
O(n ^log_3(2))
.  
.  
.  
  * $W(n)=5W(n/4)+n$
.  o(n^log_4(5))
.  
.  
.  
.  
  * $W(n)=7W(n/7)+n$
.  
    
.  Θ(n^{\log_7(7)} or Θ(n^1)
.  
.  
  * $W(n)=9W(n/3)+n^2$
.  
.  Θ(n^log_3(9)) or Θ(n^2)
.  
.  
.  
  * $W(n)=8W(n/2)+n^3$
.  
.  Θ(n(log2(8) or Θ(n^3)
.  
.  
.  
  * $W(n)=49W(n/25)+n^{3/2}\log n$
.  
.  
.  Θ(n^3/2)
.  
.  
  * $W(n)=W(n-1)+2$
.  
.  
.  o(n)
.  
.  
  * $W(n)= W(n-1)+n^c$, with $c\geq 1$
.  
    O(n^c +1)
.  
.  
.  
  * $W(n)=W(\sqrt{n})+1$

o(log(n))

2. Suppose that for a given task you are choosing between the following three algorithms:

  * Algorithm $\mathcal{A}$ solves problems by dividing them into
      five subproblems of half the size, recursively solving each
      subproblem, and then combining the solutions in linear time.
    
  * Algorithm $\mathcal{B}$ solves problems of size $n$ by
      recursively solving two subproblems of size $n-1$ and then
      combining the solutions in constant time.
    
  * Algorithm $\mathcal{C}$ solves problems of size $n$ by dividing
      them into nine subproblems of size $n/3$, recursively solving
      each subproblem, and then combining the solutions in $O(n^2)$
      time.

    What are the asymptotic running times of each of these algorithms?
    Which algorithm would you choose?

a = O(n^2.32)
b = o(n)
c = o(n^2)

alogirthm b is the best overal while A has the highest run time complexity 

3. Now that you have some practice solving recurrences, let's work on
  implementing some algorithms. In lecture we discussed a divide and
  conquer algorithm for integer multiplication. This algorithm takes
  as input two $n$-bit strings $x = \langle x_L, x_R\rangle$ and
  $y=\langle y_L, y_R\rangle$ and computes the product $xy$ by using
  the fact that $xy = 2^{n/2}x_Ly_L + 2^{n/2}(x_Ly_R+x_Ry_L) +
  x_Ry_R.$ Use the
  stub functions in `main.py` to implement Karatsaba-Ofman algorithm algorithm for integer
  multiplication: a divide and conquer algorithm that runs in
  subquadratic time. Then test the empirical running times across a
  variety of inputs in `test_main.py` to test whether your code scales in the manner
  described by the asymptotic runtime. Please refer to Recitation 3 for some basic implementations, and Eqs (7) and (8) in the slides https://github.com/allan-tulane/cmps2200-slides/blob/main/module-02-recurrences/recurrences-integer-multiplication.ipynb
 
 def karatsuba(x, y):
 if x < 10 or y < 10:
 return x *y
///calculating number of digits in each number implenmented 
 n = max(len(str(x)), len(str(y)))
 n2 = n//2
//splitting numbers into two parts for the func
 a, b = div(x, 10 **n2)
 c, d = div(y, 10 ** n2)

 ac = karatsuba(a, c)
 bd = karatsuba(b,d)
 ad_bc = karatubsa((a + b), (c + d)) - ac - bd

 results = ac * 10 ** (2 *n2) + ad_bc * 10 ** n2 + bd

 return result 


 //testing code 

 test_case = [1245, 7890), (133485, 129429400), (23, 45)]

 ///measuring running time for each test case for alogirthm 

 for x, y in test_case:
 start = time.time()
 result = karatuba(x,y)
 end = time.time() 
print("Input: " + x * y + "result: " + result + "Time: " + end_time - startime + "seconds.")


