## Meta
| Field          | Value                                                  |
| -------------- | ------------------------------------------------------ |
| 🔗 Link        | [2195C](https://codeforces.com/contest/2195/problem/C) |
| ⭐ Difficulty   | 1100                                                   |
| 📅 Date solved | 28-05-2026                                             |
| ⏱ Time spent   | 1hr                                                    |
| 🧠 How solved  | #me                                                    |
| ✅ Confidence   | Good                                                   |
| ❌ WA count     | 1                                                      |

---

## Classification
- **Tags:** #greedy #constructive 

---

## Key Insight
> You only need to change the elements that contradicts, so that the operation is minimal . 



---

## Signal
> You cant change the element which you used as a basis for the change of your current element, such that , after changing your basis element , current number doesnt satisfy condition. if this is the case , this is a constructive problem . 



---

## My Approach
> I actually got a wa on this for wrong approach. I thought i dont need constructive way to find how much operation i need. so i thought if i take each separate pair and check if they contradict or not and counting how much contradicting separate pair is there would be ok . but the problem is i havent thought about taking separate pair , you can miss a pair where it would have contradicted but you separated them and didnt see the contradiction. 
> later on after thinking , why would judge have answer as 1 , and i would have 0, found out that i am missing tihs simple thing. I think i should stop seeing verdicts of judges . Because them makes it easy to find wheres problem with my code. 



---

## Dead Ends
> 1. Trying to come up with number that doesnt contradict with neither previous nor the next element. Because coming up requires you to go through the numbers for which there wont be a contradiction and that is time consuming. and it would be a very heavy approach . 
> 2. any other o(n^2) approach . 



---

## Explanation (Step 4)
> So what the statement says is , you will be given a sequence of numbers, you have to ensure that all adjacent number let a, b . satisfies this    7-a != b or 7-b !=a. or a!=b
> now lets say 5 2 4 , now lets look at 5 2 pair, they are contradicting because 7-5 =2 , so we have to either change 5 or 2. now if we change 5 on the basis of 2, it might happen that next time you work with 2 4 , you might change 2. so it contradicts the law of constructivism. 
> so we have to change 2 here so that it doesnt contradict with 5. now we can choose any numbers less or equal than 6 except 2 itself. But we also have to think about 4 , because if we put 3 on the place, that would contradict with 4 in next move , causing more operation .  now we cant let it happen because they asked to minimize operation. But thinking what wouldnt contradict with the later element is resource heavy , so what can we do ? 
> we try an assumption method. we dont know what numbers to put in between , so it doesnt contradict with adjacent numbers. so we just get rid of the task of finding out which number it is , and just think that , we already got a number that doesnt contradict with the adjacent, so i used a number out of the working space , it can be 0 , it can be 100. you can use x agreeing that , x is a number that doesnt contradict with previous element nor contradicts with the later element. This way we completely got rid of finding for which number there wont be any contradiction.
> So you can say , i did have to use the constructive method .but its still a O(n) approach ig. 



---

## Code
```cpp
#include<bits/stdc++.h>
using namespace std;

#define ll long long 

void solve(){
    int n;
    cin>>n;
    vector<int>a(n);
    for(int i =0;i<n;i++)cin>>a[i];
    int cnt = 0;
    for(int i = 0 ; i<n-1;i++){
        if((a[i]==a[i+1]) || (a[i+1]==7-a[i]) || (a[i]==7-a[i+1])){a[i+1]=0;cnt++;}
    }
    cout<<cnt<<endl;
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
| 28-05-2026 | first solve |
