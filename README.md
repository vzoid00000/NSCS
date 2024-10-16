
# NSCS Zusammenfassung


# OSPF (Open Shortest Path First)

## Allgemeines
- OSPF ist ein link-state Routing-Protokoll.
- Bietet Skalierbarkeit durch die Verwendung von Areas.
- Link-state speichert die gesamt topology.
- Konvergenz in Netzwerken = Alle Router haben die gleiche, aktuelle Sicht auf die Netzwerktopologie.
- Es gibt zwei Versionen:
  - **OSPFv2**: Für IPv4
  - **OSPFv3**: Für IPv6

## Exchange messages
1. **Hello**: Entdecken von Nachbarn und Aufbau von Nachbarschaften.
2. **Database Description (DBD)**: Informationen über die Link-State-Datenbank austauschen.
3. **Link-State Request (LSR)**: Anfordern von spezifischen Link-State-Anzeigen.
4. **Link-State Update (LSU)**: Versenden von Link-State-Anzeigen.
5. **Link-State Acknowledgment (LSAck)**: Bestätigen des Empfangs von LSAs.

## Databases
![image](https://github.com/user-attachments/assets/59c1af44-f510-466b-a8f1-ce16d1d18aed)





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


