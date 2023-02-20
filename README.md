# **STA-basic-to-advance**
# Contents 
 <div class="toc">
  <ul>
    <li><a href="#header-1">Section 1 - Lectures and labs</a></li>
	<ul>
        <li><a href="#header-1_1">STA Defination</a></li>
      </ul>
      <ul>
        <li><a href="#header-1_2">Timing Paths</a></li>
      </ul>
    	<ul>
        <li><a href="#header-1_3">Timing and path elements</a></li>
      </ul>
	<ul>
        <li><a href="#header-1_4">Setup and Hold cecks</a></li>
      </ul>
   	<ul>
        <li><a href="#header-1_5">Slack Calculation</a></li>
      </ul>
    	<ul>
        <li><a href="#header-1_6">SDC Overview</a></li>
      </ul>
    	<ul>
        <li><a href="#header-1_7">Clocks</a></li>
      </ul>
    	<ul>
        <li><a href="#header-1_8">Generated Clocks</a></li>
      </ul>
    	<ul>
        <li><a href="#header-1_9">Boundary Constrains</a></li>
      </ul>
    	<ul>
        <li><a href="#header-1_10">DAY-1 LABs-OpenSTA introduction, Input to OpenSTA, Constrain creation and OpenSTA Runcsript</a></li>
      </ul>
   </div>
  
<div class="toc">
  <ul>
    <li><a href="#header-2">Section 2 -Lactures and Labs </a></li>
	<ul>
        <li><a href="#header-2_1"> Other timming chekcs</a></li>
      </ul>
      <ul>
        <li><a href="#header-2_2">Design Rule checks</a></li>
      </ul>
	<ul>
        <li><a href="#header-2_3">Latch Timing</a></li>
      </ul>
	  <ul>
        <li><a href="#header-2_4">STA Text Report</a></li>
      </ul>
    	<ul>
        <li><a href="#header-2_5">Day-2 LABs-Liberty files, SPEF, timing reports</a></li>
      </ul>
</div>
  
  <div class="toc">
  <ul>
    <li><a href="#header-3">Section 3 -Lectures and Labs </a></li>
	<ul>
        <li><a href="#header-3_1">Multiple Clocks </a></li>
      </ul>
      <ul>
        <li><a href="#header-3_2">Timing arcs and clocks</a></li>
      </ul>
	<ul>
        <li><a href="#header-3_3">Setup and Hold Details</a></li>
      </ul>
    	<ul>
        <li><a href="#header-3_4">Setuo and Hold Details</a></li>
      </ul>
    	<ul>
        <li><a href="#header-3_5">STA Text report</a></li>
      </ul>
    	<ul>
        <li><a href="#header-4_6">Day 3 labs- Understanding full reg to red STA analysis, slack calculation and review setup check report</a></li>
      </ul>
   </div>
	  
<div class="toc">
  <ul>
    <li><a href="#header-4">section 4 - Lectures and labs </a></li>
	<ul>
        <li><a href="#header-4_1">Crosstalk and noise</a></li>
      </ul>
      <ul>
        <li><a href="#header-4_2">Operating Models and other variation</a></li>
      </ul>
	<ul>
        <li><a href="#header-4_3">Clock gating checks</a></li>
      </ul>
	  <ul>
        <li><a href="#header-4_4">Checks on Async pins</a></li>
      </ul>
    	<ul>
        <li><a href="#header-4_5">Day 4 lans- Understanding clocks gating check and async pin checks</a></li>
      </ul>
</div>
	
<div class="toc">
  <ul>
    <li><a href="#header-5">section 5 -lactures and labs</a></li>
	<ul>
        <li><a href="#header-5_1">clock groups</a></li>
      </ul>
      <ul>
        <li><a href="#header-5_2">Clock propertires</a></li>
      </ul>
	<ul>
        <li><a href="#header-5_3">Timing exceptions</a></li>
      </ul>
    	<ul>
        <li><a href="#header-5_4">Multiple models</a></li>
      </ul>
    	<ul>
        <li><a href="#header-5_5">Day 5 lab-Revisit slack computation, understand CRPR and ECO insertion</a></li>
      </ul>
</div>

<div class="toc">
  <ul>
    <li><a href="#header-6">References</a></li>
  </ul>
</div>

<div class="toc">
  <ul>
    <li><a href="#header-7">Acknowledgement</a></li>
  </ul>
</div>

# <h1 id="header-1">Section 1- Lactures and labs </h1>	 
## <h1 id="header-1_1"> STA defination</h1>
The full form of STA is static timing analysis.
	
