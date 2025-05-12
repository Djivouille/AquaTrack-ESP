# AquaTrack ESP

[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)

## LE PROJET

AquaTrack ESP est un projet DIY qui permet de mesurer la quantité d'eau consommée en utilisant un Webmos D1 Mini Pro et un capteur de débit d'eau. Le projet est basé sur ESPHome pour une intégration facile avec les systèmes domotiques.

![Project Overview](images/project_overview.png)

## LES PRÉ-REQUIS

- Connaissances de base en électronique et en programmation.
- Un environnement de développement pour ESPHome.
- Accès à un réseau Wi-Fi pour la configuration et le suivi.

## LE BOÎTIER

Le boîtier est conçu pour protéger les composants électroniques des éléments extérieurs. Il peut être fabriqué à l'aide d'une imprimante 3D ou acheté prêt à l'emploi. Assurez-vous qu'il est étanche pour éviter les dommages causés par l'eau.

![Boîtier](images/boitier.png)

## LE HARDWARE

- Webmos D1 Mini Pro
- Capteur de débit d'eau


![Hardware Setup](images/hardware_setup.png)

## LE YAML pour ESP HOME

Voici un exemple de configuration YAML pour ESPHome :

```yaml
esphome:
  name: aquatrack_esp
  platform: ESP8266
  board: d1_mini_pro

wifi:
  ssid: "VOTRE_SSID"
  password: "VOTRE_MOT_DE_PASSE"

# Configuration du capteur de débit d'eau
sensor:
  - platform: pulse_counter
    pin: D1
    name: "Water Flow Sensor"
    unit_of_measurement: "L/min"
    icon: "mdi\:water-pump"
    count_mode:
      rising_edge: INCREMENT
    total:
      name: "Total Water Usage"
      unit_of_measurement: "L"
