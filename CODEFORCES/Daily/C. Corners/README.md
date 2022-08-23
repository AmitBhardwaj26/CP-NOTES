
<h2><a href="https://codeforces.com/problemset/problem/1720/C">C. Corners</a></h2>
<h3>Easy</h3>
<hr>
<div><p>
 
  You are given a matrix consisting of n rows and m columns. Each cell of this matrix contains 0 or 1.

Let's call a square of size 2×2 without one corner cell an L-shape figure. In one operation you can take one L-shape figure, with at least one cell containing 1 and replace all numbers in it with zeroes.

Find the maximum number of operations that you can do with the given matrix.

Input
The first line contains one integer t (1≤t≤500) — the number of test cases. Then follow the descriptions of each test case.

The first line of each test case contains two integers n and m (2≤n,m≤500) — the size of the matrix.

Each of the following n lines contains a binary string of length m — the description of the matrix.

It is guaranteed that the sum of n and the sum of m over all test cases does not exceed 1000.

Output
For each test case output the maximum number of operations you can do with the given matrix.

Example
inputCopy
4
4 3
101
111
011
110
3 4
1110
0111
0111
2 2
00
00
2 2
11
11
outputCopy
8
9
0
2
Note
In the first testcase one of the optimal sequences of operations is the following (bold font shows l-shape figure on which operation was performed):

Matrix before any operation was performed:


 
</p>