STA is a method of verifying timing performance of a design. we can do the same analysis using other methods like,
	<ul>
		<li><a>simulation</a></li>
	</ul>
	<ul>
		<li><a>SPICE simulation</a></li>
	</ul>
but now a days it is not exist.
	
Now, let us see the features of STA.
### STA features
<ul>
		<li><a>Static</a></li>
	</ul>	
It is static in nature. it does not run dynamically. it does not run on the test benches. Because of the static nature, STA is fast and has a larg capacity. It collapse whole design into minimal cycle and analyze once.
	
<ul>
		<li><a>Exhaustive</a></li>
	</ul>
it is exhaustive. it's use mathematical techhniques instead of input vectors.so, it's required riming checks are performed on all possible paths and scenarios.
<ul>
		<li><a>Functionality</a></li>
	</ul>	
It does not verify the logic functionality of design. for that we need to equivalance checking on that side.
<ul>
		<li><a>Conservative</a></li>
	</ul>
it is conservative in nature and be pasimastic in many cases to ensure there is enough gaurd band for the design timing requirment.
	
	
STA works only for the synchonous designs only. it does not verify asynchronous part of the design.
	
### Inputs to STA
<ul>
		<li><a>Netlist</a></li>
	</ul>
contais the design information.
<ul>
		<li><a>SDC or Constrain file</a></li>
	</ul>
It comtains all information about what you want the time.
<ul>
		<li><a>Logic Libraries</a></li>
	</ul>
It contains all the information about delays of logic cells and tansition time of those cells.

## <h1 id="header-1_2"> Timing Paths</h1>
STA breaks the paths at
<ul>
		<li><a>Ports</a></li>
	</ul>

<ul>
		<li><a>Sequencial elements</a></li>
	</ul>
	
<img width="317" alt="image" src="https://user-images.githubusercontent.com/123488595/219953189-9426e854-43c6-449e-85f6-55026da4ae11.png">

Here, in this circuit, "IN","OUT" and "CLK" are ports and flops are sequencial logics.

In this circuits, there are four paths available. in which path 1 is, port to port path. path 2 is, port to sequential element path. similarly other 2 paths also.
	
## <h1 id="header-1_3">Timing path elements</h1>
Now, let's understand the components of timing path. The components are:
<ul>
		<li><a>Startpoint</a></li>
	</ul>
Start point is where data is launched by clock or where data must be available at specific time. Mostly the input ports or register clock pins are start point.
	
<img width="318" alt="image" src="https://user-images.githubusercontent.com/123488595/219954246-3689c8ec-c1d5-46c9-8d8d-5904d422a542.png">

	
In this circuit, for Path 1, start point is "IN" port. for path 2 also, start point is "IN" port. In path 3, start point is clock pin. similarly, for the path 4 also, start point is clock pin.
<ul>
		<li><a>Endpoint</a></li>
	</ul>
Endpoints are where data is captured by clock edge or where the data must be available ar a specific time. Usually output port or register data pins are endpoints.
	
<img width="307" alt="image" src="https://user-images.githubusercontent.com/123488595/219954306-d37cd016-f386-453c-a4b4-8eb1f284fc65.png">

Here, for path 2, the endpoint is the data pin of flop and for path 1, the endpoint is the "OUT" pin.
<ul>
		<li><a>Combinational logic</a></li>
	</ul>
Combinational logic is an elements that have no memory or internal state. for example, in above circuit is logic a is like given below,
<img width="269" alt="image" src="https://user-images.githubusercontent.com/123488595/219954588-83470332-076e-4135-b7e2-c2b81210fdf1.png">

But the point for the notice is that in combinational logic also, that can be more than one paths may be available.
	
## <h1 id="header-1_4">Setup and Hold checks </h1>
### Setup check
Setup check means the data should be available at the input of sequencial decvice , sometime before clock edge that capture the data. This enforces max delay on the data path.
	
Setup  time of a flop is dependent on the technology node and value is available in the logic libraries. let's understand this by using some waveform,
<img width="233" alt="image" src="https://user-images.githubusercontent.com/123488595/219955311-d1cb6711-8911-4909-beaf-42abe1e6b47f.png">
 	
### Hold check
Hold check means, data should at the input of sequential device for sometime after the clock edge that captures the data. This enforce min delay on the data path. let's understand this by using some waveform,
<img width="230" alt="image" src="https://user-images.githubusercontent.com/123488595/219955569-ada60bf2-c92d-440c-9077-2420c59e7053.png">

