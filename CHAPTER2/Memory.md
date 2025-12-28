# Introduction

Memory is the General Purpose medium to store data.

## Primary Memory

The part of computer where programs and data are stored

## Bit

The bit or `Binary Digit` is the smallest data unit in the computer

## Byte Order (2)

1) little Endian
2) big Endian

### Little Endian (L -> R)

![Little Endian](../CHAPTER2/img/little_endian.png)

### Big Endian (R -> L)

![Big ENdian](../CHAPTER2/img/big_endian.png)

### Little Vs Big Endian

![Little Vs Big Endian](../CHAPTER2/img/big_little_endian.png)

## Error Correcting Codes (ECC)

Parity checking work has 2 types:
### PARITY:
#### EVEN

![even parity](../CHAPTER2/img/even_parity.png)

#### UNEVEN

01011011 => uneven amount of true bits => we add a 0 to make keep it an `uneven` amount: 101011011

### Hamming codes:

![Hamming codes](../CHAPTER2/img/hamming_codes.png)

#### CHECKS (N)

the amount of checks is the same as the `number` of `parity` bits

![Hamming checks](../CHAPTER2/img/hamming_checks.png)

#### CHECK 1

![Check 1](../CHAPTER2/img/hamming_check_1.png)

#### CHECK 2

![Check 2](../CHAPTER2/img/hamming_check_2.png)

#### CHECK 3

![Check 3](../CHAPTER2/img/hamming_check_3.png)

#### CHECK 4

![Check 4](../CHAPTER2/img/hamming_check_4.png)

#### BLOCK CHECK

you wil note that this method does not check the `first` bit for errors.
but we can use this bit for a `parity check` of the first bit that whey we can check if there are 2 or more errors.

> [WARNING]
> there is a better version calculating the error position of this using `xor`: by xor'ing all the `true` bits binary positions the bit flip position comes out at the end

![ECC](../CHAPTER2/img/ecc_overhead.png)

## Cache

a cache is a small and fast region of memory that in the case of hardware sits next to the CPU cores, wich makes it very fast

![cache simple diagram](../CHAPTER2/img/cache.png)
