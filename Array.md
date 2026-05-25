## Meta
| Field          | Value                                                  |
| -------------- | ------------------------------------------------------ |
| 🔗 Link        | [2209B](https://codeforces.com/contest/2209/problem/B) |
| ⭐ Difficulty   | 900                                                    |
| 📅 Date solved | 26-05-2026                                             |
| ⏱ Time spent   | 1hr                                                    |
| 🧠 How solved  | #me                                                    |
| ✅ Confidence   | strong                                                 |
| ❌ WA count     | 0                                                      |

---

## Classification
- **Tags:** #greedy 

---

## Key Insight
> the problem supports O(n^2). for each index i calculate two things. x = number of element that are bigger than v[i]. y = elements that are smaller than v[i]. then take max of them. 



---

## Signal
> They asked to maximize the number of elements for which we can get | ai-k | > | aj - k |
	so you have to find for what k , you get the maximum number of elements. 


---

## My Approach
> i actually first went for the deadend number 1 . then saw that my output is not getting same with them, then i thought more , and saw that , i have to choose k in such a way that i get to bag most of the elements. so how do i choose k , so that i get max value ?



---

## Dead Ends
> 1. trying to work other way around, like first finding how much if there is more negative or more positive in the consequence. that wont work . 
> 2. They asked to maximise the reward by choosing such k , not the maximum reward i can get for the worst case of k . 



---

## Explanation (Step 4)
> so they will give you an array , for each index i , you have to maximize number of  elements after i , for which this becomes true.  | ai-k | > | aj - k | for any k . so you have to choose k such a way that you can take more elements. Basically a greedy approach . Actually we dont have any requirement for k , k is actually useless. k depends on something . what is that? 
> if i see there are more elements that are smaller than my current candidate, what will be the k? 
> i will choose a positive value of k , so now i can actually take all the elements smaller than my candidate. see ? k was never a problem . likewise, i will also find the elements bigger than my current candidate, and now i will take whats more , either number of bigger elements , or number of bigger elements. hmm which one should i take ? 



---

## Code
```cpp
#include <bits/stdc++.h>
using namespace std;
#define op() ios_base::sync_with_stdio(false);cin.tie(NULL);

#define ll long long

int main(){
    op();
    ll t;
    cin>>t;
    while(t--){
     ll size;
     cin>>size;
     vector<ll>v(size);
     for(int i=0;i<size;i++)cin>>v[i];
    int smaller = 0;
    int bigger = 0;
    for(int i =0;i<size-1;i++){
        smaller = 0;
        bigger = 0;
        for(int j =i+1;j<size;j++){
            if(v[i]>v[j])smaller++;
            else if(v[i]<v[j])bigger++;
        }
        cout<<max(smaller,bigger)<<" ";
    }
    cout<<0<<endl;
   }
}

```

---

## Review Log
| Date | Result |
|------|--------|
| 26-05-2026 | first solve |
