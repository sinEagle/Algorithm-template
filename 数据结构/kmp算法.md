[Acwing 831. KMP字符串](https://www.acwing.com/problem/content/833/)

### C++

```cpp
#include <iostream>

using namespace std;

const int N = 100010, M = 1000010;

int n, m;
int nxt[N];
char s[M], p[N];

int main() {
    cin >> n >> p + 1 >> m >> s + 1;
    
    for(int i = 2, j = 0; i <= n; i ++) {
        while(j && p[i] != p[j + 1]) j = nxt[j];
        if(p[i] == p[j + 1]) j ++;
        nxt[i] = j;
    }
    
    for(int i = 1, j = 0; i <= m; i ++) {
        while(j && s[i] != p[j + 1]) j = nxt[j];
        if(s[i] == p[j + 1]) j ++;
        if(j == n) {
            //匹配成功
            printf("%d ", i - n);
            j = nxt[j];
        }
    }
    
    return 0;
}

```

### Java

```java
import java.util.*;
import java.io.*;

class Main {
    private static final int N = 100010;
    private static final int M = 1000010;
    private static int[] nxt = new int[N];
    private static BufferedReader in = new BufferedReader(new InputStreamReader(System.in));
    private static BufferedWriter out = new BufferedWriter(new OutputStreamWriter(System.out));
    public static void main(String[] args) throws IOException {
        int n = Integer.parseInt(in.readLine());
        String s1 = " " + in.readLine();
        int m = Integer.parseInt(in.readLine());
        String s2 = " " + in.readLine();
        char[] p = s1.toCharArray();
        char[] s = s2.toCharArray();
        
        for(int i = 2, j = 0; i <= n; i ++) {
            while(j != 0 && p[i] != p[j + 1]) j = nxt[j];
            if(p[i] == p[j + 1]) j ++;
            nxt[i] = j;
        }
        for(int i = 1, j = 0; i <= m; i ++) {
            while(j != 0 && s[i] != p[j + 1]) j = nxt[j];
            if(s[i] == p[j + 1]) j ++;
            if(j == n) {
                out.write(i - n + " ");
                j = nxt[j];
            }
        }
        out.flush();
        
    } 
}
```

### Python

```python
def solve(n, p, m, s, nxt):
    j = 0
    for i in range(2, n + 1):
        while j and p[i] != p[j + 1]:
            j = nxt[j]
        if p[i] == p[j + 1]:
            j += 1
        nxt[i] = j
    j = 0
    for i in range(1, m + 1):
        while j and s[i] != p[j + 1]:
            j = nxt[j]
        if s[i] == p[j + 1]:
            j += 1
        if j == n:
            print(i - n, end=' ')
            j = nxt[j]

if __name__ == "__main__":
    n = int(input())
    p = ' ' + input()
    m = int(input())
    s = ' ' + input()
    
    nxt = [0] * 100010
    solve(n, p, m, s, nxt);
```



