---
title: "Passwdgen"
date: 2018-01-01T18:13:45+01:00
project: https://github.com/martinlebeda/passwdgen
draft: false
---

Postarší script v perlu pro generování hesel, které by se daly vyslovit a tím
pádem i zapamatovat. Zároveň výsledkem nejsou žádné reálná slova, která by se
dala dohledat ve slovnících. 

<!--more-->

Volně inspirováno funkčností, která byla ve starších verzích SCO OpenServer a
umožňovala generovat hesla uživatelům. 

Generování hesel je založeno na náhodném střídání slabikotvorných a ostatních
hlásek, takže výsledek lze většinou vyslovit a tím i zapamatovat lépe než čistě
náhodný shluk znaků.

Umí i další věci:

  - volitelná délka generovaného výrazu
  - Malá a velká písmena
  - Použití různých kategorií specálních znaků
  - lze zvolit počet nabízených náhodných výrazů
  - lze požadovat ve vygenerovaném výrazu určitý řetězec definovaný regulárním
    výrazem
    
Vznikl někdy kolem roku 2001, ale používám jej dodnes.
Funguje pro mé potřeby dostatečně a tak dalším rozvojem zatím nepočítám...
