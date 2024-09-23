# ⚙️ **8051 8x8 Dot Matrix Display Interfacing**

<p align="center">
  <img src="https://github.com/gmostofabd/8051-LED-Matrix/blob/0c26dcf16bbefdaef8ab29a2f253245c7e258868/assets/images/LEDMATRIX_8051_Ckt.png" alt="AT89C51 Dot Matrix Circuit" width="70%">
</p>

This repository demonstrates how to interface an 8x8 dot matrix display with the 8051 microcontroller using **shift registers** to manage the large number of pins required for controlling the display. The project includes complete assembly code, Proteus simulation files, and documentation, along with screenshots and photos from testing.

## 📦 **Project Overview**
The project showcases the integration of an **8x8 Dot Matrix Display** with the **AT89C51** microcontroller, part of the 8051 family. The display is controlled using **shift registers** (like 74HC595), which significantly reduce the number of GPIO pins required from the microcontroller. The Proteus simulation files allow you to visualize and test the functionality before implementing it on hardware.

### **Key Features:**
- **Dot Matrix Display Control**: Display patterns or scrolling text on the 8x8 dot matrix using the 8051 microcontroller.
- **Shift Register (74HC595)**: Used to extend the number of output pins for controlling the matrix.
- **Proteus Simulation**: Includes simulation files for dot matrix display interfacing with the 8051 MCU.
- **Test Results**: Screenshots and photos from actual tests provide insights into the project's performance.

## 🔧 **Hardware Components**
- **AT89C51 Microcontroller**: Manages control signals for the 8x8 dot matrix display.
- **74HC595 Shift Registers**: Extends the output pins needed to control the display.
- **8x8 Dot Matrix Display**: The display used to show characters, symbols, or animations.
- **Power Supply**: Provides the necessary voltage and current for the system.

## 🖥️ **Simulation & Testing**
This project was simulated using **Proteus Design Suite** to verify the dot matrix display's behavior and control before real-world implementation. The repository includes:
- Assembly code for controlling the dot matrix display.
- Proteus simulation file showing display operation.
- Screenshots and photos taken during the testing phase.

---

### 🚀 **Steps to Run the Project:**
1. **Clone this repository**:
   ```bash
   git clone https://github.com/yourusername/8051_Dot_Matrix_Interfacing.git
   ```
2. **Open the Proteus Simulation**: 
   Load the provided simulation file in **Proteus Design Suite** and run it to observe the display's behavior.
3. **Compile and Upload the Code**:
   Use **MIDE-51** or any other 8051-compatible IDE to compile the assembly code and generate the HEX file.
4. **Test on Hardware**:
   After programming the microcontroller, assemble the circuit with the dot matrix display and shift registers, and power it on to observe real-time results.

---

## 📄 **Included Files:**
- **Assembly Code**: The code to drive the 8x8 dot matrix display using the 8051 microcontroller.
- **Proteus Simulation Files**: Pre-built simulation to test and visualize the circuit.
- **HEX File**: Ready-to-upload HEX code for the microcontroller.
- **Screenshots & Photos**: Visual proof of successful testing on both Proteus and hardware.

---

## 👨‍💻 **Code View**

```assembly
; 8051 Assembly Code for 8x8 Dot Matrix Display using Shift Registers

ORG 0000H           ; Start Program at address 0
MOV P1, #00H        ; Initialize Port 1 (connected to 74HC595 shift registers)
MOV DPTR, #MYCODE   ; Load the address of the code block
LCALL DISPLAY_CTRL  ; Call the dot matrix display control routine

; Dot Matrix Display Control Subroutine
DISPLAY_CTRL:
    MOV A, P1       ; Load the current value of Port 1 into Accumulator
    MOV P1, A       ; Send the value to Port 1 (shift register input)
    ACALL DELAY     ; Call delay for display timing
    RET             ; Return from subroutine

DELAY:
    MOV R0, #255    ; Load the maximum count for delay loop
DELAY_LOOP:
    DJNZ R0, DELAY_LOOP ; Decrement R0 until it reaches zero
    RET             ; Return from delay subroutine

END
```

---
# ⚙️ **Additional Informations**


##  **About Dot Matrix Display**

