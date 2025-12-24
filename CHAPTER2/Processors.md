# the CPU explained

- [the CPU explained](#the-cpu-explained)
  - [Control Unit](#control-unit)
  - [ALU (Arithmetic and Logic Unit)](#alu-arithmetic-and-logic-unit)
  - [BUS](#bus)

![CPU_GENERAL_LAYOUT](/img/CPU_general_layout.png)

## Control Unit

**The Control Unit (CU)** is the part of the **CPU** that **directs and coordinates all operations** inside the computer.  
It tells the **processor**, **memory**, and **input/output devices** *what to do, when to do it, and how to do it.*

- **Program Counter (PC)** — holds the address of the next instruction  
- **Instruction Register (IR)** — stores the current instruction  
- **Decoder** — interprets the instruction  
- **Control Signal Generator** — issues control and timing signals  
- **Clock/Timing Unit** — synchronizes all CPU operations

## ALU (Arithmetic and Logic Unit)

**The Arithmetic and Logic Unit (ALU)** is the part of the **CPU** that **performs all mathematical calculations and logical operations**.  
It handles **arithmetic operations**, **comparison operations**, and **bitwise operations**, providing the results to registers or memory as needed.  

- **Accumulator (ACC)** — stores intermediate results of calculations  
- **Arithmetic Operations** — addition, subtraction, multiplication, division  
- **Logical Operations** — AND, OR, NOT, XOR, comparisons  
- **Shifter/Rotator** — performs bit shifts and rotations for data manipulation  
- **Status/Flag Register** — indicates results of operations (zero, carry, negative, overflow)  

The ALU works closely with the **Control Unit**, which provides the instructions and timing signals needed to perform each operation.

## BUS

the Bus is the part of the cpu/computer that connects all the components together.