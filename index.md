---
label: Forside
icon: home
---

# Velkommen til **NETDEV**.

![](/img/retype-hero.png)

## Hvad er NETDEV?

Vi er en dokumentations hjemmeside som er lavet for at få nem og hurtig adgang til informationer omkring netværk og netværksudstyr.

Samt er målet også at folk der intet ved, kan lære noget omkring netværk og netværksudstyr.

### Din første konfiguration

I denne guide vil jeg tage dig igennem din første konfiguration af en cisco router og switch. (ios)

Her er en simpel konfiguration af en [!badge text="router" variant="ghost" ](router.md) og en [!badge text="switch" variant="ghost" ](router.md).

+++ :icon-x-circle: R1
```js
interface fastethernet 0/0
 ip address 172.16.0.1 255.255.255.0
 no shutdown

```
[!button icon="mark-github" text="Se resten af guiden"](test.md)
+++ :icon-arrow-switch: SW1 
```js
interface vlan 1
 ip address 172.16.0.2 255.255.255.0
 no shutdown

```
[!button icon="mark-github" text="Se resten af guiden"](test.md)
+++




