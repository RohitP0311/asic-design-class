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

* In the RISCV, There are four core instruction formats: R, I, S, B,J & U. Instructions must be aligned on a four-byte boundary memory. 

**What are the instruction sets in RISCV?**

* The instruction set is designed for the wide range of uses. The base instruction set has a fixed length of 32-bit naturally aligned instructions. The RISC-V instruction set is the core of the 
  architechture, defining the set of operations that a RISC-V processor can perform. The instruction set is designed to be simple and efficient with a few basic instructions that can be combined to 
  perform complex operations.

There are total 6 types of instructions in RISC-V:

* R Type
     r-type format is use to carry out various operations using logical and arithmatic instructions.
     There are six sub fields in R types -
  
     ![RType](https://github.com/RohitP0311/asic-design-class/blob/main/Task4/RType.png)
  
     1.OpCode
                                                                                                                                                                                               
     2.Funct3
  
     3.Funct7
  
     4.rd
  
     5.rs1
  
     6.rs2

* 


