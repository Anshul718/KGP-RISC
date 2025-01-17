# KGP-RISC
 A Single-Cycle 32-bit RISC Architecture CPU build using verilog for Artix-7 FPGA.
 Complete FPGA working project is avaliable in [KGP-RISC](https://github.com/Anshul718/KGP-RISC/tree/master/KGP_RISC) directory.
# Modules
 **Module**  | **Description**
 ------------- | -------------
 **KGP_RISC.v**   | Top module to control all other modules.
 **ALU.v**  | Module to perform arithmetic operations only. <br><br>Modules used under ALU.v are : <br> 1) Arithmetic_Barrel_Right_Shifter.v, <br>2) Barrel_Shifter.v, <br>3) hybrid_adder.v, <br>4) MUX_2x1.v, <br>5) twos_complement.v, <br>6) twos_complement_64.v, <br>7) Combinational_32x32_Multiplier.v
 **branch.v** | Perform all the logical operations for branching instructions.
 **assignInputs.v** | Module provides modified and appropriate sign extended input to ALU module depending upon OPCODE and FCODE.
 **InstDecode.v** | This module decodes 32-bit instruction input to generate opcode, fcode, rs, rt, imm, shamt, etc. 
 **InstrFetch.v** | Gets instruction from Block-RAM (BRAM) using Program Counter (PC) and decides next PC depending upon braching condition.
 **regBank.v** | This module contains 32 32-bit registers that we will use to write our MIPS program. Assignment of registers_name to corresponding register_number in regBank is provided in [Instruction_Fromat_and_Decodings.pdf](https://github.com/Anshul718/KGP-RISC/blob/master/Instruction_Format_and_Decodings_asgn10_Grp_47_17CS10005_17CS10007.pdf) file.
 **writeAddress.v** | This module provides address(register number), data, and control signal for instructions involving register write/update.
 **intmem.coe** | Stores 32-bit program instructions. Used when creating BRAM.
 **__.tb** | Test Bench for corresponding __.v file
# Usage Information
 > - Register $t0 (register number 8 or r[7]) is used to output final result.
 > - Block RAM 1(blk_mem_gen_v7_3.v) is used to store 32-bit program instructions. This module is generated by Core Generator using **intmem.coe** . 
 > - Block RAM 2(blk_mem_gen_v7_3b.v) is initialised empty and used as ROM to store input data like array during program execution. This module is also generated by Core Generator.
 > - Use [Target_Code_Generator.ipynb](https://github.com/Anshul718/KGP-RISC/blob/master/Code%20Genertor/Target_Code_Generator.ipynb) module to generate 32-bit instructions from assembly code. Instructions are generated according to the [Instruction Format and Decodings](https://github.com/Anshul718/KGP-RISC/blob/master/Instruction_Format_and_Decodings_asgn10_Grp_47_17CS10005_17CS10007.pdf).
 >
 > **NOTE :** 
 >> - Create Block RAM 1 using core generator first then import all the other __.v and __.tb modules using Add source to your project. Before importing KGP_RISC_ucf.ucf make sure to set KGP_RISC.v as top module.
 >> - **blk_mem_gen_v7_3.v** and **blk_mem_gen_v7_3b.v** are just a verilog modules accessing BRAM.
# Schematic Diagram
 ![](https://github.com/Anshul718/KGP-RISC/blob/master/Schematic_Diagram.jpg)
# Sample Test File
 MIPS Assembly code and corresponding Instruction Memory
 ![](https://github.com/Anshul718/KGP-RISC/blob/master/Sample_Code.png)
# Simulation
 Linear Search Simulation
 ![](https://github.com/Anshul718/KGP-RISC/blob/master/Simulation.png)
