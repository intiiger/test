## RelSim: Framework for System-Level Lifetime Reliability Modeling
Developed by Suan Jung, Yebin Chon, Jeongmin Hwang, and William J. Song\
Intelligent Computing Systems Lab, Yonsei University\
Current release: private development in progress (Feb. 2022)

## Introduction
Architectural heterogeneity has been advocated as a design strategy to enhance performance and energy efficiency. 
With various types of processing units (PUs) in a system, a workload is executed using multiple heterogeneous PUs. 
However, heterogeneous designs raise lifetime reliability concerns since different types of PUs have disparate roles and thus are irreplaceable. 
With diverse failure mechanisms and reliability distributions, it is a challenging problem to estimate system-level lifetime reliability of heterogeneous PUs that have different design specifications and undergo dissimilar stress conditions in various use-case situations. 

RelSim is a software framework for evaluating the lifetime relablity of heterogeneous processors coping with above problems.
RelSim can be configured to model diverse designs of heterogeneous processors with various mix of failure mechanisms (e.g., electromigration, gate oxide breakdown)  statistical distributions (e.g., lognormal, Weibull),  and use-defined execution scenarios for lifetime reliability assessment. 
RelSim conducts a sizable set of Monte Carlo simulations to estimate the lifetime reliability of the heterogeneous system, and it engages graphics processing units (GPUs) to accelerate the compute-intensive statistical calculations. 
The framework is also configurable to simulate a variety of dynamic reliability management (DRM) schemes such as replacement (e.g., spare components) and k-out-of-n (e.g., graceful degradation) models.

## Compile and Run
RelSim uses g++ and nvcc to compile C++ codes to execute on CPUs and GPUs. 
Compiling with nvcc which is for both CPU and GPU codes are available with below commands. 

	$ make gpu

Or, if user's environment is with only CPU, below commands compiles with g++.

	$ make cpu

Finally, compiled output 'relsim' evaluates the lifetime of system defined by three inputs. Run command is simply exectuing relsim as below. 
	
	$ ./relsim

## User file configuration
The framework takes three sets of inputs, i) definitions of failure models, ii) system specifications, and iii) use case conditions. 
They are located in directory 'input' as 'model.in', 'system.in', and 'use_case.in'. Each file is filled as examplary with enough explanation. 
Users can easily utilize and change the values and configuration in the files. 

1. 'model.in' 

	It specifies model parameters and statistical distributions to simulate failure mechanisms which facilitate the aging of the system. The present description is based on JEDEC 2016, so the users can just adopt it without modification if they are without any information. 

2. 'system.in' 

	It describes system description at which the target MTTF is defined. It includes the number of PUs, size of heterogeneous components, as well as operating voltage, temperature, and stress time at which the targeted lifetime of a system is defined (i.e., product specifications). Different type of PUs are defined respectively. Users can add or subtract the PUs by the configuration of system they want to evaluate. The detail explanation of the values to be defined is given in the file and also, the example of NVIDIA XAVIER is offered in the file. 

3. 'use_case.in' 

	It describes operation scenarios where system components actually work. Multi-state use-cases can be applied. The use conditions are defined respectively for PUs. The detail explanation is offered in the file. 

Users can easily reconfigure the system architecture or change the use conditions to evaluate by modifying those input files without compiling relsim again. 

## Download
To obtain the latest version of RelSim, use the following git command in a terminal.

	$ git clone https://github.com/yonsei-icsl/RelSim

## Reference and Contact
Below shows the brief information of the related publication which is under preparation. 

	@article{jung_icsl2021,
    author    = {S. Jung and Y. Chon and J. Hwang and B. Kim and A. Trivedi and W. Song},
    title     = {{Computational Framework for Lifetime Reliability Assessment of Heterogeneous Computing Processors}},
    journal   = {under review},
    month     = {Feb.},
    year      = {2022},
	}

