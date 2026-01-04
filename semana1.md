# Semana 1

Esta semana no pude resolver demasiados problemas, practicamente para todos tuve que usar test case generados y stress testing ya que no se me ocurrían los casos en los que mi solución fallaba.

## Ejercicio 1
- [Dungeon](https://codeforces.com/contest/2164/problem/C) --


Enunciado: 

Este ejercicio es similar al que nos explicó Agus la última clase, básicamente (enfrentar \(m\) cosas contra \(n\) cosas), en este caso **monstruos vs espadas**.
Se menciona que una espada que tenga poder 
puede matar a un monstruo de salud \( y \) si y solo si \(y <= x \).

Se nos dan tres arreglos: \(a,b,c\)
- `a`: poder de las espadas  
- `b`: vida de los monstruos  
- `c`: se explica más adelante  

Después de matar a un monstruo de vida \(y \) , la espada \(a_i \) de poder \(x\) se destruye y, si \(c_i > 0 \), obtenemos una nueva espada de poder \(max(x, c_i)\).

**Output:** imprimir el mayor número de monstruos que puedes matar.

Solucion:

<details>
<summary><strong>Resumen del enunciado (spoiler)</strong></summary>
</details>


<script type="text/javascript" src="//cdnjs.cloudflare.com/ajax/libs/mathjax/2.7.1/MathJax.js?config=TeX-AMS-MML_HTMLorMML"></script>
<script type="text/x-mathjax-config">
 // Make responsive
 MathJax.Hub.Config({
 "HTML-CSS": { linebreaks: { automatic: true } },
 "SVG": { linebreaks: { automatic: true } },
 });
</script>

