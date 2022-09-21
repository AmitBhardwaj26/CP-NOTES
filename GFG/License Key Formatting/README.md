
<h2><a href="https://practice.geeksforgeeks.org/problems/license-key-formatting/1">License Key Formatting</a></h2>
<h3>Medium</h3>
<hr>
<div><p>
 Given a string S that consists of only alphanumeric characters and dashes. The string is separated into N + 1 groups by N dashes. Also given an integer K. 

We want to reformat the string S, such that each group contains exactly K characters, except for the first group, which could be shorter than K but still must contain at least one character. Furthermore, there must be a dash inserted between two groups, and you should convert all lowercase letters to uppercase.

Return the reformatted string.

</p>


<p><strong>Example 1:</strong></p>
<pre><strong>Input:</strong>  nums1 = [1,2,3,2,1], nums2 = [3,2,1,4,7]
<strong>Output:</strong> 3
</pre>


Example 1:

Input: 
S = "5F3Z-2e-9-w", K = 4
Output: "5F3Z-2E9W"
Explanation: The string S has been split into two
parts, each part has 4 characters. Note that two
extra dashes are not needed and can be removed.
Example 2:

Input:
S = "2-5g-3-J", K = 2
Output: "2-5G-3J"
Explanation: The string s has been split 
into three parts, each part has 2 characters 
except the first part as it could
be shorter as mentioned above.

Your Task:  
You don't need to read input or print anything. Your task is to complete the function ReFormatString() which takes a string S and an integer K as input and returns the reformatted string.


Expected Time Complexity: O(N)
Expected Auxiliary Space: O(N)
  
  
<hr>
 <strong><b>Solution</b></strong>
 <br>
 <p><pre>
 class Solution {
public:
    int findLength(vector<int>& nums1, vector<int>& nums2) {
        ios_base::sync_with_stdio(0);
        int n = nums1.size(),m = nums2.size();
        vector<vector<int>>dp(n,vector<int>(m,0));
        for(int i = n-1; i>=0; i--){
            for(int j = m-1; j>=0; j--){
                if(i==n-1 || j==m-1){
                    if(nums1[i]==nums2[j]){
                        dp[i][j] = 1;
                    }
                }
                else{
                    if(nums1[i]==nums2[j]){
                        dp[i][j] = 1+dp[i+1][j+1];
                    }
                }
            }
        }
        int ans = 0;
        for(int i = 0; i<n; i++){
            for(int j = 0; j<m; j++){
                ans = max(ans,dp[i][j]);
            }
        }
        return ans;
    }
};
 </pre>
</p>
