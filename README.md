
# NSCS Zusammenfassung


# OSPF (Open Shortest Path First)

## Allgemeines
- OSPF ist ein link-state Routing-Protokoll.
- Bietet Skalierbarkeit durch die Verwendung von Areas.
- Link-state speichert die gesamte topology.
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
Hello macht auch: Elect the Designated Router (DR) and Backup Designated Router (BDR)

## Der Nutzen eines Designated Router (DR)
- Creation of multiple adjacencies: es gibt dann einfach unnötig viele adjacencies
- Extensive flooding of LSAs: jedes mal wenn sich etwas bei der topology ändert, flooden dann die router was zu unnötigen traffic führt wenn es so viele adjacencies gibt
- Wenn man eben alle Sachen zu einen Designated Router (DR) sendet, vermeidet man diese Probleme
- Backup Designated Router (BDR) ist einfach ein backup Designated Router (DR), wenn der eben ausfällt
- Alle anderen Router werden dann zu DROTHERs. Ein DROTHER ist ein router, der nicht der DR oder BDR ist
![image](https://github.com/user-attachments/assets/ef8b06a7-f6f6-4ee1-8e9e-7a8332fcf3f1)

## Link-state routing process to reach a state of convergence
1. Verbindung zwischen routern aufbauen
2. exchange Link-State Advertisements
3. build Link State Database
4. shortest path first algorithm ausfuehren also dijkstra
5. Beste route aussuchen

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
