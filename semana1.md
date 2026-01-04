# Semana 1
Esta semana no pude resolver demasiados problemas, practicamente para todos tuve que usar test case generados y strees testing ya que no se me ocurrian los casos en los que mi solucion fallaba.
## Ejercicio 1
- [Dungeon](https://codeforces.com/contest/2164/problem/C) --

Resumen del enunciado de este ejercicio.-

Este ejercicio es similar al que nos explico agus la ultima clase basicamente (enfrentar m cosas contra n cosas), en este caso mounstruos vs espadas (monsters and swords)
nos menciona que una espada que tenga poder x puede matar a un mounstruo de salud y si y solo si y <= x (el poder de la espada es mayor o igual a la vida del mounstruo)
se nos meciona que nos daran tres conjuntos o arreglos b,a,c en b se almacenera de forma numerica la vida de los mounstruos, en a el poder de nuestras espadas y luego c que se explicara mas adelante
despues de matar a un mountruo de vida y, la espada ai de poder x se destruira y si ci es  > 0 entonces obtendremos una nueva espada de poder max(x,ci).
Output : Imprime el mayor numero de mounstruos que tu puedes matar.
