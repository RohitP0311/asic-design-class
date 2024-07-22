# Task 1 : Write a C program for the sum of 1 to 5 Natural numbers using GCC compiler.

Write & run a 'c' code in gcc compiler and perform the sum of 1 to 5 numbers.

Step1: First ensure that we are in the home directory
   
![Home Directory](https://github.com/RohitP0311/asic-design-class/blob/main/Task1/Home%20Directory.png)

Step2: Write a C program in the leafpad editor using 
         'leafpad sum1ton.c &'
         step1 : create a C file in the home directory

       leafpad sum1ton.c

         
![Leafpad Editor](https://github.com/RohitP0311/asic-design-class/blob/main/Task1/Leafpad%20Editor.png)

![C Program](https://github.com/RohitP0311/asic-design-class/blob/main/Task1/C%20Program.png)

Step3: Compile the program in gcc compiler using command 'gcc sum1ton.c'

![GCC Compiler](https://github.com/RohitP0311/asic-design-class/blob/main/Task1/Gcc%20Compiler.png)

Step4: Final output of the programme

![Final Outpad](https://github.com/RohitP0311/asic-design-class/blob/main/Task1/Final%20Output.png)
   
# Task 2: Compile the same program using RISCV Compiler and check the output.

Now we check the same programme in RISC5 Simulator.

Step1: Run the same programme in RISC5 Simulator

![RISCV Simulator](https://github.com/RohitP0311/asic-design-class/blob/main/Task2/RISCV%20Simulator.png)

Step2: The commands will get displayed in the 'main'

![Main_O1](https://github.com/RohitP0311/asic-design-class/blob/main/Task2/Main_O1.png)

![Disassembly of section](https://github.com/RohitP0311/asic-design-class/blob/main/Task2/Disassembly%20of%20section.png)

Step3: Now run the program with Ofast compiler

![main_fast](https://github.com/RohitP0311/asic-design-class/blob/main/Task2/Main_Fast.png)


# Task 3

Step1: Now, we will verify the output using gcc and RiscV compilers, sum should be 15 in both the cases.

![RiscV_out](https://github.com/RohitP0311/asic-design-class/blob/main/Task3/RiscV_Out.png)

Step2: Now we will debug the commands using 'Spike -d pk sum1ton.o' command & also verify that content of the register gets modified after any operation(eg. addi, lui, li).

![Debug](https://github.com/RohitP0311/asic-design-class/blob/main/Task3/Debug.png)

Here, we can see that contents of register a0 has been changed after performing operation.


