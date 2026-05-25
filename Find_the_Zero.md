## Meta
| Field          | Value                                                     |
| -------------- | --------------------------------------------------------- |
| 🔗 Link        | [2209C](https://codeforces.com/problemset/problem/2209/C) |
| ⭐ Difficulty   | 1400                                                      |
| 📅 Date solved | 25-05-2026                                                |
| ⏱ Time spent   | .5hr                                                      |
| 🧠 How solved  | pure #editorial                                           |
| ✅ Confidence   | still need to work on this                                |
| ❌ WA count     | 3                                                         |

---

## Classification
- **Tags:**  #interactive #constructive 

---

## Key Insight
> if two index has the same number , then it has to be 0 . 
> if you take each pairs each time exluding 1st and 2nd index  , and still couldnt get 1 , then you , you check if 1st and 3rd index is unequal, and also check if 1st and 4th index is unequal , if we still couldnt get 1 , then the index has to be 2. 



---

## Signal
> As its a interactive problem , you have to funnel down your approach as such that , your wanted solution gets cornered each by each . Its like guessing someones mind with a binary search  approach that if this is not correct/incorrect then the solution is in this range.  



---

## My Approach
> I actually havent tried much with this problem , as its already a 1400 problem , and mainly i have never attempted interactive problem , But i actually had fun solving this.As i had very less idea how to filter down the result , i dont what its called in math term to reduce the search area according to answer , but it is what it is . hehe . but what i tried on my own is trying the pair approach , but couldnt go much further. as i was shortsighted on this problem . But i genuinely loved to know this new thing. GG 



---

## Dead Ends
> 1. trying all pairs. 
> 2. o(n^2) wont work , as at best you can use o(n+1). 



---

## Explanation (Step 4)
> let me grab my coffee. 
> kay, so as its a interactive problem . lemme tell you what is interactive problem . Its an interactive guessing game. you try to find the answer in  limited try. You have to ask such way that the guess becomes more obvious in that much try. 
> 
> this particular problem will give you a size n . Imagine there is an array of 2n size , where there 1 to n numbers . and n numbers of 0 . you will ask if ai and aj are equal or not . if equal they will say 1 if not they will say 0. if 1 , you already have found the index . because theres only two zero that can be same, theres not repeatation of numbers from 1 to n . 
> 
> you have n+1 ask, so you have to use it wisely . Think how you can narrow it down ? 
> if you take pairs of 2n , you will have n ask . if you go this way , they can never keep the 0 together because you will find it already . what if all 0s are tucked with each numbers . 
> so it can be this 
> 0 1 0 2 0 3 0 4 
> or 
> 1 0 2 0 3 0 4 0 
> 
> so after using the n choices of pairs. you check if 1st index and 3nd index are different .if they are same you got the answer . if not , ask if 1 and 4 is diferent , if yes there you go , if not then only possible answer is index 2. now notice , we have used query 1, 3 and query 1 4 after using n queries , so this is not possible .so whats the way? 
> see, we are checking 1 to 4 anyways, so why not start from 3 for the pair search . that way we would still have choices left to check 1, 3 and 1 ,4. 
> 
> I dont think if i succeed to explain it to you properly , well i am sure its not the best explanation, but i am really feeling happy to solve this problem , to experience something new (i am probably high xD ). 



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
      int n;
      cin>>n;
      int i = 1;
      int decision = -1;
      while(i<n){
        cout<<"? "<<2*i+1<<" "<<2*i+2<<endl;
        cout.flush();
        cin>>decision;
        if(decision==1)break;
        i++;
      }
      if(decision==1){cout<<"! "<<2*i+1<<endl;cout.flush();}
      else{
            cout<<"? "<<1<<" "<<3<<endl;
            cout.flush();
            cin>>decision;
            if(decision==1){cout<<"! "<<1<<endl;cout.flush();}
            else {
                cout<<"? "<<1<<" "<<4<<endl;
                cout.flush();
                cin>>decision;
                if(decision==1){cout<<"! "<<1<<endl;cout.flush();}
                else {cout<<"! "<<2<<endl;cout.flush();}

            }
      }
      
    }
}

```

---

## Review Log
| Date | Result |
|------|--------|
| 25-05-2026 | first solve |
