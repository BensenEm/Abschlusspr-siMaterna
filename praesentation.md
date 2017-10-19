# Projektreview Showcase

##Idee

1. Neue Technologien probieren

2. Kombinieren mit neuen FirstSprit Möglichkeiten (CaaS)

3. Gewinnen von Kunden

   **=> $ $ $**


---
##Neue Technolgien: 
Software
* FirstSpirit, Content As A Service
* Augmented Reality 
* Voice Recognition

Hardware
* AR Brille (kein 3D/ Virtual Reality)


---
##Verschiedene Anwendungsszenarien
Für die Entwicklung der Anwendungsszenarien wurde ein Brainstorming durchgeführt. 
Im Ergebnis entstanden 3 potentiell interessante Usecases.
1. Mitarbeiter Vertrieb
2. Mitarbeiter Service
3. Kunde

---
##Szenario Kunde
> Kunde betritt Showroom. Trägt Brille.
> Kunde geht zum Fahrzeug. Ein Interface wird eingeblendet.
> Interface bleibt am Fahrzeug 'haften'.
> Kunde kann via Sprache oder Fernbedienung innerhalb des Interfaces navigieren. 
> Fahrzeugdaten werden via CaaS abgerufen und aktualisiert.
> Kunde bekommt Fahrzeugdaten (statisch und dynamisch), Videos/ Bilder  angezeigt.
> Kleine Animationen verbessern das Erlebnis.

---

#Historie

---
##Einarbeitung Android, FirstSpirit & CaaS. 

---
##Test App. CaaS
   * Stellt Einzelrequest an Caas
   * bekommt Bild als Zeichenkette zurück.

---
##Ankunft Vuzix. 
   * Leichte Enttäuschung bei allen Beteiligten
   * Near Eye*Microdisplay/Visual Assistant* anstatt *Optical See Through*.
   * Sofort Probleme bei der Anbindung an das Vuzix SDK.
   * Wenig/ Schlechter Support.

---
##Recherche Alternativen
   * Preisrange von USD 200 bis ca USD 4000
   * Qualitätskriterien
   * Field Of View, Displaytype, GP Kapazitäten, Tethering, Gewicht, Support, Verfügbarkeit
   * AR Brillen:
     * Hololens, Microsoft - 
     * Meta2, Meta - 
     * ODG R7 - 
     * Epson Moverio BT300  
     * ShimaLaforgel 
   * VR Brillen:
     * Oculus Rift, HTC Vive, Google Daydream, Sony Playstation VR

---
5. Entscheidung für Epson Moverio BT300
   * See Through Display
   * Preis aktzeptabel
   * Epson relativ etabliert und zu Support fähig

---
6. Test App.  Basics.
   * Bilder, Text und Video. 
   * Menüleiste mit Icons
   * Fragments. 

---
7. Test App. Listen
   * Recyclerview

---
8. Ankunft Epson Moverio
   * Erster Eindruck: deutlich besser als bei Vuzix. Interessantes Bild.
   * Schärfegrad an den Rändern des Displays je nach Träger unterschiedlich.
   * Testen erster Apps hinterlässt ordentlichen Eindruck.

---
9. Test App. Objekterkennung
   * Erste Runde: QR Codes
   * Recherche alternativer QR Codes:
     * Facebook Messenger, Snapchat, Qrhacker
   * Aber: QR Codes auf große Distanz kaum Trackbar und wenn dann nur indem man riesige Codes verwendet. Visuell wenig ansprechend.
   * Zweite Runde: Imagetracking
     * Komplexe Bilder, kontrastreich, flach, glanzfrei
     * Verwendungsidee: Banner der im Showroom hinter dem Fahrzeug steht dient der Erkennung.
   * Dritte Runde: Objekterkennung
     * ausstehend.

---
10. RB fügt CaasAbfrage Komponente hinzu.

---
11. Recherche AR Frameworks 
   * EasyAR - ausreichend, kostenlos
   * Vuforia - top, kostenpflichtig oder branding
   * ARToolKit, Kudan, Wikitude - noch nicht ausführlich recherchiert.

