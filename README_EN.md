This is an automatic translation, may be incorrect in some places. See sources and examples!

# Gyvertimer
Millis () / Micros ()
** Attention, the library is outdated!Use [Timerms] (https://github.com/gyverlibs/timerms) **
- millisecond and microsecond timer
- Two operating modes:
    - interval mode: Timer "triggers" every given time interval
    - Tymauta mode: The timer "triggers" once after the time (until the next restart)
- Office functions:
    - Start
    - Stop
    - Reset
    - Continue

## compatibility
Compatible with all arduino platforms (used arduino functions)

### Documentation
There is [expanded documentation] to the library (https://alexgyver.ru/gyvertimer/)

## Content
- [installation] (# Install)
- [initialization] (#init)
- [use] (#usage)
- [Example] (# Example)
- [versions] (#varsions)
- [bugs and feedback] (#fedback)

<a id="install"> </a>
## Installation
- The library can be found by the name ** gyvertimer ** and installed through the library manager in:
    - Arduino ide
    - Arduino ide v2
    - Platformio
- [download the library] (https://github.com/gyverlibs/gyvertimer/archive/refs/heads/main.zip). Zip archive for manual installation:
    - unpack and put in * C: \ Program Files (X86) \ Arduino \ Libraries * (Windows X64)
    - unpack and put in * C: \ Program Files \ Arduino \ Libraries * (Windows X32)
    - unpack and put in *documents/arduino/libraries/ *
    - (Arduino id) Automatic installation from. Zip: * sketch/connect the library/add .Zip library ... * and specify downloaded archive
- Read more detailed instructions for installing libraries [here] (https://alexgyver.ru/arduino-first/#%D0%A3%D1%81%D1%82%D0%B0%BD%D0%BE%BE%BE%BED0%B2%D0%BA%D0%B0_%D0%B1%D0%B8%D0%B1%D0%BB%D0%B8%D0%BE%D1%82%D0%B5%D0%BA)
### Update
- I recommend always updating the library: errors and bugs are corrected in the new versions, as well as optimization and new features are added
- through the IDE library manager: find the library how to install and click "update"
- Manually: ** remove the folder with the old version **, and then put a new one in its place.“Replacement” cannot be done: sometimes in new versions, files that remain when replacing are deleted and can lead to errors!


<a id="init"> </a>
## initialization
`` `CPP
// Mode: MS/US
Gtimer mytimer (mode);
Gtimer mytimer (Mode, Interval);
`` `

<a id="usage"> </a>
## Usage
`` `CPP
VOID SetinTerval (Uint32_T Interval);// Installation of the interval of the timer (also launch and drop the timer) - interval mode
VOID settimeout (uint32_t timeout);// Installation of the timer timer (will also launch and drop the timer) - Timout mode
Boolean Isready ();// Returns True when the time has come
Boolean Isenabled ();// Return the condition of the timer (stopped/launched)
VOID Reset ();// Tiemer resetting to the established period of work
VOID Start ();// Launch/restart (with account reset)
VOID Stop ();// Stop the timer (without resetting)
VOID Resume ();// Continue (without resetting)

// Office
VOID setmode (Boolean Mode);// Installation of the operating mode manually: Auto or Manual (Timer_Interval / Timer_timeout)
`` `

<a id="EXAMPLE"> </a>
## Example
The rest of the examples look at ** Examples **!
```CPP
#include "gyvertimer.h"
Gtimer mytimer (MS);// Create a millisecond timer

VOID setup () {
  Serial.Begin (9600);
  Mytimer.SetinTERVAL (500);// configure the interval
}

VOID loop () {
  if (mytimer.isread ()) serial.println ("Timer!");
}
`` `

<a id="versions"> </a>
## versions
- V2.0 - an improved timer operation algorithm
    - multiple intervals
    - Protection against passes
    - Protection from overflow Millis ()
    - Defaine removed
- V2.1 - Defaines returned
- V2.2 - Improved stability
- V3.0
    - The logic of work is divided into interval and timaut
    - added the general class GTimer (for millisecond and microsecond timer)
    - Added the ability to stop and continue the timer account
- V3.2
    - Added isenabled
    - the opportunity not to launch a timer when creating

<a id="feedback"> </a>
## bugs and feedback
Create ** Issue ** when you find the bugs, and better immediately write to the mail [alex@alexgyver.ru] (mailto: alex@alexgyver.ru)
The library is open for refinement and your ** pull Request ** 'ow!


When reporting about bugs or incorrect work of the library, it is necessary to indicate:
- The version of the library
- What is MK used
- SDK version (for ESP)
- version of Arduino ide
- whether the built -in examples work correctly, in which the functions and designs are used, leading to a bug in your code
- what code has been loaded, what work was expected from it and how it works in reality
- Ideally, attach the minimum code in which the bug is observed.Not a canvas of a thousand lines, but a minimum code