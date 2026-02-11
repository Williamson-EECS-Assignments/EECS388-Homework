## Multiple Choice
1. Which of the following is stored in the program counter register?
	1. Current instruction machine code
	2. Next instruction machine code
	3. Starting address of the program instructions
	4. ==Address of the next instruction==
2. Which of the following is stored in the *$ra* register?
	1. The current memory address of the end of the stack.
	2. The memory address of the start of the stack for the current function
	3. ==The return address of caller's next instruction to execute after completing callee==
	4. The constant value 0
3. Which of the following is stored in the *$sp* register?
	1. ==The current memory address of the end of the stack==
	2. The memory address of the beginning of the stack for the current function
	3. The memory address of the next instruction to execute from the caller function
	4. The constant value 0
## True / False
4. During the Assembler step (preprocessing, compiling, assembler, linker) the assembly code is converted into the object/machine code.
	- ***True***
5. The three types of MIPS instruction formats are r-type, i-type, and j-type.
	- ***True***
6. The three types of MIPS instruction formats have different size instructions
	- ***False***
## Short Answer
7. You and your friend are debugging as RS-232 serial UART and you attach a signal probe to the transmit line. You see the following picture on the oscilloscope. Answer the following questions:
	![[HW2-Q7.png|400]]
	1. What are the **raw** data bits of the transmission on the wire? The blue lines help separate each bit being transmitted (+12V for 0, -12V for 1).
		- ***10110100***
	2. What ascii character does this represent? Answer as a single character, without quotation marks, be sure you use the correct upper or lowercase letter (Example: z). Hint: Remember the order of bits in a UART transmission are LSB first!
		- ***-***
	3. What is the baud rate (bits per second) of the transmission? Assume each bit is taking approximately 66 microseconds each. Round to the nearest while number, do no put units or commas in your answer. Example (12345)
		- $\text{baud}=\dfrac{1}{66\times10^{-6}}\approx15152$
	4. How long does it take to transmit the entire transmission (1 start bit, 8 data bits, 1 stop bit)? Answer in microseconds, rounded to the nearest while microsecond, Do not include units in your answer (Example: 345)
		- $(10)_{\text{bits}}\times(66)_{\text{microseconds}}=\boxed{660_{\text{microseconds}}}$
	5. If this byte is received by a microcontroller and stored with a memory mapped 8-byte FIFO RX queue, what would you have to do to take the value out of the RX queue?
		- $\boxed{\text{Read from the UART RX data register}}$
8. Fill out the yellow fields and convert the C instructions into MIPS assembly and Machine Code.
	1. Part A - Assume that $a1 and $a2 hold the values of y and z respectively. User $t0 to hold the result.
		- add \$t0, \$a1, \$a2
		- 0
		- 5
		- 6
		- 8
		- 0
		- 32
		- 00000_00101_00110_01000_00000_00000
	2. Part B - Assume $s2 has the base address of the array and variable h is in register $s3. Use $t0 register to hold the result.
		- lw \$t0, 8(\$s2)
		- 35
		- 18
		- 8
		- 8
		- 100011_10010_01000_0000'0000'0000'1000
		- $\text{add \$t0, \$t0, \$s3}$
	3. Part C - Assume 'Exit' has an address of 2010 decimal.
		- j Exit
		- 2
		- 2010
		- 000010_00'0000'0000'0000'0111'1101'1010
![[HW2-Q8.png|500]]
9. Assume we have a MIPS datapath show below with the following values inside of the registers. Fill in the table below with the values for A-F for the next two instructions as they are executing. Assume the instructions occur sequentially, so if the first instruction changes a register, it is modified and that would be the value in the register if accessed by later instructions.
	- *$t0 = 0x0000_FFFF*
	- *$t2 = 0x0000_000F*
	- *$t3 = 0x0000_0FFF*
	- *$t4 = 0x0000_0040*
	- *$s1 = 0x0000_0002*
	- *$s2 = 0x0000_0F0F*
	- *$PC = 0x8000_0004* (Address of the subtract instruction)

