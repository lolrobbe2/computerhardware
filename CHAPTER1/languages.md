# introduction

## Languages, levels, and virtual machines
examples: 
1) JAVA-VM
2) dotnet JIT interpreter

| Machine Language LEVEL | VM TYPE | DESCRIPTION                                                                                                                  |
| ---------------------- | ------- | ---------------------------------------------------------------------------------------------------------------------------- |
| 0                      | M0      | **actual computer**, directly executed by circuitry.                                                                         |
| 1                      | M1      | VM: either interpreted by an interpreter running on M0 ore translated to L0                                                  |
| 2                      | M2      | VM: either interpreted by an interpreter running on M1 or M0 or are translated to L1 or L0                                   |
| N                      | MN      | VM: either interpreted by an interpreter running on a lower machine or are translated to machine language of a lower machine |