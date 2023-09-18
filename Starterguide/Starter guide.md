---
label: Basal router konfiguration
icon: gear
---
## Første konfiguration af en router

I denne guide vil jeg tage dig igennem din første konfiguration af en cisco router og switch. (ios)

Her er en simpel konfiguration af en [!badge text="router" variant="ghost" ](router.md) og en [!badge text="switch" variant="ghost" ](router.md).
### Opstart af router og user EXEC Mode

Når du starter din router op for første gang, vil du blive mødt af en prompt, som ser sådan her ud:

```js
would you like to enter the initial configuration dialog? [yes/no]: 
```
Her er det vigtigt at vi vælger nej, da vi selv vil konfigurere routeren.<br>
Så du skriver bare `no` og trykker enter.

nu vil den prompte Promte dig med en anden prompt, som ser sådan her ud:

```js
Press RETURN to get started!
```

Så du trykker selvfølgelig bare enter, og så vil du blive mødt af en prompt, som ser sådan her ud:

```js
Router>
```
Når du kan se et > tegn, efterfulgt af routerens navn, er du i det der hedder [!badge text="user EXEC Mode" variant="ghost"], som er en begrænset tilstand, hvor du ikke kan lave de store ændringer.

### Privileged EXEC Mode

Så derfor skriver vi `Enable` og trykker enter, så vi kan komme ind i [!badge text="Privileged EXEC Mode" variant="ghost" ](#privileged-exec-mode), som er en tilstand hvor vi kan se hele routerens konfiguration, og lave små ændringer.

Når du er i [!badge text="Privileged EXEC Mode" variant="ghost" ](#privileged-exec-mode) så ser prompten sådan her ud:

```js
Router#
```
Det er typisk her vi ville lave `ping`, og `show` kommandoer.

### Global Configuration Mode
Vi vil meget gerne et tand højere op, så vi skriver `configure terminal` og trykker enter, så vi kan komme ind i [!badge text="Global Configuration Mode" variant="ghost" ](#global-configuration-mode), som er en tilstand hvor vi kan lave ændringer i routerens konfiguration.

Når du er i [!badge text="Global Configuration Mode" variant="ghost" ](#global-configuration-mode) så ser prompten sådan her ud:

```js
Router(config)#
```
Det er denne mode hvor vi laver alle vores ændringer, og det er også her vi vil lave vores første konfiguration.<br>

### Hostname

Det første vi starter med, er at give routeren et navn, så vi kan identificere den.<br>
for at gøre dette skiver vi følgende:

```js
hostname R1
```
hostname er en kommando som sætter routerens navn, og R1 er det navn vi har valgt at give routeren.<br>
`hostname <navn>` 
!!!warning Info
Bemærk at der ikke må være mellemrum i navnet.<br>
`hostname R 1` :icon-x-circle-fill:<br>
`hostname R1` :icon-feed-issue-closed:<br>

!!!
Når du har skrevet kommandoen, trykker du enter, og prompten vil nu se sådan her ud:
```js
R1(config)#
```

### Interface mode / IP-adresse

Nu har vi givet routeren et navn, så nu vil vi gerne sætte en `ip-adresse` på routeren, så vi kan sætte den til at kommunikere med andre enheder.

For at gøre dette, skal vi ind i interface mode, som er en tilstand hvor vi kan lave ændringer på de forskellige porte på routeren.

For at komme ind i interface mode, skriver vi `interface <navn på interface>` og trykker enter.<br>
På nogen routere kan der være forskellige interfaces, som fx FastEthernet og GigabitEthernet.
Denne router har kun FastEthernet interfaces, så vi skriver `interface fastethernet 0/0` og trykker enter.
`fastethernet` er hastigheden på porten, og `0/0` er port nummeret.

Hvis du er i tvivl om hvilke interfaces der er på din router, kan du skrive `show ip interface brief` og trykke enter, så vil du få en liste over alle interfaces på routeren.
!!!warning Info om kommandoer i forskellige modes.
Bemærk at alle `show` kommandoer skal skrives i [!badge text="Privileged EXEC Mode" variant="ghost" ](#privileged-exec-mode), og ikke i [!badge text="Global Configuration Mode" variant="ghost" ](#global-configuration-mode).<br>
Du kan skrive `do` foran kommandoen, så vil den virke i [!badge text="Global Configuration Mode" variant="ghost" ](#global-configuration-mode).<br>
Hvis du ikke lige magter at skrive hele kommandoen, kan du også bare skrive `sh ip int br` og trykke enter, så vil den også virke.<br>

Der er rigtig mange forkortelser i ios, så det er bare med at lære dem, så du kan skrive dem hurtigt. :smile: <br>
evt se listen her: [Cisco IOS Shortcuts](#interface-mode--ip-adresse) 


!!!

Når du er i interface mode, så ser prompten sådan her ud:
```js	
R1(config-if)#
```
Nu er vi i interface mode, og vi vil gerne sætte en ip-adresse på porten, så vi kan sætte den til at kommunikere med andre enheder.

kommandoen til dette er `ip address <ip-adresse> <subnetmaske>`
Vi vil gerne sætte ip-adressen `172.16.0.1` på porten, så vi skriver `ip address 172.16.0.1 255.255.255.0` og trykker enter.

Når du har skrevet kommandoen, trykker du enter, og prompten vil nu se sådan her ud:
```js
R1(config-if)#
```
Grunden til jeg bliver ved med at skrive prompten, er for at du kan se og forstå hvilken mode du er i. :smile: <br>
Dette er meget vigtigt, at forstå, da nogen kommandoer kun kan bruges i bestemte modes.<br>

Nu har vi sat en ip-adresse på porten, så nu vil vi gerne aktivere porten, så den kan sende og modtage data.

For at gøre dette, skriver vi `no shutdown` og trykker enter.

Når du har skrevet kommandoen, trykker du enter, og nu vil der komme en masse tekst på skærmen, som ser sådan her ud:
```js
R1(config-if)# %LINK-5-CHANGED: Interface FastEthernet0/0, changed state to up
```
Dette er bare routeren som fortæller os at porten er blevet aktiveret / slået til.<br>

### show running-config
Hvis du nu skriver `end` og trykker enter, vil du komme tilbage til [!badge text="Privileged EXEC Mode" variant="ghost" ](#privileged-exec-mode).<br>


!!!warning Info
`exit` tager dig ud af den mode du er i, og tilbage til den mode du var i før.<br>
`end` tager dig tilbage til [!badge text="Privileged EXEC Mode" variant="ghost" ](#privileged-exec-mode).
!!!


```js
R1#
```
Dette betyder at du er tilbage i [!badge text="Privileged EXEC Mode" variant="ghost" ](#privileged-exec-mode), og du kan nu se din konfiguration ved at skrive `show running-config` og trykke enter.

Du vil nu i bunden af terminalen se et promt som ser sådan her ud:
```js
--More--
```
Dette betyder at der er mere tekst, som ikke kan vises på skærmen, så du skal trykke på `mellemrum` for at kunne se hele konfigurationen. <br>
Eller `enter` for at se en linje ad gangen.
Konfigurationen vil se sådan her ud:
```js
Current configuration : 571 bytes
!
version 12.4
no service timestamps log datetime msec
no service timestamps debug datetime msec
no service password-encryption
!
hostname R1
!
!
!
!
!
!
!
!
ip cef
no ipv6 cef
!
!
!
!
!
!
!
!
!
!
!
!
spanning-tree mode pvst
!
!
!
!
!
!
interface FastEthernet0/0
 ip address 172.16.0.1 255.255.255.0
 duplex auto
 speed auto
!
interface FastEthernet0/1
 no ip address
 duplex auto
 speed auto
 shutdown
!
interface Vlan1
 no ip address
 shutdown
!
ip classless
!
ip flow-export version 9
!
!
!
!
!
!
!
!
line con 0
!
line aux 0
!
line vty 0 4
 login
!
!
!
end
```

Alle de `!` er bare kommentarer, som ikke har nogen betydning for konfigurationen.<br>
De adskillere blot de forskellige sektioner af konfigurationen.
!!!warning Info
Bemærk at der ikke står `no shutdown` nogen steder i running-config.<br>
Dette er fordi ios kun viser `shutdown`, så hvis du ikke kan se `shutdown` på en port, så er den aktiv.

!!!

Her er alt den samlede konfiguration vi har lavet på routeren:


```js
hostname R1
!
interface fastethernet 0/0
 ip address 172.16.0.1 255.255.255.0
 no shutdown
```
Hvis du er inde i [!badge text="Global Configuration Mode" variant="ghost" ](#global-configuration-mode), kan du blot kopiere og indsætte konfigurationen, og så vil den virke.<br>
Man kan faktisk skrive hele konfigurationen i en tekst fil, og så kopiere og indsætte den i routeren, og så vil den konfigurere sig selv. :smile: <br>
Dog skal man huske at alt skal være skrevet rigtigt, ellers vil det selfølig ikke virke.

## Sikkerhed og SSH

Nu er routeren konfigureret, så nu vil vi gerne sikre den, så andre ikke kan komme ind og lave ændringer på den.

For at gøre dette, skal vi lave en bruger, som har adgang til routeren, og så skal vi sætte en adgangskode på routeren.
Vi skal også kryptere adgangskoden, så den ikke står i klartekst.

Der er mange muligheder for kryptering og hashing bla:
Diffie-Hellman, RSA, AES, 3DES, SHA, MD5 osv.

Vi starter simplet ud, så her vil vi "bare" bruge Type 5 kryptering.
Type 5 er faktisk en rigtig svær kryptering at cracke, så det er en god start.

### ip domain-name

Først skal vi sætte en `ip domain-name` på routeren.<br>
Dette gør vi ved at skrive `ip domain-name <domæne navn>` og trykke enter. inde i [!badge text="Global Configuration Mode" variant="ghost" ](#global-configuration-mode).<br>
`<domæne navn>` er det domæne navn som routeren er en del af - Det kan være hvad som helst.<br>
Jeg har valgt at kalde mit domæne for `test.dk`.<br>
Så jeg skriver `ip domain-name test.dk` og trykker enter.
!!!warning Info
Bemærk at der ikke må være mellemrum i domæne navnet.<br>
`ip domain-name test .dk` :icon-x-circle-fill:<br>
`ip domain-name test.dk` :icon-feed-issue-closed:<br>
!!!
Domænet bliver brugt til at lave vores RSA nøgle, som vi skal bruge til at kryptere SSH sessionen.

Hvis man prøver at lave en RSA nøgle uden et domæne, vil man få denne fejl:
```js
% Please define a domain-name first.
```

### crypto key generate rsa

Når vi har sat et domæne på routeren, kan vi lave en RSA nøgle.<br>
For at lave en RSA nøgle, skriver vi `crypto key generate rsa` og trykker enter.<br>
Dette vil prompte os med en masse spørgsmål.<br>
Det første spørgsmål er hvor mange bits nøglen skal være på.<br>
Jeg har valgt at sætte den til 1024 bits, da det er en god størrelse til en router.<br>
!!!warning Info
Bemærk at jo flere bits nøglen er på, jo længere tid tager den at lave.<br>
Jo flere bits nøglen er på, jo sværere er den at cracke.<br>
!!!

Sådan ville det se ud når den prompter dig med spørgsmålet:
```js	
How many bits in the modulus [512]:
```
Her er det vigtigt at du skriver `1024` og trykker enter, så du får en 1024 bits nøgle.<br>
Hvis du ikke skriver noget, vil den lave en 512 bits nøgle, og det er ikke særlig sikkert.<br>
Vi skal have `SSH Version 2`, og det kræver en nøgle der er højrere end 768 bits.<br>

Når du har skrevet `1024` og trykket enter, vil den prompte dig med dette:
```js
% Generating 1024 bit RSA keys, keys will be non-exportable...[OK]
```








!!!warning Type 5 kryptering
Type 5 er delt op således:<br>
`$1$<salt>$<hash>`<br>

`$1$` indikerer at det er Type 5 kryptering.<br>
`<salt>` er en tilfældig streng som er tilføjet til passwordet, for at gøre det sværere at cracke.<br>
`$` er en seperator.<br>
`<hash>` er det faktiske hashede password.<br>

Her er passwordet i min konfig: `$1$mERr$YlCkLMcTYWwkF1Ccndtll`<br>
Lad os dele det op, så du kan se hvordan det ser ud.<br>

`$1$` indikerer Type 5.<br>
`<salt>` er **mERr**<br>
`<hash>` er **YlCkLMcTYWwkF1Ccndtll**.<br>
!!!
