## Meta
| Field          | Value                                                     |
| -------------- | --------------------------------------------------------- |
| 🔗 Link        | [1873E](https://codeforces.com/problemset/problem/1873/E) |
| ⭐ Difficulty   | 1100                                                      |
| 📅 Date solved | 29-05-2026                                                |
| ⏱ Time spent   | 2hr                                                       |
| 🧠 How solved  | #editorial                                                |
| ✅ Confidence   | Need another review                                       |
| ❌ WA count     | 1                                                         |

---

## Classification
- **Tags:** #binary-search #sorting 

---

## Key Insight
> Find , for a certain height , how much water can you accommodate.



---

## Signal
 If a height $x$ requires too much water (fails), then any height _greater_ than $x$ is guaranteed to fail even harder 



---

## My Approach
> I used a difference vector, to find , at each level how much cell is free , so i can accommodate water in them. although , this was a good approach , this can cause memory error, as the numbers are huge. 
> so after no finding way, headed over to editorial.. Found out it needs a binary search approach. 



---

## Dead Ends
> 1. Mathematical close form , h = (w+sumofa)/n wont work , it has flaw. 
> 2. finding each levels capacity using difference vector, it will cause memory error. 
> 3. for each height , finding water capacity using capacity = max(0,height-a[i]); you will get tle



---

## Explanation (Step 4)
> The main thing is to find the correct height that can allocate the water properly , now checking water capacity for each height will cause tle. so thats why used binary search , as we know , less height will have less capacity to offer , and more height will offer more capacity , we need to find for which height it is the optimum capacity. so we just implemented a binary search where low is the minimum height of the array . and high is the max water capacity . we also kept track of the answer as we dont know if our current water capacity will ever be met by any height , so to get the optimum height , we kept track of it. 



---

## Code
```cpp
#include<bits/stdc++.h>
using namespace std;

#define ll long long 

void solve(){
   ll n,w;
   cin>>n>>w;
   vector<ll>a(n);
   ll low = 2e9;
   for(int i =0;i<n;i++){cin>>a[i];low=min(low,a[i]);}
   ll high = 2e9;
     ll mid;
     ll ans=low;
   while(low<=high){
        mid= low+(high-low)/2;
        ll water = 0;
        for(int i =0;i<n;i++)water+= max( 0ll,mid-a[i]);
        if(water<=w){
            ans=mid;
            low = mid+1;
        }
        else high = mid-1;
   }  
   cout<<ans<<endl; 
}
int main(){
    int t;
    cin>>t;
    while(t--)
    solve();
}
```

---

## Review Log
| Date | Result |
|------|--------|
| 29-05-2026 | first solve |
