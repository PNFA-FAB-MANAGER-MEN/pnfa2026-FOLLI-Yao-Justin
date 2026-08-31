# Fiche projet — Équipe 10

> Livrable L2 · Jalon J1 (samedi 29 août 2026) · validée par l'encadreur référent.
> Aucune fabrication n'est autorisée avant la validation de ce jalon.

# Reformulation du projet

**Système de pointage biométrique et de gestion horaire scolaire à base d'ESP32**

Un dispositif embarqué installé à l'entrée de l'école permet aux élèves de pointer leur présence par empreinte digitale. Le dispositif comprend :

- Une authentification par capteur d'empreinte digitale
- Des témoins lumineux (LED) pour indiquer le statut du pointage (succès, échec, en attente)
- Un buzzer pour le retour sonore
- Un écran LCD affichant l'heure en temps réel (fonction horloge) et les messages de pointage
- Une connexion WiFi vers une plateforme web pour :
  - la consultation et l'extraction des données de présence
  - la programmation d'horaires de sonnerie (alarmes déclenchées à distance selon un planning défini par l'administration)

Le système fonctionne donc en 2 volets : le **dispositif physique** (ESP32 + périphériques) et la **plateforme web** (backend + base de données + interface admin) qui communique avec l'ESP32.

# Liste du matériel

**Carte principale**
- ESP32  Wi-Fi intégré

**Module empreinte digitale**
- Capteur d'empreinte digitale R307 ou AS608 (communication UART, compatible ESP32)

**Affichage**
- Écran LCD 16x2 avec 
- Module I2C (pour limiter le nombre de pins utilisés)

**Signalisation**
- 2 LED (vert/rouge) + résistances 220Ω
- Buzzer actif 5V

**Horloge / temps réel**
- Module RTC DS3231 (pour garder l'heure précise même sans Wi-Fi, plus fiable que le NTP seul)

**Sonnerie de l'école (déclenchement à distance)**
- Une sortie à explorer plutard (La sonnerie sera simulé par le buzzeur pour ce prototype)

**Alimentation**
- Alimentation 5V/2A (adaptateur secteur) pour le boîtier fixe
- Régulateur si besoin d'alimenter capteur + LCD + relais simultanément

**Divers**
- Boîtier de protection à modeliser et à imprimer
- Câbles Dupont / breadboard pour prototypage, puis PCB ou plaque pastillée pour version finale
- Bouton poussoir (reset/admin local, optionnel)
- Bouton ON/OFF pour le système

**Côté plateforme web**
- Backend (Laravel) + base de données (MySQL)
- API REST pour que l'ESP32 envoie les données de pointage et récupère les horaires de sonnerie
- Interface admin pour gérer élèves, consulter présences, programmer les alarmes