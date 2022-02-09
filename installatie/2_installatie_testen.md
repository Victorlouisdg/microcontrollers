# Installatie Testen
## Introductie
---

Om je installatie te testen, zullen we:
1. Een nieuw `PlatformIO` **project aanmaken**
2. De **code** van dit project **uploaden** naar de Dwenguino

Als je de virtuele machine gebruikt, zal je zien dat wij al een `test` project aangemaakt hebben. Als je wil kan je rechtstreeks naar stap 2 gaan en de code van dit test project al een proberen up te loaden. Volg daarna zeker ook eens de instructies om een nieuw `PlatformIO` project aan te maken. 

## PlatformIO project aanmaken
---
Voor elk practicum en het project maak je best een afzonderlijk `PlatformIO` project. 

* Een nieuw `PlatformIO` project aanmaken
  * Klik in VSCode op het **PlatformIO icoontje** (in de balk links)
  * Klik onder PIO Home op **Open**
  * Klik **New Project**, nu zou het venster te zien in **Figuur 1** moeten verschijnen:
    * Kies een naam ,bijvoorbeeld `practicum 1`
    * Delecteer als board **Dwenguino_avr (Dwengo)**, let op dat de **_avr** er zeker in staat
    * `Framework:` mag leeg blijven
  * Klik **finish**, als je de default location gekozen hebt, zou je nu een project moeten hebben in `~/Documents/PlatformIO/Projects`


**Figuur 1**: Project wizard van `PlatformIO`

![project wizard](https://i.imgur.com/irZqFBA.png)

## Code uploaden naar de Dwenguino
Voor we code kunnen uploaden naar het bordje, moeten we drie dingen doen:
1. Code voorzien met een **main()** functie in de `src` map
2. PlaformIO configuren om de code juist up te loaden, dit doen we in `platformio.ini`
3. Het bordje aan je laptop aansluiten met de **programmer**


### Instructies

---

#### 1. Main functie voorzien
* Zoek de **src** folder en maak een nieuw bestand **main.c**
* Kopieer onderstaande code naar **main.c** en save het bestand

Code voor `main.c`:
```c
#include <avr/io.h>
#include <util/delay.h>

int main(void)
{
    // make the LED pin an output for PORTB5
    DDRA = 0xFF;    // Set all portA pins as output
    PORTA = 0;      //Turn all LEDS off

    while (1)
    {
        _delay_ms(500);

        // toggle the LED
        PORTA ^= 0b10101010;
    }

    return 0;
}
```
Nu zou je de code al moeten kunnen compileren, dit kan je testen door onder **PROJECT TASKS** op **Build** te klikken.

---

#### 2. PlatformIO upload configureren
* Zoek het **platformio.ini** in je project
* Vervang de inhoud door onderstaande code:

Code voor `platformio.ini`:
```ini
[env:dwenguino_avr]
platform = atmelavr
upload_protocol = usbasp
board = dwenguino_avr
upload_port = usb
upload_flags =
    -C
    ; use "tool-avrdude-megaavr" for the atmelmegaavr platform
    $PROJECT_PACKAGES_DIR/tool-avrdude/avrdude.conf
    -p
    $BOARD_MCU
    -P
    $UPLOAD_PORT
    -c
    usbasp
upload_command = sudo ~/.platformio/packages/tool-avrdude/avrdude $UPLOAD_FLAGS -U flash:w:$SOURCE:i
```

---

#### 3. Programmer aansluiten
* Verbind de programmer met het Dwenguino bord zoals op **Figuur 2**, met de roze kabel naar het scherm toe
* Verbind het andere uiteinde met een USB poort van je laptop

**Figuur 2**: Oriëntatie van de programmer op het Dwenguino bord

![programmer_connection](https://i.imgur.com/HIOESql.jpg)


---

#### Uploaden met PlatformIO
* Klik **Upload** onder **PROJECT TASKS** in het Platformio menu
  * Als alternatief kan je ook in de balk onderaan op het pijltje &#x2794;
 klikken.

 Als je nu **[SUCCESS]** ziet verschijnen in de Terminal, is de upload gelukt en staat je code nu op de Dwenguino. Je zou moeten zien dan de helft van leds nu elke 4 seconden aan en uit gaan.

Als dat zo is, ben je klaar om aan practicum 1 te beginnen!


#### Problemen met de upload

Als je geen **[SUCCESS]** te zien krijgt, maar **[FAILED]** met:
```
avrdude: error: could not find USB device with vid=0x16c0 pid=0x5dc vendor='www.fischl.de' product='USBasp'
```

Controleer dan:
  * De aansluiting van de programmer
  * Als je de Virtual Box gebruikt
    * Dat het Virtual Box Extension Pack geïnstalleerd is
    * Dat je bovenaan bij Devices > USB de programmer ziet staan (iets met **fischl**) en dat die geselecteerd is

Als dit allemaal niet werkt, probeer dan VSCode, de virtual box en je laptop opnieuw op te starten. Als uploaden nog steeds niet lukt, vraag dan hulp aan een van de begleiders.