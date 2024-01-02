---
title: "Solving Leetcode Questions || 60 Days DSA Challange || #Day 2"
datePublished: Tue Jan 02 2024 15:30:16 GMT+0000 (Coordinated Universal Time)
cuid: clqwia9s0000k08l424gre9la
slug: solving-leetcode-questions-60-days-dsa-challange-day-2
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1704190754566/5d4257cc-e0e1-4bc7-8c7e-5b417417c502.png
ogImage: https://cdn.hashnode.com/res/hashnode/image/upload/v1704190832447/785886d9-f302-4adf-afe4-cbf5404e21d8.png
tags: interview, dsa, 2articles1week, wemakedevs, mayankaggarwal, mayank

---

## Q1.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1704188267215/70a24eca-4e97-4aae-8d55-80845895bd27.png align="center")

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1704188283440/047eefbc-b9c7-4ce0-820d-e145503acbc0.png align="center")

**Explaining**

The Question says that we need to find the matching word from a given string in the dictionary. With Some constraints:-

* `1 <= s.length <= 300`
    
* `1 <= wordDict.length <= 1000`
    
* `1 <= wordDict[i].length <= 20`
    
* `s` and `wordDict[i]` consist of only lowercase English letters.
    
* All the strings of `wordDict` are **unique**.
    

So to Answer this Question we can first see the Greedy approach. A greedy approach to this question says that we can match every letter of the first string with a word in the dictionary if the match is not found then we shift to the next word in the dictionary. This approach will work fine for the question But This will cause TLE (Time Limit Exceeded) Error.

So, to solve it we will need to optimize this approach or think of a new approach. If we think of a new approach the simplest we can think of is can compare the words in a dictionary with the string which seems to be a better solution for the problem as we will be able to reduce the time complexity of the problem by skipping some of the indexes. This will be a top-bottom Approach so, let's Implement it:

```cpp
class Solution {
public:
    int helper(int i,string s,set<string>& dict){
        if(s.size()==i) return 1;
        string temp;
        for(int j=i;j<s.size();j++){
            temp+=s[j];
            if(dict.find(temp)!=dict.end()){//found the word
                if(helper(j+1,s,dict)) return 1;
            }
        }
        return 0;
    }
    bool wordBreak(string s, vector<string>& wordDict) {
        set<string> st; // we are using set so that we can use .find() function to find in string easily
        for(auto i:wordDict)     st.insert(i);
        return helper(0,s,st);   
    }
};
```

Still, the time complexity of the code is very high because there is a lot of recalculation of the problems in the code. So this is the time when Dynamic programming comes to play its role. So we will add a dp array that stores the values that were calculated earlier. So that we can reduce time by reusing the values that were calculated earlier. So Let's implement this in the same Code :

```cpp
int dp[300];
class Solution {
public:
    int helper(int i,string s,set<string>& dict){
        if(s.size()==i) return 1;
        string temp;
        if(dp[i]!=-1)return dp[i];
        for(int j=i;j<s.size();j++){
            temp+=s[j];
            if(dict.find(temp)!=dict.end()){//found the word
                if(helper(j+1,s,dict)) return dp[i]=1;
            }
        }
        return dp[i]=0;
    }
    bool wordBreak(string s, vector<string>& wordDict) {
        memset(dp,-1,sizeof(dp));
        set<string> st;
        for(auto i:wordDict)     st.insert(i);
        return helper(0,s,st);   
    }
};
```

## Q2.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1704190269114/cdc52acd-164e-4cbc-8215-45097171959d.png align="center")

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1704190278444/648a2165-1a38-4913-9ddc-1d633af91fde.png align="center")

**Naive method:**  
For every coin We will take it or we will not take it so we will get 2 paths to walk on. If our total amount is reached then we will take min of these two paths and return it.

```cpp
class Solution {
public:
    int help(vector<int>& coins, int amount, int n)
    {
        if(amount == 0) return 0;
        if(n < 0 || amount < 0) return INT_MAX-1;
        int one = help(coins,amount,n-1);
        int two = 1+help(coins,amount-coins[n],n);
        return min(one,two);
    }
    
    int coinChange(vector<int>& coins, int amount) {
        int ans = help(coins,amount,coins.size()-1);
        return (ans < INT_MAX-1)?ans:-1;
    }
};
```

Here I have taken two base cases where amount == 0 in which case we reach our amount and return the result and other is (n &lt; 0 || amount &lt; 0) in this case we cannot get result so we will set it to INT\_MAX so that it will not effect my min(one,two). This solution on submitting gives **TLE**

**Memoization**  
To reduce time we will just use an 2D array to store our result. Since we are solving our problem recursively you can store the value you got for certain {amount,n} and store it and use it for next time. implementation is:

```cpp
class Solution {
public:
    int help(vector<int>& coins, int amount, int n,vector<vector<int>>&h)
    {
        if(amount == 0) return 0;
        if(n < 0 || amount < 0) return INT_MAX-1;
        if(h[n][amount]!= -1) return h[n][amount];
        int one = help(coins,amount,n-1,h);
        int two = 1+help(coins,amount-coins[n],n,h);
        h[n][amount] = min(one,two);
        return h[n][amount];
    }
    
    int coinChange(vector<int>& coins, int amount) {
        vector<vector<int>>h(coins.size()+1,vector<int>(amount+1,-1));
        int ans = help(coins,amount,coins.size()-1,h);
        return (ans < INT_MAX-1)?ans:-1;
    }
};
```

