## Meta
| Field          | Value                                                     |
| -------------- | --------------------------------------------------------- |
| 🔗 Link        | [2197B](https://codeforces.com/problemset/problem/2197/B) |
| ⭐ Difficulty   | 1100                                                      |
| 📅 Date solved | 27-05-2026                                                |
| ⏱ Time spent   | .5 hr                                                     |
| 🧠 How solved  | #me                                                       |
| ✅ Confidence   | High                                                      |
| ❌ WA count     | 0                                                         |

---

## Classification
- **Tags:** #math #implementation
---

## Key Insight
> In the a array , let x is situated before the y , but in the permutation array , x is situated after y. then its not possible to generate a from the permutation . 


---

## Signal
> For this type of problem , finding for what cause , we have to print NO is more effective. 



---

## My Approach
> My first thought was , as its a yes no problem , and i am also not told to minimize the operation , so i have no limits. Then i looked for any constraints on the problem that might help me to find for what condition it would be a "NO". I mistook a little , i thought that , i cant operate on the last element , but later saw that i can . After working with some examples, i found out that you cant bring a number over another number, which means , you cant have a number in a , that comes later in the permutation array , thats it , implemented it . 



---

## Dead Ends
> 1. O(n^2) approach wont work like  trying to simulate it . 
> 2. you cant always look for the index in right time. that would be a naive approach . you have to keep something like map . 




---

## Explanation (Step 4)
> you are given a permutation array  P and a normal array a of same size, you can choose to copy one element into the next element in the permutation array , formally 
> you can do pi = pi+1     or      pi+1 = pi. 
> means you can duplicate items in the permutation array , now can you make this duplicate operation and make it look like the normal array ?
> 
> let us take two element from  array a. lets call them a3 and a5 , so first number is at 3rd index and second number is at 5th index. now they are also in the permutation array , lets say a3's index in Permutation array is x, and a5s index in permutation array is y . if a3->x > y <- a5 
> only then things wont work . if the whole array passes this condition , we are ok to say yes, otherwise no. 



---

## Code
```cpp
#include<bits/stdc++.h>
using namespace std;

#define ll long long 

void solve(){
    int n;
    cin>>n;
    vector<int> p(n);
    vector<int>a(n);
    map<int,int>m; //keeping index of elements of p for quick look up . 
    for(int i = 0;i<n;i++){
        cin>>p[i];
        m[p[i]]=i;
    }
    for(int i =0;i<n;i++)cin>>a[i];
    bool ok = true;
    for(int i =0;i<n-1;i++){
        if(m[a[i]]>m[a[i+1]]){
            cout<<"NO"<<endl;
            ok = false;
            break;
        }
    }
    if(ok) cout<<"YES"<<endl;
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
| 27-05-2026 | first solve |
