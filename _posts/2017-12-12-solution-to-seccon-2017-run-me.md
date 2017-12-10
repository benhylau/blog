---
layout: post
title: "Solution to SECCON 2017 Run Me!"
author: capitol
category: ctf
---
![fibonacci](/images/fibonacci.jpg)

##### name:
Run Me!

##### category:
programming

##### points:
100

#### Writeup

We got a small python program that calculated a number and printed the flag.

```python
import sys
sys.setrecursionlimit(99999)
def f(n):
    return n if n < 2 else f(n-2) + f(n-1)
print "SECCON{" + str(f(11011))[:32] + "}"
```

Only problem was that it was pretty slow. Looking at the function f, it became clear
that it was a recursive implementation of a fibonacci number calculator.

We can simplify the program by pre-calculating the number, since the input 11011 is static.
[This](http://wolframalpha.com/) is a good resource for doing math online. That gives us the program:

```python
print "SECCON{" + str(650761408323317176677727615418728824035834139276098998490249192132666758545760517800054917034155243927170284032856159641073239445267259027201529090078896791094491606651280986273375358475762477790432186275595009347181655230560612893072010176744437899125794062096822499169737341076562268978822309439778493884517811269755645677051823939101818750862488649336629337157213652909313926271909722579127327516034001078889493903847162940951919936666981110589496109534874704781719109928400031417346568159901873387957504386076864598280589140560720555215586103334108606666557885182543411057646507987554088958465040914897691939542285281414546306123632401776970176802858533764858159120251846344138169520194579452006975065591700295752709436626337896977143749517364692359205470520308998499747373023079909096931930849470838600436193492730120598058390332468715098569506803288748815104425904241644846838395455904535450056833234799685571736399955768131656445051569947468596781842534517197721000873495062895837282533156293369623617362342118583768869069357254102738089664559884034222599617271201387495056590015984399482556187470258510628428546129648977633092532344658489593547730850249245718744514953339799649429008307017831938762015220771469692523759803441301822573457181350382636976785308875676049259482221646051841764952498511738390807032009076345712915067307334601511409483180854512241289677598260345859220604188459466566218428522712526307485414327912984814200699366287893779866533195964875622418194229718474283906639970274067803465246049255487228512317014925146357266424154230175016287402954010234339299976926358623916935423402962510413409907048690682619724213875769975891654986212343055742766929242325603302953851160284942626779251037312496874310855130377517889541404945838665610608950717555040757378177019719117615549280661866187332498803134726445107694994290546795927294081948416543673731399120512192375688817905543314233147723782998209741461558386215456190659067634677870007289790910629423072714321397319111715970130151174669992797276293445539760861617336440030158167771970869191088140343413881822920781894388333124029339099939263144538805634147654202831717365638267529461536461367917300661565377015525846611173849663494461429041123993952629470445363197932541803303152120627201578910609457626560492171665716942761589)[:32] + "}"
```

flag was SECCON{65076140832331717667772761541872}