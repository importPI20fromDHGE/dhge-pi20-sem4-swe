# Allgemein

### Leerzeichen /  Orthogonale Linien

```
@startuml

!define spaces &#0032;&#0032;&#0032;&#0032;&#0032;&#0032;&#0032;&#0032;
skinparam linetype ortho

rectangle "Hallo spaces spaces" as A
rectangle "spaces spaces moin spaces spaces" as B

A --> B

@enduml
```

![1_SPACES_ORTHLINE](https://user-images.githubusercontent.com/105500704/169084659-23d49e9f-0b30-4710-9a15-39b5c176a601.png)

### Stereotypes

```
@startuml

skinparam rectangle<<rr>> {
  borderColor			green
  backgroundColor		red
  fontColor			yellow
  rectangleShadowing		true
  stereotypeFontColor		red
}

rectangle A <<rr>>

@enduml
```
![2_STEREOTYPES](https://user-images.githubusercontent.com/105500704/169084641-28f78a4a-b1c5-41b8-8248-db14b6b38026.png)


### Styles für Verbindungen


```
@startuml

a "Text"--[#green,dashed]r->"Anderer Text" b : \t "Linienüberschrift" \t
    
[hidden]

@enduml
```
- Farbe: siehe „Farben“
- Style: dashed, dotted
- : \t → „Verlängerungs-Trick“ für Horizontale Linien
- [Hidden] -> Linie ist unsichtbar

![3_LINES](https://user-images.githubusercontent.com/105500704/169084582-546d5c70-0943-46d7-97db-9a0d9b1217f5.png)

### Diverse

| Command | Description |
| ------------- | ------------- |
|  scale 500 width  | Skalieren horizontal  |
| scale 300 height  | Skalieren vertical  |
|left to right direction|Richtungsangabe Gesamt|
|top to bottom direction|Richtungsangabe Gesamt|

### Farben

![4_COLORTABLE](https://user-images.githubusercontent.com/105500704/169084540-75500917-2038-4d2e-8a20-d89969def202.png)

## Klassendiagramm

### Objekte

```
@startuml
abstract        		abstract
abstract class  		"abstract class"
annotation      		annotation
circle          		circle
()              		circle_short_form
class           		class
diamond         		diamond
<>              		diamond_short_form
entity          		entity
enum            		enum
interface       		interface
@enduml
```

![image](https://user-images.githubusercontent.com/105500704/169085491-6ae3fbc4-0519-4b4e-bad1-b1f638d5e1f2.png)

### Verbindungen

```
@startuml
Class01 <|-- Class02
Class03 *-- Class04
Class05 o-- Class06
Class07 .. Class08
Class09 -- Class10
@enduml
```

![image](https://user-images.githubusercontent.com/105500704/169085624-9cf1ae16-8269-41c4-a4e1-1b3dbd4b8a7d.png)

### Packages und Klassendefinitionen

```
@startuml

package CD{
	class "Hund" as H{
		- name : string
		- alter : int
		+ getName() : string
		+ setName(string) : void
		
		-Hund()
		-~Hund()
	}
	
	class "Mensch" as M{
		- name : string
		- alter : in
		
		+getName() : string
		+setName(string) : void
	}
}

M "2" *-r- "1" H : \t

@enduml
```

![image](https://user-images.githubusercontent.com/105500704/169085772-4fd3003f-3e1e-47fa-b48b-77a84017d43f.png)

## Sequenzdiagramme

### Objekte 

```
@startuml
actor Foo1
boundary Foo2
control Foo3
entity Foo4
database Foo5
collections Foo6
Foo1 -> Foo2 : To boundary
Foo1 -> Foo3 : To control
Foo1 -> Foo4 : To entity
Foo1 -> Foo5 : To database
Foo1 -> Foo6 : To collections
@enduml
```
![image](https://user-images.githubusercontent.com/105500704/169085903-a1c1ebce-fb93-4353-8d33-d4e280f1cdde.png)

### Verbindungen
```
@startuml
Bob ->x Alice
Bob -> Alice
Bob ->> Alice
Bob -\ Alice
Bob \\- Alice
Bob //-- Alice

Bob ->o Alice
Bob o\\-- Alice

Bob <-> Alice
Bob <->o Alice
@enduml
```
![image](https://user-images.githubusercontent.com/105500704/169086016-89bb9086-59f8-46c4-b19a-50e03eb8d857.png)

### Beispiele
```
@startuml
activate Mensch
Mensch -> Hund: erwerben(x,y,z)
activate Hund
Hund --> Mensch:
|||
Mensch -> Nahrung : erwerben(x,y,z)
activate Nahrung
Nahrung --> Mensch:
|||
Mensch -> Hund : fuettern(Nahrung)
Hund --> Mensch
Destroy Nahrung
|||
Mensch -> Hund: spazieren (x)
Hund --> Mensch
deactivate Mensch
deactivate Hund
@enduml
```

![image](https://user-images.githubusercontent.com/105500704/169086133-9abec90c-6046-449e-bdda-8240ecebf8fb.png)

```
@startuml
| |
Start
|Auftragsverwaltung|
:Auftrag annehmen;
|Lager|
->Lager anfragen;
:lager anfragen;
if (vorrätig?) then (vorhanden)
	:Produkt aus Lager nehmen;
else (nicht vorhanden)
	|Produktion|
	:Herstellung;
	|Lager|
	:einlagern
	:Produkt aus Lager nehmen;
endif
|Auftragsverwaltung|
:Versand;
| |
stop

@enduml
```
![image](https://user-images.githubusercontent.com/105500704/169086212-f0c7abfa-2160-4349-a1a8-d3f57fc91990.png)

## Blockdiagramme

### Beispiele

```
@startuml

!define spaces &#0032;&#0032;&#0032;&#0032;&#0032;&#0032;&#0032;&#0032;
skinparam linetype ortho


rectangle D{
	rectangle "A spaces spaces spaces" as A
	rectangle "B" as B
	rectangle C
}

A -down--> B
A -down--> C
B -right-> C : \t\t

@enduml
```
![image](https://user-images.githubusercontent.com/105500704/169086304-4e63688f-b9be-4384-8ae3-098b1256e6c0.png)

## Komponentendiagramme

### Beispiele
```
@startuml

!define spaces &#0032;&#0032;&#0032;&#0032;&#0032;&#0032;&#0032;&#0032;
skinparam linetype ortho

component "D spaces spaces spaces spaces spaces spaces" as D
component "A spaces spaces spaces" as A
component "B spaces\n\n" as B
component "C spaces\n\n" as C

D *-- A
D *-- B
D *-- C

A #-0)-# B

A #-down0)-# C

B#-right0)-# C : \t\t\t
B#-right(0-# C : \t\t\t

@enduml
```
![image](https://user-images.githubusercontent.com/105500704/169086399-6e542941-2495-4643-ac5e-3dc83798cc9f.png)

## Repository

### Git
```
@startuml

skinparam linetype ortho
top to bottom direction

rectangle "local 1 \t" as l1{
	rectangle rep1 as "Git Repo"
	rectangle dev1 as "Developer"	
}

rectangle "local 2 \t" as l2{
	rectangle rep2 as "Git Repo"
	rectangle dev2 as "Developer"	
}

rectangle "local 3 \t" as l3{
	rectangle rep3 as "Git Repo"
	rectangle dev3 as "Developer"	
}

rectangle "non_local"{
	rectangle rep as "Git Repo"
}

together {
	rectangle rep1 as "Git Repo"
	rectangle rep2 as "Git Repo"
	rectangle rep3 as "Git Repo"
}

together {
	rectangle dev1 as "Developer"	
	rectangle dev2 as "Developer"	
	rectangle dev3 as "Developer"	
}

rep <--> l1
rep <--> l2
rep <--> l3
rep1 <--> dev1
rep2 <--> dev2
rep3 <--> dev3

@enduml
```

![image](https://user-images.githubusercontent.com/105500704/169086529-d9167fcd-0a14-4322-9aa0-492142a581fc.png)

## SVN

## CLient-Server-Struktur (Beispiel)


```
@startuml

skinparam linetype ortho

!define spaces &#0032;&#0032;&#0032;&#0032;&#0032;&#0032;&#0032;&#0032;

rectangle s as "\n spaces spaces spaces Server spaces spaces spaces\n"
rectangle c1 as "Client 1"
rectangle c2 as "Client 2"
rectangle c3 as "Client 3"
rectangle cn as "client n"
database db1 as "\nDB 1\n"
database db2 as "\nDB 2 \n"
cloud www as "www"

c1 "request" <--u-> "response" s
c2 "request" <--u-> "response" s
c3 "request" <--u-> "response" s
cn "request" <--u-> "response" s
s <-r-> db1
s <-l-> db2
s <-u-> www
@enduml
```

![image](https://user-images.githubusercontent.com/105500704/169086641-7b2a4698-b4c6-4578-bc25-efe05bdbf8fc.png)

## Simulationsprogramm (Beispiel)

```
@startuml

skinparam linetype ortho

rectangle f as "Fatclient\nEchtzeitmessung und -Verarbeitung \n"
database DB as "\nDatenserver\n"
rectangle mpi as "MPI Data Processing" {
	rectangle mpi1 as "MPI-Sys 1"
	rectangle mpi2 as "MPI-Sys 2"
	rectangle mpin as "MPI-Sys n"
}

cloud c as "Cloud-Services"{
	cloud "Service 1"
	cloud "Service 2"
	cloud "Service n"
}

f -> DB
DB <-> mpi
mpi1<->mpi2
mpi1<->mpin
mpi2<-u->mpin

DB <-d-> c

@enduml
```

![image](https://user-images.githubusercontent.com/105500704/169086783-0b815763-e62f-4b03-8546-a0aab50015e9.png)

## Three-Tier-Struktur (Beispiel)

```
@startuml

skinparam titleBorderThickness 2
skinparam titleBorderColor gray
skinparam titleBackgroundColor lightgray


title "Beispiel 3 Tier Architektur: ERP-System"

top to bottom direction

rectangle u as "1..n Anwender mit ERP-Client"
note right of u #transparent
Lädt und visualisiert Daten 
endnote

rectangle l as "1..n Datenserver"
note right of l #transparent
Stellt und verwaltet Daten
end note

rectangle d as "1..n Anwendungsserver"
note right of d #transparent
Nutzt Daten für Prozesse
(AG-Berechnungen, Lagerverwaltung, [...])
end note

u <--> l  
l <--> d


@enduml
```

![image](https://user-images.githubusercontent.com/105500704/169086880-c6d0bedd-44e0-4a2e-849e-194b4d2fd8bd.png)

## Kette (Beispiel)

```
@startuml
skinparam classAttributeIconSize 0
skinparam linetype ortho
left to right direction
scale 1100*1200
 
!define LEER &#0032;&#0032;&#0032;&#0032;&#0032;&#0032;&#0032;&#0032;&#0032;
skinparam Shadowing false
skinparam rectangle<<Layout>> {
  borderColor         Transparent
  backgroundColor     Transparent
  fontColor           Transparent
  stereotypeFontColor Transparent
  rectangleShadowing  false
}
skinparam rectangle<<myGruen>> {
bordercolor         Transparent
backgroundColor     Transparent
fontColor           green
stereotypeFontColor Transparent
   }
  
!define r(x,y) rectangle "x" as y
!define r(x)   rectangle "x"
 
r(Ablauf) {
 
actor " " as S
 
   'r(Start\n , A<<myGruen>>)
   r(Phase1 ,1)
  
   r(Phase2.1,21)
   r(Phase2.2,22)
 
  
   r(Phase3  ,3)
  
   r(Endprodukt,EP)
  
   'r(Sales\n ,ES<<myGruen>>)   
   
   usecase E as "
                    Übergabe \n
                    ==
                    Marketing
                    ..
                    Verkaufs-Abt.
                    =="
} 
 
S  --> 1 
 
1  --> 21
1  --> 22 
 
21 --> 3
22 --> 3 
 
3  --> EP
EP --> E
 
@enduml
```
![image](https://user-images.githubusercontent.com/105500704/169087022-08ca8596-8a66-4da0-8736-bd732ec77c0d.png)
