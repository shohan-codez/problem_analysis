## Meta
| Field          | Value                                                  |
| -------------- | ------------------------------------------------------ |
| 🔗 Link        | [2280B](https://codeforces.com/contest/2208/problem/B) |
| ⭐ Difficulty   | #-1100                                                 |
| 📅 Date solved | 22-05-2026                                             |
| ⏱ Time spent   | 3hr                                                    |
| 🧠 How solved  | mostly solo , but took help of #AI after 3rd wa        |
| ✅ Confidence   |                                                        |
| ❌ WA count     | 8                                                      |


---

## Classification
- **Tags:** #greedy #math 

---

## Key Insight
> Only the first time you have to remove k-p smallest card till you get the win card, but after that operation , you have to take n-k smallest cards , and after the first operation the cost is always the same. 



---

## Signal
> if each turn costs actually the same according to the minimizing cost condition , we can just divide total cost with each run cost. 



---

## My Approach
> As my solution was not fully correct, i will tell you the part i worked. the problem said , each card has a cost, and given array of cost, i can just use them as cards , this way things will get much easier. then i thought , that i can take any elements from first k numbers till i get the p. wherever from i take , p always moves in front. so i thought , i can just keep taking the kth number each time till i get p , or i can get numbers from 1 to k , both i can do. so the range to take numbers from is not 1 to k , its 1 to p . and to minimize cost,i will sort 1 to p , and take p-k elements from the first. thats it for the first time to get wincard. now we can do two thing, either remove those elements or zero them out. all the cards goes to the back. so i called them firstsum. and this will look like this 
> (numbers that are bigger than firstsum)-> x | (numbers after p)-> y  | (firstsum) | p
> after that i will take the minimum numbers from x and y and create secondsum and remove them to make the first element of the firstsum come to kth position. now these whole thing comes back to square. and now i can say that for rest turn , total cost will be 
>  totalcost = firstsum + wincost + secondsum , i thought if i do m/totalcost then i would get to answer , but turns out i was wrong to an extent. i didnt observed the statement more . Thats why faced so much WA. 


---

## Dead Ends
> ❌ **Attempt:** Used firstsum + secondsum + wincost as the cycle cost, divided m by it → **Why wrong:** firstsum is only paid once (first play), not every cycle. After first play, those cards cycle back into the pool so cycle cost is just cheapest n-k cards + wincost.


---

## Explanation (Step 4)
> what problem said: you are given some cards with cost, and you want to use one wanted card the most time , but you are not allowed to cost more than a limit and you cant use the wanted card if its not in the allowed range . all you can do is keep taking numbers from the allowed range so that desired cards come to the allowed range.  so what means in order to use the wanted card most time with the lowest cost you have to keep choosing smallest numbers in the range so that desired card comes the most. after first operation the cost becomes fixed, so we can just divide with the total cost and get answer, so the whole problem boils down to find that repeating cost. after pushing back the p-k smallest element from the 1 to p , the p actually becomes at the last. so now in order to bring p to k , we have to remove smallest n-k elements from the sequence excluding p. this is the circular cost. thats it. 



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
      int n,k,p,m;
      cin>>n>>k>>p>>m;
      vector<int>v(n);
      for(int i =0;i<n;i++)cin>>v[i];
        int firstsum = 0; 
        int secondsum = 0;
        if(k==n){
            cout<<m/v[p-1]<<endl;
            continue;
            
        }
        sort(v.begin(),v.begin()+(p-1));
        int wincost= v[p-1];
        int zero = 0;
        for(int i =0;i<(p-k);i++){
            firstsum += v[i];
          
        }
        firstsum += v[p-1];
        v[p-1] = 0;
        sort(v.begin(),v.end());
        int count = 0;
        for(int i = 0; i < n && count < (n-k); i++){
            if(v[i] != 0){ secondsum += v[i]; count++; }
        }
        int totalsum = secondsum+wincost;
        int ans =0;
        if(firstsum<=m)
        ans = 1 + (m-firstsum)/totalsum;

        cout<<ans<<endl;
    }
   
    

}

```

---

## Review Log
| Date       | Result      |
| ---------- | ----------- |
| 22-05-2026 | first solve |
