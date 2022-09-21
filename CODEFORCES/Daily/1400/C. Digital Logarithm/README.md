
<h2><a href="https://codeforces.com/problemset/problem/1728/C">C. Digital Logarithm</a></h2>
<h3>1400</h3>
<hr>
<div><p>
  Let's define f(x) for a positive integer x as the length of the base-10 representation of x without leading zeros. I like to call it a digital logarithm. Similar to a digital root, if you are familiar with that.

You are given two arrays a and b, each containing n positive integers. In one operation, you do the following:

pick some integer i from 1 to n;
assign either f(ai) to ai or f(bi) to bi.
Two arrays are considered similar to each other if you can rearrange the elements in both of them, so that they are equal (e. g. ai=bi for all i from 1 to n).

What's the smallest number of operations required to make a and b similar to each other?

Input
The first line contains a single integer t (1≤t≤104) — the number of testcases.

The first line of the testcase contains a single integer n (1≤n≤2⋅105) — the number of elements in each of the arrays.

The second line contains n integers a1,a2,…,an (1≤ai<109).

The third line contains n integers b1,b2,…,bn (1≤bj<109).

The sum of n over all testcases doesn't exceed 2⋅105.

Output
For each testcase, print the smallest number of operations required to make a and b similar to each other.

  
</p>

  
Example
inputCopy
4
1
1
1000
4
1 2 3 4
3 1 4 2
3
2 9 3
1 100 9
10
75019 709259 5 611271314 9024533 81871864 9 3 6 4865
9503 2 371245467 6 7 37376159 8 364036498 52295554 169
outputCopy
2
0
2
18
Note
In the first testcase, you can apply the digital logarithm to b1 twice.

In the second testcase, the arrays are already similar to each other.

In the third testcase, you can first apply the digital logarithm to a1, then to b2.
  

<hr>
 <h2><strong><b>Solution</b></strong></h2>
 <br>
 <pre>
 
#include<bits/stdc++.h>
using namespace std;
#define FAST() ios_base::sync_with_stdio(false);    cin.tie(nullptr);     cout.tie(nullptr);
#define ll long long
#define ld long double
#define pb push_back
#define Mod 1e9+7
#define mii map<int,int> 
#define All(v) v.begin(), v.end()
#define br cout<<endl;
typedef vector<int> vi;
typedef vector<string> vs;
typedef pair<int, int> pii;
int dir[4][2]={{-1,0},{0,-1},{0,1},{1,0}};
 
int main()
{
FAST();
int tt; cin>>tt;
while(tt--)
{
   int n,ans=0; cin>>n;
   map<ll,int> m,m1;
   map<int,priority_queue<int,vector<int>,greater<int>>> ma,mb;
   ll a[n];
   for(int i=0;i<n;i++) {ll x; cin>>x; m[x]++;}
   for(int i=0;i<n;i++)
   {
      ll x; cin>>x;
      int l2=floor(log10(x)+1);
      if(m[x]==0)
      {
          if(x>9) mb[l2].push(1);
          else mb[x].push(0);
          m1[x]++;
      } 
      else m[x]--;

   }
   for(auto it: m)
   {
      ll x=it.first,y=it.second;
      int l1=floor(log10(x)+1);
      while(y>0)
      {
        y--;
        if(x>9) ma[l1].push(1);
         else ma[x].push(0);
      }
      // else if(y>0) m1[x]--;
   }
  //  for(auto it: ma)
  //  {
  //    cout<< it.first<<" "<<it.second.size()<<"\n";
  //    priority_queue<int,vector<int>,greater<int>> p=it.second;
  //    while(p.size()>0)
  //    {
  //      cout<<p.top()<<" "; p.pop();
  //    } 
  //    cout<<"\n";
  //  }
  //  for(auto it: mb)
  //  {
  //    cout<< it.first<<" "<<it.second.size()<<"\n";
  //    priority_queue<int,vector<int>,greater<int>> p=it.second;
  //    while(p.size()>0)
  //    {
  //      cout<<p.top()<<" "; p.pop();
  //    } 
  //    cout<<"\n";
  //  }
   for(auto it: ma)
   {
      int x=it.first;
      while(it.second.size()>0 && mb[x].size()>0  )
      {
         int a=it.second.top(); it.second.pop();
         int b=mb[x].top(); mb[x].pop();
         ans+=a+b;
        //  cout<<ans<<endl;
      }
      while(it.second.size()>0 )
      {
         int a=it.second.top(); it.second.pop();
          ans+=(x==1?a:a+1);
      }
   }
   for(auto it: mb)
   {
     int x=it.first;
      while(it.second.size()>0 )
      {
         int b=it.second.top(); it.second.pop();
         ans+=(x==1?b:b+1);
      }
   }

   cout<<ans<<"\n";
     
}
return 0;
}
          
 </pre>

