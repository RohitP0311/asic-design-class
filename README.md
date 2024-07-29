<details>
   <summary>Lab1: Write a C program for the sum of 1 to 5 Natural numbers using GCC compiler. </summary>

# Task 1 : Write a C program for the sum of 1 to 5 Natural numbers using GCC compiler.

Write & run a 'c' code in gcc compiler and perform the sum of 1 to 5 numbers.

Step1: First ensure that we are in the home directory
   
![Home Directory](https://github.com/RohitP0311/asic-design-class/blob/main/Task1/Home%20Directory.png)

Step2: Write a C program in the leafpad editor using 'leafpad sum1ton.c &'
      create a C file in the home directory

       leafpad sum1ton.c

         
![Leafpad Editor](https://github.com/RohitP0311/asic-design-class/blob/main/Task1/Leafpad%20Editor.png)

![C Program](https://github.com/RohitP0311/asic-design-class/blob/main/Task1/C%20Program.png)

Step3: Compile the program in gcc compiler using command 'gcc sum1ton.c'

       gcc sum1ton.c

       

![GCC Compiler](https://github.com/RohitP0311/asic-design-class/blob/main/Task1/Gcc%20Compiler.png)

Step4: Final output of the programme

![Final Outpad](https://github.com/RohitP0311/asic-design-class/blob/main/Task1/Final%20Output.png)

</details>   

<details>
     <Summary>Lab2: Compile the same program using RISCV Compiler and check the output. </summary>

   
# Task 2: Compile the same program using RISCV Compiler and check the output.

Now we check the same programme in RISC5 Simulator.

Step1: Run the same programme in RISC5 Simulator

       riscv64-unknown-elf-gcc -O1 -mabi=lp64 -march=rv64i -o sum1ton.o sum 1ton.c


![RISCV Simulator](https://github.com/RohitP0311/asic-design-class/blob/main/Task2/RISCV%20Simulator.png)

Step2: The commands will get displayed in the 'main'

![Main_O1](https://github.com/RohitP0311/asic-design-class/blob/main/Task2/Main_O1.png)

![Disassembly of section](https://github.com/RohitP0311/asic-design-class/blob/main/Task2/Disassembly%20of%20section.png)

Step3: Now run the program with Ofast compiler using the following command- 

        riscv64-unknown-elf-gcc -Ofast -mabi=lp64 -march=rv64i -o sum1ton.o sum1ton.c


![main_fast](https://github.com/RohitP0311/asic-design-class/blob/main/Task2/Main_Fast.png)

</details>

<details>
   <Summary>Lab3:Simulation using Spike, Debugging & Observations using O1 and Ofast compilers.  </Summary>
      
# Task 3: Simulation using Spike, Debugging & Observations using O1 and Ofast compilers.

Step1: First we will observe the commands using O1 compiler. Use the following command for O1 compiler - 

       riscv64-unknown-elf-gcc -O1 -mabi=lp64 -march=rv64i -o sum1ton.o sum 1ton.c

In the main section we can find out the list of operations for the program. 
![Main_O1](https://github.com/RohitP0311/asic-design-class/blob/main/Task2/Main_O1.png)

Step2: Now, we need to observe the main operations using another compiler Ofast. Use the following command to use Ofast compiler- 

              riscv64-unknown-elf-gcc -Ofast -mabi=lp64 -march=rv64i -o sum1ton.o sum1ton.c

In the main section we can find out the list of operations for the program.
![main_fast](https://github.com/RohitP0311/asic-design-class/blob/main/Task2/Main_Fast.png)

Step3: Now, we will verify the output using gcc and RiscV compilers, sum should be 15 in both the cases. For Spike simulation use following command-

         spike pk sum1ton.o


![RiscV_out](https://github.com/RohitP0311/asic-design-class/blob/main/Task3/RiscV_Out.png)

Step2: Now we will debug the commands using 'Spike -d pk sum1ton.o' command & also verify that content of the register gets modified after any operation(eg. addi, lui, li).

To debug use following command - 

         spike -d pk sum1ton.o



![Debug](https://github.com/RohitP0311/asic-design-class/blob/main/Task3/Debug.png)

Here, we can see that contents of register a0 has been changed after performing operation.

</details>
   
# Task 4: To Identify RISC-V Instruction type and find 32 bit pattern

* In the RISCV, There are four core instruction formats: R, I, S, B, J & U. Instructions must be aligned on a four-byte boundary memory. 

**What are the instruction sets in RISCV?**

* The instruction set is designed for the wide range of uses. The base instruction set has a fixed length of 32-bit naturally aligned instructions. The RISC-V instruction set is the core of the 
  architechture, defining the set of operations that a RISC-V processor can perform. The instruction set is designed to be simple and efficient with a few basic instructions that can be combined to 
  perform complex operations.

There are total 6 types of instructions in RISC-V:

* R Type
     r-type format is use to carry out various operations using logical and arithmatic instructions.
     There are six sub fields in R types -
  
     ![RType](https://github.com/RohitP0311/asic-design-class/blob/main/Task4/RType.png)
  
     + OpCode(7 bits): Basic Operation Code
     + Funct3(3 bits): Function Code
     + Funct7(7 bits): Function code for additional instruction differentiation
     + rd(5 bits): Destination register
     + rs1(5 bits): First source register
     + rs2(5 bits): Second source register

* I type       
     + I-type instructions in the RISC-V architecture are used for operations that involve an immediate value along with one or two registers.
    +  These instructions typically perform operations such as arithmetic with immediate values, load operations, and certain branch instructions.
    +  The format of I-type instructions includes fields for a source register, destination register, an immediate value, a function code, and an opcode.
    +  The instruction format is as follows:

 ![IType](https://github.com/RohitP0311/asic-design-class/blob/main/Task4/IType.png)

 + immediate (12 bits): Immediate value used for operations.
    + rs1 (5 bits): Source register.
    + funct3 (3 bits): Function code for instruction differentiation.
    + rd (5 bits): Destination register.
    + opcode (7 bits): Basic operation code for I-type instructions.

* S Type 
  
    + S-type instructions in the RISC-V architecture are used for store operations, where data is stored from a register into memory.
   + The format of S-type instructions includes fields for two source registers, an immediate value that determines the memory offset, a function code, and an opcode.
   +  The format is as follows: 

  ![SType](https://github.com/RohitP0311/asic-design-class/blob/main/Task4/SType.png)
    + imm[11:5] (7 bits): Upper 7 bits of the immediate value.
    + rs2 (5 bits): Second source register (contains the data to be stored).
    + rs1 (5 bits): First source register (base address register).
    + funct3 (3 bits): Function code for instruction differentiation.
    + imm[4:0] (5 bits): Lower 5 bits of the immediate value.
    + opcode (7 bits): Basic operation code for S-type instructions.
 
* B Type

    + B-type instructions in the RISC-V architecture are used for conditional branch operations.
    +  These instructions are designed to alter the flow of execution based on comparisons between two registers. 
    +  The format of B-type instructions includes fields for two source registers, an immediate value that determines the branch offset, a function code, and an opcode.
    +  Following is the instruction format:
    
     ![BType](https://github.com/RohitP0311/asic-design-class/blob/main/Task4/BType.png)
    + imm[12] (1 bit): The 12th bit of the immediate value.
    + imm[10:5] (6 bits): The 10th to 5th bits of the immediate value.
    + rs2 (5 bits): Second source register.
    + rs1 (5 bits): First source register.
    + funct3 (3 bits): Function code for instruction differentiation.
    + imm[4:1] (4 bits): The 4th to 1st bits of the immediate value.
    + imm[11] (1 bit): The 11th bit of the immediate value.
    + opcode (7 bits): Basic operation code for B-type instructions

* U Type

    + U-type instructions in the RISC-V architecture are used for operations involving large immediate values, typically for loading upper immediate values or computing addresses.
    +  The format of U-type instructions includes fields for a destination register, a large immediate value, and an opcode.
    +  The instruction format is as follows:
  
     ![UType](https://github.com/RohitP0311/asic-design-class/blob/main/Task4/UType.png)

    + immediate[31:12] (20 bits): The upper 20 bits of the immediate value.
    + rd (5 bits): Destination register.
    + opcode (7 bits): Operation code for U-type instructions.
    + The immediate value is stored in the upper 20 bits of a 32-bit word, with the lower 12 bits set to zero when used in calculations.

* J type
    + J-type instructions in the RISC-V architecture are used for jump operations, allowing for altering the program control flow by jumping to a specified address.
    + These instructions are typically used for unconditional jumps, like calling functions or implementing loops.
    + Following is the instruction format: 
     
    ![JType](https://github.com/RohitP0311/asic-design-class/blob/main/Task4/JType.png)
    + imm[20] (1 bit): The 20th bit of the immediate value.
    + imm[10:1] (10 bits): The 10th to 1st bits of the immediate value.
    + imm[11] (1 bit): The 11th bit of the immediate value.
    + imm[19:12] (8 bits): The 19th to 12th bits of the immediate value.
    + rd (5 bits): Destination register where the return address is stored.
    + opcode (7 bits): Operation code for J-type instructions.
  

## Identifying RISC-V Instruction Type-
1. ```ADD r11, r12, r13```
    
   + OpCode for ADD = 0110011
   +  rd = r11 = 01011
   + rs1 = r12 = 01100
   + rs2 = r13 = 01011
   + func3 = 000
   + func7 = 0000000
   + R Type
   + 32 Bit Instruction: 0000000 01011 01100 000 01011 0110011


2. ```SUB r13, r11, r12```


    + Opcode for SUB = 0110011
    + rd = r13 = 01101
    + rs1 = r11 = 01011
    + rs2 = r12 = 01100
    + func3 = 000
    + func7 = 0100000
    + R Type
    + 32 Bit Instruction: 0100000 01100 01011 000 01101 0110011

3. ```AND r12, r11, r13```

    + Opcode for AND = 0110011
    + rd = r12 = 01100
    + rs1 = r11 = 01011
    + rs2 = r13 = 01101
    + func3 = 111
    + func7 = 0000000
    + R Type
    + 32 Bit Instruction: 0000000 01101 01011 111 01100 0110011

4. ```OR r8, r12, r5```

    + Opcode for OR = 0110011
    + rd = r8 = 01000
    + rs1 = r12 = 01100
    + rs2 = r5 = 00101
    + func3 = 110
    + func7 = 0000000
    + R Type
    + 32 Bit Instruction: 0000000 00101 01100 110 01000 0110011

5. ```XOR r8, r11, r4```

    + Opcode for XOR = 0110011
    + rd = r8 = 01000
    + rs1 = r11 = 01011
    + rs2 = r4 = 00100
    + func3 = 100
    + func7 = 0000000
    + R Type
    + 32 Bit Instruction: 0000000 00100 01011 100 01000 0110011

6. ```SLT r30, r20, r4```
   
    + Opcode for SLT = 0110011
    + rd = r0 = 11110
    + rs1 = r1 = 10100
    + rs2 = r4 = 00100
    + func3 = 010
    + func7 = 0000000
    + R Type
    + 32 Bit Instruction: 0000000 00100 10100 010 1110 0110011      

7. ```ADDI r31, r21, 5```

    + Opcode for ADDI = 0010011
    + rd = r2 = 11111
    + rs1 = r2 = 10101
    + imm = 000000000101
    + func3 = 000
    + I Type
    + 32 Bit Instruction: 000000000101 10101 000 11111 0010011

8. ```SW r21, r19, 4```

    + Opcode for SW = 0100011
    + rs1 = r19 = 10011
    + rs2 = r21 = 10101
    + imm = 0000000 0100
    + func3 = 010
    + S Type
    + 32 Bit Instruction: 0000000 10101 10011 010 0100 0100011

9. ```SRL r26, r21, r20```

    + Opcode for SRL = 0110011
    + rd = r26 = 11010
    + rs1 = r21 = 10101
    + rs2 = r20 = 10100
    + func3 = 101
    + func7 = 0000000
    + R Type
    + 32 Bit Instruction: 0000000 10100 10101 101 11010 0110011


11. ```BNE r0, r19, 20```

    + Opcode for BNE = 1100011
    + rs1 = r0 = 00000
    + rs2 = r19 = 10011
    + imm = 000000 001010
    + func3 = 001
    + B Type
    + 32 Bit Instruction: 0000000 00000 00000 001 01010 1100011

12. ```BEQ r0, r0, 15```

    + Opcode for BEQ = 1100011
    + rs1 = r0 = 00000
    + rs2 = r0 = 00000
    + imm = 000000 001111
    + func3 = 000
    + B Type
    + 32 Bit Instruction: 0000000 00000 00000 000 01111 1100011

13. ```LW r23, r21, 2```

    + Opcode for LW = 0000011
    + rd = r23 = 10111
    + rs1 = r21 = 10101
    + imm = 000000000010
    + func3 = 010
    + I Type
    + 32 Bit Instruction: 000000000010 10101 010 10111 0000011

14. ```SLL r25, r21, r20```

    + Opcode for SLL = 0110011
    + rd = r25 = 11001
    + rs1 = r21 = 10101
    + rs2 = r20 = 10100
    + func3 = 001
    + func7 = 0000000
    + R Type
    + 32 Bit Instruction: 0000000 10100 10101 001 11001 0110011

| Instruction       | Type | 32-bit Representation                 |
|-------------------|------|---------------------------------------|
| ADD r11, r12, r13 | R    | 0000000 01011 01100 000 01011 0110011 |
| SUB r13, r11, r12 | R    | 0100000 01100 01011 000 01101 0110011 |
| AND r12, r11, r13 | R    | 0000000 01101 01011 111 01100 0110011 |
| OR r8, r12, r5    | R    | 0000000 00101 01100 110 01000 0110011 |
| XOR r8, r11, r4   | R    | 0000000 00100 01011 100 01000 0110011 |
| SLT r30, r20, r4  | R    | 0000000 00100 10100 010 1110 0110011  |
| ADDI r31, r21, 5  | I    | 000000000101 10101 000 11111 0010011  |
| SW r21, r19, 4    | S    | 0000000 10101 10011 010 0100 0100011  |
| SRL r06, r01, r1  | R    | 0000000 00001 00001 101 00110 0110011 |
| BNE r0, r19, 20   | B    | 0000000 00000 00000 001 01010 1100011 |
| BEQ r0, r0, 15    | B    | 0000000 00000 00000 000 01111 1100011 |
| LW r23, r21, 2    | I    | 000000000010 10101 010 10111 0000011  |
| SLL r25, r21, r20 | R    | 0000000 10100 10101 001 11001 0110011 |

| Assembly Instruction | Hexadecimal Representation |
|----------------------|----------------------------|
| ADD r11, r12, r13    | 0x00B605B3                 |
| SUB r13, r11, r12    | 0x40C58359                 |
| AND r12, r11, r13    | 0x00D5F326                 |
| OR r8, r12, r5       | 0x00598633                 |
| XOR r8, r11, r4      | 0x004B8233                 |
| SLT r30, r20, r4     | 0x004A0E33                 |
| ADDI r31, r21, 5     | 0x005A0F13                 |
| SW r21, r19, 4       | 0x01593223                 |
| SRL r06, r01, r1     | 0x0111633                  |
| BNE r0, r19,         | 0x00000A63                 |
| BEQ r0, r0, 15       | 0x00000F63                 |
| LW r23, r21, 2       | 0x002A5F83                 |
| SLL r25, r21, r20    | 0x014A9B33                 |

## Task 2
* In Terminal install iverilog and GTKWave.
* To simulate and run the verilog code, use following command in the terminal

        $ iverilog -o iiitb_rv32i iiitb_rv32i.v iiitb_rv32i_tb.v
        $ ./iiitb_rv32i

  * To run the GTKWave and see the output waveform, see the following command:

         $ gtkwave iiitb_rv32i.vcd

 ![GTKWave](https://github.com/RohitP0311/asic-design-class/blob/main/Task4/JType.png)  
