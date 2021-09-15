# Introduction

## What is an Operating System?
	- is a software that runs in kernel mode
	- it performs two things
		- providing application programmer a clean abstract set of resources
		- manage these hardware resources

## Resource Management
	- it includes multiplexing(sharing) resources in two different ways:
		- time
			- different programs take turn using CPU
		- space
			- different programs take part of the resource



## Processors
	- CPU is the brain. it has three basic cycle: fetch from memory, decode its type and operands, execute it. 
	- CPU have its own memory because accessing memory takes much longer than executing. so, all CPUs contain registers. 
	- Registers
		- hold variables and temporary result
		- Special Registers
			- **Program counter**: contains the memory address of next instruction
			- **Stack pointer**: whic points to the top of the current stack in memory.
			- **PSW(Program Status Word)**: contains the condition code bits, cpu priority, the mode(user or kernel), various other control bits.
	- CPU designers have abonded the simple model of fetching, decoding and executing one instruction at a time. Modern CPUs can execute more than one instruction at the same time. The organization is called a **pipeline**. 
	- More advanced than **pipeline** is **superscalar** CPU were multiple execution units(integer arithmetic, floating-point arthimetic, Boolean operations) are present.
	- Most CPUs, except simple ones, have two modes: Kernels and user mode. 
	- In Kernel mode, the CPU can execute every instruction in its instruction set and use every feature of the hardware.
	- In User mode, only a subset of instructions are executed and features are accessed. To obtain services, it must make system call. 

###	Multithreading and Multicore Chips
