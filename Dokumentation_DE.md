#Dokumentation Android Anwendung ShowcaseApp:

## `java ` Folder

###de.materna.ar.MainActivity (Teaser).

* Hat ein SurfaceView (GLSurfaceView) das wiederum das HelloAR haelt. Beide Klassen sind weitestgehend von EasyAR implementiert. Ein Groяteil des dort vorhandenen Codes wird Momentan nicht gebraucht. Sollte das Projekt aber um 3D Animationen erweitert werden, koennte dieser noch hilfreich sein.
* In der HelloAR werden Bilddaten (aus app/src/main/assets/trackers.json) in eine trackers liste geladen
* Es wird regelmaeяig der Camerastream mit den trackers abgeglichen.
* Wird ein Bild erkannt, wird eine 3x4 Matrix ausgelesen, aus dieser werden ungefaehre Bildschirmkoordinaten berechnet.
* Die Koordinaten werden vom Observer (HelloAR) an den Subscriber in die MainActivity zurueckgereicht.
* In der MainActivity wird dann ein ein und ausfaden des Teaser eingeleitet.
* Ist der Teaser sichtbar laesst sich der naechste Bildschirm durch Buttonklick annavigieren.

###de.materna.ar.CentralActivity (Main Screen).

* Databinding in der Activity und der dazugehoerigen XML https://developer.android.com/topic/libraries/data-binding/index.html
* Ein Listener horcht ob das Mikrofon was erkennt/hoert (voice.VoiceControlService)
* Die Animationen der Activity werden in dem onWindowsChanged() Callback gestartet (animateActivityStart()), da diese direkt nach der onResume() aufgerufen wird.
* Da der Start des Videos ausserhalb des Bildschirmsliegt muss das layout/position zu Animationsstart manuel programmiert werden.
* Views werden zu Transitions und dann zu TransitionSets zusammengefuegt und konfiguriert (Startdelay, Duration).
* Ein Listener wartet auf das Ende der Animation und beginnt dann das Video und startet das CaaS Update
* Close Button ist equivalent zu Androids Pfeil zurueck Button. Play Button startet VideoActivity.

###de.materna.ar.VideoActivity (Video Fullscreen).
* Einfache Aktivity die das Video im Vollbild abspielt.
* Ein MediaController wird mit einem VideoView verbunden und das Video Gestartet.

###de.materna.ar.ShowcaseApp

###de.materna.ar.easyAr.GLView

* SurfaceView, die zum Zeichnen einer eigenen Oberflaeche benoetigt wird. Falls OpenGL Grafiken in Zukunft hinzugefuegt werden sollen, wird diese benoetigt. 
* Ausserdem Praktisch fuer uns, da die SurfaceView eine eigene Rendermethode hat, die wir auch fuer den Teaser mitnutzen.

###de.materna.ar.easyAr.HelloAR
* Die ARListener sind notwendig, da durch sie fading und postioning des Teasers weitergeleitet werden.
* Bilddaten/ zu trackende Images werden aus _app/src/main/assets/trackers.json_ in eine trackers liste geladen.
* Es wird regelmaeяig der Camerastream mit den trackers abgeglichen.
* Wird ein Bild erkannt, wird eine 3x4 Matrix ausgelesen, aus dieser werden ungefaehre Bildschirmkoordinaten berechnet: `transformCoorinates (float[]):Vec2`.
* Die Koordinaten werden vom Observer (HelloAR) an den Subscriber in die MainActivity zurueckgereicht.
* Soll der Stream der Camera auch im Display angezeigt werden, Zeile 238 einkommentieren.

###de.materna.ar.easyAr.BoxRenderer
* Hier werden 3D Objekte erzeugt
* Kann in _de.materna.ar.easyAr.HelloAR: Zeile 266_ einkommentiert werden

###de.materna.ar.model.Vehicle
* Bildet die Fahrzeug Bean ab

###de.materna.ar.model.VehicleBuilder
* Builder

###de.materna.ar.ButtonHoverListener
* Diese Klasse wurde nur notwendig, da beim Hovereffekt der Buttons, auf der Brille die Farbe des Buttonicons nicht geswitcht wurde. Haette das einwandfrei geklappt
  haette das Hovern in XML geloest werden koennen.

