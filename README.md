# SMA-SBS-Ladesteuerung
SMA SBS 5.0 Home Assistant Ladesteuerung


🔋 Home Assistant – Akkusteuerung für SMA-Wechselrichter via Modbus

Diese Home Assistant-Automatisierung ermöglicht die flexible Steuerung eines SMA-Wechselrichters über das Modbus-Protokoll. Sie erlaubt die dynamische Anpassung von Lade- und Entladeleistungen des Batteriespeichersystems basierend auf vordefinierten Betriebsmodi und Benutzerpräferenzen.​

⚙️ Funktionen

Modusbasierte Steuerung: Unterstützt verschiedene Betriebsmodi wie „Akku schnell Laden“, „Akku schnell Entladen“, „Akku 0.2C laden“, „Akku Pause“ und „Normal Modus“.​
Modbus-Kommunikation: Sendet spezifische Befehle an den Wechselrichter, um Lade- und Entladeleistungen sowie andere Parameter anzupassen.​
Automatische Trigger: Reagiert auf Änderungen von Eingabehilfen oder alle 5 Minuten, um die aktuellen Einstellungen zu überprüfen und anzuwenden.​
Flexibilität: Ermöglicht die einfache Anpassung der Lade- und Entladeleistungen durch Benutzer über die Home Assistant-Oberfläche.​
🧰 Erforderliche Helfer

Um die Automatisierung vollständig nutzen zu können, müssen folgende Eingabehilfen in Home Assistant erstellt werden:​

🎚️ Eingabefelder
input_select.akkusteuerung_sma_wr: Auswahl des gewünschten Betriebsmodus. Mögliche Optionen:​
Akku schnell Laden​
Akku schnell Entladen​
Akku 0.2C laden​
Akku Pause​
Normal Modus​
input_number.akkusteuerung_ladestaerke_soll: Gewünschte Ladeleistung in Watt.​
input_number.akkusteuerung_entladestaerke_soll: Gewünschte Entladeleistung in Watt.​
input_number.akkusteuerung_02c_ladestaerke: Ladeleistung für den 0.2C-Modus in Watt.​
🔘 Schalter
input_boolean.akku_opti_automatik: Aktiviert oder deaktiviert die automatische Steuerung.​
GitHub Docs
Diese Helfer können über die Home Assistant-Benutzeroberfläche unter Einstellungen > Geräte & Dienste > Helfer erstellt werden.​

🔌 Modbus-Konfiguration

Stelle sicher, dass dein SMA-Wechselrichter über Modbus erreichbar ist und korrekt in Home Assistant konfiguriert wurde. Beispielkonfiguration:​

modbus:
  - name: sma-sr_wr
    type: tcp
    host: <IP_DEINES_WECHSELRICHTERS>
    port: 502
Ersetze <IP_DEINES_WECHSELRICHTERS> durch die tatsächliche IP-Adresse deines Wechselrichters. Weitere Informationen zur Modbus-Konfiguration findest du in der Home Assistant-Dokumentation.​

📝 Hinweise

Die Automatisierung setzt voraus, dass der Wechselrichter Modbus-Befehle akzeptiert und korrekt auf die angegebenen Registeradressen reagiert.​
Es wird empfohlen, die Modbus-Kommunikation zunächst zu testen, um sicherzustellen, dass die Verbindung stabil ist und die Befehle korrekt umgesetzt werden.​
Bei Unsicherheiten bezüglich der Registeradressen oder der Modbus-Konfiguration konsultiere bitte die Dokumentation deines Wechselrichters oder wende dich an den Hersteller.​
