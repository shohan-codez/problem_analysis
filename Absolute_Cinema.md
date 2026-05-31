## Meta
| Field          | Value                                                  |
| -------------- | ------------------------------------------------------ |
| 🔗 Link        | [2229B](https://codeforces.com/contest/2229/problem/B) |
| ⭐ Difficulty   | #-800                                                  |
| 📅 Date solved | 24-05-2026                                             |
| ⏱ Time spent   | 1hr                                                    |
| 🧠 How solved  | Editorial                                              |
| ✅ Confidence   | OK                                                     |
| ❌ WA count     | 5                                                      |

---

## Classification
- **Tags:** #math #greedy 

---

## Key Insight
> take all numbers that are highest and sum. you only have to keep one number for a. thats why find the highest minimum each time to keep it in b. 



---

## Signal
> if they tells you to maximize the max(a)+sum of b , you have to take all highest numbers. sum += max(a,b); and just keep a number that is minimum highest in the a. that way you are taking the most reward. 



---

## My Approach
> This was a problem of spectral cup div1+2. although i was able to solve A , but couldnt solve B , tried several times. my approach was take the max all time . and then find the max that has the highest opposite value. add it with the sum. 
> 		sum+= max(a[i],b[i]);
           minmax = max(minmax,min(a[i],b[i]));
       with this bit of code , we are actually finding the highest opposite we rejected for b . 



---

## Dead Ends
> wrong : finding highest value opposite of the max, because max wont always have the highest opposite value. 
> Because you dont need to put max in a to have max(a)+sumof(b).



---

## Explanation (Step 4)
> This problem was really unintuitive for me . i dont know why i havent thought about what satisfies the optimum value. I mean how to get to the optimum value. 
> 
> so you are given two array of same size, array a and array b. you have to do maximize the 
> max(a) + sumofb
> for that you always take the highest of each index for b . thats how you optimize sumofb , and for max(a) find the highest value in a after swapping  . and that is your max(a); thats it. it could be solved more easily if you see what happens after you swap all the highest into b . You may think of keeping a max in a . but that doesnt have any diffrence , because you are doing max(a)+sumofb. so sumofb already will include that max(a) if you hadnt put that in a. 

let me put it more simply , you are asked to maximize this max(a)+sumofb . what is the condition of maximising this ? you take the best of both of the array for sumofb , and after doing that , you take best of whats left for a. thats it , you are taking best from the whole 2 array. that way you maximize the wholesum. 



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
       ll size;
       cin>>size;
       vector<ll>a(size);
       vector<ll>b(size);
       ll globalmax = 0;
       ll sum= 0;
       for(int i =0;i<size;i++)cin>>a[i];
       for(int i =0;i<size;i++)cin>>b[i];
        ll minmax = 0;
       sum = 0;
       for(int i =0;i<size;i++){
           sum+= max(a[i],b[i]);
           minmax = max(minmax,min(a[i],b[i]));
       }
            sum = sum+minmax ;
            cout<<sum<<endl;

    }
   
    

}

```

---

## Review Log
| Date           | Result      |
| -------------- | ----------- |
| 24-05-2026     | first solve |
| [[2026-05-30]] | 1st review  |