###de.materna.ar.Speechlistener
###de.materna.ar.ARListener
###de.materna.ar.Utils

- Utility Functionen die in verschiedenen Klassen verwendet werden

###de.materna.ar.caas.rest.response.MaserPrice
###de.materna.ar.caas.rest.response.MaserPriceResponse
###de.materna.ar.caas.rest.CaasCollection
###de.materna.ar.caas.rest.CaasRestClient
###de.materna.ar.caas.FinancingJobService
###de.materna.ar.caas.FinancingJobServiceManager
###de.materna.ar.voice.VoiceCommand
###de.materna.ar.voice.VoiceControllableActivity
###de.materna.ar.voice.VoiceControlService



##  `res` Folder

##### `layout`Folder:

Vorab: manche Elemente sind unsichtbar (Transitionen werden durch Sichtbarkeitswechsel ausgelöst)

- `activity_main.xml` besteht aus
  - preview: enthält GLSurfaceView Zeichnungen (Kamerastream , 3D Objekte)
  - button: Abkürzung für Testzwecke zur nächsten Activity. Ist unsichtbar, liegt oben links.
  - scene_root: enthält den eigentlichen Teaser
  - speechbubble: Sprechblase unten links
- `activity_central.xml` besteht aus
  - layout: muss oberstes tag sein, da sonst binding nicht funktioniert
  - closeButton:
  - background_layer; Name, Untertitel, Hintergrundstreifen
  - video_box: skaliert um schwarzen Rand zu verdecken. enthält Video, Button und Text für Video (derzeit nicht nötig)
  - text_container: enthält die gebindeten Daten, und Button. 
- `activity_video.xml` besteht aus 
  - video_container_full, button_close, speechbubble
  - hintergrund von speechbubble. da ohne hintergrund zum zeitpunkt des testens die bubble nicht angezeigt wurde. dont know why.
- `teaser.xml`
  - das eigentliche sichtbare teaserlayout 


***

##### `drawable`folder

- Bilder (jpg, png) müssen je nach Auflösung im entsrprechenden Ordner liegen (eg drawable-ldpi). Sonst werden sie nicht angezeigt.

- Icons können durch XML als Vektoren eingfügt werden. Die Beschreibung des Vektorpfades findet man u.a. im Dateiformat SVG.  https://iconmonstr.com/ hilft

- Um Hovereffekte zu ermöglichen kann man verschiedenen Zustandsversionen eines Icons abspeichern und dann je nach Zustand darauf verweisen. Beispiel:

- `button_main`: 

  ```
  <?xml version="1.0" encoding="utf-8"?>
  <selector xmlns:android="http://schemas.android.com/apk/res/android">

      <item android:drawable="@drawable/button_hover" android:state_focused="true"/>
      <item android:drawable="@drawable/button_hover" android:state_hovered="true"/>
      <item android:drawable="@drawable/button_normal" android:state_hovered="false"/>

  </selector>
  ```

  verweist u.a. nach:

- `button_hover`

  ```
  <?xml version="1.0" encoding="utf-8"?>
  <vector xmlns:android="http://schemas.android.com/apk/res/android"
      android:width="24dp"
      android:height="24dp"
      android:viewportWidth="24"
      android:viewportHeight="24">

      <path
          android:strokeColor="@color/ar_light_blue"
          android:fillColor="@android:color/white"
          android:pathData="M0,0 l24,0 l0,24 l-24,0 z"
          android:strokeWidth="1"/>

  </vector>
  ```

  ​

***

##### `anim` Folder

- anim file animiert pfade oder gruppen von pfaden. 
- um eine Animation tatsächlich umzusetzten braucht es drei dateien:
  - `anim` : anim.xml : die animations anweisung
  - `drawable` : icon.xml : das zu animierende icon
  - `drawable ` : icon_anim.xml : fasst die oberen beiden zusammen

Guter Einstieg: http://www.androiddesignpatterns.com/2016/11/introduction-to-icon-animation-techniques.html

***

##### `values`Folder

enthält Templates für Strings, Farben, Dimensionen (Größen), Styles. Genutzt in diesem Projekt werden `dimens.xml`, und `colors.xml`

***

##### `raw`Folder

enthält die videos im mp4 Format