| Instruction         | A -<br>Address of instruction (subtract) | B -<br>Instruction in machine code | C -<br>Value Inside register *rs* | D -<br>Value inside register *rt* | E -<br>Result to write back into *rd* destination register | F -<br>Address of next instruction<br>(Program Counter) |
| ------------------- | ---------------------------------------- | ---------------------------------- | --------------------------------- | --------------------------------- | ---------------------------------------------------------- | ------------------------------------------------------- |
| *sub $t0, $t2, $s1* | 0x8000_0004                              | 0x0151_4022                        | 0x0000_000F                       | 0x0000_0002                       | 0x0000_000D                                                | 0x8000_0008                                             |
| *sw $t0, 4(\$t4)*   | 0x8000_0008                              | 0xAD88_0004                        | 0x0000_0040                       | 0x0000_000D                       | ***N/A***                                                  | 0x8000_000C                                             |

10. The Arduino Uno R3 uses an ATMega328P Atmel processor. You've read the datasheet and found the offset (0xC1) for the UART 0 - UCSR0B register, which controls if the board has the receiver and transmitter enabled.
	```C
	#include <stdint.h>
	
	/* I/O -> base address */
	#define IO_BASE_ADDR    0x20
	
	/* I/O register offsets from the datasheet */
	#define UCSR0B_OFFSET   0xC1
	
	/* Full SRAM-mapped address */
	#define UCSR0B_ADDR     (IO_BASE_ADDR + UCSR0B_OFFSET)
	
	int main(void) {
		/* Pointers to the registers (Line 15) */
		
		/* enable transmitter (TXEN0 bit) and receiver (RXEN0 bit) */
	}
	```
	1. Write the code for line 15 to create a `uint8_t` pointer and initialize it to the address of the UCSR0B control register.
		```C
		volatile uint8_t* USCR0B_ptr = (volatile uint8_t*)UCSR0B_ADDR;
		```
	2. Write the code to enable the transmitter (set bit to 1) and enable the receiver (set bit to 1) on line 18 without changing any other values in the register. Assume that TXEN0 is defined to 3 and RXEN0 is defined to 4.
		```C
		*USCR0B_ptr |= (1 << TXEN0) | (1 << RXEN0);
		```
10. Wire up the following circuit so that: 
	1. The micro controller 1 can turn on the LED using GPIO pin 8 in an active-low configuration.
	2. The microcontroller 2 can read if the button is pressed or not in an active-high configuration by reading GPIO pin 9.
	3. The microcontroller 2 can use a UART connection to tell microcontroller 1 that the button is pressed.
	![[HW2-Q11.png|450]]
Match the pins specified on the left with what they will be wired to on the right.  If something is not connected, just select "Not connected". Available options are: Microcontroller 2 TX, terminal d., button terminal c., Not connected, Microcontroller 1 RX, LED terminal a., resistor terminal b.

| Pin                      | Wired to             |
| ------------------------ | -------------------- |
| Microcontroller 1 TX     | Not connected        |
| Microcontroller 1 RX     | Microcontroller 2 TX |
| Microcontroller 1 +5V    | LED terminal a.      |
| Microcontroller 1 GND    | Not connected        |
| Microcontroller 1 GPIO 8 | resistor terminal b. |
| Microcontroller 1 GPIO 9 | Not connected        |
| Microcontroller 2 TX     | Microcontroller 1 RX |
| Microcontroller 2 RX     | Not connected        |
| Microcontroller 2 +5V    | button terminal c.   |
| Microcontroller 2 GND    | terminal d.          |
| Microcontroller 2 GPIO 8 | Not connected        |
| Microcontroller 2 GPIO 9 | button terminal c.   |
- ==This answer lost me 0.5 points, so check it==
11. RS-232 serial con be configured in several ways. The protocol always requires 1 start bit. It can have 1 or two stop bits. It can have 7 or 8 data bits. It can have even, odd or no parity bits. Here are some of the formats:
	- 9600-8-N-1 (9600 baud, 8 data bits, no (N) parity bit, 1 stop bit)
	- 115300-7-E-2 (115200 baud, 8 data bits, 1 (E) even parity bit, 2 stop bits)
	- 38400-8-O-1 (38400 baud, 8 data bits, (O) odd parity bit, 1 stop bit)
	You receive the following RS-232 serial transmission. Assuming its received correctly, answer the following questions.
	![[HW2-Q12.png|400]]
	1. Is it even, odd, or no parity?
		- ***Odd parity***
	2. Assuming all 11 bits of the data transmission were received in 2291.66 microseconds, what is the baud rate?
		- $\text{baud}=\dfrac{11}{2291.66\times10^{-6}}\approx4800$
	3. Write out the format of the RS-232 protocol used by this transmission.
		- ***4800-8-O-1***