## <h1 id="header-1_5">Slack Calculation </h1>
Setup Slack = (Data required time) - (Data arrival time)
<ul>
		<li><a>Data arrival time</a></li>
	</ul>
It is time taken by the signal to travel from startpoint to endpoint.
<img width="265" alt="image" src="https://user-images.githubusercontent.com/123488595/219955805-9e568e76-ca56-46d6-96ca-baf8e142e47c.png">

One endpoint have multiple arrival times with respect to start point.
<img width="253" alt="image" src="https://user-images.githubusercontent.com/123488595/219955885-b3b12679-b996-49cf-8a1e-ee684027821f.png">
<ul>
		<li><a>Data required time</a></li>
	</ul>
It is the time before what the signal should be arrived.
<img width="252" alt="image" src="https://user-images.githubusercontent.com/123488595/219955986-a853c890-7776-4315-83c2-2a38f69fec6d.png">

<ul>
		<li><a>Slack</a></li>
	</ul>
Slack is the difference between the required time and arrival time. If slack is positive then data arrives earlier then requied time. 
	
<img width="278" alt="image" src="https://user-images.githubusercontent.com/123488595/219956169-c3b17b79-aa30-4839-ad15-0bdb506f59d5.png">

If slack is nagative then data arrives latter then required time. so we have to fix this problem.
	
<img width="271" alt="image" src="https://user-images.githubusercontent.com/123488595/219956271-dbe0fa4a-9974-431f-b631-3fd5456dc56b.png">

## <h1 id="header-1_6"> SDC overview</h1>
SDC comands are set of comands which are provided to the STA tools as a input to do timing analysis. The first set of comands are constrains fot timing. these specify the parameters affecting the frequency of the design. examples of these comands are,
<ul>
		<li><a>creat_clock</a></li>
	</ul>
<ul>
		<li><a>creat_generated_clock</a></li>
	</ul>
<ul>
		<li><a>set_clock_groups</a></li>
	</ul>
<ul>
		<li><a>set_clock_transition</a></li>
	</ul>
<ul>
		<li><a>set_timing_derate</a></li>
	</ul>
	
The constrains for defining the area and power specify restriction about the area and power. for example,
<ul>
		<li><a>set_max_area</a></li>
	</ul>
<ul>
		<li><a>set_max_dynamic_power</a></li>
	</ul>

Constrains for design rules is requirements for the target technology. for example,
<ul>
		<li><a>set_max_capacitance</a></li>
	</ul>
<ul>
		<li><a>set_min_capacitance</a></li>
	</ul>
<ul>
		<li><a>set_max_transition</a></li>
	</ul>
<ul>
		<li><a>set_max_fanout</a></li>
	</ul>
Constraines for interfaces are assumptions on the design boundary. for example,
<ul>
		<li><a>set_driving_cell</a></li>
	</ul>
<ul>
		<li><a>set_input_delay</a></li>
	</ul>
<ul>
		<li><a>set_output_delay</a></li>
	</ul>
<ul>
		<li><a>set_load</a></li>
	</ul>

Constraines for specific modes and configuration are assumptions on the value allowed. for example,
<ul>
		<li><a>set_case_analysis</a></li>
	</ul>
<ul>
		<li><a>set_logic_dc</a></li>
	</ul>
<ul>
		<li><a>set_logic_one</a></li>
	</ul>
<ul>
		<li><a>set_logic_zero</a></li>
	</ul>
some exceptional to design constrain. these are relax the requirement set by other commands or default STA tool analysis. for example,
<ul>
		<li><a>set_false_path</a></li>
	</ul>
<ul>
		<li><a>set_multiple_path</a></li>
	</ul>
<ul>
		<li><a>set_max_delay</a></li>
	</ul>
<ul>
		<li><a>set_min_delay</a></li>
	</ul>
<ul>
		<li><a>set_disable_timing</a></li>
	</ul>

## <h1 id="header-1_7"> clocks</h1>
Clocls ate specified using the command "create_clock". create_clock specifies the primary source, tipically on PLL or on other input port of design. It specifies the time period, information about waveform like rise and fall instant, rise and fall amplitude. Then we attached the clock to certain design like in below example, clock ois created on the "ck" port and this will met "C1". in addition to that there is a name of the clock also mentioned there.

<img width="282" alt="image" src="https://user-images.githubusercontent.com/123488595/220032938-9d4d4213-d201-4c91-be7f-807fc7434469.png">

