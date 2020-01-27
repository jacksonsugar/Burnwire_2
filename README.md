# Burnwire_2
Dependencies and code for a compact self-contained burn wire based on the ATmega328p & DS3231 Real Time Clock

Steps for deployment

1) Download and install Arduino IDE from the official website:  https://www.arduino.cc/en/Main/Software
2) Clone this repository to your device by following the green link above [Download ZIP]
3) Open Adruino IDE and configure bootloader for the ATmega328p and USBtiny programmer

      Tools -> Board: -> Arduino Pro or Pro Mini (3.3V, 8MHz) w/ Atmega328

      Tools -> Programmer -> USBtinyISP

4) Import .zip libraries from repository into Arduino IDE 

      Sketch -> Include Library -> Add .ZIP Library..
            
            Low-Power-master.zip
            
            RTClib-master.zip

5) Set laptop/desktop clock to UTC should your application require it

6) Connect burn wire and programmer to your laptop and open terminal

      sudo avrdude -c usbtiny -p atmega328p -v
      
      This checks the state of the microcontroller if fuses do not return (E:FF, L:E2, H:D9)
      
      sudo avrdude -c usbtiny -p atmega328p -F -U lfuse:w:0xe2:m -U hfuse:w:0xd9:m -U efuse:w:0xff:m
 

9) Open Burnwire_2.ino and set times for the burn cycle and strobe delay found in the first few lines of code seperated by the "/". Do not edit code outside the lines provided.

10) Upload Burnwire_2.ino to the burn wire and unplug from programming device
      
      --> Note: Elapsed time programmed begins once shorting plug is installed. 

11) Install shorting plug and wait for flash

12) Deploy!
