# # EDUCONTROLE — Équipe N°10

> Dispositif autonome de pointage biométrique et de sonorisation scolaire qui apprend aux élèves de Terminale à automatiser la gestion de présence par empreinte digitale.

![Photo du dispositif terminé](docs/medias/photo-finale.jpg)

**Vidéo de démonstration (1 à 2 min)** : [lien à insérer]

## L'équipe

| Nom    | Discipline       | Username         | Rôle               | Période |
| :----- | :--------------- | :--------------- | :----------------- | :------ |
| ADOKOU | CHIMIE           | Victtech-designe | Documentation      | (S1→S4) |
| HODIO  | MATHEMATIQUE     | hodiamarc        | Modélisation 3D    | (S1→S4) |
| ABISSI | MATHEMATIQUE     | Victtech-designe | PCB / Electronique | (S1→S4) |
| FOLLI  | GENIE-ELECTRIQUE | Am-justin        | Developpement Web  | (S1→S4) |

## Intention pédagogique

**Discipline :** Génie Electrique / Informatique - Niveau : Lycée Technique - Effectif : 35 élèves
**Objectifs d'apprentissage :**

- Comprendre le fonctionnement d'un capteur biométrique AS608 (UART, 1000 empreintes)
- Programmer une horloge temps réel RTC DS3231 pour l'horodatage et la sonorisation automatique
- Concevoir un boîtier 20mm/7mm tolérance 0.2mm et un PCB avec BMS + 2x 18650
  **Chapitre programme officiel :** Systèmes embarqués, IoT et gestion de base de données.

## Architecture

![alt text](<Architecture EduControle.png>)

**Principe :**
`[Doigt] -> AS608/R307 -> MCU -> RTC DS3231 (heure) -> LCD 16x2 + Buzzer + BMS/2x18650 -> Site Web 4 pages`

- Fonction 1 : Pointage = Si empreinte OK -> LCD "Présent HH:MM" + log base
- Fonction 2 : Sonnerie = Si heure == heure programmée (07:00, 10:00, 12:00, 15:00, 18:00) -> Buzzer 3s / Sortie sirène V2

## Sommaire du dépôt

| Dossier     | Contenu                                                                                                                         |
| ----------- | ------------------------------------------------------------------------------------------------------------------------------- |
| `docs/`     | Fiche projet, cahier des charges, journal quotidien (15,16,17/09), séquence pédagogique, sécurité, tests, guide de reproduction |
| `hardware/` | CAO boîtier 20mm/7mm capot 2mm, fichiers impression 3D PLA 2h15, PCB KiCad + BMS, schéma RTC DS3231 + AS608 + LCD 16x2          |
| `firmware/` | Code Arduino : enrôlement AS608, reconnaissance, gestion RTC, déclenchement buzzer/sirène, librairie Adafruit Fingerprint       |
| `software/` | Site Web 4 pages : Accueil, Liste élèves, Présences du jour, Stats retards/absences                                             |
| `bom/`      | Nomenclature : R307/AS608, DS3231, LCD 16x2 (20x4 prévu V2), BMS, 2x 18650 + support, Buzzer, PLA                               |

> Les dossiers sans objet pour ce projet sont conservés (exigence ED-03) et signalés ici :
> `hardware/molds/` — sans objet, exemption ET-FAB-06 justifiée dans la fiche projet.
> `hardware/cnc/` — sans objet, aucune opération d'usinage retenue.

## Avancement

| Jalon          | Date       | État | Release                                           |
| -------------- | ---------- | ---- | ------------------------------------------------- |
| J0 Lancement   | 25/08      | ✅   | —                                                 |
| J1 Idée cadrée | 29/08      | ✅   | v0.1                                              |
| J2 Conception  | 05/09      | ✅   | v0.2 - Boîtier 20mm/7mm + PCB KiCad               |
| J3 Prototype   | 12/09      | ✅   | v0.5 - Soudure 12 pts 350°C 0.2 ohm               |
| J4 Intégration | 16/09      | ✅   | v0.9 - RTC DS3231 + AS608 OK + 4 pages web        |
| Gel du dépôt   | 17/09 18 h | ✅   | v1.0 - PCB V2 + Sonnerie auto + Base 4 empreintes |

## Reproduire ce dispositif

Renvoi : [guide de reproduction](docs/06-guide-de-reproduction.md) — coût estimé : 35 500 FCFA.

- AS608 : 12 000 F | DS3231 : 2 500 F | LCD 16x2 : 3 500 F | BMS+2x18650+support : 7 000 F | PCB : 5 000 F | PLA + Buzzer : 5 500 F

## Licences

- **Logiciel** : MIT — pour permettre la réutilisation libre par les autres lycées techniques.
- **Matériel** : CERN-OHL-S v2 — pour garantir le partage des améliorations du boîtier et PCB en open hardware.
- **Documentation et médias** : CC BY-SA 4.0 — pour diffusion pédagogique libre avec attribution.

## Crédits et remerciements

- Librairie : Adafruit Fingerprint Sensor Library (BSD)
- Modèle 3D : Boîtier custom Fusion360 / Tinkercad
- INFPP / MEN - PNFA 2026-2027 - Encadreurs S1 à S4

---

_Projet intégrateur PNFA 2026-2027 · Certification 1 — Praticien · INFPP / MEN_
