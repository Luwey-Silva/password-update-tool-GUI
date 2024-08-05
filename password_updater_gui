#!/bin/bash

# Skript zum Ändern des Benutzerpassworts auf mehreren Remote-Linux-Servern mit Whiptail

# Überprüfen, ob das Skript als root ausgeführt wird
if [ "$(id -u)" -ne 0 ]; then
  whiptail --title "Fehler" --msgbox "Dieses Skript muss als root ausgeführt werden." 8 40
  exit 1
fi

# Remote-Server-Daten
# IP-Adressen und Hostnamen der Remote-Server
SERVER1="192.168.178.151"
SERVER2="192.168.178.152"
SERVER3="remote-rdp"  # Hostname eines weiteren Servers
SSH_USER="root"  # Standard-SSH-Benutzer

# Funktion zum Ändern des Passworts auf einem Remote-Server
change_password_remote() {
  local server=$1
  # Ändert das Passwort für den Benutzer auf dem Remote-Server
  ssh "$SSH_USER@$server" "echo '$USERNAME:$PASSWORD' | chpasswd"

  # Überprüfung, ob der Befehl erfolgreich war
  if [ $? -eq 0 ]; then
    whiptail --title "Erfolg" --msgbox "Passwort für Benutzer $USERNAME auf dem Remote-Server $server erfolgreich geändert." 8 40
  else
    whiptail --title "Fehler" --msgbox "Fehler beim Ändern des Passworts auf dem Remote-Server $server." 8 40
  fi
}

# Funktion zum Ändern des Passworts lokal
change_password_local() {
  # Ändert das Passwort für den Benutzer lokal
  echo "'$USERNAME:$PASSWORD' | sudo chpasswd"

  # Überprüfung, ob der Befehl erfolgreich war
  if [ $? -eq 0 ]; then 
    whiptail --title "Erfolg" --msgbox "Passwort für Benutzer $USERNAME lokal erfolgreich geändert." 8 40
  else
    whiptail --title "Fehler" --msgbox "Fehler beim Ändern des Passworts lokal." 8 40
  fi
}

# Funktion zum Ändern des Passworts auf allen Remote-Servern
change_password_all_remotes() {
  # Ruft die Funktion change_password_remote für alle definierten Server auf
  change_password_remote $SERVER1
  change_password_remote $SERVER2
  change_password_remote $SERVER3
}

# Funktion zur Eingabe und Überprüfung des Benutzernamens und Passworts
get_username_and_password() {
  # Benutzername abfragen
  USERNAME=$(whiptail --title "Benutzernamen eingeben" --inputbox "Geben Sie den Benutzernamen ein, dessen Passwort geändert werden soll:" 8 40 --title "Benutzername" 3>&1 1>&2 2>&3)
  if [ $? -ne 0 ]; then exit 1; fi

  # Neues Passwort abfragen
  PASSWORD=$(whiptail --title "Neues Passwort" --passwordbox "Geben Sie das neue Passwort ein:" 8 40 --title "Passwort" 3>&1 1>&2 2>&3)
  if [ $? -ne 0 ]; then exit 1; fi

  # Passwort bestätigen
  PASSWORD_CONFIRM=$(whiptail --title "Passwort bestätigen" --passwordbox "Geben Sie das neue Passwort erneut ein:" 8 40 --title "Passwort bestätigen" 3>&1 1>&2 2>&3)
  if [ $? -ne 0 ]; then exit 1; fi

  # Überprüfen, ob die Passwörter übereinstimmen
  if [ "$PASSWORD" != "$PASSWORD_CONFIRM" ]; then
    whiptail --title "Fehler" --msgbox "Die Passwörter stimmen nicht überein." 8 40
    exit 1
  fi
}

# Menü anzeigen
# Erster Hinweis, um die Benutzer zu warnen
if whiptail --yesno "Dieses Programm ändert das Passwort für SERVER1, SERVER2 und Remote-RDP. Sind Sie sicher?" 10 100; then
  echo
else
  exit 1
fi

# Auswahlmenü für die Benutzeraktion
OPTION=$(whiptail --title "Passworten von Server und Dienste Aktualisieren - Luwey Silva" --menu "Wähle eine Option aus" 18 100 10 \
  "Passwort lokal ändern (SERVER4)" "" \
  "Passwort auf Remote-Servern ändern (SERVER1, SERVER2, Proxy-guacamole)" "" 3>&1 1>&2 2>&3)

# Überprüfung, ob eine Option gewählt wurde
if [ -z "$OPTION" ]; then
  exit
else
  echo "Passwort wurde aktualisiert."
  echo "Der Benutzer hat $OPTION ausgewählt."
fi

# Benutzername und Passwort abfragen
get_username_and_password

# Aktion basierend auf der Auswahl durchführen
case $OPTION in
  "Passwort lokal ändern")
    change_password_local
    ;;
  "Passwort auf Remote-Servern ändern")
    change_password_all_remotes
    ;;
  *)
    exit 1
    ;;
esac
