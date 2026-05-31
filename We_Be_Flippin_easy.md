## Meta
| Field          | Value                                                    |
| -------------- | -------------------------------------------------------- |
| 🔗 Link        | [2229C1](https://codeforces.com/contest/2229/problem/C1) |
| ⭐ Difficulty   | 900                                                      |
| 📅 Date solved | 24-05-2026                                               |
| ⏱ Time spent   | 1.5hr                                                    |
| 🧠 How solved  | only me.                                                 |
| ✅ Confidence   | High                                                     |
| ❌ WA count     | 2                                                        |

---

## Classification
- **Tags:** #math #greedy 

---

## Key Insight
> only take the position that has different signs. 



---

## Signal
> **Consecutive same-sign elements behave as one unit.** So reduce the array to alternating signs, then work backwards flipping from the last positive.



---

## My Approach
> first i tried a simple version of it , an array where there is only 1 , either -ve or +ve. if there is a +ve at the very last we have to flip it for sure. after this operation the closest -ve to the last will become +ve. so you have to find where is the position that has sign difference. thats it . i got wa because first i printed the array in wrong order. and then got wa because i should have counted sign diference till the last position . go to explanation to see more. 



---

## Dead Ends
> 1. O(n^2) wont work . if you try to simulate it during runtime you will get tle for sure. 
> 2. sorting wont work 
> 3. finding different position before finding the position that has the positive. 



---

## Explanation (Step 4)
> Simplified statement: you are given a sequence of +ve and -ve of lenght n. you choose an index that is +ve. then you flip the elements from 1 to that index. 
> 
> General solution : make all +ve signs -ve with minimal move possible. if there are some +ve together, they will change signs at the same time. so they will actually work like 1 sign, 
> so if you have sequence like this + - + + + - - - + - +  
> it can be reduced to this -> + - + - + - + so you can already see we only need to work with the position that has different signs. now we should start from the last. thats why we will find the last position of positive during input. we  include that to the position array . now we will start from the first and push positions that has difference . then just sort the array in a decreasing manner, and just print with the count of operation . It was really easy problem , i should have solved A,B,C of this contest.



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
        for(int i =0;i<size;i++){
            cin>>v[i];
            if(v[i]>0) position = i;
        }
        if(position==-1){
            cout<<0<<endl;
            continue;
        }
        int cnt = 1;
        vector<ll>pos;
        for(int i =0;i<position;i++){
		    if((v[i]>0 && v[i+1]<0)|| (v[i]<0 && v[i+1]>0){
			    pos.push_back(i+1);
			    cnt++;
		    }
        }
        pos.push_back(position+1);
        cout<<cnt<<endl;
        for(int i =pos.size()-1;i>=0;i--)cout<<pos[i]<<" ";
        cout<<endl;




    }
       
   
    

}
```

---

## Review Log
| Date           | Result      |
| -------------- | ----------- |
| 24-05-2026     | first solve |
| [[2026-05-30]] | 1st review  |
