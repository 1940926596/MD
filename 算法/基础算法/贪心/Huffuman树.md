# Huffuman树

## 合并果子

在一个果园里，达达已经将所有的果子打了下来，而且按果子的不同种类分成了不同的堆。

达达决定把所有的果子合成一堆。

每一次合并，达达可以把两堆果子合并到一起，消耗的体力等于两堆果子的重量之和。

可以看出，所有的果子经过 n−1 次合并之后，就只剩下一堆了。

达达在合并果子时总共消耗的体力等于每次合并所耗体力之和。

因为还要花大力气把这些果子搬回家，所以达达在合并果子时要尽可能地节省体力。

假定每个果子重量都为 1，并且已知果子的种类数和每种果子的数目，你的任务是设计出合并的次序方案，使达达耗费的体力最少，并输出这个最小的体力耗费值。

例如有 3 种果子，数目依次为 1，2，9。

可以先将 1、2 堆合并，新堆数目为 3，耗费体力为 3。

接着，将新堆与原先的第三堆合并，又得到新的堆，数目为 12，耗费体力为 12。

所以达达总共耗费体力=3+12=15。

可以证明 15 为最小的体力耗费值。

## 优先队列解决

```cpp
#include<iostream>
#include<algorithm>
#include<queue>
#include<cstring>

using namespace std;

const int N=1e4+10;
int a[N];
int n;
priority_queue<int,vector<int>,greater<int>> q;
void huffman(){    
    int res=0;
    
    for(int i=0;i<n-1;i++){
        int a=q.top();
        q.pop();       
        int b=q.top();
        q.pop();   
        res+=(a+b);
        q.push(a+b);       
    }    
    cout<<res<<endl;
    
}

int main(){
    
    cin>>n;
    for(int i=0;i<n;i++){
        cin>>a[i];
        q.push(a[i]);
    }
    huffman();
    return 0;
}
```



