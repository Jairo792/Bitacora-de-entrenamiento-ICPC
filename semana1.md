
# Semana 1

Esta semana no pude resolver demasiados problemas, practicamente para todos tuve que usar test case generados y stress testing ya que no se me ocurrían los casos en los que mi solución fallaba.

## Ejercicio 1
- [Dungeon](https://codeforces.com/contest/2164/problem/C) --


Enunciado: 

Este ejercicio es similar al que nos explicó Agus la última clase, básicamente (enfrentar $$ m $$ cosas contra  $$ n $$ cosas), en este caso **monstruos vs espadas**.
Se menciona que una espada que tenga poder 
puede matar a un monstruo de salud $$ y $$ si y solo si $$ y <= x$$.

Se nos dan tres arreglos: \(a,b,c\)
- `a`: poder de las espadas  
- `b`: vida de los monstruos  
- `c`: se explica más adelante  

Después de matar a un monstruo de vida $$ y $$ , la espada $$ a_i $$ de poder $$ x $$ se destruye y, si $$ c_i > 0 $$, obtenemos una nueva espada de poder $$ max(x, c_i) $$.

**Output:** imprimir el mayor número de monstruos que puedes matar.



**Solucion:**
<details>
<summary><strong>Spoiler de la Solucion </strong></summary>
```cpp
#include <bits/stdc++.h>
using namespace std;
#define forr(i,a,b) for(int i=int(a);i<int(b);++i)
#define forn(i,n) forr(i,0,n)
#define dforr(i,a,b) for(int i=int(b)-1;i>=int(a);--i)
#define dforn(i,n) dforr(i,0,n)
#define fore(e,c) for(const auto &e : (c))
#define fst first
#define snd second
using ll = long long;
using ull = unsigned long long;
using ld = long double;
template<class T>ostream&operator<<(ostream&o,vector<T>const&v){o<<"[ ";for(auto const&x:v)o<<x<<" ";return o<<"]";}
template<class T,class U>ostream&operator<<(ostream&o,pair<T,U>const&p){return o<<"("<<p.fst<<", "<<p.snd<<")";}
template<class T>void maxa(T&x,T const&y){  x=max(x,y);  }
template<class T>void mina(T&x,T const&y){  x=min(x,y);  }
template<class T>void sort2(T&x,T&y){  if(y<x)swap(x,y);  }
template<class T>void sort3(T&x,T&y,T&z){  sort2(x,y);sort2(y,z);sort2(x,y);  }
#define RAYA cerr<<"===============================================\n"
/*
 #include<bits/stdc++.h>
using namespace std;
#define ll long long
const int MAXN=2e5+5;
int n,m;
struct node{int b,c;}a[MAXN];
void solve(){
	cin>>n>>m;
	multiset<int> S;
	for(int i=1;i<=n;i++){
		int x;cin>>x;S.insert(x);
	}
	int ans=0;
	for(int i=1;i<=m;i++) cin>>a[i].b;
	for(int i=1;i<=m;i++) cin>>a[i].c;
	sort(a+1,a+m+1,[&](node x,node y){
		if((x.c==0)^(y.c==0)) return x.c>y.c;
		return x.b<y.b;
	});
	for(int i=1;i<=m;i++){
		auto it=S.lower_bound(a[i].b);
		if(it==S.end()) continue;
		int x=*it;S.erase(it);
		ans++;
		if(a[i].c) S.insert(max(a[i].c,x));
	}
	cout<<ans<<'\n';
}
int main(){
	// freopen("Otomachi_Una.in","r",stdin);
	// freopen("Otomachi_Una.out","w",stdout);
	ios::sync_with_stdio(false);cin.tie(0);cout.tie(0);
	int T;cin>>T;
	while(T--) solve();
	return 0;
}
 **/
 
int main (){
  ios::sync_with_stdio(false);cin.tie(0);cout.tie(0);
  int tt;
  cin >> tt;
  
  forn(TT,tt){  
	 int n, m;
	 cin >> n >> m;
	 multiset<ll>espadas;
	 vector <ll> xd(n);
	 forn(i,n){
		ll x;
		cin >> x;
		xd[i] = x;
		espadas.insert(x);
	 }
	 vector<pair<ll,ll>> ms(m);
	 forn(i,m){
		cin >> ms[i].first;
	 }
	 forn(i,m){
		cin >> ms[i].second;
	 }
	 sort(ms.begin(), ms.end(),[&](pair<ll,ll>x,pair<ll,ll>y){
		 if(x.second == 0 && y.second != 0)
		    return false;
		 else if(x.second != 0 && y.second == 0)
			return true;
		 else {
			return x.first < y.first;
		 }
	 });
	 int ans = 0;
	 cerr << xd << '\n';
	RAYA ;
	 for(auto it: ms){
		cerr << it << '\n';
	 }
	 RAYA;
	 forn(i,m){
		auto it = espadas.lower_bound(ms[i].first);
		if(it == espadas.end())
		  continue;
		ans++;
		 ll v = *it;
		if(ms[i].second != 0){
		  espadas.erase(it);
		  espadas.insert(max(v,ms[i].second));	
		} else {
		  espadas.erase(it);
		} 
	 }
	 cout << ans << '\n';
  }
}
```
</details>


-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

**Errores que cometi:**

<details>
<summary><strong>Errores post Solucion </strong></summary>
Pense que si solamente ordenaba las espadas de mayor a menor, y luego ordenabamos los mounstruos de menor a mayor con su respectivo c_i podriamos solucionar el problema, pero claro esto es un error
aunque nuestra espada mas fuerte logre acabar con muchos mounstruos mas debiles sin que afecte su poder o incluso incrementano su poder, nada nos grantiza que despues con algun monstruo esta desaparezca y no podamos vencer a los siguientes,
por lo que es mas conveniente matar a cada monstruo con la espada mas pequenia suficientemente poderosa para acabar con el asi mejorando su poder sin necesidad de usar alguna espada mas fuerte, asi siempre maximizaremos todo lo que se pueda el poder de nuestras espadas.    


```cpp
void solve(){
    int n,m;
    cin >> n >> m;
    vector<ll>swords(n);
    vector<pair<ll,ll>>monsters(m);
    forn(i,n){
        cin >> swords[i];
    }
    
    forn(i,m){
        ll vida;
        cin >> vida;
        monsters[i].first = vida;
    }
    
    forn(i,m){
        ll recompensa;
        cin >> recompensa;
        monsters[i].second = recompensa;
    }
    
    sort(swords.rbegin(), swords.rend());
    
    sort(monsters.begin(), monsters.end(),[&](pair<ll,ll>x,pair<ll,ll>y){
      if(x.second == 0 && y.second != 0)
          return false;
      else if(x.second != 0 && y.second == 0)
        return true;
      else {
        return x.first < y.first;
      }
    });
    
    int j = 0;
    int ans = 0;
    
    forn(i,n){
        for(;j < m; j++){
            ll x = monsters[j].first;
            ll y = monsters[j].second;
            if (x <= swords[i]){
                ans++;
                if(y)
                    swords[i] = max(swords[i],y);
            }else{
                break;
            }
        }
    }
    
    cout << ans << '\n';
}
int main (){
    ios::sync_with_stdio(false);cin.tie(0);cout.tie(0);
    int tt = 1; 
     cin >> tt; 
    forn(TT,tt){solve();}
}
```
</details>



<script type="text/javascript" src="//cdnjs.cloudflare.com/ajax/libs/mathjax/2.7.1/MathJax.js?config=TeX-AMS-MML_HTMLorMML"></script>
<script type="text/x-mathjax-config">
 // Make responsive
 MathJax.Hub.Config({
 "HTML-CSS": { linebreaks: { automatic: true } },
 "SVG": { linebreaks: { automatic: true } },
 });
</script>

