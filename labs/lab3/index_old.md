title = 'Lab 3 - SPI - "I/O"'

# Lab 3 - SPI - "I/O"

## Objectives

This lab is your first introduction to interfacing hardware components with an MCU.  You will connect push buttons to your MSP430 and then write a program that uses polling to determine which button is pushed.  You will also use your debugger and a Liquid Crystal Display (LCD) to display different types of information.  Timing is critical for LCD operation, so you'll learn to use a Logic Analyzer to measure the timing of your signals.

## Details

### The Basic Idea

I've given you some encrypted messages and their keys.  You'll write a program that leverages your code from the Cryptography Lab to decrypt them using inputs taken from buttons.  You'll prompt users via messages on LCDs to select a key and message, then decrypt it.

First, your program will display a two-line message on the LCD asking the user to push one of three buttons to select the key to use in decryption (Top line: "Key?", bottom line: "Press123").  You'll wait until a button is pushed and record the selection.  Next, you'll display a second two-line message on the LCD asking the user to use the same three buttons to select the message to decrypt (Top line:"Message?, bottom line: "Press123").  Again, you'll wait until a button is pushed and record the selection.  You'll then display a final two-line message reflecting the choices (for example, top line:"Key: 1", bottom line: "Msg: 2").  Then, you'll attempt to use the selected key to decrypt the selected message and store the result in RAM, just like in Lab 2.

I've given you the code to initialize and clear the LCD.  But I'm relying on you to implement a few critical subroutines it needs to work.  We're interfacing with an LCD driver chip that takes in information via SPI.  You'll need to write the `INITSPI` subroutine to initialize the SPI subsystem on your MSP430 appropriately.  You'll also need to designate a Slave Select (SS) signal and implement the `SET_SS_HI` and `SET_SS_LO` subroutines to change it.  Timing is critical in working with hardware.  The code I've given you relies on two subroutines that implement software delays of different lengths (`LCDDELAY1` - 40.5 microseconds and `LCDDELAY2` - 1.65 milliseconds).  You'll need to implement these and verify their length using the Logic Analyzer.  To calculate the number of CPU cycles necessary to achieve these delays, you'll need to know your clock speed precisely.  This varies across MSP430 chips, so you'll need to use your logic analyzer to view your clock signal, record its period, and convert it to a frequency.

You'll have to do all this to achieve required functionality.

What if your design is to be mass-produced?  Since the clock speed varies across chips, you can't be sure of the length of your delays in every MSP430.  To achieve B Functionality, you'll have to make your clock speed exactly 1MHz.

To achieve A Functionality, you must display the decrypted message continuously scrolling across the LCD screen.

### Required Functionality

- The encrypted messages and keys will be stored in ROM - any location in ROM is acceptable.  The decrypted message will be stored in RAM starting at 0x0200.  Labels shall be used to refer to these elements.
- The final decrypted byte of every message is the # sign - like in the Cryptography lab.
- Good coding standards, in accordance with the [Lab guidelines](/admin/labs.html), must be used throughout.

I've [given you some code](given_code.html) to use as a starting point for this lab.  Do not alter any subroutines unless specifically instructed to do so.

**NOTE: This code uses UCB0, NOT UCA0!  Write your subroutines accordingly.**

This is the longest lab you've undertaken thus far.  **Use a modular approach to design / test**.  Here's a suggested list of steps:

**Step 1**: The Subsystem Master Clock (SMCLK) is the same speed as the Master Clock (MCLK) that runs your CPU.  Measure its period via logic analyzer - you'll want to screen capture / print this for your lab notebook.  There will be a table on the board for all students to record their CPU speed - record yours there.  **Never forget to ground your logic analyzer**.

**Step 2**: Use the SMCLK speed you found in **Step 1** to calculate the necessary length of your software delay loop.  Use GPIO to demo both the `LCDDELAY1` (40.5 microsecond) and `LCDDELAY2` (1.65 millisecond) delay routines you've created - print and store these screenshots in your lab notebook.  **After this step, get your lab notebook signed off for Logic Analyzer functionality**.

**Step 3**: Implement the `INITSPI`, `SET_SS_HI`, and `SET_SS_LO` subroutines.  Perform the necessary wiring in your Geek Box.  You'll know you've been successful when the LCD screen goes blank.

SPI Notes:

- The LCD driver chip expects data to be read on the first clock edge and changed on the second.
- The LCD driver chip expects the clock should be low when not transmitting.
- The Launchpad doesn't come with an ACLK source installed.
- The LCD can handle an unscaled SMCLK.
- Other configuration info you can gather from the SPI lesson notes and datasheet.

Geek box wiring details:

- **ENSURE YOUR MSP430 AND GEEKBOX SHARE A COMMON GROUND**
    - If you neglect this, the LCD will be unpredictable
    - This is very difficult to debug
- Ensure the jumpers for MOSI, MISO, and CLK are connected (near the LCD on your Geek Box)
- Ensure the jumper is connected from SS to the center pin (NOT GPIO)

![Jumpers](jumpers_close2.jpg)

![Jumpers](jumpers_close3.jpg)

- Connect the signals from your Launchpad to the Geek Box
    - MOSI to Pin 17
    - MISO to Pin 19
    - CLK to Pin 21
    - SS to Pin 23

![Wiring](wiring.jpg)

![Wiring](wiring2.jpg)

- Above image also shows common ground (rightmost wire)
- Above image also connects 5V from Geek Box to board
    - This is to run MSP430 without power from the USB
    - If you hook this up while your USB cable is connected, you could have problems

**Step 4**: Write code to print the messages to the LCD screen.  You'll need to use the LCD Datasheet along with the provided subroutines to accomplish this.

**See the [LCD Notes](lcd_notes.html) for a lot of useful information.**

Printing notes:

It's a good idea to define your strings in memory and terminate them with a known character.  That way, you can print character-by-character in a loop rather than writing an enormous, repetitive block of code.
You should define your strings in memory (`.string`) and print them with a subroutine.  You should terminate the string with a known character (typically NULL) so you can print character-by-character.  Don't repeat yourself!  I don't want to see massive, repetitive blocks of code.

**Step 5**: Connect PB1-3 to GPIO.  Demonstrate that you can detect a button press and release.

Button notes:

The push buttons in the Geek Box are **active low**.  But they don't need the MSP430 to provide an internal pull-up resistor.

Push buttons can sometimes bounce - you'll need to account for that so you don't confuse a single button push for multiple button pushes.  There are couple of potential approaches to this:

- include a debounce delay.  **Usually**, bouncing occurs immediately after a button is pressed and immediately after it's released.  To combat this, you can include a short delay (~10 milliseconds) before checking the button state again.  In most cases, this will avoid the bouncing.
- the truest way to test whether a button has been released is to ensure it's in the released state for a long period of time.  This can be accomplished by testing a button repeatedly over a short interval (~1 milliseconds) once you detect a release to ensure it's always in the released state.  If not, you can assume it's a false alarm due to bouncing.

**Step 6**: Integrate the button press code with the code for your messages.  Show that you can display the appropriate messages and record the appropriate button presses.

**Step 7**: Integrate your decryption alrgorithm.  Test with different combinations of messages and keys.  If the user selects a key that doesn't correspond to the appropriate message, there's the chance the end message character (`#`) will never be encountered - so limit decryption to a maximum of 50 bytes.

**Step 8**: Demo!

Here are the three messages:

Message 1:
```
0xff,0xc3,0xc2,0xd8,0x8b,0xc2,0xd8,0x8b
0xc6,0xce,0xd8,0xd8,0xca,0xcc,0xce,0x8b
0x9a,0x8a,0x88
```

Message 2:
```
0x99,0xa5,0xa4,0xbe,0xed,0xa4,0xbe,0xed
0xa0,0xa8,0xbe,0xbe,0xac,0xaa,0xa8,0xed
0xff,0xec,0xee
```

Message 3:
```
0xbb,0x87,0x86,0x9c,0xcf,0x86,0x9c,0xcf
0x82,0x8a,0x9c,0x9c,0x8e,0x88,0x8a,0xcf
0xdc,0xce,0xcc
```

Key 1: `0xcd`  
Key 2: `0xef`  
Key 3: `0xab`

Key 1 decrypts message 2.  
Key 2 decrypts message 3.  
Key 3 decrypts message 1.

Results will be verified using the debugger.

### B Functionality

Congratulations!  Your program is going to be mass produced!  This makes you concerned - you know that default clock speed isn't consistent across MSP430 chips and realize this could result in different delays in different devices.

Luckily, TI factory calibrates all devices for some common frequencies and gives information necessary to make each chip run precisely at those frequencies.  A good place to learn more is section 5.2.5.2 "Adjusting the DCO Frequency" in the MSP430x2xx Family Users Guide.

In addition to the Required Functionality, your program must configure the MSP430 to run at exactly 1MHz.  You must verify this with the logic analyzer, adjust your delays to reflect the change in frequencies, and verify the delays with the logic analyzer.

### A Functionality

In addition to B Functionality, your program must display the decrypted message scrolling across the screen following the final screen.  The final screen should delay for 2 seconds (verified with logic analyzer) prior to the beginning of scrolling.

## Prelab

Paste the grading section in your lab notebook as the first page of this lab.

Include whatever information from this lab you think will be useful in creating your program.

Accomplish **Step 1** of the Required Functionality.  I'll check that you know your SMCLK speed, have written it on the board, and have attached the printout in your lab notebook.

Perform the required calculations for your `LCDDELAY1` and `LCDDELAY2` - you can implement them if you'd like, but I won't check that for the prelab.

## Notes

Read the [guidance on Labs / Lab Notebooks / Coding standards](/admin/labs.html) thoroughly and follow it.

Use assembler directives for placing strings / byte sequences in memory:
```
stringLabel     .string     "This is a string!"
byteLabel       .byte       0xab,0xcd,0xef
```

## Grading

| Item | Grade | Points | Out of | Date | Due |
|:-: | :-: | :-: | :-: | :-: |
| Prelab | **On-Time:** 0 ---- Check Minus ---- Check ---- Check Plus | | 5 | | BOC L16 |
| Required Logic Analyzer | **On-Time** -------------------------------------------------------------------- **Late:** 1Day ---- 2Days ---- 3Days ---- 4+Days| | 10 | | COB L18 |
| Required Functionality | **On-Time** -------------------------------------------------------------------- **Late:** 1Day ---- 2Days ---- 3Days ---- 4+Days| | 35 | | COB L18 |
| B Functionality | **On-Time** -------------------------------------------------------------------- **Late:** 1Day ---- 2Days ---- 3Days ---- 4+Days| | 10 | | COB L18 |
| A Functionality | **On-Time** -------------------------------------------------------------------- **Late:** 1Day ---- 2Days ---- 3Days ---- 4+Days| | 10 | | COB L18 |
| Lab Notebook | **On-Time:** 0 ---- Check Minus ---- Check ---- Check Plus ----- **Late:** 1Day ---- 2Days ---- 3Days ---- 4+Days| | 30 | | COB L19 |
| **Total** | | | **100** | | |
