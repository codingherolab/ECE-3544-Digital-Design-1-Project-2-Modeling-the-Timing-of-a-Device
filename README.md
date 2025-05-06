# ECE-3544-Digital-Design-1-Project-2-Modeling-the-Timing-of-a-Device

Download Here: [ECE 3544 – Digital Design 1 Project 2: Modeling the Timing of a Device](https://codingherolab.com/product/ece-3544-digital-design-1-project-2-modeling-the-timing-of-a-device/)

For Custom/Original Work email codingprolab@gmail.com/whatsapp +1(541)423-7793

Purpose

The purpose of this project is to use Verilog as a means for modeling the timing of a module. You will model an available component (the 74HC/HCT85 4-bit magnitude comparator) and use a delay model to analyze the timing of a system that utilizes the component.

 

Requirements

You must have the current version of ModelSim-Altera Starter Edition installed on your computer. The instructions in this assignment are consistent with that version of ModelSim. Even if these instructions are consistent with other versions of ModelSim, you should use the version indicated here.

 

The DE1-SoC Board is not required for this project. This project involves only simulation.

 

Instructions

Study the clk and counter4bit Simulate clk and counter4bit using the tb_clk and tb_counter modules.
 

I have provided Verilog models for a clock generator and a 4-bit synchronous counter. Study these two models to gain a good understanding of the behavior that they are meant to simulate. In particular, observe the manner in which each one uses parameters to establish default delays for their behavior in simulation. Please note that these modules have not been written with synthesizability in mind. In the particular case of the clock, the module cannot be used to generate a real clock signal, and we will not use it for that purpose. It is only meant to simulate the behavior of a clock in test benches.

 

I have also provided test benches for the clock generator and the counter. Study these test benches. Remember that test benches do not have their own ports. Instead, the test bench module generates stimulus values for the module you want to test. Use the test benches to simulate the clock and counter modules. Study the simulation results to further your understanding of how the clock generator and counter modules operate.

 

Among other things, the test benches will demonstrate the operation of the modules and the manner in which they should be connected within a system. The test benches also demonstrate the manner in which the designer can override a parameter when the module is instantiated. This technique is very useful, as it also works in situations where a synthesizable module is being instantiated in a higher-level module that we also intend to synthesize.

 

 

Use the 4-bit counter module as the basis for developing an 11-bit counter. Use the 4-bit counter’s test bench module as the basis for developing a test bench for your 11-bit counter.
 

Copy and modify the 4-bit counter module supplied with this project description. Name the new counter module counter11bit_YOURPID. Your 11-bit counter should have the same delay parameters as the 4-bit counter. Even though we have not yet formally studied synchronous counters, you should be able to infer the proper structure for your 11-bit counter from the 4-bit counter that I have given you. Remember that in a synchronous sequential circuit, your procedural model should use a non-blocking assignment to target the counter’s state.

 

Use the test bench for the 4-bit counter as a model for making a test bench for the 11-bit counter. Name the test bench tb_counter11bit_YOURPID. In your report, include waveforms that demonstrate the correct behavior of your counter. You do not have to include the entire sequence of 11-bit counter states, but you should provide representative sections.

 

Develop and verify an untimed Verilog model for the 74HC/HCT85 4-bit magnitude comparator described in the 7485 Datasheet included with this specification. Develop a test bench for your comparator module.
 

Implement a Verilog model having the same behavior as the function table on Page 4 of the datasheet and the logic circuit given in Figure 5 of the datasheet. You may use Verilog’s built-in gate primitives to create a structural model, a behavioral model using continuous assignment, or a behavioral model using procedural assignment. (I strongly encourage you to use a behavioral model!) If there are discrepancies between the logic diagram and the function table, consider the function table to be correct.

 

Use the following module declaration for your circuit:

 

module hc85_YOURPID(a_in, b_in, ia_lt_b, ia_eq_b, ia_gt_b,

qa_lt_b, qa_eq_b, qa_gt_b);

input [3:0] a_in, b_in;

input       ia_lt_b, ia_eq_b, ia_gt_b;

output      qa_lt_b, qa_eq_b, qa_gt_b;

 

In each case where the specification provides the module declaration for a component, you must use that module declaration exactly as it appears. Failure to use the module declarations as provided will prevent the assignment graders from verifying the operation of your modules. If this happens, you will receive no credit for the affected portions of the project.

 

Write a test bench that uses the outputs of your 11-bit counter to drive the inputs of your comparator circuit. Name your test bench tb_hc85_YOURPID. Your test bench should instantiate the clock generator, counter, and comparator models in a way that correctly connects their inputs and outputs together. Use the block diagram below as a model for structuring your test bench.

 

 

Figure 1: Counter test-bench structure

 

To simulate your hc85 module with the counter module, your hc85 module must have a `timescale directive before the module declaration. Use the same directive as the 4-bit counter example: `timescale 1 ns/100 ps. The timescale directive tells the simulator that the value of one unit of time (#1) is 1 ns, and the precision (the smallest valid fraction of a time unit) is 100 ps.

 

In your report, include waveforms of inputs to and outputs from the untimed hc85 module that confirms its consistency with the function table on Page 4 of the datasheet. You do not have to include all combinations of the inputs on your waveforms, but you must show that your module behaves correctly for each line of the function table.

 

Do not proceed to Step 4 until you have verified the correct operation of the untimed model.

 

Use a specify block to add propagation delays to your hc85
 

Use the typical propagation delays at 25 degrees C and 4.5V from Page 6 of the 74HC85 datasheet. You do not have to worry about the output transition time, only the propagation delays.

 

Simulate the timed model using your test bench. Your report should include waveforms showing the correct operation of the model with delays. You should also include waveforms with sufficient resolution to show that the delays are correct.

 

Create a behavioral model of a 14-bit register.
 

Your register must have the following module declaration:

 

module register14bit_YOURPID(clk, d_in, q_out);

input        clk;

input  [13:0] d_in;

output [13:0] q_out;

 

This register should parallel load the values of d_in as the register state q_out on each rising edge of clk. The functionality of this module is essentially that of the 74FCT821 component described in the 74821 data sheet, but without the ability to tri-state the outputs. Your model of the 14-bit register should not include any delays. Even though we have not yet formally studied synchronous counters, you should be able to infer the proper structure for your 14-bit register from information I have provided in lecture. Remember that in a synchronous sequential, your procedural model should use a non-blocking assignment to target the register’s state.

Create a test bench to verify the correct operation of your register. Name the test bench tb_register14bit_YOURPID. Your report should include a waveform showing its correct operation.

 

Use your models for the counter, the 74HC85, and the 14-bit register (74FCT821) to create the model of a digital system as described below.
 

The system consists of two blocks and a clock generator. You should instantiate these elements in a test bench module named tb_systemX_YOURPID. Replace X with a number that denotes the version number of the test bench, as described further below.

 

In the transmit module, the counter provides its outputs as the inputs to an hc85. The 11-bit counter value that serves as the comparator input and the 3-bit counter output are both registered.
 

module transmit_YOURPID (clk, ctr_clr, ctr_en, reg_out);

input         clk, clear, ctr_en;

output [13:0] reg_out

 

In the receive module, the registered 11-bit counter value from the transmit module is applied as the input to an hc85. The outputs of this “receive-side” hc85 and the registered values from the “transmit-side” hc85 should be applied to a comparator. The comparator output valid should equal 1 if both comparator outputs are the same and 0 otherwise. The comparator should have no delay.
 

module receive_YOURPID (clk, reg_in, valid);

input         clk;

input  [13:0] reg_in;

output        valid;

 

The transmit and receive modules both use the same clock, as generated by the clk module.

 

Figure 2: System test bench structure

 

 

The first version (tb_system1_YOURPID) should define a value for the PERIOD parameter of the clk module that is sufficiently large to respect the propagation delays of the modules in the system. This should allow you to demonstrate that the system always shows the correct behavior , i.e., it should register the correct values on the transmit side, it should display a correct value for valid during each clock period on the receive side, etc.

 

The second version (tb_system2_YOURPID) should define a value for the PERIOD parameter of the clk module that is just small enough to cause the system to show incorrect behavior at some point.

 

Project Submission

Your project submission should include the following items:

 

A project report containing the following elements:
A restatement of the assignment’s objectives.
A discussion of the approach you took to modeling the comparator and counter modules, and a description of any design decisions you made as a part of implementing your modules.
Waveforms that demonstrate the correct operation of each of the modules you create. Discuss how you formulated the tests contained in your test benches and how you verified the correctness of your implementation.
An analysis of how you determined the PERIOD parameter of the clk module to demonstrate valid and invalid behavior of the system implemented in tb_systemX. In particular, you should provide an analysis of the shortest clock period that will always allow correct (valid) behavior of the system.
Waveforms that demonstrate valid and invalid behavior of the system.
A discussion of your conclusions and the lessons you learned from the assignment.
 

Your report should be in PDF format. Include your PID in your report filename, e.g., project2report_jthweatt.pdf.

 

Source files and test benches, as follows:
counter11bit_YOURPID
tb_counter11bit_YOURPID
hc85_YOURPID with delay implemented
tb_hc85_YOURPID
register14bit_YOURPID
tb_register14bit_YOURPID
transmit_YOURPID
receive_YOURPID
tb_system1_YOURPID
tb_system2_YOURPID
 

Replace instances of YOURPID in file names with your Virginia Tech PID. Submit your report and source as a single zip file on the project assignment page. Include your PID in the name of your archive file, e.g., project2files_jthweatt.zip.

 

Grading for your submission will be as described on the cover sheet included with this description. You must include the provided cover sheet as the first page of your report. I have provided it as a .doc so that you can make it the first page of your report prior to converting it into a PDF file.
