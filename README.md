Author: Patrick Souty
  
Dual `Linky` power meter monitoring with `Home Assistant` and `ESP32` for `TIC` data link interface
  
Based on following hardware:
  
- `ESP32` `DOIT-DEVT-KIT-V1` including module `ESP-WROOM32`
- `TIC` optocoupler interface boards
- 5.2V power supply
- 2 Power meters
  - French `Linky` type power meter with `TIC` data link (serial date @ 1200 or 9600 b/s over a 50 kHz carrier)

Software: 

- ` ESPHOME ` for the `ESP32` firmware with teleinfo driver
- `Home-assistant` app running on Raspberry PI3, for monitoring and data analysis

## Project description - English version ##

This project is dedicated to the monitoring of 2 distinct `Linky` power meter (French smart power meter) with a single `ESP32` module as the low level interface and `Home Assistant` for data monitoring.

`ESPHOME` is used to generate the ERSP32 firmware with the use of TELEINFO driver for the `TIC` data link interpretation.
It has been preferred to a `TASMOTA` solution because this later cannot be configured to monitor two separate data links.
Two interface boards based on an optocoupler H11AA1 are used for the `TIC` signal demodulation and galvanic isolation.
This interface insures compliance to the Enedis-NOI-CPT_54E specification document.
There exists a lot of similar projects for the use of `TIC` power meter interface for energy monitoring but I have found none with the ability to monitor two power meter with a single `ESP32` module.

The overall electronic is housed inside a plastic box placed in the boiler room.
It is connected to the two power meters outside the house, through two twisted pairs from an Ethernet cable.
The `ESP32` communicates over Wi-Fi with `Home Assistant` running on a RPI 3B.

## Description du projet -  version Française  ##

Ce projet est destiné au suivi en temps réel des consommations électriques grâce à l'exploitation des liaisons de données `TIC` des compteurs `Linky`. Il utilise un module `ESP32` unique pour la dé-commutation des trames `TIC` des 2 compteurs `Linky` qui équipent ma maison.
Le 1er compteur est dédié presque uniquement à la pompe à chaleur qui chauffe la maison et le 2ème couvre tous les autres usages.
Cela a permis de conserver des contrats de 9 kVA et surtout une installation en monophasé.

`ESPHOME` a été utilisé pour le firmware de l'ERSP32 en le compilant avec le driver TELEINFO  pour la dé-commutation de la liaison `TIC`.
J'ai testé également la solution `TASMOTA` qui était légèrement plus simple à mettre en oeuvre mais je ne l'ai pas retenu car elle ne permet malheureusement pas de gérer simultanément 2 liaisons `TIC`.
Deux cartes d'interface basées sur un optocoupler H11AA1 sont utilisées pour la démodulation du signal `TIC` et pour l'isolation galvanique.
Ces cartes sont nécessaires pour assurer la conformité au document de spécification Enedis-NOI-CPT_54E et pour assurer l'interface avec l'ERC32.
Il existe de nombreux projets similaires destinés à s'interfacer avec les compteurs `Linky` mais je n'en ai trouvé aucun permettant de se connecteur à 2 compteurs simultanément avec un seul module `ESP32`, d'où ce projet spécifique.

L'ensemble de l'électronique est logée dans un boîtier de raccordement électrique et installée dans le local chaufferie.
Elle est connectée aux 2 compteurs à l'extérieur de la maison grâce à un câble Ethernet de 10 m dont 2 des 4 paires torsadées sont utilisées.
Le module `ESP32` communique en Wi-Fi avec `Home Assistant` qui tourne sur un RPI 3B.