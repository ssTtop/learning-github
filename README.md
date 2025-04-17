# learning-github


### Solution

    #include <bits/stdc++.h>

    using namespace std;
    
    typedef long long ll;
    
    const ll maxn = 1e5 + 5;
    const ll inf = 1e9;
    
    ll arr_x[maxn], arr_y[maxn], rsq_x[maxn], rsq_y[maxn];
    
    int main() {
        ios_base::sync_with_stdio(0);
        cin.tie(0);
    
        ll n, m, q;
        cin >> n >> m >> q;
        for (int i = 0; i < n; i++) {
            cin >> arr_x[i];
        }
        for (int i = 1; i <= n; i++) {
            cin >> rsq_x[i];
            rsq_x[i] += rsq_x[i - 1];
        }
        for (int i = 0; i < m; i++) {
            cin >> arr_y[i];
        }
        for (int i = 1; i <= m; i++) {
            cin >> rsq_y[i];
            rsq_y[i] += rsq_y[i - 1];
        }
        for (int i = 0; i < q; i++) {
            ll a, b, k;
            cin >> a >> b >> k;
            ll l = -inf, r = inf;
            while (l < r) {
                ll mid = l + (r - l) / 2;
                ll sumx = rsq_x[upper_bound(arr_x, arr_x + n, mid) - arr_x];
                ll sumy = rsq_y[upper_bound(arr_y, arr_y + m, (mid - b) / a) - arr_y];
                if (sumx + sumy < k) {
                    l = mid + 1;
                }
                else {
                    r = mid;
                }
            }
            cout << l << "\n";
        }
        return 0;
    }



