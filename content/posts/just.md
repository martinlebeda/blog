---
title: "Just"
date: 2018-03-14T14:00:53+01:00
draft: true
---

Just je jednoduchý automatizační nástroj pro správu projektů inspirovaný make.
Nemá sice všechny možnosti make, ale zase je podstatně jednodužší a přináší
zajímavé vlastnosti, které nemá make.

<!--more-->

## Co umí a neumí just

Just neumí inkrementální kompilaci. Určitě neumí i celou řadu dalších věcí. Je
to spíše spouštěč dalších aplikací. Takže při překladu programů v C make
rozhodně nenahradí. Není to nástroj pro náhradu make, který zajišťuje
inkrementální kompilaci projektu. 

Just se může velmi dobře uplatnit při akcích spojených se spouštěním příkazů,
které zajišťují nejrůznější servis projektu. Může volat make, maven a další
buildovací nástroje, které jsou pro různé jazyky různé a tím je integrovat. 

Osobně pracuji na projektech, které používají zároveň npm pro klienta v
javascriptu a mvn pro server psaný v javě, nebo mají dokonce klienta psaného v
Delphi a tím pádem buildovací nástroje nespolupracují nebo spolupracují jen
obtížně (musí se psát vlastní pluginy do mavenu a podobně). Just je snadno
zintegruje dohromady, např. příkaz `just clean` spustí jak maven, tak npm a
ještě další pomocné příkazy přímo v shellu.

Tím že část akcí, které nejsou spojené přímo s kompilací může velmi jednoduše
zajišťovat sám Just, jsou konfigurace v make, mvn, atd. mnohem jednodužší.

## Instalace

https://github.com/casey/just
% TODO

## řídící soubor 
  
Řídící soubor se jmenuje `justfile` nebo `Justfile` a jednotlivé úlohy jsou
označované jako předpisy. Mohou na sobě záviset a vyvolání předpisu tak může
spustit celou kaskádu akcí. 

% TODO jak vypadá jednoduchý justfile


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

