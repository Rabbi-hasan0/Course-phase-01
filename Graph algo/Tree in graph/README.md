<img src = "https://github.com/Rabbi-hasan0/Course-phase-01/blob/main/Graph%20algo/Graph-visual/4.png">

### DFS in Tree:
```c++
void dfs(int u, int p) {       // u is node and p is parent
    for(auto v: g[u]) {
        if(p != v) {
            dfs(v, u);          // v hocce child node and u hocce parent node
        }
    }
}
```

### Find Depth of node using dfs:

### Input:
````
7
1 2 
1 3
2 4 
2 5
3 6
3 7
````
```c++
#include <bits/stdc++.h>
#define print(x) cout << x << '\n'
#define int long long
using namespace std;

const int N = 1e5 + 7;
vector<int> g[N], depth(N);
void dfs(int u, int p) {
    depth[u] = depth[p] + 1;     // Node depth = (parent er depth + 1) kore dicci;
    for(auto v: g[u]) {
        if(p != v) {
            dfs(v, u);          // v hocce child node and u hocce parent node
        }
    }
}
int32_t main() {
    ios_base::sync_with_stdio(false);
    cin.tie(nullptr);
    int t = 1; //cin >> t;
    while(t--){
        int n; cin >> n;
        for(int i = 1; i < n; i++) {
            int u, v; cin >> u >> v;
            g[u].push_back(v);
            g[v].push_back(u);
        }
        dfs(1, 0);
        cout << "node = depth\n"; 
        for(int i = 1; i <= n; i++) {
            cout << "   " << i << " = " << depth[i] << '\n';
        } cout << '\n';
    }
    return 0;
}