## Lumberjack Kit - Guía de ensamble

Esta guía de ensamble te ayudara a construir tu teclado Lumberjack. El proceso es relativamente sencillo y solo necesitaras un mínimo de experiencia soldando.



## Antes de empezar

* Se requieren las siguientes herramientas, que no se incluyen en el kit:

    * Estaño para soldar (soldadura)
    * Cautín
    * Pinzas de corte
    * 58 a 60 switches MX (Dependiendo del layout)

*  Revisa la lista de componentes en el [BOM](BOM.md).
    * Los componentes tienen marcado su valor o nombre.
    * Es importante no confundir los diodos zener (2 piezas) con los diodos 1N4148 (60 piezas), pues su función es diferente.
    * Si no tienes experiencia previa soldando componentes, puedes revisar la siguiente guia: 
        * https://learn.adafruit.com/adafruit-guide-excellent-soldering/tools
    
## Soldado de componentes

### Diodos Zener (D61,62)

Solde los diodos Zener D61 y D62. Estos diodos son componentes con polarización específica (orientación), por lo tanto se debe tener cuidado con la dirección de los mismos. La línea negra en el diodo es el cátodo y debe soldarse en el pad cuadrado de la pcb.

![Diodos Zener](images/guide/zener.jpg)

### Resistores (R1,2,3,4,7,8)

Solde los resistores.

Asegurese de utilizar los resistores correctos en cada lugar. Puede identificar los resistores por la cantidad de los mismos, por su valor marcado en la etiqueta o bien por su valor identificando el código de colores en las bandas de los resistores:

* R1,7,8: 1.5kΩ Café, verde, negro, café, verde
* R2,3: 75Ω Violeta, verde, negro, dorado, rojo
* R4: 10kΩ Café,verde, negro, rojo, rojo

![Resistores](images/guide/resistors.jpg)

### Resistors en caso de upgradear al puerto USB-C (R5,6)

Si decides instalar el conector USB-C, necesitas soldar estos 2 resistores extras (incluidos en el kit).

* R5,6: 5.1kΩ Verde, café, negro, café, rojo

![Resistores USB-C](images/guide/resistors-usbc.jpg)

### Diodos 1N4148 (D1-60)

Solde los diodos

Solde los diodos Zener D61 y D62. Estos diodos son componentes con polarización específica (orientación), por lo tanto se debe tener cuidado con la dirección de los mismos. La línea negra en el diodo es el cátodo y debe soldarse en el pad cuadrado de la pcb.

![Diodos 1N4148](images/guide/diodes.jpg)

### Crystal (Y1)

Solde el cristal de cuarzo.
Este componente no tiene una polarización específica.

![Cristal](images/guide/crystal.jpg)

### Capacitores (C1,2,4,5)

Solde los capacitores pequeños amarillos de 22 pF C1 y C2 (marcados como 22)

Solde los capacitores de 100 nF (marcados como 104)

No confunda los valores de los capacitores

![Capacitores](images/guide/capacitors.jpg)

Dejaremos el capacitor electrolítico al final, pues por su altura puede incomodar el tranajar con la pcb boca-abajo.

### USB connector (J1)
#### USB Mini

Coloque el conector USB dentro de la marca de la pcb en el lado inverso de la pcb (los pines deberan quedar hacia la parte superior). Por el tamaño del componente este se mantendrá fijo para que se solde.

Se recomienda soldar primero una de las patillas del conector y posteriormente los pines, seguido de la otra patilla.


![USB](images/guide/usb.jpg)


### LEDs (LED1,2)

Solder the LEDs.

LEDs are a polarized component and therefore take care of direction, the short leg is the cathode and goes in the square pad on PCB.

![LEDs](images/guide/led.jpg)

### IC socket (U1)

Solder on the IC socket. 

The IC socket mounts a polarized component, check the notch on silkscreen and IC Socket.

![IC Socket](images/guide/ic-socket.jpg)

Do not insert microcontroller into the socket before soldering the socket to the PCB.

### Electrolytic capacitor (C3)

Electrolytic capacitor is a polarized component, the short leg is the cathode and goes in the circular (left) pad on PCB.

The soldermask around the pads can cause confusion about which is the square pad as the circular pad has a square soldermask pattern around it, so be careful and double check. If in doubt, the capacitor should be orientated so that the side with the white line on it is on the left.

To fit under the component cover, ensure that your capacitor body is less than 10mm tall.

![Capacitor](images/guide/capacitor.jpg)

### Resettable fuse (F1)

Solder on the resettable fuse.

After soldering, bend the fuse over to that it lays flat on the PCB.

