## 

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
  

