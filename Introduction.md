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

## Computer Hardware Review

### Processors
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

####	Multithreading and Multicore Chips
	- what to do with abundance of transistors(the list below in increasing of memory):
		- superscalar architectures: multiple functional units
		- put bigger caches on the CPU chips (eventually, we will reach: __diminishing returns__)
		- replicate not only the functional units, but also control logic (multithreading, basically, to hold the state of two different threads)
		- beyond multithreading, CPU chips can have more complete processors or cores

### Memory
	- There is constructed as hierarcy of layers
		- Registers (1 nsec access time, with <1KB capacity)
		- Cache (2 nsec access time, with 4MB capacity)
		- Main Memory (10 nsec access time, with 1-8GB)
		- Magnetic disk (10msec access time, with 1-4 TB)
### Disks
	- data is written in a series of conecteric circles. at a given arm position, each of the heads read an annular region called **track**. all the tracks for a given arm position form a **cylinder**.
### I/O Devices
	- Devices consits of a controller(is a chip or a set of chip that physically contorls the device) and the device itself
	- the software that talks to the controller(commands and responses) is called **device driver**.
	- Drivers can be put into kernel in three ways:
		- relink the kerenl with the new driver and reboot
		- to make an enetry in OS file telling it that it needs the direr and reboot
		- OS to be able to accpet new drivers on the fly without reboot
	- the collection of all device registers forms the I/O port space
	- I/O can be done in three ways:
		- user program issues a system call. (__busy waiting method__)
		- driver starts the device and ask it to give an interrupt when it finished
		- makes use of special hardware a DMA (Direct Memory Access) chip that can control the flow of bits between memory and some controller
### Buses
	- it is the network that connects all the above components
	- Buses
		- main bus: PCIe (Peripheral Component Interconnect Express)
		- DMI (Direct Media Interface)
		- USB (Universal Serial Bus)
		- SCSI (Small Computer System Interface) 
		- PCI
### Booting the computer
	- all PC contains a parentboard(formerly called motherboard). On the parentboard is a program called BIOS. 
	- BIOS
		- contains low-level I/O software
		- it first checks to see how much RAM is installed and whether other basic devices are installed and working correctly.
		- then, it scans the PCIe and PCI buses to detect all devices attached to them.
		- BIOS determines the boot device by trying a list of devices stored in the CMOS memory
		- Then, it boots the bootable device by reading the first sector, storing into memory and executing. (the bootloader runs now) 
		- loader, then, reads OS from the active parition and starts it
		- OS queries the BIOS to get configuration information. it gets all the device drivers and loads them into the kernel. it initializes its tables, creates background process needed, and starts up GUI.

## Operating System Concepts

### Processes
	- it is a program in execution
	- it is a container that holds all the information needed to run a program.
	- process table where all the information about each process other than the contents of its own address space
### Address Spaces
	- holds the executing programs
	- a set of address each process uses, typically running from 0 to some maximum
	- Issues to consider
		- when keeping multiple programs in memory, how do one keep them from interfering with one another
		- in management of the address space of the processes, what happens when a process has more address space than the computer provides? (virtual memory)
### Files
	- an abstraction over disks and other I/O devices 
	- device independet clean abstraction model
	- they are organized as trees
	- **directory** is a way of grouping files together
	- at every instant, each process has a current working directory
	- **pipe** is a sort of psuedofile that can be used to connect two processes

### Input/Output
### Protection
### The shell












