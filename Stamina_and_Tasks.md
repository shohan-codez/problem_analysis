## Meta
| Field          | Value                                                     |
| -------------- | --------------------------------------------------------- |
| 🔗 Link        | [2208C](https://codeforces.com/problemset/problem/2208/C) |
| ⭐ Difficulty   | 1300                                                      |
| 📅 Date solved | 23-05-2026                                                |
| ⏱ Time spent   | 4hr                                                       |
| 🧠 How solved  | most of the thought by me, but at the end i used #AI      |
| ✅ Confidence   | stil needs more review                                    |
| ❌ WA count     | 0                                                         |

---

## Classification
- **Tags:** #DP

---

## Key Insight
> if you go from the right to left , you can find subproblems already done for you , which makes it a dp problem. if you choose to use the element, the result get affected by like this 
>  point = c[i] + (1-p[i]/100)*prev 
>  so all you have to do is come from the right calculating prev earlier . basically modification of kadanes algorithm , or just dp. kadanes algorithm had the option to go back and forth , but this cant go back.  



---

## Signal
> if the current choice has some gains, and also have consequence for the later to choose globally optimum , you apply dp from the right to left. just know first choices contributes to the global optimum. 



---

## My Approach
> I first spent about 1 hours to just think of the decision tree , about how each decision goes to the end. although it had some dp sense , but i felt like this would create time limit for 10^5 . then i thought that , this type of massive tree could have been solved by kadane's algorithm. so i learned how kadanes algorithm actually works, and tried to understand how i can fit this problem into kadanes algorithm. my last aproach before consulting with ai was this 
> 
	start from the right. 
	take best of c[i] ,  c[i]+ (1-p/100)prev  , prev ; where prev is the last c[i+1]+(1-p[i+1])*(previous prev) . 
	basically , we only take c[i] , or the whole sequence , just skip it. 
	what i did wrong is taking c[i] , thats it , it would be max(prev, c[i]+(1-p/100)*prev) thats it . 



---

## Dead Ends
> thinking left to right. you should think from the right to left , that way you already know the future. 



---

## Explanation 
> The problem is basically about , you have a sequence of choice, each choice has some gain , and also has some cost. all you have to think about is if i take this choice at hand , how would it work out at the end of the day ? 
> the consequence after choosing the current choice is , point = c[i] + (1-p/100) X rest. 
> now as you dont know the rest , in order to know rest you have to come backwards. 
> lets give you an example 
> c1 c2 c3 c4 c5 
> p1 p2 p3 p4 p5 
> now in order to know what happens to the points after choosing the first choice.
>  points = c1 + (1-p1/100)x rest , rest means whatever the result of the choice we will make later. but as we always take the same decision , the rest will be the same. 
>  if we have taken all the choice lets see how the points look . 
>  points = c1 + (1-p1/100) c2 + (1-p1/100)(1-p2/100) c3 + (1-p1/100)(1-p2/100)(1-p3/100) c4+ (1-p1/100)(1-p2/100)(1-p3/100)(1-p4/100) c5. [can you see the pattern ?]
>  
> 	   =  c1 + (1-p1/100)(c2 + (1-p2/100)c3 + (1-p2/100)(1-p3/100) c4 + (1-p2/100)(1-p3/100)(1-p4/100) c5)
>    i think you get the idea that in order to calculate current i should know the rest. thats why keep calculating the rest from the back . and for each time coming from the back we said , either we take you or we skip you and this way just finding the global maximum. 

	i actually enjoyed this problem , got to learn something new. 



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
        vector<long double>c(size);
        vector<long double>p(size);
        for(int i =0;i<size;i++){cin>>c[i];cin>>p[i];}        
        long double prev = c[size-1];
        long double newprev ;
        for(int i =size-2;i>=0;i--){
            newprev = c[i]+(1.0-(p[i]/100.0))*prev;
            prev = max(newprev,prev);
        }
       cout<<fixed<<setprecision(10)<<prev<<endl;
    }
   
    

}

```

---

## Review Log
| Date           | Result      |
| -------------- | ----------- |
| 23-05-2026     | first solve |
| [[2026-05-30]] | 1st review  |
