---
title: "Hugo Site Generator"
date: 2018-03-09T09:32:32+01:00
draft: true
---

Začal jsem řešit myšlenku jak publikovat své poznámky ohledně technických
věcí. Nejlépe ve smyslu za málo peněz hodně muziky. Kdo by to tak nechtěl?

<!--more-->

## Proč tyhle stránky a proč Hugo

Proč vlastně psát poznámky veřejně? 
% utřídím a učešu si myšlenky

Proč hugo právě Hugo? Všichni řeší Staticky generované stránky. Po první
reakci, to je k ničemu jsem se nechal poučit, k čemu to vlastně je, jsem
zjistil, že to je vlastně príma věc a pustil se do akce.
% starý koncept easyBlog

Proč vlastně použít statický generátor webu:

  - Statické stránky jsou prakticky nenapadnutelné, což může být výhoda zejména
    pokud nechci svůj čas trávit údržbou, popřípadě údržbě nerozumím a vlastně
    ani rozumět nechci.
  - veřejné hostovací služby
  - Vývojářské workflow
  - Psaní v markdown (textile...)

Nevýhody:

  - Musím se naučit obsluhovat generátor
  - Ne vždy musí statické stránky dostačovat.

## Instalace Hugo

Navzdory dlouhé stránce jsem zvolil podle mne nejjednodužší cestu k instalaci.
Přešel jsme na stránku s releasy a prostě stáhnul pro svou platformu. Jak je u
Go programů zvykem, v balíčku byla jen jedna binárka, soubor s licencí a
readme. Instalaci jsem pak odbyl rozpakováním a zkopírováním birárky do
`~/bin/`, kde se nachází i další podobné programy (např. fzf) a bylo hotovo.

## Založení stránek

Postup dle https://gohugo.io/getting-started/quick-start/


## Nastavení tématu

Nejprve jsem zkusil nainstalovat základní téma, zvolil jsem
[Kiera](https://themes.gohugo.io/hugo-kiera/), "Hugo Theme for creative and technical writing". 
Vše šlo podle jednoduchého návodu skvělě a tak jsem se pustil do zápisu prvního příspěvku a
zvědavě se podíval na vzhled webu jak popisuji níže.

Samozřejmě jsem se první dobrou netrefil. Web po zkompilování vypadal úplně
jinak, než jsem si představoval. Takže další pokus. Tentokrát jsem zvolil téma
[Hyde](https://themes.gohugo.io/hyde/), které se zdálo mít pro mé oko lepší
fonty. Samozřejmě to je dosti individuální a každý člověk to může cítit jinak.

```
cd themes
git clone https://github.com/spf13/hyde.git
```

Nastavit `theme = "hyde"` do `config.toml` a už jsem koukal... na totálně
rozbitou stránku. Server spuštěný na pozadí (popsáno níže) změnu tématu nedal a
bylo potřeba jej otočit, pak již bylo vše ok.

Toto téma požaduje nastavení postranního panelu. Což jsem samozřejmě neměl, ale
jsou tam i výchozí hodnoty, takže 


## sepsání prvního postu

První post jsem začal psát jako své poznámky vlastně ještě před událostmi
spojenými s výměnou tématu. Sloužíl okamžitě jako poznámkový blok, který jsem
později jen upravil do publikovarelné podoby

```
hugo new posts/hugo-site-generator.md
gvim content/posts/hugo-site-generator.md
```



- draft a označení postu za dokončený

### spuštění testovacího serveru

Jakmile je nový příspěvek založen je možné spustit testovací server.

```sh
hugo server -D
```

Na konzoli se objeví hlášení o tom co se děje, jak jej zastavit a na jaké
adrese je možné se na něj připojit a následně. Po každém uložení nějaké změny
Hugo přeloží, přerenderuje a v prohlížeči se objeví výsledek. Takže je možné
vidět průběžně výsledky - velmi užitečné.

## sidebar a menu

## Nastavení metadat stránek
  
## Obarvení zdrojáků

## Zveřejnění

Pro zveřejnění vygenerovaných stránek je možné použít mnoho služeb. Mě jako
nejjednodužší varianta přišel github. Ale stejně jednoduché je vybrat si i jiný
hosting.

Jednoduchý a funkční postup je tady:
https://gohugo.io/hosting-and-deployment/hosting-on-github/.

Postup je možné prakticky krok za krokem použít a dobrat se tak k funkčním
stránkám. 

## Dojmy

- rychlost
- jednoduchost
- rozšiřitelnost