Here is a visual representation of an 8x8 dot matrix display. Each circle corresponds to an LED that can be turned on or off to display characters or patterns. The rows are labeled R1 to R8 and the columns C1 to C8. This type of display is often used for showing text, symbols, and basic graphics in embedded systems.
import matplotlib.pyplot as plt
import numpy as np

<div align="center">

<pre>
8x8 Dot Matrix (Rows and Columns)

    C0   C1   C2   C3   C4   C5   C6   C7
   _______________________________________
R0 | ○ | ○ | ○ | ○ | ○ | ○ | ○ | ○ |
R1 | ○ | ○ | ○ | ○ | ○ | ○ | ○ | ○ |
R2 | ○ | ○ | ○ | ○ | ○ | ○ | ○ | ○ |
R3 | ○ | ○ | ○ | ○ | ○ | ○ | ○ | ○ |
R4 | ○ | ○ | ○ | ○ | ○ | ○ | ○ | ○ |
R5 | ○ | ○ | ○ | ○ | ○ | ○ | ○ | ○ |
R6 | ○ | ○ | ○ | ○ | ○ | ○ | ○ | ○ |
R7 | ○ | ○ | ○ | ○ | ○ | ○ | ○ | ○ |
</pre>

</div>





An **8x8 LED Matrix Display** is a grid of 64 LEDs arranged in 8 rows and 8 columns. It is widely used for displaying characters, symbols, and simple graphics. Each LED in the matrix is positioned at the intersection of a row and a column, allowing for the control of individual LEDs by selecting the corresponding row and column.

### **Key Concepts:**
1. **Multiplexing**: In an 8x8 LED matrix, controlling all 64 LEDs individually would require 64 GPIO pins. To reduce this number, multiplexing is used, which controls the LEDs by lighting up one row or column at a time at a very fast rate, giving the appearance that multiple LEDs are on simultaneously.
   
2. **Row-Column Scanning**: The matrix is controlled by switching on a row and applying voltage to the corresponding columns to light up specific LEDs. The process is repeated rapidly for each row to create stable images or patterns.

3. **Shift Registers (74HC595)**: To manage the large number of LEDs with fewer GPIO pins from a microcontroller (like the 8051), shift registers are often used. A single shift register can control 8 outputs using only 3 GPIO pins (data, clock, and latch). This allows for efficient control of the matrix.

4. **Common Anode/Cathode**: LED matrices can be either common anode (where all the positive terminals of the LEDs are connected together for each row or column) or common cathode (where the negative terminals are connected). The type determines how the control signals are applied to the rows and columns.


#  Connection Diagram for 8x8 Dot Matrix with 8051 Microcontroller:
<div align="center">

<pre>
    8051 MCU                        8x8 Dot Matrix LED
   __________                        __________________
  |          |                      |                  |
  |  P1.0 ---|--------------------->| R0   C0         |
  |  P1.1 ---|--------------------->| R1   C1         |
  |  P1.2 ---|--------------------->| R2   C2         |
  |  P1.3 ---|--------------------->| R3   C3         |
  |  P1.4 ---|--------------------->| R4   C4         |
  |  P1.5 ---|--------------------->| R5   C5         |
  |  P1.6 ---|--------------------->| R6   C6         |
  |  P1.7 ---|--------------------->| R7   C7         |
  |__________|                      |_________________|

</pre>

</div>



### **Applications**:
- **Scrolling Text**: An 8x8 matrix can display scrolling text by shifting characters left or right across the matrix.
- **Simple Animations**: The matrix can be used to show simple animations or graphics by lighting specific LEDs in sequence.
- **Numeric or Alphabetic Display**: It can display numbers, letters, and symbols by lighting up the corresponding LEDs in predefined patterns.

### **Interfacing with Microcontrollers (e.g., 8051)**:
- The 8051 microcontroller can control the matrix using GPIO pins to scan the rows and columns and send data via shift registers.
- Assembly code or C programming is used to generate patterns or characters on the matrix by controlling the row and column pins.
- **Proteus Simulation**: Simulations help visualize the control of the matrix before hardware implementation.

In summary, an 8x8 LED matrix is a flexible and compact way to display visual information using simple control techniques like multiplexing, making it ideal for embedded systems applications.


---
