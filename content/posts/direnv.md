---
title: "Direnv"
date: 2018-03-18T14:13:41+01:00
draft: false
---

Direnv je nástroj pro shell, který umožní nastavovat proměnné prostředí po
vstupu do určitého adresáře a po jeho opuštění směrem nahoru jsou proměnné opět
uvedeny do původního stavu. Je tedy schopen vytvořit lokální nastavení
prostředí. Ideální pokud pracujete na více projektech, které vyžadují
specifické proměnné a nechcete si zaplevelit svůj obecný profil. Nebo pokud v
každém projektu je pro proměnnou požadována jiná hodnota. Heslo programu
`Unclutter your .profile` je výstižné.

<!--more-->

Jako programátor nepracuji na jediném programu, ale musím střídat více
nastavení, narazil jsem na potřebu používat různé verze kompilátorů, knihoven
či jiných nástrojů na jednom počítači. Každý projekt požaduje mírně jiné
nastavení. Toto se zatím daří řešit instalací různých verzí do různých adresářů
a následně nastavením prostředí, nemusím tak používat těžkotonážní
řešení jako je Vagrant. Vagrant je nástroj jistě mocný, mnohem mocnější než
výše uvedené a zajisté existují pádné důvody pro jeho použití, ale já jsem
zvolil řešení výrazně lehčí a pro mne dostačující.

## Instalace

Instalace byla opravdu tak jednoduchá jak slibuje návod na stránkách. Jelikož
<<<<<<< Updated upstream
je program jediná binárka (napsaná v [go](https://golang.org/)) stáhl jsem
||||||| merged common ancestors
je program jediná binárka (napsaná v [go]()) stáhl jsem
=======
je program jediná binárka (napsaná v go) stáhl jsem
>>>>>>> Stashed changes
zkompilovanou verzi a zkopíroval do cesty k ostatním. Dále stačí
<<<<<<< Updated upstream
přidat jeden řádek na konec konfigurace shellu (v mám případě do
`~/.zshrc`) a je hotovo: 
||||||| merged common ancestors
přidat jeden řádek na konec konfigurace shellu (v mám případě do
`~/.config/fish/config.fish`) a je hotovo: 
=======
přidat jeden řádek na konec konfigurace shellu (v mém případě do
`~/.config/fish/config.fish`) a je hotovo: 
>>>>>>> Stashed changes
```
eval "$(direnv hook zsh)"
```
Další shelly jsou popsány v dokumentaci na stránkách [programu](https://direnv.net/).


[Konfigurace](https://direnv.net/#man/direnv.toml.1) samotného `direnv` je v
souboru `$HOME/.config/direnv/config.toml` a zejména umožňuje specifikovat pomocí
whitelistu cesty ve kterých je použití `direnv` povoleno. Lze jej použít i v
jiných cestách, ale je potřeba jej explicitně povolit.

## Použití

Použití je jednoduché, přejít do adresáře a nastavit prostředí pomocí souboru
`.envrc`. Řídicí soubor je bash script, nemusí v něm být jen nastavení
prostředí, ale i další běžné příkazy, které se normálně provedou. Po jeho
provedení program vyhodnotí rozdíly a doplní je v aktuálním shellu.

```
$ cd ~/Sandbox/tst
$ vim .envrc
# vyeditovat nastavení prostředí - výpis je níže 
direnv: error .envrc is blocked. Run `direnv allow` to approve its content.

# Co je v .envrc nastaveno:
$ cat .envrc 
export FOO=foo
export FOO1=foo01
export XXXX=yyyy
echo ahoj
```

Nic se ovšem neprovedlo, místo toho program upozornil že jej máme povolit.
Pokud není adresář ve whitelistu, je potřeba `direnv` nejprve povolit, aby se
automaticky nespouštělo něco nepěkného, co by tam někdo podstrčil a co
nechceme. A při změně `.envrc` jinak než příkazem `direnv edit` je potřeba
povolení zopakovat.

```
$ direnv allow
direnv: loading .envrc
ahoj
direnv: export +FOO +FOO1 +XXXX

# vyeditovat .envrc, je možno i normálně jakýmkoliv editorem,
# ale takto se změny rovnou promítnou a povolí
$ direnv edit
direnv: loading .envrc
ahoj
direnv: export +FOO +FOO1 +XXXX +YYYY

# pořídím podadresář aaa pro pozdější použití 
$ mkdir aaa

# při každém opuštění adresáře mimo podstrom se prostředí vynuluje
$ cd ~
direnv: unloading

# při každém vstupu se prostředí nastaví, a to i pro přímý vstup do 
# podadresáře nebo při vyvolání terminálu z filemanageru kdekoliv v podstromu
$ cd Sandbox/tst/aaa/
direnv: loading ../.envrc
ahoj
direnv: export +FOO +FOO1 +XXXX +YYYY

```

Příkaz `direnv` má samozřejmě více parametrů a vychytávek, které jsou popsány
na stránkách https://direnv.net/ nebo v manuálu.


