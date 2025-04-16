# 🔋 Home Assistant – Akkusteuerung für SMA-Batterie-Wechselrichter via Modbus

Diese Home Assistant-Automatisierung ermöglicht die flexible Steuerung eines SMA-Wechselrichters über das Modbus-Protokoll. Sie erlaubt die dynamische Anpassung von Lade- und Entladeleistungen des Batteriespeichersystems basierend auf vordefinierten Betriebsmodi und Benutzerpräferenzen.

## ⚙️ Funktionen

- **Modusbasierte Steuerung**: Unterstützt verschiedene Betriebsmodi wie "Max Ladeleistung", "Max Entladeleistung", "Akku Pause (Standby)", "Netzladen inkl. PV Überschuss wenn vorhand" und "Normal Modus".
- **Modbus-Kommunikation**: Sendet spezifische Befehle an den Wechselrichter, um Lade- und Entladeleistungen sowie andere Parameter anzupassen.
- **Automatische Trigger**: Reagiert auf Änderungen von Eingabehilfen oder alle 5 Minuten, um die aktuellen Einstellungen zu überprüfen und anzuwenden.
- **Flexibilität**: Ermöglicht die einfache Anpassung der Lade- und Entladeleistungen durch Benutzer über die Home Assistant-Oberfläche.
- **Batterie Laufzeit Berechnung**: Hier wird ihnen angezeigt wie lange der Akku noch durch hällt beim aktuellen entladen der Batterie.

## 🧰 Erforderliche Helfer

Um die Automatisierung vollständig nutzen zu können, müssen folgende Eingabehilfen in Home Assistant erstellt werden:

### 🎚️ Eingabefelder

- **`input_select.akkusteuerung_sma_wr`**  
  Auswahl des gewünschten Betriebsmodus. Mögliche Optionen:
  - `Max Ladeleistung (W)`
  - `Max Entladeleistung (W)`
  - `Akku Pause ( Standby)`
  - `Normal Modus`
  - `Netzladen`

- **`input_number.akkusteuerung_ladestaerke_soll`**  
  Gewünschte Ladeleistung in Watt.

- **`input_number.akkusteuerung_entladestaerke_soll`**  
  Gewünschte Entladeleistung in Watt.


### 🔘 Schalter

- **`input_boolean.akku_automatik`**  
  Aktiviert oder deaktiviert die automatische Steuerung.

Diese Helfer können über die Home Assistant-Benutzeroberfläche unter **Einstellungen > Geräte & Dienste > Helfer** erstellt werden.

## 🔌 Modbus-Konfiguration

Stelle sicher, dass dein SMA-Wechselrichter über Modbus erreichbar ist und korrekt in Home Assistant konfiguriert wurde. Beispielkonfiguration:

```yaml
modbus:
- name: sma-sr_wr
  type: tcp
  host: 192.xxx.x.xx
  port: 502
  delay: 5
  timeout: 5
    sensors:

