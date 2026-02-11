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

3. Match the following terms and definitions

| Term                   | Definition                                                        |
| ---------------------- | ----------------------------------------------------------------- |
| While loop             | Repeatedly executes a code block as long as condition is TRUE     |
| * dereference operator | Used to access value stored in the memory location pointed at     |
| Pointer                | A derived variable type that is used for storing a memory address |
| if statement           | Allows you to conditionally execute code when statement is TRUE   |
| Array                  | Used for storing a collection of elements of the same type        |
| \#include              | A preprocessor directive for inserting .h header files            |
| & reference operator   | Used to get the memory location of a variable                     |
| do while loop          | Correct match:<br>Guaranteed to execute the loop at least once    |
4. The following program has some unit tests designed to check the correct operation of the arithmetic functions. Review the program and identify on what lines there are errors in the unit test
	- Line 48
	- Line 56
5. Which step of the compiler toolchain translates C code into assembly instructions?
	- Assembler
	- ==Compiler==
	- Linker
	- Preprocessor
6. What are the results of the following operations? Fill in your answers with only digits, without spaces, underscores, or prefixes like 0b or 0x.
	- A: 0xF4
	- B: 0b0010_0010
	- C: 0b0101_1000
	- D: 0b0000_0010
7. Assume you have a pointer variable that is declared and initialized to the address of a register that controls 32 LEDs (each bit in memory represents an LED, this is known as a register bank). Assume integers are 4 byte values (32 bits). Finish the code that would turn on every other LED (example: on, off, on, off, …, on, off, on, off). Assume writing a 0 will turn the LED off, and writing a 1 will turn it on. For your final answer, be sure that the first LED represented by BIT0 is set to off.
```C
#define LED_REGISTER_ADDER (0x40002000) //LED reg address
int main(void) {
	int * led_register_ptr = (int *)LED_REGISTER_ADDR;
	*led_register_ptr = ???; //Replace ??? with correct hex val
	return 0;
}
```
Complete the code for the `led_register_ptr` to set every other LED on.
- ==*led_register_ptr = 0xAAAAAAAA;==
- *led_register_ptr = 0x10101010;
- *led_register_ptr = *0x10101010;
- *led_register_ptr = *0xAAAAAAAA;

8. What is the total memory capacity of a system with 16-bit addresses, and an addressability of 4 bytes per address?
	- ==2,097,152 bits or 262,144 bytes==
	- 262,144 bits or 32,768 bytes
	- 524,288 bits or 65,536 bytes
	- 1,048,576 bits or 131,072 bytes
9. Answer the following questions about the GPIO diagram. Assume that when written with a logical ‘1’ the GPIO output is set to 6V, and when written with a logical ‘0’ the GPIO is set to 0V (ground).
	1. What value would you need to set to turn the LED on? 1 or 0?
		- ==0==
	2. Given the following active-low GPIO output, what resistance (in ohms) would you need to use to ensure that 25 milliamps goes through the LED? Assume there is no forward voltage drop across the LED. Write your answer as a whole number without units
		- ==240 ohms==
10. Consider the following 32-bit 2’s complement number: 0xF123AC40. Select the correct statements.
	1. ==It represents a negative number==
	2. It’s an odd number
	3. ==It’s an even number==
	4. The most significant bit is zero
	5. ==The least significant bit is zero==
11. Assume for all binary representations that you have 4-bits of storage available

| Signed Decimal | Signed Magnitude Binary Representation | Signed 2's complement binary representation | Unsigned binary representation | Unsigned Hexidecimal |
| -------------- | -------------------------------------- | ------------------------------------------- | ------------------------------ | -------------------- |
| 15             | N/A                                    | N/A                                         | ==0b1111==                     | ==0xF==              |
| -1             | ==0b1001==                             | ==0b1111==                                  | N/A                            | N/A                  |
| -8             | N/A                                    | ==0b1000==                                  | N/A                            | N/A                  |
| 7              | ==0b0111==                             | ==0b0111==                                  | ==0b0111==                     | ==0x7==              |
| 10             | N/A                                    | N/A                                         | ==0b1010==                     | ==0xA==              |
12. Why are the boxes blacked out in the previous problem?
	- The numbers can be represented with 4 bits, but not with hex
	- The numbers can be represented with 4 bits with ascii
	- ==Some of the numbers can't be represented with signed magnitude in 4 bits==
	- ==Some negative numbers can't be represented with unsigned binary/hex==
13. Answer the following questions about this MIPS instruction: add $t3, $t4, $t5
	1. Which register is the ‘rd’ destination register?
		- ==$t3==
	2. What is the decimal number address of the ‘rs’ first source register (example - $t0 address is 8)?
		- ==12==
	3. Assume the following values are in register memory. What would the new value in the ‘rd’ destination register be after executing this add instruction?
		- ==95==
14. Update the register memory and main memory tables after the following MIPS load word and store word instructions execute. Assume the following initial values are in register and main memory. Assume the instructions execute sequentially.
	1. lw \$t0, 12(\$s1)
		- ==$t0=104==
	2. sw \$t3, 4(\$s1)
		- ==0x2C=654==
	3. lw \$t8, -16(\$s1)
		- ==$t8=127==
	4. sw \$a0, -8(\$v0)
		- ==0x8=24==