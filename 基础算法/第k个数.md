[Acwing786. 第k个数](https://www.acwing.com/problem/content/788/)





### C++

```cpp
#include <iostream>

using namespace std;

const int N = 100010;

int n, k;
int q[N];

int quick_sort(int l, int r, int k) {
    if(l == r) return q[l];
    int x = q[l], i = l - 1, j = r + 1;
    while(i < j) {
        do i ++ ; while (q[i] < x);
        do j -- ; while (q[j] > x);
        if(i < j) swap(q[i], q[j]);
    }
    int sl = j - l + 1;
    if (k <= sl) return quick_sort(l, j, k);
    else quick_sort(j + 1, r, k - sl);
    
}

int main() {
    cin >> n >> k;
    
    for(int i = 0; i < n; i ++ ) cin >> q[i];
    
    cout << quick_sort(0, n - 1, k) << endl;
        
    return 0;
}
```



### Python

```python
def quick_select(arr, l, r, k):
    if l >= r:
        return arr[l]
    i, j, x = l - 1, r + 1, arr[(l + r) >> 1]
    while i < j:
        while True:
            i += 1
            if arr[i] >= x:
                break
        while True:
            j -= 1
            if arr[j] <= x:
                break
        if i < j:
            arr[i], arr[j] =  arr[j], arr[i]
    sl = j - l + 1
    if k <= sl:
        return quick_select(arr, l, j, k)
    else:
        return quick_select(arr, j + 1, r, k - sl)

if __name__ == "__main__":
    n, k = map(int, input().split())
    arr = list(map(int, input().split()))
    print(quick_select(arr, 0, n - 1, k))
    
```