we can have more then two values on the waveform like given below,
<img width="227" alt="image" src="https://user-images.githubusercontent.com/123488595/220033130-2e83106c-3e9e-4d0d-b797-58d210d1dced.png">

but in this case we have to define the full clock period here. if we not define the waveform and just mention the time period at that time automatically it will take 50% duty cycle.

<img width="195" alt="image" src="https://user-images.githubusercontent.com/123488595/220033641-a23916ef-ae7f-49bc-bbcd-f37fc1184d4c.png">

We can have one more option to use two clocks C1 and C2 of two different time period by using MUX by "create_clock_add switch" command. Here MUX will behaves like switch. By using this we can define two clocks at same port and use anyone according to our use.  

<img width="249" alt="image" src="https://user-images.githubusercontent.com/123488595/220034337-1445f20f-9da9-4171-bc1c-13e7b75456e1.png">

## <h1 id="header-1_8"> Generated Clocks</h1>
Generated clocks are the clocks which are define inside the design. Tipically devided version of parent clock or multiple version of parent clock. The command for that is "create_generated_clock_(devide or multiplied by number)-(source from where this clock is created)-(name of the parant clock)". for example,

<img width="212" alt="image" src="https://user-images.githubusercontent.com/123488595/220056562-5363368d-baf5-4f65-a39d-37e1bfbdf721.png">


<img width="223" alt="image" src="https://user-images.githubusercontent.com/123488595/220056301-609b8529-e46d-4816-a198-137115312059.png">

Instead of devide and multiple, we can give command as per rise and fall time of parant clock waveform. for example,
	
<img width="209" alt="image" src="https://user-images.githubusercontent.com/123488595/220056904-50d9319a-42ad-42d6-89ea-d68443f9ef50.png">

In additional to edge, we can add edge shift. when we use edge shift, we have to use edge with it. for example,
	
<img width="236" alt="image" src="https://user-images.githubusercontent.com/123488595/220057628-10ba117b-2984-4f48-b2bf-10a005803975.png">

Generated clock have multiple paths from master clock to the generated clock. But the worst path is sequential path even when we do setup and max and min delay for do timing analysis. The right path for timing analysis is combinational path.
	
<img width="224" alt="image" src="https://user-images.githubusercontent.com/123488595/220059941-37a03266-45f1-41aa-8c93-4dc12ea2831c.png">

## <h1 id="header-1_9">Boundary Constraints</h1>
Port delays can be defined by using these commands,
<ul>
		<li><a>set_input_delay</a></li>
	</ul>
<ul>
		<li><a>set_output_delay</a></li>
	</ul>
These input and output delays are defines the delays of input and output, outside of the logic cell.
If we have more than one delay on the same port then we have to use the command "_add_delay" aftet thrr setting the clock.
	
### Additional boundary constraints
What is the transition on the input, that how fast or how slow input is rising, this can be specified by given below multiple methods:

<img width="248" alt="image" src="https://user-images.githubusercontent.com/123488595/220091702-850389da-6208-4cf3-a86f-7ba1b2e459b8.png">

In the first method of "set_drive" command, we have to specify the drive which is nothing but we specify the resistance value. based onn that we can calculate, how fast the rising and falling of input occures by STA tool.

In the second method of "set_driving_cell" command, we specified the cell of driving port. based on the cell, the libray will be checked and according to the library, the delay can be calculated by STA tool.
	
In the third method of "set_input_transition", we cann directly set the specific transition time value.
	
On the output side also, we have to know the specific value of the load.this can be specified by multiple methods like given below,

<img width="370" alt="image" src="https://user-images.githubusercontent.com/123488595/220094599-466edd80-1e5e-4331-b28c-36e2ff8bb9a3.png">

Now we have both commands like, "set_input_transition" and "set_clock_transition". so, if CTS is not run the we have to use "set_clock_transition" command. and if CTS is  run then we just need to give "set_input_transition" command, and tool will automatically calculate other values and use it.
	
## <h1 id="header-1_10">DAY-1 labs</h1>
### OpenSTA introduction
OpenSTA is a gate level static timing verifier. As a stand-alone executable it can be used to verify the timing of a design using standard file formats.
<ul>
		<li><a>Verilog netlist</a></li>
	</ul>
<ul>
		<li><a>Liberty library</a></li>
	</ul>
<ul>
		<li><a>SDC timing constraints</a></li>
	</ul>
