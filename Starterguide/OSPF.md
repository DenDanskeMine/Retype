---
label: OSPF
icon: globe
---

# OSPF

OSPF er en [!badge text="IGP" variant="ghost" ](/test.md) (Interior Gateway Protocol), som bruges til dynamisk routing.<br>

OSPF står for Open Shortest Path First, og er en af de mest brugte routing protokoller.<br>
Navnet er lidt misledende da det ikke er den fysiske korteste vej den vælger.<br>
Den vælger den vej der har den laveste [!badge text="metric" variant="ghost" ] (omkostning).
Metric er en værdi der bliver beregnet sp ledes: [!badge text="båndbredde / interface hastighed" variant="ghost" ].<br>




OSPF er en link-state protokol, hvilket betyder at den sender information omkring alle sine naboer til alle andre routere i netværket.

Routerne ser sig selv som toppen af netværket, og alle andre routere er naboer til dem.
Her er et viruelt eksempel på det:
+++ :icon-workflow: Topologi
```mermaid
flowchart LR
	1((("&nbsp;R1&nbsp;"))) --- 2((("&nbsp;R2&nbsp;")))
	style 1 fill:#99e2b4,stroke-width: 0px
	style 2 stroke-width: 0px
	2 --- 3((("&nbsp;R3&nbsp;")))
	style 3 stroke-width: 0px
```
+++ :icon-x-circle: R1
```mermaid
flowchart TD
	1((("&nbsp;R1&nbsp;"))) --- 2((("&nbsp;R2&nbsp;")))
	style 1 fill:#99e2b4,stroke-width: 0px
	style 2 stroke-width: 0px
	2 --- 3((("&nbsp;R3&nbsp;")))
	style 3 stroke-width: 0px
```

+++ :icon-x-circle: R2
```mermaid
flowchart TD
	1((("&nbsp;R2&nbsp;"))) --- 2((("&nbsp;R1&nbsp;")))
	style 1 fill:#99e2b4,stroke-width: 0px
	style 2 stroke-width: 0px
	1 --- 3((("&nbsp;R3&nbsp;")))
	style 3 stroke-width: 0px
```
+++ :icon-x-circle: R3
```mermaid
flowchart TD
	1((("&nbsp;R3&nbsp;"))) --- 2((("&nbsp;R2&nbsp;")))
	style 1 fill:#99e2b4,stroke-width: 0px
	style 2 stroke-width: 0px
	2 --- 3((("&nbsp;R1&nbsp;")))
	style 3 stroke-width: 0px
```
+++

Så det vil altså sige at R1 ser R2 og R3 som naboer, og R2 ser R1 og R3 som naboer osv.

Hver router har en [!badge text="LSDB" variant="ghost" ] (Link State Database), som er en liste over alle naboer og deres omkostninger.

Denne dtabase bliver formet af [!badge text="LSAs" variant="ghost" ] (Link State Advertisements), som er pakker der bliver sendt ud til alle naboer, og indeholder information omkring routeren der sender pakken.


## LAB Setup

![](/img/OSPF.png) 

### Plan

Vi skal konfigurere OSPF på alle routere, så de kan snakke sammen.<br>
I dette LAB bruger vi et single area, som er area 0.

Når vi er færsige med at konfigurere, skal vi verificere at det virker.<br>
Målet er at PC1 kan pinge PC2, og at PC2 kan pinge PC1.

### Konfiguration

+++ :icon-x-circle: R1
```js
router ospf 1
 network
```
![](/img/OSPF_R1.png) 
+++ :icon-x-circle: R2
```js
router ospf 1
 network
```
![](/img/OSPF_R2.png)
+++ :icon-x-circle: R3
```js
router ospf 1
 network
```
![](/img/OSPF_R3.png)
+++