---
12. TestApp. AR Framework.
   * EasyAR. Leichte Einbindung. Kostenlos. Verschiedene Beispiele. Performance ok.
   * Vuforia. Zwar besser/ schneller aber nicht ohne Wasserzeichen kostenlos erhältlich.

---
13. TestApp. Button Animation.
    * Idee: Auswahl von Buttons durch hinschauen/ bewegen. 
    * Dann Auslösen einer Animation die den Auswahlprozess signalisiert 
    * Leider am Ende keine verwendung im Projekt.
    * ***Problem***: erste schwere Unterschiede zwischen Brille und Smartphone.
    * Buttonhovereffekte auf Telefon funktional, auf Brille fehlerhaft. Umständlicher Umbau.  Verdoppelung von Code, zunehmende komplexität die normalerweise unnötig gewesen wäre

---
14. TestApp. Sprachsteuerungsmodul von RB.
    * Funktioniert in Dresden.

---
15. ShowcaseApp. Teaser
    *Design Überlappungen. Eigentlich von Android nicht vorgesehen/ bzw. nicht sauber umzusetzen (negative Margins). Neg. Margins werden nur in bestimmten Viewklassen verwendet. Erfahrung: Zuerst rausfinden ob alles grundsätzlich umsetzbar ist, dann erst mit implementierung anfangen... *
    * Teaser Designumsetzung. Erstes Design.
    * Teaser Einblendung und sticky
    * ***Herausforderung*** : Umwandeln von Bildtrackingdaten in Bildschirmpositionen
      3x4 Matrix  --> x,y Koordinaten

---
16. ShowcaseApp. Main Screen
    * Main Screen Designumsetzung Erstes Design.
    * Einbinden von Video.
    * Einbinden von CaaS Daten
    * ***Herausforderung***: Caas Polling in seiner ursprünglichen Implementierung nur Anroid 5 kompatibel (für Brille), in Android 7 Schwierigkeiten und neuimplementierung notwendig.
    * Einbinden von statischen Daten (DataBinding).
    * Buttons

---
17. ShowcaseApp.  CaaS Update
    * Visualisierung von Update
    * Animationen von Vektorgrafiken

---
18. ShowcaseApp. Animation Video Screen
    * Fullscreen Video inklusive Mediacontroller.

---
19. TestApp. Sprachsteurung auf Brille.
    * Funktioniert nicht. 
    * Fehler meldet dass Audiokanal belegt ist. In Wahrheit hat die Software kein Zugriff auf das Mikrofon. Unterschiedliche Handhabe von Berechtigungen führte zu verstecktem Fehler unter Android 7.
    * Hinzu kommt ein kaputtes Mikro vom mitgelieferten Headset.
    * Zum Glück wird Fehler vor Versand gefunden. 

---
20. Zunehmende Schwierigkeiten mit Brille. 

    * Grünstich immer deutlicher
      * Transparenzen verhalten sich unerwartet. 
    * WLAN Login Problematisch
    * Mikro fehlerhaft

     => Entscheidung: **Brille wird eingesendet**.

---
21. Arbeit wird auf Smartphone fortgesetzt.
    * Plötzlich sieht Design anders aus.
    * Unterschiedliche Bildschirmauflösungen bei Android zwar normal, aber bisher nicht vorgesehen gewesen.
    * Unterschiedliche Pixeldichten
    * Keine Pixeldichte auf Brille angegeben. Kein Testen möglich. 

---
22. Zweiter Designentwurf. 
    * Umsetzung Teaser
    * Umsetzung Main Screen
    * VideoScreen Unverändert

---
23. Transitionen. Animationen beim Übergang zwischen Screens.
    * FadeIn/ FadeOut Teaser
    * FadeIn, Slides Main Screen

---
## Showcase Demo

![alt text][logo]

---
##Zukunft

1. Menünavigation/ Eigeninteraktion
2. Anbindung Commedia
3. Online Sprachsteuerung
4. Verwendung besserer AR Tools/Frameworks
5. Auswahl durch Fokussieren
6. Verschiedene Fahrzeuge in Abhängigkeit vom Tracking Image
7. 3D Objekte tracken
8. Details Screen ... umsetzen


---
#### Quellen:
[logo]: lambo.jpg "Gelber Lambo"
