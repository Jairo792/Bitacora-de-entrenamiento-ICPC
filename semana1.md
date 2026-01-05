
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
<summary>Spoiler de la solucion </summary>
<pre>
<code lang="language-cpp">
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

int main (){
  cin.tie(0);  
  cin.sync_with_stdio();
  int tt;
  cin >> tt;
  
  forn(TT,tt){
	 int n, m;
	 cin >> n >> m;
	 
	 multiset<ll>espadas;
	 
	 forn(i,n){
		ll x;
		cin >> x;
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
	RAYA ;
	 for(auto it: ms){
		cerr << it << '\n';
	 }
	 RAYA;
	
	// return 0;
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
</code>
</pre>
</details>



**Errores que cometi:**

<details>
<summary><strong>Errores post Solucion </strong></summary>
Pense que si solamente ordenaba las espadas de mayor a menor, y luego ordenabamos los mounstruos de menor a mayor con su respectivo c_i podriamos solucionar el problema, pero claro esto es un error
aunque nuestra espada mas fuerte logre acabar con muchos mounstruos mas debiles sin que afecte su poder o incluso incrementano su poder, nada nos grantiza que despues con algun monstruo esta desaparezca y no podamos vencer a los siguientes,
por lo que es mas conveniente matar a cada monstruo con la espada mas pequenia suficientemente poderosa para acabar con el asi mejorando su poder sin necesidad de usar alguna espada mas fuerte, asi siempre maximizaremos todo lo que se pueda el poder de nuestras espadas.    
</details>



<script type="text/javascript" src="//cdnjs.cloudflare.com/ajax/libs/mathjax/2.7.1/MathJax.js?config=TeX-AMS-MML_HTMLorMML"></script>
<script type="text/x-mathjax-config">
 // Make responsive
 MathJax.Hub.Config({
 "HTML-CSS": { linebreaks: { automatic: true } },
 "SVG": { linebreaks: { automatic: true } },
 });
</script>

