# DESIGN-A-4-STAGE-PIPELINED-PROCESSOR-WITH-BASIC-INSTRUCTIONS-LIKE-ADD-SUB-AND-LOAD.

"COMPANY": CODTECH IT SOLUTIONS

"NAME":CHALLAMBETI SRAVANTHI

"INTERN ID":CT06DG3299

"DOMAIN":VLSI

"DURATION":6 WEEKS

"MENTOR":NEELA SANTOSH

DESCRIPTION FOR TASK 3:


The goal of this project is to design a 4-stage pipelined processor that supports three basic RISC-like instructions: ADD, SUB, and LOAD. The processor is to be implemented in Verilog HDL (Hardware Description Language) and simulated to demonstrate the pipeline working across each instruction stage.

The pipeline stages implemented are:

1. Instruction Fetch (IF)


2. Instruction Decode (ID)


3. Execute (EX)


4. Write Back (WB)



Each instruction passes through these stages, and with pipelining, multiple instructions are processed simultaneously at different stages, increasing throughput.


---

💻 TOOLS USED

1. Hardware Description Language

Verilog HDL is used for designing the processor. It allows us to model and simulate hardware components in code.


2. Simulation Tools

Icarus Verilog (iverilog): An open-source Verilog compiler used to compile and simulate Verilog designs.

GTKWave: A waveform viewer used with Icarus Verilog to visualize signal transitions and debug the pipeline stages.


3. Editor Platform

VS Code (Visual Studio Code) or Vivado Design Suite (for Xilinx FPGAs) can be used to write Verilog code.

Alternatively, online Verilog IDEs like EDA Playground or Makerchip can also be used for writing and testing code quickly without installation.



---

⚙️ EXPLANATION OF PIPELINED PROCESSOR

The processor handles three instructions:

ADD R1, R2, R3  → R1 = R2 + R3

SUB R2, R1, R5  → R2 = R1 - R5

LOAD R6, 1      → R6 = mem[1] (mocked to return constant)


Each instruction is encoded in 16 bits, split as follows:

| Opcode(4) | Destination(4) | Source1(4) | Source2/Immediate(4) |

The processor is implemented using a modular design, all written in a single Verilog module for simplicity.


---

🔹 Instruction Fetch (IF)

In the first stage, the processor uses the Program Counter (PC) to fetch the instruction from instruction memory. Every clock cycle, the PC increments by one to fetch the next instruction.

Input: PC

Output: 16-bit instruction



---

🔹 Instruction Decode (ID)

The instruction is passed to the ID stage through a pipeline register IF_ID_instr. Here, the processor:

Decodes the opcode

Identifies the destination and source registers

Reads the register file to get source operand values


This prepares the data needed for execution in the next stage.


---

🔹 Execute (EX)

In this stage, the ALU (Arithmetic Logic Unit) performs the required operation:

ADD: Operand1 + Operand2

SUB: Operand1 - Operand2

LOAD: Mocked to return 0xAB (a constant representing memory read)


The result is temporarily stored in EX_WB_result to be used in the write-back stage.


---

🔹 Write Back (WB)

In the final stage, the processor writes the result from the EX stage back into the destination register using the reg_file array.

The register is updated using the values held in the pipeline register EX_WB_result, and the write is controlled using the EX_WB_we (write enable).


---

🎯 APPLICATIONS

This 4-stage pipelined processor design can be applied in:

1. Educational Purposes

Helps students understand the core functionality of CPU internals.

Demonstrates the concept of pipelining and instruction-level parallelism.



2. FPGA Implementation

This processor can be synthesized onto an FPGA using tools like Vivado or Quartus.

Helpful for embedded systems and hardware prototyping.



3. Computer Architecture Labs

Used in labs to show performance improvement due to pipelining.

Can be extended with hazards, forwarding, branching, and memory write.





---

📌 WHY THIS DESIGN IS IMPORTANT

Pipelining is a fundamental concept in modern processor design. Even this basic example shows:

Parallel execution: Multiple instructions processed simultaneously.

Throughput increase: Every clock cycle completes part of an instruction.

Scalability: More instructions (like STORE, JUMP, NOP, BRANCH) can be added.

Extensibility: You can add data hazard handling, stalls, and forwarding units.


This design is the starting point for building a full RISC processor like MIPS or RISC-V, and is highly relevant for students, researchers, and embedded designers.


---

📚 SUMMARY

Task: Design a 4-stage pipelined processor with ADD, SUB, LOAD

Language: Verilog HDL

Tools: Icarus Verilog, GTKWave, VS Code, Vivado

Stages: IF, ID, EX, WB

Result: Working simulation with parallel instruction processor

#OUTPUT

<img width="1366" height="768" alt="Image" src="https://github.com/user-attachments/assets/5cd03282-52d6-4210-b7df-46961db82ccd" />
