---
Title: Upgrade-Guide Windows 10 Home/Pro/Enterprise zu Windows 10 IoT Enterprise LTSC
---

## Schritt 1: ISO-Datei herunterladen
Lade die Windows 10 Enterprise LTSC ISO herunter:
**Download Link**:  
[https://drive.massgrave.dev/de-de_windows_10_enterprise_ltsc_2021_x64_dvd_71796d33.iso](https://drive.massgrave.dev/de-de_windows_10_enterprise_ltsc_2021_x64_dvd_71796d33.iso)  
Hinweis: Dies ist die Standard-Version von Windows 10 Enterprise LTSC (ohne IoT), aber sie behält deine Systemsprache bei Deutsch. Das passen wir später an.

---

## Schritt 2: Systemsprache überprüfen
Stelle sicher, dass deine Systemsprache auf **Deutsch** eingestellt ist. Führe dazu in der PowerShell folgenden Befehl aus:

```powershell
dism /english /online /get-intl | find /i "Default system UI language"
```

Die Ausgabe sollte ```de-DE``` sein.

Falls die Sprache nicht Deutsch sondern Englisch ist, findest du hier die passende ISO-Version:
[Windows LTSC Versions](https://massgrave.dev/windows_ltsc_links#:~:text=en%2Dgb_windows_10_enterprise_ltsc_2021_x86_dvd_baa2b09f.iso-,English,-x64)

---

## Schritt 3: Daten sichern
⚠️ Sichere alle wichtigen Daten (_Lesezeichen, Passwörter, Bilder, Downloads etc._) von deinem Laufwerk ```C:```.
Hinweis: Der Upgrade-Prozess verläuft in der Regel reibungslos, aber du wechselst u.U. von Version 22H2 zu 21H2. Vorsicht ist immer ratsam.

---

## Schritt 4: Registry-Key anpassen
Führe in der PowerShell den folgenden Befehl aus, um den Registry-Key zu setzen:

```powershell
reg add "HKLM\SOFTWARE\Microsoft\Windows NT\CurrentVersion" /v EditionID /d IoTEnterpriseS /f
```
Starte anschließend **schnell** das Setup aus der ISO-Datei.

---

## Schritt 5: Upgrade durchführen
Wähle im Setup die Option **"Behalte persönliche Daten und Apps bei"**.
⚠️ Wichtig: Sei wirklich zügig, da diese Option nach kurzer Zeit nicht mehr verfügbar ist.
Lasse die Installation anschließend durchlaufen.

---

## Schritt 6: Upgrade auf IoT Enterprise LTSC
Nach dem Upgrade aktiviere deine Windows-Kopie mit folgendem Key:
```QPM6N-7J2WJ-P88HH-P3YRH-YY74H```
Dein System wird möglicherweise neu starten.
Deine Windows-Version ist nun angepasst.

---

## Schritt 7: Windows legitim aktivieren
Öffne die PowerShell und führe folgenden Befehl aus:

```powershell
irm https://get.activated.win | iex
```
Wähle Option [1] (alternativ auch 3, 4 oder 5, [1] oder [3] sind aber zu bevorzugen).
Windows ist nun aktiviert.

---

## Schritt 8: Microsoft Store wiederherstellen (falls notwendig)
Falls der Microsoft Store nach dem Upgrade fehlt und benötigt ist, führe in der PowerShell folgenden Befehl aus:

```powershell
wsreset -i
```
> Warte etwa 2 Minuten, bis der Store wieder verfügbar ist.

Den AppInstaller kannst du bei Bedarf hier herunterladen:
https://apps.microsoft.com/detail/9nblggh4nns1
> Der Microsoft Store muss dafür auf dem System installiert sein.

---

✅ Das Upgrade ist nun abgeschlossen, und dein System läuft unter Windows 10 IoT Enterprise LTSC.