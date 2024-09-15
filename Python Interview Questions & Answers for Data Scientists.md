### Q1: Given two arrays, write a python function to return the intersection of the two? For example, X = [1,5,9,0] and Y = [3,0,2,9] it should return [9,0] ###

Answer:
```
set(X).intersect (set(Y))
```
Set:

define set like this: temp = set((x, y , 2, 4))

temp.update((5))

temp.remove((5))

temp.discard((5)) -- doesnt raise an error if elem not present in set

temp.clear() -- removes everything

first_set.union(second_set)

first_set.intersection(second_set)

first_set - second_set

first_set.symmetric_difference(second_set)

a.issubset(b)

a.issuperset(b)

a.isdisjoint(b)

frozenset: immutable set, so now canbe used as a key to a dictionary

### Q2: Given an array, find all the duplicates in this array? For example: input: [1,2,3,1,3,6,5] output: [1,3] ###

Answer:
```
set1=set()
res=set()
for i in list:
  if i in set1:
    res.add(i)
  else:
    set1.add(i)
print(res)
```


### Q3: Given an integer array, return the maximum product of any three numbers in the array? ###

Answer:

```
import heapq

def max_three(arr):
    a = heapq.nlargest(3, arr) # largerst 3 numbers for postive case
    b = heapq.nsmallest(2, arr) # for negative case
    return max(a[2]*a[1]*a[0], b[1]*b[0]*a[0])
```

### Q4: Given an integer array, find the sum of the largest contiguous subarray within the array. For example, given the array A = [0,-1,-5,-2,3,14] it should return 17 because of [3,14]. Note that if all the elements are negative it should return zero.

```
def max_subarray(arr):
  n = len(arr)
  max_sum = arr[0] #max
  curr_sum = 0 
  for i in range(n):
    curr_sum += arr[i]
    max_sum = max(max_sum, curr_sum)
    if curr_sum <0:
      curr_sum  = 0
  return max_sum    
      
```

### Q5: Define tuples and lists in Python What are the major differences between them? ###

Answer:

Lists:
In Python, a list is created by placing elements inside square brackets [], separated by commas. A list can have any number of items and they may be of different types (integer, float, string, etc.). A list can also have another list as an item. This is called a nested list.

1. Lists are mutable
2. Lists are better for performing operations, such as insertion and deletion.
3. Lists consume more memory
4. Lists have several built-in methods


Tuples:
A tuple is a collection of objects which ordered and immutable. Tuples are sequences, just like lists. The differences between tuples and lists are, the tuples cannot be changed unlike lists and tuples use parentheses, whereas lists use square brackets.

1. Tuples are immutable
2. Tuple data type is appropriate for accessing the elements
3. Tuples consume less memory as compared to the list
4. Tuple does not have many built-in methods.


* Mutable = we can change, add, delete and modify stuff
* Immutable = we cannot change, add, delete and modify stuff

### Q6: Compute the Euclidean Distance Between Two Series? ###
```
```

### Q7: Given an integer n and an integer K, output a list of all of the combination of k numbers chosen from 1 to n. For example, if n=3 and k=2, return [1,2],[1,3],[2,3] ### 

Answer
```
from itertools import combinations
def find_combintaion(k,n):
    list_num = []
    comb = combinations([x for x in range(1, n+1)],k)
    for i in comb:
        list_num.append(i)
    print("(K:{},n:{}):".format(k,n))
    print(list_num,"\n")
```

### Q8: Write a function to generate N samples from a normal distribution and plot them on the histogram ###

