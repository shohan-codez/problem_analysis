## Meta
| Field          | Value                                                        |
| -------------- | ------------------------------------------------------------ |
| 🔗 Link        | [2230B](https://codeforces.com/contest/2230/problem/B)       |
| ⭐ Difficulty   | 1000                                                         |
| 📅 Date solved | 25-05-2026                                                   |
| ⏱ Time spent   | 2 hr                                                         |
| 🧠 How solved  | #editorial but my approach was satisfying 80% of the problem |
| ✅ Confidence   | Reviewed                                                     |
| ❌ WA count     | 3                                                            |

---

## Classification
- **Tags:** #greedy #math 

---

## Key Insight
> you want to keep the sequence as untouched as possible , find out whats that longest sequence. what would be the longest beautiful sequence? the longest beautiful sequence would be the one , that has the most even in the left and most odd in the right. 



---

## Signal
> idk what to write in the signal , because this problems always has some nuance , so generalization doesnt work ig. 



---

## My Approach
> As i have to remove elements such way that no subsequence can be generated that is multiple of 4. so 4 gets removed first. its must. Then i saw if i remove 4 , for what condition a subsequence can be multiple of 4. that is if the 2 is after an odd. so there cant be no even after odd, or no odd before even. 
> 
> so i found the first position of the odd. and the last position of 2. then i calculated how many odd i have to remove till the last 2. or how many 2 i have to remove after the first odd. 
> then i take the minimum of them and add the count of 4 
> 
> this approach works for most of the case , but seems like its not the optimal solution. 



---

## Dead Ends
> 1. O(n^2) way , where you find each subsequence and count how many even on the left and how many odd on the right. 
> 2. My approach , because there are some cases , idk , where my solution is not optimal. 
> 



---

## Explanation (Step 4)
> As you already know , we have to just find the longest sequence where we have most even on the left and most odd on the right , so the sequence lenght will be for each index: number_of_2_on_the_left + number_of_odd_on_the_right. 
> in order to not get tle, you have to have a prefix of even , and suffix of odd. 
> 
> which means you have to keep count for each sequence , of how much 2 is there on the left till now , and how much odd is there on the right till now . we took only 2 as even because we will remove the 4 anyways, so neglected them . 
> 
> then for each index you take the best length, and if you subtract the best length from original lenght , you will find out how many element to remove. There you go!!!!



---

## Code
```cpp
#include <bits/stdc++.h>
using namespace std;
#define op() ios_base::sync_with_stdio(false);cin.tie(NULL);

#define ll long long 
#define endl '\n'

int main(){
    op();
    ll t;
    cin>>t;
    while(t--){
        string s;
        cin>>s;
        vector<ll>even;
        vector<ll>odd(s.length());
        int evencnt = 0;
        int oddcnt =0;
        for(int i =s.length()-1;i>=0;i--){
            if(s[i]=='1' || s[i]=='3')oddcnt++;
            odd[i]=oddcnt;
        }
        for(int i =0;i<s.length();i++){
            if(s[i]=='2')evencnt++;
            even.push_back(evencnt);
        }
        ll length= 0;
        for(int i =0;i<s.length();i++){
            length = max(length,(even[i]+odd[i]));
        }
        cout<<s.length()-length<<endl;
      
    }
}

```

---

## Review Log
| Date           | Result      |
| -------------- | ----------- |
| 25-05-2026     | first solve |
| [[2026-05-30]] | 1st review  |
