## Meta
| Field          | Value                                                    |
| -------------- | -------------------------------------------------------- |
| 🔗 Link        | [2229C2](https://codeforces.com/contest/2229/problem/C2) |
| ⭐ Difficulty   | Dunno                                                    |
| 📅 Date solved | 24-05-2026                                               |
| ⏱ Time spent   | 2hrs                                                     |
| 🧠 How solved  | #editorial but i was almost there.                       |
| ✅ Confidence   | wouldnt be able to solve without help.                   |
| ❌ WA count     | 2 wa for minor presentation error                        |

---

## Classification
- **Tags:** #constructive #math 

---

## Key Insight
> Its basically an upgraded version of C1. you can make all the element negative before a +ve , and then just flip it . thats how you get to know what will be the value . 
> 



---

## Signal
> "When you can perform prefix flip operations and want to optimize a sum — think about what each flip achieves globally. If making a prefix negative then flipping gives you absolute values, try every valid flip point and use prefix/suffix arrays to find the optimal one in O(n)."



---

## My Approach
> I saw that , if we have a positive. we can make all negative before it , and then we can just flip all of it. and all we have to do is to know for which positive we have to do this . 



---

## Dead Ends
> 1. Thinking of implementing with dp .at first this sure as hell looks like dp but  dunno if it will work or not , havent tried it . 
> 2. literal greedy wont work. 
>  



---

## Explanation (Step 4)
> This problem have the same constraints like the easy version of it. but this time you have to maximise the sum . now you can only choose an index which has positive value. and from the c1 we will negate all the previous values. so the sum eventually becomes this 
> 
> prefix(abs(1 to x-1)) - x + suffixof(x+1 to n) 
> because after the operation this actually becomes the above equation . so now we have to find for which x, we get the maxsum . if we dont get any position it means there is all positive ,or there is all negative. 
> 
> after finding the position , we will apply tools of the easy version of this problem here. and find which position we have to flip to get all negative , and just mishmash them and viola!!!!!



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
        int size;
        cin>>size;
        vector<ll>v(size);
        ll position = -1;
        ll sum = 0;
        vector<ll>prefix(size);
        for(int i =0;i<size;i++){
            cin>>v[i];
            sum+= v[i];
        }
        ll best = sum;
        sum = 0;
        vector<ll>suffix(size);
        for(int i = size-1 ; i>=0;i--){ 
            sum += v[i];
            suffix[i]= sum; 
        }   
        sum = 0;
        for(int i =0;i<size;i++){
            sum += abs(v[i]);
            prefix[i] = sum;
        }    
         for(int i =1;i<size-1;i++){
            ll currentsum = prefix[i-1]+suffix[i+1]-v[i];
            if(currentsum>best && v[i]>0){
                position = i ;
                best = currentsum;
            }
        }
        if( v.back()>0 && (prefix[size-2]-v.back())>best){
            position = size-1;
        }
        if(position==-1){
            cout<<0<<endl;
            continue;
        }
         vector<ll>pos;
        for(int i =0;i<position-1;i++){
            if((v[i]>0 && v[i+1]<0)|| (v[i]<0 && v[i+1]>0)){pos.push_back(i+1);}
        }
        if(v[position-1]>0 && v[position])pos.push_back(position);
        reverse(pos.rbegin(),pos.rend());
        pos.push_back(position+1);
        cout<<pos.size()<<endl;
        for(auto i : pos)cout<<i<<" ";
            cout<<endl;
    }
}

```

---

## Review Log
| Date | Result |
|------|--------|
| 24-05-2026 | first solve |