Answer:
Using bultin Libraries:
```
import numpy as np
import matplotlib.pyplot as plt

x = np.random.randn((N,))
plt.hist(x)
```
From scratch: 
![Alt_text](https://github.com/youssefHosni/Data-Science-Interview-Questions/blob/main/Figures/Python%20questions%208.png)


### Q9: What is the difference between apply and applymap function in pandas? ###

Answer:

Both the methods only accept callables as arguments but what sets them apart is that applymap is defined on dataframes and works element-wise. While apply can be defined on data frames as well as series and can work row/column-wise as well as element-wise. In terms of use case, applymap is used for transformations while apply is used for more complex operations and aggregations. Applymap only returns a dataframe while apply can return a scalar value, series, or dataframe.


### Q10: Given a string, return the first recurring character in it, or “None” if there is no recurring character. Example: input = "pythoninterviewquestion" , output = "n" ###

Answer:
```
input_string = "pythoninterviewquestion"

def first_recurring(input_str):
  
  a_str = ""
  for letter in input_str:
    a_str = a_str + letter
    if a_str.count(letter) > 1:
      return letter
  return None

first_recurring(input_string)

```

### Q11: Given a positive integer X return an integer that is a factorial of X. If a negative integer is provided, return -1. Implement the solution by using a recursive function. ###

Answer:
```
def factorial(x):
    # Edge cases
    if x < 0: return -1
    if x == 0: return 1
    
    # Exit condition - x = 1
    if x == 1:
        return x
    else:
        # Recursive part
        return x * factorial(x - 1)
```

### Q12: Given an m-by-n matrix with positive integers, determine the length of the longest path of increasing within the matrix. For example, consider the input matrix:

        [ 1 2 3 ]
        
        [ 4 5 6 ]
        
        [ 7 8 9 ]        
        
        The answer should be 5 since the longest path would be 1-2-5-6-9 


Answer:

```
MAX = 10

def Longest_Increasing_Path(dp, mat, n, m, x, y):
     
    # If value not calculated yet.
    if (dp[x][y] < 0):
        result = 0
         
        #  // If reach bottom right cell, return 1
        if (x == n - 1 and y == m - 1):
            dp[x][y] = 1
            return dp[x][y]
 
        # If reach the corner
        # of the matrix.
        if (x == n - 1 or y == m - 1):
            result = 1
 
        # If value greater than below cell.
        if (x + 1 < n and mat[x][y] < mat[x + 1][y]):
            result = 1 + LIP(dp, mat, n,
                            m, x + 1, y)
 
        # If value greater than left cell.
        if (y + 1 < m and mat[x][y] < mat[x][y + 1]):
            result = max(result, 1 + LIP(dp, mat, n,
                                        m, x, y + 1))
        dp[x][y] = result
    return dp[x][y]
 
# Wrapper function
def wrapper(mat, n, m):
    dp = [[-1 for i in range(MAX)]
            for i in range(MAX)]
    return Longest_Increasing_Path(dp, mat, n, m, 0, 0)
```    

### Q13: 𝐄𝐱𝐩𝐥𝐚𝐢𝐧 𝐰𝐡𝐚𝐭 𝐅𝐥𝐚𝐬𝐤 𝐢𝐬 𝐚𝐧𝐝 𝐢𝐭𝐬 𝐛𝐞𝐧𝐞𝐟𝐢𝐭𝐬 ###

Answer:

Flask is a web framework. This means flask provides you with tools, libraries, and technologies that allow you to build a web application. This web application can be some web pages, a blog, a wiki, or go as big as a web-based calendar application or a commercial website.

Benefits of Flask:
1. Scalable
Flask’s status as a microframework means that it can be used to grow a tech project such as a web app very quickly. 

2. Flexible
It allows the project to be rearranged and moved around. Also makes sure that the project structure does not collapse when a part is altered.

3. Easy to negotiate
At its core, the microframework is easy to understand for web developers also giving them more control over their code and what is possible.

4. Lightweight
Certain parts of a design of a tool/framework might need assembling and reassembling and do not rely on a large number of extensions to function which gives web developers a certain level of control. Further, Flask also supports modular programming, which is where its functionality can be split into several interchangeable modules and each module acts as an independent entity and executes a part of the functionality.

### Q14: 𝐖𝐡𝐚𝐭 𝐢𝐬 𝐭𝐡𝐞 𝐝𝐢𝐟𝐟𝐞𝐫𝐞𝐧𝐜𝐞 𝐛𝐞𝐭𝐰𝐞𝐞𝐧 𝐥𝐢𝐬𝐭𝐬, 𝐚𝐫𝐫𝐚𝐲𝐬, 𝐚𝐧𝐝 𝐬𝐞𝐭𝐬 𝐢𝐧 𝐏𝐲𝐭𝐡𝐨𝐧, 𝐚𝐧𝐝 𝐰𝐡𝐞𝐧 𝐲𝐨𝐮 𝐬𝐡𝐨𝐮𝐥𝐝 𝐮𝐬𝐞 𝐞𝐚𝐜𝐡 𝐨𝐟 𝐭𝐡𝐞𝐦? ####

Answer:

All three are data structures that can store sequences of data. but with some differences.

List denoted by [ ], set by { } , and array/tuple by ( )

𝐋𝐢𝐬𝐭: built-in data type in Python that helps store data in sequence with a very rich API that allows insertion removal retrieval and expansion. one of its benefits is that it allows the use of many data types in the same lists as it can store string, integers, floats of any other derived objects. one of its cons that are very slow if it will be used in numerical computation.

𝐀𝐫𝐫𝐚𝐲: on the other hand array can only store a single data type like integers only, float only, or any derived object only. but unlike lists, it's very efficient in terms of speed and memory usage (NumPy is one of the best libraries that implements array operations as it's a very rich library that solves many problems in numerical computation like vectorization, broadcasting, ...etc).

𝐒𝐞𝐭: it's also a built-in data type in Python and can store more that data types. but it does not allow for the existence of duplicates and if there are duplicates it only uses one of them. provide a lot of methods like unions, diffs, and intersections.


### Q15: Only pairs whose wealth sum is a power of 3 can enter. Given N and wealth. Sample input: N=4, wealth=[1,5,2,4]. Sample output: 2.

Helper function to check if a number is a power of 3

1. Take log
a+b = 3^k
log(a+b) = k*log(3)
k = log(a+b)/log(3)
k = log(a+b-3)
k.is_integer()
if k is an interger then (a+b) is a power of 3.
Drawbacks: Import math might not always be avaialble

2. Keep dividing by 3, if eventually you get 1 then good. If dividing by 3 leads to a remainder other than 0 then its not a power of 3
def is_pow3(x):
    while x > 1:
        if x % 3 != 0:
            return False
        x //= 3
    return x == 1
then loop through n,n+1 to check sums of pairs O(n^2)
   
3. Compute all powers of 3 in a single operation as we know 3^20 is max - this makes it a constant operation o(1)
```
def solve(n, w):
    pow3 = [3**i for i in range(21)]  # Precompute powers of 3 up to 3^20
    freq = Counter()  # Initialize a Counter to track frequency of wealth values
    cnt = 0

    for i in range(n):
        for p in pow3:
            req = p - w[i]  # Calculate the required pair value
            cnt += freq[req]  # Add frequency of `req` to count if it exists
        
        # Update the frequency map after checking, to avoid pairing with itself
        freq[w[i]] += 1

    return cnt
```




















