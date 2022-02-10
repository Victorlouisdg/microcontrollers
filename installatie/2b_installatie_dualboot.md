# Installatie Dual-Boot
## Introductie
---

Dual-booten wilt zeggen dat je op één computer twee besturingssystemen installeert. Deze besturingssystemen krijgen elk een hun eigen deel van de harde schrijf. Bij het opstarten van je computer krijg je bij een dual-boot een menu met de keuze of je bvb. `Windows 10` of `Ubuntu 20.04` wilt opstarten.

Dual-booten is tegenwoordig heel veilig, omdat de gebruitke tools veel checks ingebouwd hebben om te zorgen dat je niet veel mis kan doen. Toch is het sterk aangeraden om een **backup** te maken van alle belangrijke bestanden op je laptop voor je aan het dual-booten begint.

Na de dual-boot voorzien we ook nog instructies om een aantal programma's te installeren die ook nodig zijn voor dit vak zoals `VSCode` en `PlatformIO`.

## Installatie-instructies
---

* Dual-boot installeren
    * Volg de stappen in dit artikel: 
        * https://www.tecmint.com/install-ubuntu-alongside-with-windows-dual-boot/
    * Het meest voorkomende probleem is dat `Windows` zijn partitie niet wil verkleinen. Als dit voorkomt, zoek dan de foutmelding op op Google en vraag hulp aan de begeleiders.
* Extra programma's installeren in `Ubuntu`
    * `VSCode` installeren:
        * **Download** de `VSCode` **.deb** file op https://code.visualstudio.com/
        * Open een **Terminal**
        * Ga naar de `Downloads` folder met het commando **cd ~/Downloads**
        * Installeer `VScode` met **sudo apt install ./&lt;file>.deb**, waarbij je **&lt;file>** vervangt door de naam van het bestand. Als je het begin van de naam getypt hebt, kan je **Tab** gebruiken om de rest van de **naam te vervolledigen**.
    * `PlatformIO` installeren:
        * Installeer python3-venv met **sudo apt install python3-venv** 
        * Start `VSCode`
        * Klik op het **Extensions** icoon, zoek en installeer de **PlatformIO IDE**
    * `PlaformIO` configureren voor de Dwenguino.
        * Maak een nieuw bestand **dwenguino_avr.json** in `~/.platformio/platforms/atmelavr/boards` met daarin de code onderaan deze instructies

Als bovenstaande installatie succesvol was, kan je nu proberen code up te loaden naar the Dwenguino bordje.
Lees daarvoor [3_installatie_testen.md](https://github.com/Victorlouisdg/microcontrollers/blob/main/installatie/3_installatie_testen.md)

Code voor **dwenguino_avr.json**:
```json
{
  "build": {
    "core": "dwenguino", 
    "extra_flags": "", 
    "f_cpu": "16000000L",  
    "mcu": "at90usb646", 
    "variant": "leonardo"
  }, 
  "frameworks": [
    
  ], 
  "name": "Dwenguino_avr", 
  "upload": {
    "disable_flushing": true, 
    "maximum_ram_size": 4096, 
    "maximum_size": 61440, 
    "protocol": "avr109", 
    "require_upload_port": true, 
    "speed": 57600, 
    "use_1200bps_touch": true, 
    "wait_for_upload_port": true
  }, 
  "url": "http://www.dwengo.org", 
  "vendor":"Dwengo"
}

```
