# Introduction

The **CPU datapath** is the part of the CPU that **moves and processes data** between registers, the ALU, and memory to execute instructions.

## CPU data path

![Data Path](/img/CPU_datapath.png)


## Executing an instruction

1) **FETCH** instruction
2) **PC**++ (increase program counter)
3) Determine instruction **type**
4) Need **DWORD?**
   1) FETCH DWORD
   2) place DWORD into register
5) **Execute** instruction
6) Repeat

**FETCH** => **DECODE** => **EXECUTE**