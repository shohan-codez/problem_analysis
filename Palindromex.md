## Meta
| Field          | Value                                                  |
| -------------- | ------------------------------------------------------ |
| 🔗 Link        | [2227D](https://codeforces.com/contest/2227/problem/D) |
| ⭐ Difficulty   | 1200                                                   |
| 📅 Date solved | 04-06-2026                                             |
| ⏱ Time spent   | 2hr                                                    |
| 🧠 How solved  | #me                                                    |
| ✅ Confidence   | ok                                                     |
| ❌ WA count     | 0                                                      |

---

## Classification
- **Tags:** #greedy #brute-force #constructive 

---

## Key Insight
> you have to include 0 in your palindrome 



---

## Signal
> you have to take the best mex that is also a palindrome, there can be 3 ways you can make palindrome with 0



---

## My Approach
> check mex of the palindrome consisting only the first 0 , only the second 0 , and taking both . 



---

## Dead Ends
> only thinking that palindrome needs 2 zero strictly 



---

## Explanation (Step 4)
> count mex of the 3 palindrome. and take the best 



---

## Code
```cpp
#include <bits/stdc++.h>
using namespace std;
#define ll long long

void solve() {
    ll n;
    cin>>n;
    n+=n;
    vector<ll>a(n);
    for(int i=0;i<n;i++)cin>>a[i];
    ll firstpos=-1;
    ll secondpos = -1;
    for(int i=0;i<n;i++)if(a[i]==0){firstpos=i;break;}
    for(int i=firstpos+1;i<n;i++)if(a[i]==0){secondpos=i;break;}
    bool ok = true;
    ll best = 1; 
    // checking for the first zero
    vector<ll>a1;
    a1 = a;
    int i =0;
    while((firstpos-i-1)>=0 && (firstpos+i+1)<n && a[firstpos-i-1]==a[firstpos+i+1]){
        i++;
    }
    ll mex = 0;
    sort(a1.begin()+(firstpos-i),a1.begin()+(firstpos+i+1));
    for(int j =(firstpos-i);j>=0 && j<n && j<=(firstpos+i);j++){
        if(a1[j]==mex)mex++;
    }
    best = max(best,mex);
    // checking for the second zero
     vector<ll>a2;
    a2 = a;
    i =0;
    while((secondpos-i-1)>=0 && (secondpos+i+1)<n && a[secondpos-i-1]==a[secondpos+i+1]){
        i++;
    }
    mex = 0;
    sort(a2.begin()+(secondpos-i),a2.begin()+(secondpos+i+1));
    for(int j =(secondpos-i);j>=0 && j<n && j<=(secondpos+i);j++)if(a2[j]==mex)mex++;
    best = max(best,mex);
    //checking for both combination.... 
    ll length = secondpos-firstpos+1;
    for(int j =1;j<length/2;j++){
        if(a[secondpos-j]!=a[j+firstpos]){
            cout<<best<<endl;
            return;
        }
    }
    ll start = firstpos;
    for(int i =firstpos-1;i>=0;i--){
        if((i+length+1)<n && a[i]==a[i+length+1]){
            length+=2;
            start= i;
        }
        else break;
    }
    mex=0;
    sort(a.begin()+start,a.begin()+start+length);
    for(int i =start;i<(start+length);i++){
        if(a[i]==mex)mex++;
    }
    best =  max(best,mex);
    cout<<best<<endl;
}

int main() {
    ios::sync_with_stdio(0); cin.tie(0);
    int t; cin >> t;
    while (t--) solve();
    return 0;
} 
```

---

## Review Log
| Date | Result |
|------|--------|
| 04-06-2026 | first solve |
