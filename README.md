# FLASHING-OF-LEDS-WITH-LPC-1768

## AIM: 
   To interface and toggle the led with ARM LPC 1768 microprocessor           
           
## COMPONENTS REQUIRED:
##  HARDWARE:
ARM LPC1768
LED
## SOFTWARE:
KEIL MICRO VISION 4.0 IDE

# PROCEDURE:
```
⮚	Open the Keil software and select the New uvision project from Project Menu as shown below.
⮚	Browse to your project folder and provide the project name and click on save.
⮚	Once the project is saved a new pop up “Select Device for Target” opens, Select the controller (NXP: LPC1768) from NXP (founded by philips) and click on OK.
⮚	Select the controller (NXP: LPC1768) and click on OK.
⮚	As LPC1768 needs the startup code, click on Yes option to include the LPC17xx Startup file.
⮚	Create a new file by file → new to write the program.
⮚	Type the code.
⮚	After typing the code save the file as main.c eg. (abc.c).
⮚	Right click target and Add the suitable files to source group1 and header for the project.
⮚	Add the main.c along with system_LPC17xx.c.
⮚	Build the project and fix the compiler errors/warnings if any.
⮚	Code is compiled with no errors. The .bin file is still not generated.
⮚	Right Click on Target Options to select the option for generating .bin file.
⮚	Set IROM1 start address as 0x2000. Bootloader will be stored from 0x0000- 0x2000 so application should start from 0x2000
⮚	Write	the	command	to	generate	the .bin file	from
.axf file
Command: fromelf --bin projectname.axf --output filename.bin
⮚	in c/c++ → include paths → desktop (00-libfiles).
⮚	.Bin file is generated after a rebuild.
⮚	Check the project folder for the generated .Bin file.
```

## ADD FILES:
Target1:
Source group1:
Startuplpc17xx.s, main.c (t), delay.c (t), systemlpc17xx.c (t), gpio.c (t)
Header:
Delay.h, stdutils.h, gpioi.h

# PIN DIAGRAM :
 <img width="767" height="416" alt="514867264-788618af-92f5-46cb-b742-d9b7db575a87" src="https://github.com/user-attachments/assets/2629528c-e3c7-4600-a9ff-018f1b2ebdad" />

# CIRCUIT DIAGRAM:
 <img width="715" height="366" alt="514867295-6078a9ce-ba75-4f50-ad22-8066f4643baa" src="https://github.com/user-attachments/assets/62999088-e67a-4b6c-8f60-6e9daf1b9380" />

# PROGRAM:
```
#include <lpc17xx.h>
#include "delay.h"      
#include "gpio.h"

#define LED P1_29        

/* start the main program */
int main()
{
    SystemInit();                         
    GPIO_PinFunction(LED,PINSEL_FUNC_0);   
    GPIO_PinDirection(LED,OUTPUT);        
    GPIO_PinWrite(LED,LOW);

    while(1)
    {
        /* Turn On all the leds and wait for 100ms */
        GPIO_PinWrite(LED,HIGH);           
        DELAY_ms(100);

        GPIO_PinWrite(LED,LOW);           
        DELAY_ms(100);
    }
}
```
# Output:
<img width="960" height="1280" alt="514867348-ee34a328-f708-450c-b469-0fe69ed744aa" src="https://github.com/user-attachments/assets/b1479a56-f1bc-41b7-9838-83df728efd02" />

## Result:
Thus the LED is interfaced and toggled with ARM LPC1768 Microprocessor.