![Fuse](images/guide/fuse.jpg)

### Tactile switches (SW1,2)

Push the switches into the PCB and solder the legs.

![Push switches](images/guide/switches.jpg)

### ISP header (J2)

Used for programming the microprocessor with the bootloader directly. If your MCU is already programmed you can skip adding this header if you want.

![ISP header](images/guide/isp-header.jpg)

### ATMEGA328P (U1)

Insert ATMEGA328P into IC Socket.

Ensure that you insert it in the correct orientation, the semicircular mark should match that of the silkscreen.

![ATMEGA328P](images/guide/atmega328p.jpg)

### Check list

Before connecting the board to your computer, a few things to double check just to be safe:

* Take a close look at the USB connector pins and visually check there is no short between the VCC and GND pins. If you have a multimeter, now might be a good time to use it.
* Check the orientation of polarized components (ATMEGA328p, diode, electrolytic capacitor).
* Double check the correct resistor values are in the correct locations.

## Software

Note: If you got your Lumberjack as a kit, the microprocesor is already flashed with a bootloader and firmware, and you can skip this and the firmware steps.

### Bootloader

A bootloader is a piece of software on the microprocessor which can be used to flash firmware onto the microprocessor and to pass execution control to that firmware.

You will need to flash the microprocessor with a bootloader. To do this you will need another device which can be connected to the ISP headers and used to flash the bootloader to the chip. Since Lumberjack is the same as the Plaid, we can use the same bootloader.

* Download the [Plaid bootloader](https://github.com/hsgw/USBaspLoader/tree/plaid) and follow the instructions to compile the bootloader.
* Follow the [QMK ISP flashing guide](https://beta.docs.qmk.fm/using-qmk/guides/keyboard-building/isp_flashing_guide) to get the bootloader onto the chip.

Don't forget to set the fuses: low `0xd7`, high `0xd0`, extended `0xd0`.

### Firmware

Follow the [QMK firmware instructions](https://beta.docs.qmk.fm/using-qmk/guides/flashing/flashing) to build and flash the firmware.

`qmk flash -kb peej/lumberjack`

To put the board into bootloader mode so it is ready to recieve firmware, press and hold the BOOT button (SW2) while pressing and releasing the RESET button (SW1). The board will now be detected as an USBasp device and can have the firmware flashed via the USB port.

Pressing the RESET button (SW1) on its own will restart the microprocessor. Once flashed with firmware it is neccessary to reset the keyboard so as to return control to the new firmware.

Note that due to the BOOT button (SW2) sharing a pin with column 3, when pressed the keys in that column will also activate. This is expected behavour but can be a little annoying or confusing if you are not expecting it.

### Can't recognize bootloader

* Check components and soldering near ATMEGA328p.
    * Direction of ATMEGA328p
    * BOOT SW and RESET SW
    * USB connector
    * R1, R2, R3, D66, D67
* Try different USB cable, PC, USB hub
    * If you connect via USB hub, try connecting directly.

### Check list

Now the board should be fully functional, so check that everything works before adding the switches.

Plug in the PCB and use a pair of tweazers or a piece of wire to check each keyswitch pad triggers a keypress.

## Switches

### Stabilizers

If you are using 2u keys and want to use key stabilizers, fix them to the board before inserting the switches.

### Trim switch legs

When fitting key switches, the switches at the 'Q' and 'P' positions on the 2nd row will fowl on the standoffs in your keyboard case, so you need to trim down one of the stabilizing pins and part of the center pin to ensure the PCB fits flush within the case.

![Switch legs](images/guide/switch-mod1.jpg)

If you are using a 2u key on the right hand side, you will also need to trim down the center pin so that it does not fowl on the standoff. The position the case standoffs will be is marked on the soldermask of the underside of the PCB.

![Switch center pin](images/guide/switch-mod2.jpg)

### Insert switches

Insert the switches into the PCB and solder the pins of each switch.

If you are using a plate, insert the switches into the plate first and then insert into the PCB.

Ensure that the switch is fully inserted and sitting flush with the PCB before soldering.

Note also that the switch at the 'Q' position is upsidedown so that the switch pins do not interfere with the case standoffs.

## Component cover

Affix the 4 standoffs to the PCB with screws from underneath the PCB. Use the remaining 4 screws to attach the acrylic to the top of the standoffs.

Do not overtighten the screws as this could crack the acrylic.

## Case fitting

When fixing the PCB to your case you will only use the center, the left and the right screw holes. Depending on your case design, the PCB will be supported by the other standoffs.

## End

Congratulations, your build is complete.


Estoy empezando a acostumbrarme a escribir 