**Tabulation**  
For this que we can do 2D Tabulation and 1D tabulation Both, But I will talk about 1D tabulation only Here. Now According to our name suggestion, we are using a 1D array. We will set every element to infinity and one by one check from coins array that if we can use this coin to get results or not and take min of those values and store it. we will focus on these 3 lines from our recursion

```cpp
int one = help(coins,amount,n-1);
int two = 1+help(coins,amount-coins[n],n);
return min(one,two);
```

So here is the Implementatio

```cpp
class Solution {
public:
    int coinChange(vector<int>& coins, int amount) {
        vector<int>h((amount+1), INT_MAX-1);
        h[0] = 0;
        for(int i = 0; i < h.size(); i++)
        {
            for(int j = 0; j < coins.size(); j++)
            {
                if(i >= coins[j]) h[i] = min(h[i], 1 + h[i-coins[j]]);
            }
        }
        return (h[h.size()-1] < INT_MAX - 1)?h[h.size()-1]:-1; 
    }
};
```

Why Tabulation is better than Memoization?  
Although auxiliary time complexity is the same we see that the real-time time complexity of memoization will be higher.  
As for space: clearly, tabulation is a Better option

## Q3.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1704190568092/ee1feff6-4669-407f-9912-1f930ccd4d61.png align="center")

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1704190581130/40a39773-a6ea-45fd-aa79-bdf80049a352.png align="center")

# **Intuition**

To determine the number of trailing zeros in 152 factorial (152!), it's essential to understand that trailing zeros result from the multiplication of multiples of 5 and 2. The key is to count the number of 5's and 2's in the multiplication process.

Firstly, let's count the 5's: 5, 10, 15, 20, 25, and so on, totaling 20 occurrences. However, since numbers like 25, 50, 75, and 100 have two 5's each, we need to count them twice, resulting in a total of 24 occurrences.

Moving on to count the 2's: 2, 4, 6, 8, 10, and so forth. There are 50 multiples of 2, 25 multiples of 4 (counted once more), 12 multiples of 8 (counted once more), and so on. The grand total of 2's is 97 occurrences.

Since each pair of 2 and 5 contributes to a trailing zero, and we have 24 5's, we can form only 24 pairs of 2's and 5's. Thus, the number of trailing zeros in 152 factorial is 24.

In a more general formula, the number of trailing zeros in any factorial (x!) can be expressed as min(∑na=1x5a).

# **Approach**

Let, N = 152!

For those who don’t know what factorial is, 100! = 100 *99* 98 *…* 2 \* 1

We have to find how many zeroes are there at the end of this number N. To deduce this, we have to know how trailing zeros are formed in the first place. A trailing zero is formed when a multiple of 5 is multiplied with a multiple of 2. Now, all we have to do is count the number of 5’s and 2’s in the multiplication.

Let’s count the 5’s first. 5, 10, 15, 20, 25 and so on making a total of 20. However, there is more to this. Since 25, 50, 75 and 100 have two 5’s in each of them (25 = 5 *5, 50 = 2* 5 \* 5, …), you have to count them twice. This makes the grand total of 24. For people who like to look at it from a formula point of view

Number of 5’s = 100/5 + 100/25 + 100/125 + … = 24 (Integer values only)

Moving on to count the number of 2’s. 2, 4, 6, 8, 10 and so on. Total of 50 multiples of 2’s, 25 multiples of 4’s (count these once more), 12 multiples of 8’s (count these once more) and so on… The grand total comes out to

Number of 2’s = 100/2 + 100/4 + 100/8 + 100/16 + 100/32 + 100/64 + 100/128 + … = 97 (Integer values only)

Each pair of 2 and 5 will cause a trailing zero. Since we have only 24 5’s, we can only make 24 pairs of 2’s and 5’s thus the number of trailing zeros in 100 factorial is 24.

As we have seen from the above example, the number of 5’s are the limiting factor for the no of zeroes in this case and decides the number of trailing zeroes for the factorial. So, we don’t need to calculate no of 2’s.

Number of zeroes for any given factorial (x!)  
can be expressed as min(∑na=1x5a)

So, the number of zeroes at the end of 152! will be,

min(15251)+min(15252)+min(15253)+min(15254)+....

\=min(1525)+min(15225)+min(152125)+min(152625)+....

\=30+6+1+0+...

\=37

So, there are a total of 37 zeroes at the end of 152!

Thanks for reading my answer. Hope this helps. If so, please consider upvoting.

# **Complexity**

* Time complexity: The time complexity to determine the number of trailing zeros in a factorial is approximately O(log₅n), where n is the input value (152 in this case). This is because we are counting the number of multiples of 5 in the factorial.
    
* Space complexity: The space complexity is O(1) since the algorithm uses a constant amount of space regardless of the input size. We are not using any additional data structures that depend on the input.
    

```cpp
class Solution {
public:
    int trailingZeroes(int n) {
        long long powerOfFive = 5;
        long long countOfZero = 0;

        while(n/powerOfFive)
        {
            countOfZero+=n/powerOfFive;
            powerOfFive*=5;
        }
        return countOfZero;
    }
};
```