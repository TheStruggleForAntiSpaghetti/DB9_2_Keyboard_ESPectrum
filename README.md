# DB9_2_Keyboard
Converts DB9 joysticks button presses to keyboard scancodes


This project aims to translate joysticks/pads button presses to keyboard presses by using specifically designed for this purpose boards like the one from Antonio Villena's (see https://antoniovillena.es/store and search for DB9 to keyboard adapter) and also generic ATmega 32U4 boards like Arduino Pro Micro, Arduino Leonardo (for this boards it is needed to change the "#define" wrote in the first lines of the ".ino" file, and may be the desired GPIO pins assignments).

This translation is a big help for those emulators like ESPectrum (code https://github.com/EremusOne/ZX-ESPectrum-IDF , board and rubber key case also available from https://antoniovillena.es/store/product/espectrum) and FPGA boards like MiSTer which doesn't have joystick connector support, but also to allow the use and management of computer cores running inside FPGAs when a keyboard permanently connected is not desired.

The code sends keystrokes when a button is pressed on a Joystick. Two simulatenous joysticks are supported. PS/2 and USB keyboard scancodes are sent. The supported joysticks are standard one-two buttons joysticks, Sega three buttons joysticks and Sega 6 buttons joysticks.

The USB detection is done in the first seconds from the boot when the ATmega board is connected to a USB or PS/2 port and powered up. If the board is permantly connected to a computer like PC or Raspberry Pi probably the USB detection will fail as the host device is not ready to communicate with the board during the first seconds before timeout, when this happens the board must be disconnected and reconnected to the USB port.

The default map for each joystick to execute the translation from joystick buttons is done according to these sequences:

**DB9 PORT 1 (PS/2)**

CURSOR UP, CURSOR DOWN, CURSOR LEFT, CURSOR RIGHT, RIGHT ALT, ENTER, ESCAPE, F1, Z, Y, X, M

Q, A, O, P, M, ENTER, ESCAPE, F1, Z, Y, X, C

CURSOR UP, CURSOR DOWN, CURSOR LEFT, CURSOR RIGHT, ZERO, ENTER, ESCAPE, F5, Z, Y, X, M

SEVEN, SIX, FIVE, EIGHT, ZERO, ENTER, ESCAPE, F1, Z, Y, X, M


**DB9 PORT 1 (USB)**

CURSOR UP, CURSOR DOWN, CURSOR LEFT, CURSOR RIGHT, ENTER, RIGHT ALT, ESCAPE, F12, Z, Y, X, M

Q, A, O, P, M, ENTER, ESCAPE, F12, Z, Y, X, C

CURSOR UP, CURSOR DOWN, CURSOR LEFT, CURSOR RIGHT, ENTER, ZERO, ESCAPE, F5, Z, Y, X, M

SEVEN, SIX, FIVE, EIGHT, ZERO, ENTER, ESCAPE, F12, Z, Y, X, M



**DB9 PORT 2 (PS/2)**

Q, A, O, P, M, ENTER, ESCAPE, F1, Z, Y, X, C

CURSOR UP, CURSOR DOWN, CURSOR LEFT, CURSOR RIGHT, RIGHT ALT, ENTER, ESCAPE, F1, Z, Y, X, M

CURSOR UP, CURSOR DOWN, CURSOR LEFT, CURSOR RIGHT, ZERO, ENTER, ESCAPE, F5, Z, Y, X, M

SEVEN, SIX, FIVE, EIGHT, ZERO, ENTER, ESCAPE, F1, Z, Y, X, M



**DB9 PORT 2 (USB)**

Q, A, O, P, M, ENTER, ESCAPE, F12, Z, Y, X, C

CURSOR UP, CURSOR DOWN, CURSOR LEFT, CURSOR RIGHT, ENTER, RIGHT ALT, ESCAPE, F12, Z, Y, X, M

CURSOR UP, CURSOR DOWN, CURSOR LEFT, CURSOR RIGHT, ENTER, ZERO, ESCAPE, F5, Z, Y, X, M

SEVEN, SIX, FIVE, EIGHT, ZERO, ENTER, ESCAPE, F12, Z, Y, X, M



The keymaps can be changed by pressing a direction button (up, down, left, right) while the board is plugged or powered up.



**ROADMAP**

-Code for a little OLED screen connection, showing menu and information is development, the aim is to allow the use of an onscreen virtual keyboard, and also show the current map in use for each keyboard port.

-The scancodes map will be user-defined and recorded from the own joystick board.



Agreements to Antonio Villena (hardware support), Victor Íborra (testing and ideas), David Crespo (testing and protocol info), Armand (testing and ideas)

