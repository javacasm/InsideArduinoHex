# Inside Arduino Hex file

Instalamos la herramientas de avr

sudo apt

## Problema: error accediendo a datos en PROGMEM

    const PROGMEM byte a[]={1,2,3};
    void setup(){
      Serial.begin(9600);
      for (int j=0;j<sizeof(a);j++)
         Serial.println(a[j]);
    }
    void loop(){}


El código correcto sería:


    const PROGMEM byte a[]={1,2,3};
    void setup(){
      Serial.begin(9600);
      for (int j=0;j<sizeof(a);j++)
         Serial.println(pgm_read_byte_near(a + j));
    }
    void loop(){}


## Ver el contenido de un fichero

Como mucho veremos el ensamblador....

Vemos el volcado de memoria

    avr-objdump -m avr -D file.hex

Vemos el ensamblador


    avr-objdump --no-show-raw-insn -m avr -D file.hex


## Desemsamblador

ReAVR https://community.atmel.com/projects/reavr http://www.jassenbaum.de/ja-tools/reavr.html
DisAVR https://www.avrfreaks.net/forum/disavr-win32-101-beta-released

## Clonar programa en arduino

## ¿Cómo extraer el contenido de un Arduino?

Instalamos las herramientas de avr (las instalamos aunque ya están en la carpeta Arduino ~/arduino-1.8.4/hardware/tools/avr/bin/
)


    sudo apt install binutils-avr



https://reverseengineering.stackexchange.com/questions/125/how-do-i-figure-out-what-is-burned-on-an-arduino-rom
