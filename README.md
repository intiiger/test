## RelSim: Framework for System-Level Lifetime Reliability Modeling
Developed by Suan Jung, Yebin Chon, Jeongmin Hwang, and William J. Song\
Intelligent Computing Systems Lab, Yonsei University\
Current release: private development in progress (Feb. 2022)

## Introduction
RelSim is a software framework for evaluating the lifetime relablity of heterogeneous processors. Architectural heterogeneity has been advocated as a design strategy to enhance performance and energy efficiency. With various types of processing units (PUs) in a system, a workload is executed using multiple heterogeneous PUs. However, heterogeneous designs raise lifetime reliability concerns since different types of PUs have disparate roles and thus are irreplaceable. With diverse failure mechanisms and reliability distributions, it is a challenging problem to estimate system-level lifetime reliability of heterogeneous PUs that have different design specifications and undergo dissimilar stress conditions in various use-case situations. RelSim can be configured to model diverse designs of heterogeneous processors with various failure mechanisms, statistical distributions, and use-case conditions for lifetime reliability assessment. In addition, GPU acceleration is available to speed up in RelSim. 


## calibration / evaluation 
There are two steps in RelSim. First is 'calibration and the other one is 'evluation'. Calibration finds out the 

## Compile
RelSim uses g++ and nvcc to compile C++ codes to execute on CPUs and GPUs. 
Compiling with nvcc which is for both CPU and GPU codes are available with below commands. 

	$ make gpu

Or, if user's environment is with only CPU, below commands compiles with g++.

	$ make cpu

Finally, compiled output 'relsim' evaluates the lifetime of system defined by three inputs. 

## User file configuration
There are three user input files to be descripted. They are located in directory 'input' as 'model.in', 'system.in', and 'use_case.in'. Each file is filled as examplary with enough explanation. Users can easily utilize and change the values and configuration in the files. 

	* 'model.in' describes the failure types facilitating the aging of the system. 
	The parameter and distribution type should be defined to apply any failure type.
	The present description is based on JEDEC 2016, so the users can just adopt it without modification if they are without any information. 

	* 'system.in' describes the system configuration to be evluated and at which the target MTTF is defined. 
	Different type of PUs are defined respectively. 
	Users can add or subtract the PUs by the configuration of system they want to evaluate. 
	The detail explanation of the values to be defined is given in the file and also, the example of NVIDIA XAVIER is offered in the file. 
	
	* 'use_case.in' describes the use conditions at which system components actually work. 
	Multi-state use-cases can be applied. 
	The use conditions are defined respectively for PUs. 
	The detail explanation is offered in the file.

Users can easily reconfigure the system architecture or change the use conditions to evaluate by modifying those input files without compiling relsim again. 

## Download
To obtain the latest version of RelSim, use the following git command in a terminal.

	$ git clone https://github.com/yonsei-icsl/RelSim
