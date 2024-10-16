
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

## Link-state routing process to reach a state of convergence
1. Verbindung zwischen routern aufbauen
2. exchange Link-State Advertisements
3. build Link State Database
4. shortest path first algorithm ausfuehren also dijkstra
5. Beste route aussuchen

## Status types
OSPF Status:
- **down**
- **init**
- **two-way**
- **ExStart**
- **Exchange**
- **loading**
- **full**



## Konvergenzprozess
Der Prozess zur Erreichung der Konvergenz umfasst folgende Schritte:
1. Nachbarschaften etablieren
2. Link-State-Anzeigen austauschen
3. LSDB aufbauen
4. SPF-Algorithmus ausführen
5. Beste Route auswählen

## DR (Designated Router) und BDR (Backup Designated Router)
In Multiaccess-Netzen werden DR und BDR gewählt, um:
- LSAs effizient zu sammeln und zu verteilen.
- Den Netzwerkverkehr zu optimieren und die Anzahl der erforderlichen Adjacency-Relationen zu reduzieren.


