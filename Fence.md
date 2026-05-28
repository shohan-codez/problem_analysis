## Meta
| Field          | Value                                                |
| -------------- | ---------------------------------------------------- |
| 🔗 Link        | [363B](https://codeforces.com/contest/363/problem/B) |
| ⭐ Difficulty   | 1100                                                 |
| 📅 Date solved | 28-05-2026                                           |
| ⏱ Time spent   | 20 min                                               |
| 🧠 How solved  | #me                                                  |
| ✅ Confidence   | High                                                 |
| ❌ WA count     | 0                                                    |

---

## Classification
- **Tags:** #sorting #greedy 

---

## Key Insight
> We need to find the sequence with length k , that has the minimum sum . 



---

## Signal
> As we have to find the minimum sum of k length, we just do what it is told. 



---

## My Approach
> We can do as its said , simple simulation , but finding sum of k sequence each time is tiresome, so i implemented a prefix sum method. wheret ith sum will be prefix[i] - prefix[i-k]
> thats it , if we find this is the minimum sum , we just say the starting position , which is i-k+1



---

## Dead Ends
>1. finding sum each time. 



---

## Explanation (Step 4)
> Explanation is same as my approach section . 



---

## Code
```cpp
#include<bits/stdc++.h>
using namespace std;

#define ll long long 

void solve(){
    ll n , k ;
    cin>>n>>k;
    vector<ll>a(n+1);
    for(int i =1;i<=n;i++)cin>>a[i];
    for(int i =1;i<=n;i++)a[i] += a[i-1];
    ll minsum = 16*10e6;
    ll position = 0;
    for(int i = k;i<=n;i++){
        if(minsum > a[i]-a[i-k]){
            minsum = a[i]-a[i-k];
            position = i-k;
        }
    }
    cout<<position+1<<endl;    
        
}
int main(){
    // int t;
    // cin>>t;
    // while(t--)
    solve();
}
```

---

## Review Log
| Date | Result |
|------|--------|
| 28-05-2026 | first solve |
