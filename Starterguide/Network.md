Et netværk er det der forbinder Compuetere  og andre netværks enheder sammen, så de kan kommuniker.

Der er 2 typer af netværk, LAN og WAN.

## LAN

Et LAN (Local Area Network) er et netværk som er begrænset til et lille område, som f.eks. et hus eller en bygning.
Et  LAN er typisk et privat netværk, som kun er tilgængeligt for de enheder som er tilsluttet netværket.
Man kan også have et LAN som er tilgængeligt for alle, som f.eks. et offentligt wifi netværk.

[!badge text="LAN" variant="light" ](/test.md)

## WAN
WAN (Wide Area Network) er et netværk som er større end et LAN, og er typisk et netværk som er tilgængeligt for alle.
Et eksempel på et WAN er internettet, som er et netværk som er tilgængeligt for alle.


```mermaid

flowchart LR
	166881[/"ISP"\] --- 823129["WAN"]
	style 166881 fill:#99e2b4,stroke-width: 0px,text:,color:#ffffff
	style 823129 fill:#ffff,stroke-dasharray: 5,stroke:#000000,color:#fffffl
	823129 --- 230466(("Router"))
	style 230466 fill:#036666,text:,color:#ffffff
	230466 --- 171966["LAN"]
	style 171966 fill:#ffff,stroke-dasharray: 5,stroke:#000000,color:#fffffl
	subgraph 171966["LAN"]
		274694[\"PC"/]
		style 274694 fill:#5bcc90,color:#ffffff,stroke-width: 0px
	end
	subgraph 823129["WAN"]
		166881
	end

```