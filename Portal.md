## Meta
| Field          | Value                                                  |
| -------------- | ------------------------------------------------------ |
| 🔗 Link        | [2200D](https://codeforces.com/contest/2200/problem/D) |
| ⭐ Difficulty   | 1300                                                   |
| 📅 Date solved | 27-05-2026                                             |
| ⏱ Time spent   | 3hr                                                    |
| 🧠 How solved  |  key insight by #AI                                    |
| ✅ Confidence   | i should review it again in this month                 |
| ❌ WA count     | 2                                                      |

---

## Classification
- **Tags:** #greedy #sorting
---

## Key Insight
> The numbers in side the portal will never come outside, and you can always rearrange them , number outside the portal, you can not rearrange them , only choose how much of that you want to print before the inner numbers to make it lexicographically smallest. 



---

## Signal
> In order to make lexicographically smallest sequence , you have to greedily find whats the smallest number and how you can put it in the front. 



---

## My Approach
> I was actually talking with Gemini about metacognition , and how i will apply it during the problem solving, for that we used this problem , but unfortuanately it spilled an insight that , the numbers inside the portal will never get outside , and number outside the portal will never get inside. Although i didnt want it to give me insight , but i accidentally read it , and it got stuck, so implemented the solution , even after having the insight , it took some time to implement the solution , i was stuck with the idea that i can rotate the outer numbers too, but turns out i cant. so my understanding of the math model was wrong. during the coding phase , several times it happened that , i deleted whole code , so i can write more clearly again .This was an easier version , because its a permutation array , if it wasnt , it would be more hard. 
> 
	Anyways i am nowadays thinking more about improving my metacognition , maybe i will try to put my thoughts on it in any different blog. 



---

## Dead Ends
> 1. trying to simulate it. that would be naive approach O(n^2). 
> 2. DP or brute force wont work here. 



---

## Explanation (Step 4)
> You are given a permutation array, and also given two portals position inside the array , through the portal , you can move numbers in such a way that , the numbers inside the portal can rotate, and numbers outside the portal can move further or backward. They asked you to move elements such way through the portal that it becomes the lexicographically smallest permutation , 
> 
> what they are saying is you will given an array , and some range of where you can do what with the numbers, according to their rule sort the array , thats it. 
> 
> now how do you make an array lexicographically smallest? make the smallest number come to the front, thats it right ? now in order to get the smallest permutation , what do you have to ensure? 
> 
> that , smallest numbers are in the front ! now as you have some rules, you can rotate the outer numbers , you can only choose to write the sequence at the front or nah. before that lets work with the inner numbers , you can rotate them. means you can start printing  from the smallest number and print till the last of the array , and if there are numbers that are left in the array , print them from the start, you are done with the inner numbers. for the outer numbers , write out the outer number that are  smaller than the smallest number of inner numbers.  and after the writing of the inner numbers , write out the rest of the outer numbers. 
> 
> Mathematical expression , given two different array , where one array is non rotatable and other is rotatable , find the smallest array representation . 



---

## Code
```cpp
#include<bits/stdc++.h>
using namespace std;

#define ll long long 

void solve(){
    int n,x,y;
    cin>>n>>x>>y;
    vector<int>v(n);
    for(int i =0;i<n;i++)cin>>v[i];
    int innermin = 10e6;
    vector<int>outershell;
    vector<int>innershell;
    int innerminpos =0;
    for(int i =x;i<y;i++){
        innermin = min(innermin,v[i]);
        innershell.push_back(v[i]);
    }
    for(int i = 0;i<x;i++)outershell.push_back(v[i]);
    for(int i =y;i<n;i++)outershell.push_back(v[i]);
    for(int j = 0;j<innershell.size();j++){
        if(innershell[j]==innermin)innerminpos = j;
    }
     int i = 0;
    for(i ;i<outershell.size() && outershell[i]<innermin;i++)
	    cout<<outershell[i]<<" ";
    for(int j = innerminpos;j<innershell.size();j++)
	    cout<<innershell[j]<<" ";
    for(int j = 0;j<innerminpos;j++) 
	    cout<<innershell[j]<<" ";
    for(i;i<outershell.size();i++)
	    cout<<outershell[i]<<" ";
	cout<<endl;
    
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
