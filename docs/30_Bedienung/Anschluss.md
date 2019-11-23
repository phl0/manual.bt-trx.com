# Anschluss

!!! note "Hinweis"
    Beschreibung für dev-board v4.1 und Firmware Version 0.2.1

## 1. Anschluss von Funkgerät, Spannungsversorgung und PTT-Taste

Der Anschluss ans Funkgerät erfolgt in der Regel über ein
[Adapterkabel](../Zusammenbau/Anschlusskabel).

Eine [PTT-Taste](../Zusammenbau/PTT-Taste) kann direkt in das bt-trx Gehäuse
integriert (Kontakte J2), oder an die Klinkenbuchse (J3) angeschlossen werden.

!!! note "Hinweis zum PTT-select Jumper J5"
    Der **Jumper J5** muss für den Funkbetrieb **in jedem Fall** gesteckt sein.  
    Er entscheidet,

    * ob der PTT Taster direkt zum Transceiver
    durchgeschleift wird (Stellung "BTN", Pins 1-2 verbunden), oder
    * ob der ESP32
    das PTT Signal erzeugt (Stellung "uC", Pins 2-3 verbunden), wird benötigt
    für "Soft-PTT" Funktionen.

Nach dem Herstellen der Spannungsversorgung leuchtet die **bernsteinfarbene LED**
(zeigt 3.3 V Betriebsspannung des ESP32 und des BT-Moduls an),
bt-trx startet automatisch.

## 2. Herstellen der Bluetooth-Verbindung

bt-trx beginnt nach dem Start selbstständig, nach geeigneten Geräten für die
Bluetoothverbindung zu suchen und eine Verbindung herzustellen.  
Es wird nur eine Verbindung mit Geräten hergestellt, die das
"HFP"-Profil unterstützen (Autoradios, bestimmte Headsets). Eine (ungewollte)
Verbindung mit einem Smartphone kann daher nicht passieren.

**Info:**
Die Verbindung zu einfachen Bluetooth-Headsets über das "HSP"-Profil wird
aktuell noch nicht unterstützt, ist aber möglich und wird in einer der kommenden
Firmware-Versionen eingebaut werden.

Es kann notwendig sein, das Autoradio zum Verbindungsaufbau in den
Bluetooth-Pairingmodus zu versetzen, um es für bt-trx sichtbar zu machen.  
In der Regel geschieht dies über einen Menüpunkt
"Neues Bluetooth-Gerät hinzufügen" o.ä..

Sobald die Verbindung einmal erfolgeich hergestellt wurde, sollten sich die
beiden Geräte beim nächsten Start des bt-trx, bzw. des Fahrzeugs automatisch
miteinander verbinden.

Die beiden Status-LEDs (grün und blau) liefern folgende Informationen:

| Aktivität-LED (grün) | Bluetooth-LED (blau) | Status                       |
|:--------------------:|:--------------------:|------------------------------|
| aus                  | blinkt               | BT-Verbindungssuche          |
| aus                  | an                   | BT-Verbindung hergestellt    |
| blinkt               | an                   | Audio-Verbindung hergestellt |