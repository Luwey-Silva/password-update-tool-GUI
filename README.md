# Password-update-tool-GUI

- Was die Anwendung tut?

Die Anwendung **Password-update-tool-GUI** ist ein Bash-Skript, das Systemadministratoren dabei unterstützt, Benutzerpasswörter auf mehreren Linux-Servern zu verwalten und zu aktualisieren. Sie ermöglicht die sichere und effiziente Änderung von Passwörtern sowohl auf dem lokalen Server als auch auf entfernten Servern. Die Anwendung verwendet whiptail, um eine benutzerfreundliche grafische Benutzeroberfläche (GUI) im Terminal zu bieten, wodurch die Interaktion für den Benutzer vereinfacht wird.

<details>
  <summary>Warum wurden die Technologien im Projekt verwendet?</summary>

  - **Bash-Skript:** Bash-Skripte sind ideal für die Automatisierung von Aufgaben in Unix/Linux-Systemen. Sie bieten eine einfache Möglichkeit, Systembefehle auszuführen und zu skripten, was sie zur perfekten Wahl für administrative Aufgaben macht.

  - **Whiptail:** Whiptail ermöglicht es, textbasierte Dialoge in einer Shell-Skriptumgebung zu erstellen. Diese Funktionalität ist nützlich, um Eingaben vom Benutzer zu erhalten und interaktive Menüs zu bieten. Es verbessert die Benutzerfreundlichkeit erheblich, da es eine einfache GUI im Terminal bietet.
  
  - **SSH:** SSH (Secure Shell) wird verwendet, um sichere Verbindungen zu Remote-Servern herzustellen. Es ermöglicht die verschlüsselte Übertragung von Befehlen und Daten, was für sicherheitskritische Aufgaben wie Passwortänderungen unerlässlich ist. 
</details>

<details>
  <summary>Mit welchen Herausforderungen wurde man konfrontiert?</summary>

  - **Sicherheit:** Eine der größten Herausforderungen bei der Implementierung dieses Projekts war die Gewährleistung der Sicherheit. Da das Skript Passwörter verarbeitet und auf mehreren Servern Änderungen vornehmen kann, war es entscheidend, Sicherheitsmaßnahmen wie die Verschlüsselung der Datenübertragung und die Vermeidung der Speicherung von Passwörtern im Klartext zu implementieren.

  - **Benutzerfreundlichkeit:** Ein weiteres Anliegen war die Schaffung einer benutzerfreundlichen Oberfläche für die Verwaltung von Passwörtern, insbesondere für weniger technisch versierte Benutzer. Die Integration von whiptail half dabei, eine einfache und intuitive Benutzeroberfläche zu erstellen.
  
  - **Fehlerbehandlung und Robustheit:** Da das Skript auf mehreren Servern ausgeführt wird, war es wichtig, robuste Fehlerbehandlungsmechanismen zu implementieren, um sicherzustellen, dass Fehler auf einem Server nicht den gesamten Prozess beeinträchtigen.
</details>

<details>
  <summary>Welche Funktionen sollen in Zukunft implementiert werden?</summary>

  - Erweiterte Authentifizierungsmethoden: Implementierung von Unterstützung für SSH-Schlüsselpaare und andere Authentifizierungsmethoden zur Verbesserung der Sicherheit.
Multi-Faktor-Authentifizierung (MFA): Hinzufügen einer MFA-Funktionalität, um die Sicherheit weiter zu erhöhen.
Benutzerverwaltung: Erweiterung der Anwendung um Funktionen zur Verwaltung von Benutzerkonten, wie das Hinzufügen oder Entfernen von Benutzern.
Zentrales Management-Dashboard: Entwicklung einer Web- oder Desktop-Anwendung, die eine zentrale Verwaltung und Überwachung der Passwortänderungen und Serverstatus ermöglicht.
Automatische Benachrichtigungen: Implementierung einer Funktion zur Benachrichtigung von Administratoren bei erfolgreichen oder fehlgeschlagenen Passwortänderungen.
</details>

## 🏁 Einstieg <a name = "einstieg"></a>

### Voraussetzungen

Welche Dinge werden benötigt um die Software zu installieren und wie wird sie 
installiert?

Bevor Sie das Skript verwenden können, stellen Sie sicher, dass Ihr System die folgenden Anforderungen erfüllt:

```
Betriebssystem: Unix/Linux
root-Rechte: Das Skript muss als root-Benutzer ausgeführt werden.
Abhängigkeiten: Stellen Sie sicher, dass whiptail und ssh installiert sind.
```
Installieren Sie whiptail und ssh, falls diese noch nicht vorhanden sind:


```bash
sudo apt-get update
sudo apt-get install whiptail ssh git
```

### Installation

Eine Schritt für Schritt Anleitung die zeigt, wie die Entwicklungsumgebung zum 
Laufen gebracht wird.

1. Repository klonen

  - Klonen Sie das Repository auf Ihren lokalen Rechner:

```bash
git clone https://github.com/Luwey-Silva/password-update-tool-GUI.git
cd password-update-tool-GUI
```

2. Skript ausführbar machen

Machen Sie das Skript ausführbar:

```bash
chmod +x password_updater_gui.sh
```

## 🔧 Ausführung <a name = "tests"></a>
1. Skript ausführen

    - Führen Sie das Skript mit root-Rechten aus:

```bash
sudo ./admin-passwort-update-root-user-gui.sh
```

2. Benutzeroberfläche verwenden

    - Nach dem Start des Skripts erscheint ein Dialogfeld, das Sie fragt, ob Sie das Programm fortsetzen möchten. Bestätigen Sie mit "Ja".
    - Im nächsten Menü können Sie wählen, ob Sie das Passwort lokal ändern oder auf Remote-Servern aktualisieren möchten.
    - Geben Sie den Benutzernamen und das neue Passwort ein, wenn Sie dazu aufgefordert werden. Bestätigen Sie das Passwort zur Sicherheit.

3. Passwortänderung abschließen
    - Das Skript wird das Passwort gemäß Ihrer Auswahl entweder lokal oder auf den Remote-Servern ändern und Ihnen den Erfolg oder Misserfolg der Operation anzeigen.

## 🔧 Beispielablauf <a name = "tests"></a>
1. Starten Sie das Skript:

```bash
sudo ./admin-passwort-update-root-user-gui.sh
```
2. Bestätigen Sie die Fortsetzung:
3.  Wählen Sie die gewünschte Aktion:
4.  Geben Sie den Benutzernamen ein:
5.  Geben Sie das neue Passwort ein und bestätigen Sie es:

