## Meta
| Field          | Value                                                     |
| -------------- | --------------------------------------------------------- |
| 🔗 Link        | [2170B](https://codeforces.com/problemset/problem/2170/B) |
| ⭐ Difficulty   | 1200                                                      |
| 📅 Date solved | 28-05-2026                                                |
| ⏱ Time spent   | 3hr                                                       |
| 🧠 How solved  | #editorial I was into a dead end                          |
| ✅ Confidence   | Needs review                                              |
| ❌ WA count     | 4                                                         |

---

## Classification
- **Tags:** #math #numbertheory #constructive 

---

## Key Insight
> The only thing that would stop you from getting the longest length, is extra operations that we have to see how much we can waste on other . 



---

## Signal
> This problem is kinda greedy approach . you always want to get the fullest length, but check whats your diminishing factor , you can call it limiting factor. 



---

## My Approach
> I actually got a too much bit into the details, that i forgot to see the invariant of the problem . You dont need to simulate the whole process to know if you can do a thing or not . you can just look for , what are the factors that can stop me from getting what i want. 
> what i did was i tried to simulate the whole scenario to take decision made a whole bunch of code for it  , but it didnt pass the initial filter, and i was kinda stuck . so saw the editorial. 



---

## Dead Ends
> 1. trying to simulate a greedy problem is kinda ineffective. 
> 2. i dont have any other dead ends in mind rn , any O(n^2 ) wont work thats for sure. 



---

## Explanation (Step 4)
> You are given an array b . and another array whose all elements are 0 . you can choose a length of sequence and increment all of them by 1. you are given n increment operation , you have to strictly use it. and doing this you have to find whats the longest sequence you can run your increment operation . 
> 
> as the max longest operation you can do is the length of the nonzero array of b. your target is to do this. but you are stuck with strict n use , sometimes n can be as big as the sum of the whole array , meaning you can only do operation on a single element each time. so n is the limiting factor on which depends if you would be able to do the longest operation or not . 
> 
> so how would we know whats the max length we can work on ? 
> see, each x length of operation adds x to the sum . 
> as we have n operation , we need only 1 operation for whole sequence wise operation . so we have to minimize what n-1 operation contributes to the sum. thats why we chose their length as 1. so n-1 operation , would contribute n-1 to the sum , and we have rest of the sum to make with whole length wise operation . we dont need to know  if one length wise operation can cover up the whole gap . if they are bigger than length of the nonzero array , we know we can do a full length ass operation on that thats it. 



---

## Code
```cpp
#include<bits/stdc++.h>
using namespace std;

#define ll long long 

void solve(){
        ll size;
        cin>>size;
        vector<ll>a;
        ll x;
        ll sum = 0; 
        for(int i =0;i<size;i++){
            cin>>x;
            sum+= x; 
            if(x)a.push_back(x);
        }
        ll nonzero= a.size();
        ll ans = min(nonzero,sum-size+1);
        cout<<ans<<endl;
        
}
int main(){
    int t;
    cin>>t;
    while(t--)solve();
}
```

---

## Review Log
| Date | Result |
|------|--------|
| 28-05-2026 | first solve |
