# Installatie VirtualBox
## Introductie
---

Om een besturingsysteem zoals **Ubuntu 20.04** als "gast" te runnen binnen een "host" zoals bvb. Windows, kan je een **virtuele machine** gebruiken.

**VirtualBox** is een tool die toelaat om virtuele machines te runnen. Naast VirtualBox hebben we ook het extension pack nodig om vanuit de virtuele machine USB poorten te kunnen gebruiken.

De virtuele machine zelf voorzien wij als een `.zip` bestand dat je kan downloaden.


De instructies hieronder zijn geschreven voor Windows, maar de installatie voor mac OS X is zeer analoog.

## Installatie-instructies
---
Zorg dat je minstens 20GB geheugen vrij hebt op je laptop voor je aan de installatie begint.
* VirtualBox en Extenstion Pack installeren
  * Ga naar https://www.virtualbox.org/wiki/Downloads
  * Onder `VirtualBox 6.1.32 platform packages` download de versie voor **Windows hosts**
  * Onder `VirtualBox 6.1.32 Oracle VM VirtualBox Extension Pack`  download voor **All supported platforms**
  * Run de VirtualBox Installer
  * Run de Installer voor de Extension Pack
  * Open `VirtualBox`
  * Herstart jouw laptop
* Virtuele Machine inladen
  * Download [ubuntu20_ingenieursproject.zip](https://ugentbe-my.sharepoint.com/:u:/g/personal/victorlouis_degusseme_ugent_be/EZgzRnYT479BpkqPtQQXUqUBn_N6mFYxoI3L9dlSwrrw3w?e=L2Qogn)  (6GB) naar de folder `C:\Users\jouw_naam\VirtualBox VMs`
  * **Unzip** `ubuntu20_ingenieursproject.zip`
  * Dubbelklik op **ubuntu20_ingenieursproject.vbox**
* Installatie testen
  * Selecteer **ubuntu20_ingenieursproject**, die nu links in de lijst van beschikbare virtuele machines zou moeten staan
  * Klik **Start**

Als Ubuntu succesvol opstart, kan je nu proberen code up te loaden naar the Dwenguino bordje. 
Lees daarvoor [2_installatie_testen.md](https://github.com/Victorlouisdg/microcontrollers/blob/main/installatie/2_installatie_testen.md)
