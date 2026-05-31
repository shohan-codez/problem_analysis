
This is maybe my first 1400 solve , on my own , and without any wa. I guess metacognition is doing its thing. 

## Meta
| Field          | Value                                                     |
| -------------- | --------------------------------------------------------- |
| 🔗 Link        | [2173C](https://codeforces.com/problemset/problem/2173/C) |
| ⭐ Difficulty   | 1400                                                      |
| 📅 Date solved | 27-05-2026                                                |
| ⏱ Time spent   | 2hrs                                                      |
| 🧠 How solved  | only #me                                                  |
| ✅ Confidence   | High                                                      |
| ❌ WA count     | 0                                                         |

---

## Classification
- **Tags:** #numbertheory #greedy 

---

## Key Insight
> After sorting the array , you have to check for each element if it has all the multiple from the number itself to k . if not found, you stop and print -1, other wise you print the element you are working with , and remove all the multiple of it. 



---

## Signal
> This is a problem , where you will only keep going if you are satisfied with current result. 



---

## My Approach
> General solution is :
> 	sort the array , then for each element ai , search if all the multiples of ai<=k are there in the array. if you find the multiples ok , ai is now one of the answer. if you dont find for one element you stop and print -1
> 
> some nuance: 
> 	They asked you to minimize the size of the answer array . so what you have to do is , sort the given array first, so you can find all the multiples of the smaller numbers and usually smaller number will remove more numbers from the array , as a result , we will get one element for more numbers . 
> 	
> 	Another thing is complexity, you cant search for each element , that would make it O(n^2). so you should shrink your search space by removing the multiples of the current element from the search space. For this you have to keep a log of which element are searchable, formally , you have to keep a map of the elements. 





---

## Dead Ends
> 1. Working with gcd, or lcm . 
> 2. looking for each multiple. 



---

## Explanation (Step 4)
> So the statement , is , you are given an array of numbers  a and a limit k . 
> now you have to generate an array b , where 
> 1. there has to be at least one divisor of each element of given array in the  array b.
> 2. each element of b has to have all the multiples from bi to k . 
> 3. you have to minimize the size of the array b. 
>    
>    thats it. thats the thing written in the problem statement. 
> now how do we combine them into one mathematical model ? 
> now lets see an example, you are given this array 8 2 4,6 7 and k = 9 . 
> lets say you pick 8 , what are the divisors of it ? 1 , 2 , 4 , 8 . now if you pick , 1 as a divisor, there has to be all multiple of 1 from 1 to multiple <= k. so as you can see , you can only use the divisors that are already in the array . now you can use 8 ,  and it will pass the case , but its actually not optimal , it wont produce the smallest b array . so which divisor to take that will take the most multiple ? yes the smallest one that is present in the array . so we can say that we always have to take the smallest element of the array and work on it because that is optimal . Thats why we will sort the array . 
> 
> now for each element we will check if there are all multiples smaller or equal to k is present or not. if not , then we can just stop the search and say -1. During the search we will keep a log of the multiples we searched, so we dont search again . I used map for it. and if you see that there are all multiple for the current element you just push it to b . if all goes well , just print b , thats it. 



---

## Code
```cpp
#include<bits/stdc++.h>
using namespace std;

#define ll long long 

void solve(){
    int n,k;
    cin>>n>>k;
    vector<int>a(n);
    map<int,int>b; // search area map. 
    map<int,int>m; // attendance map. 
    for(int i = 0;i<n;i++){
        cin>>a[i];
        m[a[i]]++;
        b[a[i]]=1;
    }
    sort(a.begin(),a.end());
    vector<int>ans;
    bool ok = true;
    for(int i =0;ok && i<n;i++){
        if(b[a[i]]!=0){
            for(int j = 1;(a[i]*j)<=k;j++){
                if(m[a[i]*j]>0){
                    b[a[i]*j]=0; // i dont have to search for it .
                }
                else{
                    ok = false;
                    break;
                }
            }
            if(ok)ans.push_back(a[i]);  
        }  
    }
    if(ok){
        cout<<ans.size()<<endl;
        for(auto i: ans)cout<<i<<" "; cout<<endl;
    }
    else cout<<-1<<endl;
}
int main(){
    int t;
    cin>>t;
    while(t--)solve();
}
```

---

## Review Log
| Date           | Result      |
| -------------- | ----------- |
| 27-05-2026     | first solve |
| [[2026-05-30]] | 1st review  |
