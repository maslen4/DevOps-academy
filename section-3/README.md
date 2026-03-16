# Task A – Production went down

Najprv potrebujem zistiť, aký veľký dopad má daný incident, potom nájsť príčinu a čo najrýchlejšie obnoviť službu. Nakoniec treba navrhnúť prevenciu.

Celý proces by som zrejme komunikoval so zvyškom tímu.


## 1. Zistím, či je aplikácia úplne nedostupná, alebo len jej časť

Potrebujem vedieť:
- od kedy problém trvá, kľko používateľov je ovplyvnených. 
- či ide o kritickú funkcionalitu

Toto mi pomôže správne určiť prioritu a ďalší postup

## 2. Skontrolujem posledné zmeny

Možno je príčinou nejaká zmena, ktorá nastala tesne pred výpadkom. Treba skontrolovať posledné deploymenty.

## 3. Skontrolujem logy, dostupné metriky

Pozriem sa na:
- aplikačné logy
- logy kontajnerov
- CPU, RAM a disk usage



## 4. Snažím sa izolovať miesto problému

Potrebujem zúžiť problém na konkrétnu vrstvu:

- frontend
- backend
- databáza
- externé závislosti
- sieť
- kontajnerová infraštruktúra




## 5. Snažím sa obnoviť službu čo najrýchlejšie

Ak už sa mi podarilo identifikovať problém, prioritou je čo najrýchlejšie obnoviť službu.

Podľa situácie by som zvážil:

- rollback posledného deploymentu
- reštart kontajnera alebo podu
- uvoľnenie miesta na disku
- zapnutie záložnej služby, ak nejaká je

atď...


## 6. Overenie

Ak už sa mi podarilo prevádzku obnoviť, overoval by som, či je situácia stabilná a či nehrozí ďalší incident.
Treba otestovať dostupnosť všetkých služieb.



## 7. Hľadanie root cause

Ak sme problém vyriešili napríklad rollbackom k poslednej stabilnej verzii, treba zistiť, čo presne spôsobilo chybu.
Treba zistiť, čo sa stalo, prečo sa to stalo, prípadne prečo ochranné mechanizmy nezabránili výpadku.


## 8. Prevencia

Preventívne opatrenia môžu byť napríklad

- lepší monitoring
- vymyslieť nejakú rollback stratégiu
- zlepšiť/rozšíriť test cases
- disk/CPU/memory alerty
- zaviesť nejakú históriu incidentov, aby bol o tom prehľad
