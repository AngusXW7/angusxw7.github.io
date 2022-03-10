# C++ Pointer

The essence of the C languages  Pointer!

<!--more-->

Hello, I've found time in my busy schedule to come back as promised. Today, I'll talk about pointers. It's said that the essence of C is pointers, but it's also true that C should be one of the few high-level languages that can manipulate the underlying memory with pointers. I'm sure my understanding is not as deep as that of the top coders, after all, I'm just a beginner, the wording is not accurate or logic is not strict, please enlighten me ~, if there is where to say the wrong, also welcome to point out!


## WHAT IS POINTER

Before we expand the question, then, we need to figure out what a pointer is.

We often say that a pointer is an address, and that a pointer variable is a variable used to store a memory address.

As I understand it, a pointer is synonymous with your home, and a memory address is where your home actually is. When you say that a pointer points to such and such address, you are actually saying that your home is a synonym for where your home address is (that is, where your home lives). This sounds a bit like nonsense.

### EXAMPLES：

```
int* ptr= 0X12345678;
int* ptr = & XW7 home;
```

We have an int pointer **ptr** (my home pronoun): __int* ptr__  ;

This pointer points to (the actual address of my house): **0X12345678**; // Generally speaking, memory addresses are expressed in eight bits of hexadecimal, starting with 0X in order to distinguish from binary, octal and decimal

It is generally written as __int* ptr = & XW7's home__;

Let's ignore this "&" and read "=" as "is", so now this sentence is saying that ptr is the home of xw7.

Next, let's say I want to invite my friend to my house for the weekend, then I just say ptr to them and they surely can't know where my house is for no reason, right?

So we'll use "&" for the address, so int* ptr = & XW7's home now becomes ptr = 12 City 34 56th Street 78 , the actual address of my house, and again, we read "=" as "is", XW7's home is 78-56th street, 34th district, 12th city. This way my friends can find my house without any problem on weekends.

### “*”

```
int* *ptr // not exists
int* ptr = sth ;
ptr* = sth ;
```

The symbol "__*__" means something different when it follows a different owner.

But we won't see int* * variableName (int* *ptr) as something that exists.

We will only see int* variable name = something;

or *ptr = something;

```
char* c ; //char type pointer
int*  i ; //int type pointer
float* f ; //float type pointer

```

In general, if it follows a data type, like __char int float__, then it represents a pointer to that type

__char*__ is a pointer to a __char__ type;

__int*__ is a __int__ type pointer;

__float*__ is a __float__ pointer;

and so on

// on 32-bit systems, all pointers are 4 bytes in size.

```
*ptr = XW7 home ; 
 ptr = 0X12345678; 
```

But if it's followed by a variable name, like __*ptr__ above, then it's a dereference, and you have to use a pronoun. In layman's terms, adding __*__ to __ptr__ means that __ptr__ is encrypted and can only say __XW7's home__, but not the exact address of __12 City 34, 56th Street, 78__. That is, __*ptr = XW7's home , *ptr is XW7's home__.

## CONST AND *

I believe that many people have been confused by the placement of const and *, but when you get the key, you will find it very simple. You can tell what pointer constants and constant pointers are at a glance.

First of all, someone may ask, What is a const? Ha ha, cosnt is actually a modifier, the thing that is modified by him can not be changed.

Here I share my tips:

### TIP

First we list a few very common formats.
```
 const int * ptr；// 1
 int const * ptr；// 2
 int * const ptr；// 3
 ```
 How do we distinguish them ? It is very simple, we only need to look at two things, one is __*__ and the other is __ptr__;

 If const is immediately followed by __*__ then there is no doubt that const modifies *, which means that what * points to cannot be changed; // 1,2

 If const is immediately followed by __variable name__ (i.e., ptr), then const modifies the variable name, which means that the value represented by the variable name cannot be changed. // 3

 Another very important thing is that const is a "one-time thing". If you want more than one pointer or value that cannot be changed, you have to use more than one const, e.g.

```
 const int* const ptr; // both int* and ptr are immutable
 const int* const p1, const p2; // int* p1 p2 are immutable
 ```


 ### APPLICATIONS

 So after we know who is not changeable, what do we use them for; first we can get two more useful information from the naming statement, one is who the pointer points to, and the other is what the pointing thing contains.

 Let's use the example of renting a house, where the pointer represents the house and the content inside represents the tenant.

 If what is pointed to cannot be changed, then it is now the landlord identity, that is, as long as it is my house, it does not matter which tenants, you can change them at will.

 If the content of the pointer cannot be changed, then it is now the identity of the tenant, that is to say, as long as I am renting the house, it does not matter which house, you can change it at will.

 ### EXPANSION

 Further down the line, it should touch on objects and classes, let's briefly say.
  ```
 const returnType functionName ( Parameter); //  return type can not be modified
 returnType functionName (const Parameter); //  incoming parameters can not be modified
 returnType functionName (Parameter) const; //  class member parameters can not be modified
  ```

 ## ARRAY AND *

 We all know that arrays are implicitly degraded to pointers when they are passed as arguments to functions, so we arbitrarily treat arrays as a kind of pointer.

 Here are a few confusing combinations of arrays and *.

 ### EXAMPLES

 ```
 int array[];
 int* p = array;
 *p ;            // array[0]
 p+1 ;           //array[0]address + 4
 *p+1 ;          //array[0]value + 1
 *(p+1) ;        //array[1]

 *（ *（p+n)+m) = p[n][m];

```

 Suppose we have an array called array, *p =array; then.

 *p represents the first element of the array i.e. array[0] ;

  p + 1 represents the address of the first element of the array shifted back by one unit, if array is of type char the offset is 1, int the offset is 4 float the offset is 4, and so on. The address of the second element of the array is represented implicitly ;

 *p + 1 represents the value of the first element of the array + 1 i.e. (the value of array[0] ) + 1 ;

  *(p + 1 ) represents the element of the array with subscript 1, i.e. p[1] ;

  So we can simply derive a *(p+n) = p[n] ; // *( + ) = []

  What about if it's a multi-dimensional arrays ?

  It's simple *( *(p+n)+m) = p[n][m];

  ## POINTER OPERATIONS

 Always remember that in the function __ only the next level pointer can operate the current level pointer __, you may be a little confuse, I'll explain to you: 

  Without * we will call it a zero-level pointer

  *is a first-level pointer

  ** is the second level pointer

 Here we have p *p **p;

 So __*p__ can operate on __p__, __**p__ can operate on __*p__, and so on

 If you are trying to read a multilevel pointer, the reading order must be from right to left.
 
 __( * (* ( * ( * (m)))__ is like this,
 
 You have to look at __m__ first and then look at __* (m)__;

 then look at __* (* (m))__;
 
 And finally look at __*( * ( * (m)))__;


 ## SHARE AND SUMMARY


 Well that's it for today's sharing, going to get busy.

 Here to share a better [pointer tutorial](https://www.youtube.com/watch?v=h-HBipu_1P0&list=PL2_aWCzGMAwLZp6LMUKI3cc7pgGsasm2_), I hope it can be helpful to you in front of the screen.

 Heihei！

