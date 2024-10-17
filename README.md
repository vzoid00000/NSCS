
# NSCS Zusammenfassung


# OSPF (Open Shortest Path First)

## Allgemeines
- OSPF ist ein link-state Routing-Protokoll.
- Bietet Skalierbarkeit durch die Verwendung von Areas.
- Link-state speichert die gesamte topology, anders als distance vector routing (z.B. RIP) was nur den next hop speichert, deswegen konvergiert link-state routing auch schneller als distance vector routing.
- Konvergenz in Netzwerken = Alle Router haben die gleiche, aktuelle Sicht auf die Netzwerktopologie.
- Es gibt zwei Versionen:
  - **OSPFv2**: Für IPv4
  - **OSPFv3**: Für IPv6, supportet aber auch IPv4

## Areas
- Eine Area ist eine Gruppe von Routern, die alle die selbe LSDB haben
- Es gibt zwei Arten von Areas:
  - **Single-Area OSPF**: Alle router sind zusammen einer Area, best practice ist area 0 hier zu verwenden
  - **Multiarea OSPF**: Mehr als eine Area, die hierarchisch connected sind, d.h. alle Areas muessen mit area 0 connected sein. Router die die Areas verbinden heissen Area Border Routers (ABRs)

  ## Vorteile von Multiarea OSPF
  - Smaller routing tables
  - Minimizes processing and memory requirements
  - Reduced frequency of SPF calculations
  
## Databases
![image](https://github.com/user-attachments/assets/59c1af44-f510-466b-a8f1-ce16d1d18aed)

## Exchange messages
![image](https://github.com/user-attachments/assets/0972fd75-feed-49f7-8b70-57debac26f06)
- Hello: 
  - Elect the Designated Router (DR) and Backup Designated Router (BDR)
  - dead interval is 4 times the Hello interval
  - Alle 10 sec sendet er ein packet
Ein Passiv Interface also zb ein interface wo ein host dranhängt und leitet keine packets weiter

## Der Nutzen eines Designated Router (DR)
- Creation of multiple adjacencies: es gibt dann einfach unnötig viele adjacencies
- Extensive flooding of LSAs: jedes mal wenn sich etwas bei der topology ändert, flooden dann die router was zu unnötigen traffic führt wenn es so viele adjacencies gibt
- Wenn man eben alle Sachen zu einen Designated Router (DR) sendet, vermeidet man diese Probleme
- Backup Designated Router (BDR) ist einfach ein backup Designated Router (DR), wenn der eben ausfällt
- Alle anderen Router werden dann zu DROTHERs. Ein DROTHER ist ein router, der nicht der DR oder BDR ist
- DR so wird ausgewaehlt:
  - er nimmt die höhste ospf priority 
  - wenn zwei router die selbe priority haben, nimmt er die höhste router id
  
![image](https://github.com/user-attachments/assets/ef8b06a7-f6f6-4ee1-8e9e-7a8332fcf3f1)

## Link-state routing process to reach a state of convergence
![image](https://github.com/user-attachments/assets/bb584cf1-ef6f-433c-ae54-06e54416bbda)
![image](https://github.com/user-attachments/assets/55dfc9ad-fa51-48d9-a805-038be27c5444)


## Status types
OSPF Status:
- **Down state**
- **Init state**
- **Two-way state**
- **ExStart state**
- **Exchange state**
- **Loading state**
- **Full state**
  
![image](https://github.com/user-attachments/assets/af2cf362-f5dd-44a4-8415-55380c505b0c)

Um festzustellen, ob ein OSPF-Nachbar im Link vorhanden ist, sendet der Router ein Hello-Paket mit seiner Router-ID über alle OSPF-aktivierten Schnittstellen an die reservierte Multicast-Adresse **224.0.0.5.**


## OSPF Router ID
- OSPFv2 is enabled using the router ospf process-id global configuration mode command.
- OSPF router ID ist eine 32-bit value, dargestellt als IPv4 address und ist ein unique identifier von einem OSPF Router und jedes OSPF packet beinhaltet die OSPF Router ID des Absenders.
- Wofür die Router ID wichtig ist:
  - Participate in the election of the designated router (DR) = Der Router mit der highest ID wird DR, der zweithösten BDR
  - Participate in the synchronization of OSPF databases = Während Exchange State, sendet der router mit der highest ID sein DBD als erstes

- Nach der Reihenfolge wird die Router ID bestimmt:
  1. explicitly configured using the OSPF router-id rid
  2. The router chooses the highest IPv4 address of any of configured loopback interfaces
  3. The router chooses the highest IPv4 address of any of configured ipv4 address

     
## Features von OSPF
![image](https://github.com/user-attachments/assets/4b53faab-3bba-49a9-8dc6-1e67179dca27)



## LSAs
- LSUs enthalen verschiedne LSAs
- LSA enthält:
  - state and cost of each directly connected link
 
- Router flooden ihre LSAs zu ihren Neighbors





