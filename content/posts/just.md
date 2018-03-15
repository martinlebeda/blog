---
title: "Just"
date: 2018-03-14T14:00:53+01:00
draft: true
---

Just je jednoduchý automatizační nástroj inspirovaný make. Nemá sice všechny
možnosti make, ale zase je podstatně jednodužší a přináší zajímavé vlastnosti.

<!-- more -->

- co umí make a neumí just

Just neumí inkrementální kompilaci. Určitě neumí i celou řadu dalších věcí. Je to spíše spouštěč dalších aplikací. Takže při překladu programů v C make rozhodně nenahradí. 

- řídící soubor
  - recipe - předpis
  
  Jednotlivé úlohy jsou označované jako předpisy. Mohou na sobě záviset a vyvolání předpisu tak může spustit celou kaskádu akcí. 

## nastavení proměnných

Na začátku `justfile` je možné nastavit proměnné. Syntaxe zápisu je klasická
jako v shellu:
```
# proměnná dostupná v justfile
NAZEV = hodnota
# proměnná exportovaná i do spouštěných procesů
export NAZEV = hodnota
```

Jediné s čím jsem se potýkal byla expanze promenných prostředí, které se
nexpandují. Např. ve chvíli, kdy chci doplnit cestu do `PATH`, nelze napsat
`PATH = "cesta:$PATH"`, protože `$PATH` nebude expandováno, ale problém lze
obejít pomocí `PATH = \`echo "cesta:$PATH"\`` protože zpětné apostrofy spůsobí
vyhodnocení výrazu v shellu a ten samozřejmě expanzi zajistí.
  
- syntaxe podobné make
- dokumentační komentáře
- možnost zápisu v jiných jazycích
- parametrické předpisy
- vnořené předpisy