<ul>
		<li><a>SDF delay annotation</a></li>
	</ul>
<ul>
		<li><a>SPEF parasitics</a></li>
	</ul>
OpenSTA is architected to be easily bolted on to other tools as a timing engine. By using a network adapter, OpenSTA can access the host netlist data structures without duplicating them.
	
Query based incremental update of delays, arrival and required times, it will calculate.
	
### Basics of OpenSTA
It is basically timing analysis tool. it takes the design, standard cell, constraints as input and perform timing checks on the design.
	
It will done the analysis of,
<ul>
		<li><a>Report timing checks -from, -through, -to, multiple paths to endpoint </a></li>
	</ul>
<ul>
		<li><a>Report delay calculation</a></li>
	</ul>
<ul>
		<li><a>Check timing setup</a></li>
	</ul>
	
### Inputs to OpenSTA
we have to give Design as an input to the OpenSTA tool.The design will be in form of Netlist format. 

Usually provided in Verilog using read_verilog command.

#### Steps to do are:
<ul>
		<li><a>cd to lab1 directory using following unix command “cd lab1</a></li>
	</ul>
<ul>
		<li><a>Type “ls” and you will notice one of the file named “simple.v</a></li>
	</ul>
<ul>
		<li><a>simple.v is our design in Verilog format</a></li>
	</ul>
<ul>
		<li><a>Open file using “leafpad simple.v”. </a></li>
	</ul>
you would see the following, these are standard cells or lib cells instantiations

<img width="387" alt="image" src="https://user-images.githubusercontent.com/123488595/220131617-352f20af-744d-457f-ae3c-ff7679f635cd.png">

Now standerd cells are provided in ".lib" format using read_liberty command.

The typical cell view will have:
<ul>
		<li><a>Input ports definitions</a></li>
	</ul>
<ul>
		<li><a>Output port definitions</a></li>
	</ul>
<ul>
		<li><a>Functionality of the cells</a></li>
	</ul>
<ul>
		<li><a>Input to Output relationship</a></li>
	</ul>
	
Next step is Type “ls ..” and you will notice one of the file named “sky130_fd_sc_hd_tt_025C_1v80.lib”

This is our library cell information in .lib (liberty format)

Open file using “leafpad sky130_fd_sc_hd_tt_025C_1v80.lib”. 

Now, Look for “sky130_fd_sc_hd__nand2_1” in this file, Notice this is the cell which was instantiated in our Verilog design.Find out what are the input and output pins of this cel

Now timing constraints are provided in SDC format using "read_sdc" command.
	
### Constraints Creation - defining clocks
As we seen in the theory, Clocks are defined using create_clock command.
	
Lets define a clock with period 50 on port tau2015_clk. command for this is,

<img width="320" alt="image" src="https://user-images.githubusercontent.com/123488595/220133646-a3f953ab-42f6-454b-8643-fd8339b38dee.png">

Now, setting the input and output delays in the primary port which are associated with clock "tau2015_clk".  command for this is,
	
<img width="329" alt="image" src="https://user-images.githubusercontent.com/123488595/220134036-0538b9ba-bfef-4209-99d8-c769a809d3d5.png">

Now, Input transitions by environmental factors are defined. command for this is,

<img width="280" alt="image" src="https://user-images.githubusercontent.com/123488595/220134415-6d030ae0-bf2c-4fe7-9dde-d885842e9803.png">

Now, capacitive load on output pin is defined by this command,

<img width="188" alt="image" src="https://user-images.githubusercontent.com/123488595/220134670-da74af71-626d-4b02-bb4f-9687742058f8.png">

Now, Type “ls” and you will notice one of the file named “simple.sdc”. simple.sdc is our constraint file. 
	
Open file using “leafpad simple.sdc”.
	
### runScript

In runscript you can define all the commands you want to run in the openSTA tool. Tool will execute each command sequentially in order. There are some commands which are executed in parallel in some cases.Runscript is in tcl format.
	
Now, Type “ls” and you will notice one of the file named “run.tcl”. After opening this file in leafpade by "leafpade run.tcl", we can see the leafpade like this,

<img width="329" alt="image" src="https://user-images.githubusercontent.com/123488595/220135466-831f21fd-c645-49d6-84be-d611973c20ef.png">

### Run OpenSTA
Run openSTA using command “sta run.tcl -exit | tee run.log".
	

# <h2 id="header-2">Section 2- Lactures and labs </h2>	 
## <h2 id="header-2_1">Other timing checks</h2>
