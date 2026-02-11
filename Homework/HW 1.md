# EECS388 - Embedded Systems
## Homework 1

1. Convert numbers into different representations. All numbers are 8 bits in length and are 2’s complement representation
	Instructions:
	- Fill in answers in canvas for parts ‘A’ though ‘L’ from the top left to the bottom right.
	- Binary Numbers: Represent binary numbers **using only 0s and 1s**. Do not include the prefix 'b' or 'B' in your binary representation. **Do not use spaces or underscores. (Example: 11110000)**
	- Negative Numbers: When expressing negative numbers, use the '-' symbol followed by the numerical value (e.g., -5). Ensure there is no space between the '-' symbol and the number.
	- Hexadecimal Numbers: When presenting hexadecimal values, use the standard 0-9 and A-F characters. **Do not include the prefix '0x' in your hexadecimal representation**.

	Example
	- Binary Number: 0b1111_0101 (in canvas, enter *11110101*)
	- Signed Decimal Value: -11
	- Hexadecimal Number: 0xF5 (in canvas, enter *F5*)

|      Binary       |     Hex     | Unsigned Decimal | Signed Decimal |
| :---------------: | :---------: | :--------------: | :------------: |
|   *0b0011_0100*   | ==A)== $34$ |   ==B)== $52$    |  ==C)== $52$   |
| ==D)== $10001111$ |   *0x8F*    |   ==E)== $143$   | ==F)== $-113$  |
| ==G)== $10101100$ | ==H)== $AC$ |      *172*       |  ==I)== $-84$  |
| ==J)== $11100011$ | ==K)== $E3$ |   ==L)== $227$   |     *-29*      |

2. Assume an integer has a value of 0x456789AB. Write the value into the correct memory addressed starting at address '*0x08*' based on the endianness.

| Little Endian | Address | Data |
| ------------- | ------- | ---- |
| 1             | 0x08    | 0xAB |
| 2             | 0x09    | 0x89 |
| 3             | 0x0A    | 0x67 |
| 4             | 0x0B    | 0x45 |

| Big Endian | Address | Data |
| ---------- | ------- | ---- |
| 1          | 0x08    | 0x45 |
| 2          | 0x09    | 0x67 |
| 3          | 0x0A    | 0x89 |
| 4          | 0x0B    | 0xAB |

---
13. Answer the following questions about this MIPS instruction: `add $t3, $t4, $t5`
	- which register is the `rd` destination register?
	- What is the decimal number address of the `rs` first source register (example - $t0 address is 8)? 
	- Assume the following values are in register memory. What would the new value in the `rd` destination register be after executing this add instruction?

| Register | Value (decimal) |
| -------- | --------------- |
| $zero    | 0               |
| $t0      | 12              |
| $t1      | 4               |
| $t2      | -31             |
| $t3      | 64              |
| $t4      | -5              |
| $t5      | 100             |

13. Update the register memory and main memory tables after the following MIPS load word and store word instructions execute. Assume the following initial values are in register and main memory.

| Register Address | Register Date Value (in decimal) |
| ---------------- | -------------------------------- |
| $zero            | 0                                |
| $v0              | 16                               |
| $v1              | 16                               |
| $a0              | 24                               |
| $a1              | 6                                |
| $a2              | 8                                |
| $a3              | 42                               |
| $t0              | 401                              |
| $t1              | 1500                             |
| $t2              | -134                             |
| $t3              | 654                              |
| $t4              | -96                              |
| $t5              | 58                               |
| $t6              | 96                               |
| $t7              | 1024                             |
| $s0              | 2048                             |
| $s1              | 40                               |
| $s2              | 412                              |
| $s3              | 9765                             |
| $s4              | 4321                             |
| $s5              | 2222                             |
| $s6              | -2579                            |
| $s7              | 2727                             |
| $t8              | 721                              |
| $t9              | 9635                             |
| $ra              | 0xFD465789                       |
Assume the instructions execute sequentially.
1. `lw $t0, 12($s1)`
2. `sw t3, 4($s1)`
3. `lw $t8, -16($s1)`
4. `sw $a0, -8($v0)`

| Main Memory Addres | Main Memory Data Value |
| ------------------ | ---------------------- |
| 0x0                | 32                     |
| 0x4                | 511                    |
| 0x8                | 47                     |
| 0xC                | -96                    |
| 0x10               | 105                    |
| 0x14               | 49                     |
| 0x18               | 127                    |
| 0x1C               | 1111                   |
| 0x20               | 2222                   |
| 0x24               | 3333                   |
| 0x28               | 4569                   |
| 0x2C               | 456                    |
| 0x30               | 789                    |
| 0x34               | 104                    |
| ...                |                        |
