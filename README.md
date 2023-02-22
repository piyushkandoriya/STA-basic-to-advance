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
        <li><a href="#header-3_5">Day 3 labs- Understanding full reg to red STA analysis, slack calculation and review setup check report</a></li>
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
now we can see the the verilog file in the leafpad,

<img width="960" alt="image" src="https://user-images.githubusercontent.com/123488595/220688279-c1000ea4-41aa-40b6-854c-3c58d4f0a681.png">

These are standard cells or lib cells instantiations

<img width="960" alt="image" src="https://user-images.githubusercontent.com/123488595/220688881-26f9694f-7e81-4264-a85e-4fed4287da80.png">

Now standerd cells are provided in ".lib" format using "read_liberty" command.

The typical cell view have:
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

Now, Looking for “sky130_fd_sc_hd__nand2_1” in this file, Notice this is the cell which was instantiated in our Verilog design.
	
<img width="960" alt="image" src="https://user-images.githubusercontent.com/123488595/220697257-afff336e-d6db-43a3-95e5-e6a8d489016d.png">

here Pin "B" and Pin "Y" are the input and output pins of this cell.

<img width="960" alt="image" src="https://user-images.githubusercontent.com/123488595/220697732-c8d34b41-7a8d-4e88-b4cf-eafa6cafb09a.png">

<img width="956" alt="image" src="https://user-images.githubusercontent.com/123488595/220697907-444a5b9a-1632-4258-b779-8a2618a0aa64.png">

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

<img width="960" alt="image" src="https://user-images.githubusercontent.com/123488595/220702969-8e50c8c4-3d42-4d4e-89c8-7fdd453e17da.png">
<img width="959" alt="image" src="https://user-images.githubusercontent.com/123488595/220703944-9c46a1c5-e92d-4d01-b210-4ab6bcef5457.png">

	
### runScript

In runscript you can define all the commands you want to run in the openSTA tool. Tool will execute each command sequentially in order. There are some commands which are executed in parallel in some cases.Runscript is in tcl format.
	
Now, Type “ls” and you will notice one of the file named “run.tcl”. After opening this file in leafpade by "leafpade run.tcl", we can see the leafpade like this,

<img width="960" alt="image" src="https://user-images.githubusercontent.com/123488595/220705985-2f1aa9ac-e597-4d25-be9a-cd66f689f9ac.png">


### Run OpenSTA
Run openSTA using command “sta run.tcl -exit | tee run.log".

Here STA, devides this design into two parts.
	
First part is "F1" to "OUT"(noticed form start point and endpoint):
<img width="959" alt="image" src="https://user-images.githubusercontent.com/123488595/220708503-8d5f9972-7bbc-4df2-a89c-95e89fccafe9.png">
Here "Path type: MAX" means thr setup analysis.

Second part is "inp1" to "F1".(noticed form start point and endpoint)

<img width="960" alt="image" src="https://user-images.githubusercontent.com/123488595/220709615-cca738a2-9690-4781-a51b-7945e25afd81.png">


# <h2 id="header-2">Section 2- Lactures and labs </h2>	 
## <h2 id="header-2_1">Other timing checks</h2>
Till now we discussed about set up and hold check but there are other timing also ckeck in STA. like,
<ul>
		<li><a>Clock gating check</a></li>
	</ul>
This check is done on "Enable pin" with respect to "clock gating pin". results from this checks will edited in constraint file or present in the logical library.
<ul>
		<li><a>Async pin checks</a></li>
	</ul>
This ckeck is done on reset pin, clear pin and all set pin etc.here also minimum requirements is present in logical library.
<ul>
		<li><a>Data to Data check</a></li>
	</ul>
This check is done between two data pins to check data comes are required time or what? this data ckecks values specifies some constraints or global constraints.
	
Note: Setup and hold timing data is stored in logical library as per the require ment.

## <h2 id="header-2_2">DRC (Design rule check)</h2>
Otherthen timing rule check, STA also done design rule check.
<ul>
		<li><a>Slew/transition Analysis</a></li>
	</ul>
There are two types of slew. (1)Rise slew (2)Fell slew.

Rise slew is time taken by the signal to rise from 30% of Vdd to 70% of Vdd.
	
Similarely, Fall slew is time taken by the signal to fall from 70% of Vdd to 30% of Vdd.

<img width="164" alt="image" src="https://user-images.githubusercontent.com/123488595/220366161-47631a43-7eb6-4ea4-b6c0-527f85d7dba5.png">

In STA, there is always specific constraint for that maximum and minimum value of slew value is available. so, STA can check this transition time value through out the process that this slew values are maintains or not.

<ul>
		<li><a>Load Analysis</a></li>
	</ul>
In this we specifies basically the what maximum and minimum capacitance is on the port and nets. similarlly fanout load onn ports and nets also specify here.
<ul>
		<li><a>Clock Skew Analysis</a></li>
	</ul>
Slew and skew are teo different things. slew is transiton time which was required by signal for rise and fall. where skew is difference in delay of the clocks at different points.

There are two types of skews: 

(1)+ve skew
	
<img width="167" alt="image" src="https://user-images.githubusercontent.com/123488595/220370133-b68aac7b-a9fe-4877-8027-a02ffbbcfc50.png">

(2)-ve skew
	
<img width="163" alt="image" src="https://user-images.githubusercontent.com/123488595/220370296-6fa58ab4-9927-4f12-822f-a2ff6ad6a42c.png">

<ul>
		<li><a>Pulse width check</a></li>
	</ul>
<img width="182" alt="image" src="https://user-images.githubusercontent.com/123488595/220370473-d79f0c12-8c81-46f4-9061-e7f3961f33b1.png">

## <h2 id="header-2_3">Latch timing</h2>
In a flop based design, the data is captured and launched on the edges of clocks.
   
<img width="196" alt="image" src="https://user-images.githubusercontent.com/123488595/220406591-7d648200-b728-4297-a731-3ed62ef2b8f3.png">

Here if logic delay is less or more, doesn't metters. we have to complete this process between this one time period. so, there is no flexibility in this flop based design.                                         
	
Latches are not edge based triggered. latches are level trigger. it means latches can capture and launch the data during whole pulse. during this period, behavior of latch is transparent. it behaves like buffer.
	
<img width="164" alt="image" src="https://user-images.githubusercontent.com/123488595/220411549-2e3dec12-f4e8-48df-a022-7c4cedae4d5a.png">

so, latches will provide more flexibility than flops.
	
## <h2 id="header-2_4">STA text report</h2>
let's understand, how STA reports setup and holds check with given example.
	
<img width="239" alt="image" src="https://user-images.githubusercontent.com/123488595/220412963-9786eb78-d493-49e5-b8f0-a72258c1f6d0.png">

As we can see in the figure, STA convert the whole design in nodes and arcs.
there is an example of STA analysis timing report,

<img width="434" alt="image" src="https://user-images.githubusercontent.com/123488595/220413542-3732edb3-0592-42af-958b-477f4ad9c1a0.png">

Before clock tree build, STA use constraint value for calculation and after clock tree is builded, STA use actual value of delay for calculation which is called propogation delay. Here in the bottom, we can see the final slack. if it is positive then we met the timing and if it is nagative then it is violating the timing.

## <h2 id="header-2_5">DAY-2 labs</h2>
### Liberty File
The ".lib" file is an ASCII representation of the timing and power 
parameters associated with any cell in a particular semiconductor 
technology. it comtains timing models and data to calculate like,
<ul>
		<li><a>I/O delay paths</a></li>
	</ul>
<ul>
		<li><a>Timing check values</a></li>
	</ul>
<ul>
		<li><a>Interconnect delays</a></li>
	</ul>

### understanding liberty file

<img width="315" alt="image" src="https://user-images.githubusercontent.com/123488595/220416586-a3253867-4b23-4778-86a6-d1593dfbcd3d.png">

#### Liberty file Cell part
<img width="371" alt="image" src="https://user-images.githubusercontent.com/123488595/220417041-18416979-9557-4719-b8f6-f4ad8185ce70.png">

#### Liberty file pin part
<img width="364" alt="image" src="https://user-images.githubusercontent.com/123488595/220417398-2d928a28-060a-4135-8193-a09f2a5a1145.png">

#### Understanding LIB parsing

Command for reading the liberty file is "read_liberty".
Some argument data for STA,

<img width="262" alt="image" src="https://user-images.githubusercontent.com/123488595/220417823-0bd57424-ff13-4524-81f0-14451cf069e6.png">

By default take, filename for both options if none are given.
	
Then type "cd lab2" and then type "ls". 
Here we can see 2 lib files with the following names
	
<ul>
		<li><a>simple_min.lib</a></li>
	</ul>
we can Open this file using 'leafpade simple_min.lib" command.
<ul>
		<li><a>simple_max.lib</a></li>
	</ul>	
we can Open this file using 'leafpade simple_max.lib" command.	

### Exercises
Q.1) Find all cells in simplex_max.lib
	
To find the number of cells in simple_max file use this command (more simple_max.lib | grep -c "End cell")

<img width="974" alt="image" src="https://user-images.githubusercontent.com/123488595/220721384-2231b332-8291-449e-89bc-8c966b0357db.png">

here we can see that the total number of cells are 211.
	
To list out all the cells in a liberty in all cell file, use this command (more simple_max.lib | grep  "End cell")
	
<img width="960" alt="image" src="https://user-images.githubusercontent.com/123488595/220721664-24df91eb-4cc1-413c-8b50-73e180a8e126.png">

Here we can see the list of 211 cells.

Q.2) Find all the pins of cell NAND2_x1 in simple_max.lib file.
Here we found 1 output pin "o" and 2 input pin "a" & "b" in NAND2_X1 cell.
	
<img width="960" alt="image" src="https://user-images.githubusercontent.com/123488595/220722819-072a30d2-ade6-44de-86ce-179e17dce8b1.png">

<img width="1015" alt="image" src="https://user-images.githubusercontent.com/123488595/220723515-fb276791-c680-4aa9-a25d-cb83a5d9e193.png">

Q.3) What is the difference between  NAND2_X1 and NAND3_X1? 
	
NAND2_X1 is 2 input NAND gate and NAND3_X1 is 3 input NAND gate. with that capacitance is also different in these.
	
<img width="356" alt="image" src="https://user-images.githubusercontent.com/123488595/220724759-7d1f9f72-27af-4adb-b0cf-a819763511e4.png">
	
<img width="445" alt="image" src="https://user-images.githubusercontent.com/123488595/220724953-e93c7b07-a8c2-4b6f-9577-bff0abe5621b.png">

Q.4) What is the difference between simple_max.lib and simple_min.lib file.
I compared the file and found they have differnet values in cell_ fall, fall_transition, cell_rise and rise_transitionof all the cells.
	
Variations in the fabrication process could could either increase or decrease the delay pf cells. Timing analysis must take into account the min and max values of delay in liberty files. These libraries will be used by the STA tool for analysis.
	
These respresent the table which are calculated based on several equations and tells about paramenter like have different slope of rise and fall time delay, etc.
	
It specify PVT variation in max and min conditions.

<img width="960" alt="image" src="https://user-images.githubusercontent.com/123488595/220725906-40ee3624-bfea-437a-b48f-e0ba484de648.png">

<img width="960" alt="image" src="https://user-images.githubusercontent.com/123488595/220726526-8a5ec9b5-1f99-46e1-9de0-8138f1429a0a.png">

### SPEF File
Full form of SPEF file is "Standard Parasitic Exchange Format file". this SPEF file describes parasitic information of the design. we (users) can not create this file manually. it can generate automatically by STA tool.It is mainly used to pass parasitic information from one tool to another.
	
#### General syntax
A Typical SPEF File has 4 main sections as listed below,
<ul>
		<li><a>Header</a></li>
	</ul>
<ul>
		<li><a>Name map</a></li>
	</ul>
<ul>
		<li><a>Top level ports</a></li>
	</ul>
<ul>
		<li><a>Parasitic description</a></li>
	</ul>
	
#### Understanding SPEF parsing
Command for read SPEF parsing is "read_spef".

<img width="960" alt="image" src="https://user-images.githubusercontent.com/123488595/220729310-3fb2055d-ab53-42be-89d0-96552b852aa1.png">

Verilog file for the design,
	
<img width="960" alt="image" src="https://user-images.githubusercontent.com/123488595/220729998-a1bfde8c-095a-461c-b6bc-248dad91db69.png">

Circuit diagram according to the verilog file,
	
<img width="273" alt="image" src="https://user-images.githubusercontent.com/123488595/220731522-95d17c43-af69-4912-87df-803a82e165b4.png">

#### Reporting time
To do report timing on design, "report_checks" command is use.so, add following command in run.tcl.  so command will be like this,
	
<ul>
		<li><a>report_timing –num_paths 5</a></li>
	</ul>
the do rerun of STA by this command,
<ul>
		<li><a>sta run.tcl –exit | tee run.log</a></li>
	</ul>
then open the file in leafpade by
<ul>
		<li><a>leafpad run.log</a></li>
	</ul>

<img width="959" alt="image" src="https://user-images.githubusercontent.com/123488595/220732731-e6edd3ff-23ee-4c28-b906-88aece0cf5d3.png">

	
#### Understanding of timing report

<img width="317" alt="image" src="https://user-images.githubusercontent.com/123488595/220422372-9e12ae84-0ab0-4b83-88b4-b9711b004de1.png">


# <h3 id="header-3">Section 3- Lactures and labs </h2>	 
## <h3 id="header-3_1">Multiple clocks</h2>
Till now we have seen the setup and hold timing analysis for single clock. now wwe are going to discuss about more than one clocls with different frequencies are available for analysis.
	
When different frequency of clocks are present, the setup check is calculated or the most restrictive setup is identify by first expanding the clock to a comman base period.
	
<img width="206" alt="image" src="https://user-images.githubusercontent.com/123488595/220536788-4362a99b-46d4-4dce-932a-0fa9cf98c717.png">

<img width="205" alt="image" src="https://user-images.githubusercontent.com/123488595/220537089-8fca73e9-2c87-4272-b311-8f618970ff99.png">

Now, other example we are going to use to explaine the hold check,
	
<img width="249" alt="image" src="https://user-images.githubusercontent.com/123488595/220537372-5d32cdaa-37ca-465e-bab9-893f81e96a6b.png">

Rule (1):Data launched by setup launch edge must not be captured by previous capture edge.

Rule (2):Data launched next launch edge must not be captured by setup capture edge.

<img width="209" alt="image" src="https://user-images.githubusercontent.com/123488595/220537674-5328c222-7bd8-4dee-88fe-4a66a783bb3e.png">

## <h3 id="header-3_2">Timing arcs and timing sense</h2>
There are two types of timing arcs:
<ul>
		<li><a>Cell arcs</a></li>
	</ul>
cell arcs are nothing but input to the output network connections.this arcs have rise and fall time.it is basically present in logical library and they have input/output functionality and delays details.
<ul>
		<li><a>Net arcs</a></li>
	</ul>
Net arcs is the arcs which connect one cell to  another cell. same as above it is also have rise and fall time with delay details in logical library.

<img width="163" alt="image" src="https://user-images.githubusercontent.com/123488595/220539455-ef9fbf07-ec67-4a36-9607-63db47eb4efd.png">

#### combinational arcs
combinational arc is arcs which don't involve any state element.

<img width="174" alt="image" src="https://user-images.githubusercontent.com/123488595/220539886-825beb63-ebf4-4ed5-bcd7-d2838123a187.png">

#### sequential arcs
Sequential arcs are the arcs which are typically related to clock, setup and hold check, reset, every thing.

<img width="122" alt="image" src="https://user-images.githubusercontent.com/123488595/220540279-a3794d5e-8b73-466a-b127-810d4e4fa58d.png">

#### sense of the arc
Meaning of the sense of the arc is, it is impportant to figurout when the input changes wheather output is changing in the same direction or not.
	
If output follows the input then it is called positive unit arc.
	
<img width="260" alt="image" src="https://user-images.githubusercontent.com/123488595/220540797-611b1f5a-ee2b-4bdb-8d56-58b603fc5d67.png">

If output oppose the input then it is called nagetive unit arc.

<img width="212" alt="image" src="https://user-images.githubusercontent.com/123488595/220541078-e59106c3-0de2-4a4f-8275-48ffa95ce7be.png">

when it is not able to predict that output follows the input at that time it is called non unit arcs.

<img width="262" alt="image" src="https://user-images.githubusercontent.com/123488595/220541388-bfecfa03-22ab-4e24-8247-1d2d2282f6f8.png">

## <h3 id="header-3_3">Cell delays and clock network</h2>
### Cell delays	
When cells are present, at that time arcs are present and the cell arcs have the delays. Typically the delay is calculated is the function of input transition time, output load or capacitance.

<img width="159" alt="image" src="https://user-images.githubusercontent.com/123488595/220542305-6d6ee21c-359c-4bb2-93e0-aef6ddcc383c.png">

### clock network
when clock is present in the design, clock also have network which contains the buffer, inverter and this whole network is called clock network.

<img width="176" alt="image" src="https://user-images.githubusercontent.com/123488595/220542820-3f11ea10-3aa8-466e-9f25-bdfdb9a66206.png">

If capture time skew is high then launch time skew then it will make little bit easier the setup check.
	
If design is done such a way that nagetive skew will occurs, at that time it is little bit esiar for hold check.

<img width="206" alt="image" src="https://user-images.githubusercontent.com/123488595/220543748-3640810b-7f75-49f4-a9ca-27dc0f74bd68.png">
	
### Source latency and Network laency
<img width="192" alt="image" src="https://user-images.githubusercontent.com/123488595/220544057-f6428ce8-6d1d-444b-bd18-6d547f8441ce.png">

### Jitter
<img width="145" alt="image" src="https://user-images.githubusercontent.com/123488595/220544207-570db3d7-5561-4d64-a756-ca4d89971793.png">

## <h3 id="header-3_4">Setup and Hold Detailed</h2>
### Setup check revisited
Setup time says that data should be present before the clock pulse came. so setup time and other delays should be less then or equal to the total time period of the clock.
	
<img width="143" alt="image" src="https://user-images.githubusercontent.com/123488595/220544990-57b6cff4-7b15-43aa-b947-c8570c08de68.png">

### setup ckeck with clock skew
<img width="145" alt="image" src="https://user-images.githubusercontent.com/123488595/220545418-057ca00d-2c44-4279-b641-c717b465959e.png">

when clock skew is present, there is some extra delay is also added in the time period brcause the clock will come littlebit letter due to skew.

Noww if the skew is positive, then we will get additional margine to meet the setup time and if skew is nagetive then timing become more pesimistic.
	
### Setup check with clock skew and jitter
<img width="166" alt="image" src="https://user-images.githubusercontent.com/123488595/220546269-149703af-679e-4be1-abf2-2c9791ed22b4.png">

clock jitter will reduce the time period due to uncertantity.
	
### Hold check revisited
Hold check says that next setup launch change should not be the cause of current data change. it means all delays should be greater than or equal to the hold time.
	
<img width="136" alt="image" src="https://user-images.githubusercontent.com/123488595/220547526-b5a0015f-c11f-43c2-a031-fede9aa98005.png">

### Hold time with clock skew
<img width="128" alt="image" src="https://user-images.githubusercontent.com/123488595/220547782-a85455c5-fb70-4b2b-81f4-5cf5afa5ac99.png">

This clock skews are increase the hold time. so  skew time is added to the hold time.

If skew is positive then it makes the hold pasimistik and if skew is nagetive then it makes the hold optimistik.
	
### Hold time with clock skew and jitter
<img width="122" alt="image" src="https://user-images.githubusercontent.com/123488595/220548364-6878c1e2-021f-44d7-9e54-3070bd6876c7.png">

jitter will increase the hold time so jitter will be adder to the hold time.

## <h3 id="header-3_5">DAY-3 Labs</h2>

Run the lab with command "cd lab3".
### s27.v file
<img width="960" alt="image" src="https://user-images.githubusercontent.com/123488595/220737971-84d02008-6295-4a0c-9e07-0b86f1783183.png">

### s27.sdc file
<img width="960" alt="image" src="https://user-images.githubusercontent.com/123488595/220738477-b87c8393-bfa0-4f10-a900-a089645d0b31.png">

### run.tcl file
<img width="979" alt="image" src="https://user-images.githubusercontent.com/123488595/220739184-c25cfcff-ae0d-461a-b693-d1991a1ca2d6.png">

### circuit design
<img width="229" alt="image" src="https://user-images.githubusercontent.com/123488595/220550357-c8fe2576-12cd-49cf-895a-06b454b3369a.png">

By considering the above design, there are four paths are available in the design between F1 and F2.

<ul>
		<li><a>1. F1:CK→U3→U4→U6:A2→U7:A1→F2:D</a></li>
	</ul>
<ul>
		<li><a>2. F1:CK→U6→U4→U5:A1→U7:A2→F2:D</a></li>
	</ul>
<ul>
		<li><a>3. F1:CK→U6:A1→U7:A1→F2:D</a></li>
	</ul>
<ul>
		<li><a>4. F1:CK→U6→U5:A2→U7:A2→F2:D</a></li>
	</ul>

then run the STA with command "sta run.tcl -exit | tee out.txt".

Now, Type ‘leafpad out.txt’ command and the slack reported for the path is -217.323.
<img width="956" alt="image" src="https://user-images.githubusercontent.com/123488595/220739951-ab8461cd-4a99-43d8-b44f-fdd6deae5fb4.png">

### Understanding the slack computation

<img width="299" alt="image" src="https://user-images.githubusercontent.com/123488595/220551385-928cb002-28b5-425a-8064-f9fb7a23808e.png">

<img width="309" alt="image" src="https://user-images.githubusercontent.com/123488595/220551514-1017b075-f6ce-40c3-adc3-50686dfd7ee6.png">

<img width="306" alt="image" src="https://user-images.githubusercontent.com/123488595/220551668-8963960c-75dd-4b88-92e8-a20bdf70fa4e.png">

<img width="308" alt="image" src="https://user-images.githubusercontent.com/123488595/220551839-e29d9b3b-abc5-4828-8955-64a65f0f1334.png">

<img width="284" alt="image" src="https://user-images.githubusercontent.com/123488595/220551992-731f9d0c-7ce4-4668-9085-7922cf9eb0a9.png">

<img width="305" alt="image" src="https://user-images.githubusercontent.com/123488595/220552117-6bc51549-54aa-4b8d-a835-579b1cd9d1a0.png">

### Exercise 
Q.1) change the number of paths being reported to 100 and analyze each path in detail and understand.

Command for this are "report_checks -from F1/CK -endpoint_count 100" and then "sta run.tcl -exit | tee out_1.txt"

After doing that we found that the slack is reduced as compaired to the first one.

# <h4 id="header-4">Section 4- Lactures and labs </h4>	 
## <h4 id="header-4_1">Crosstalk and Noise</h4>
### Crosstalk
when there are signals or wires which are present in close proximity of eachother, the coupling capacitor is generated between them. So, because of this effect, if signal in one path (aggressor) is changes the other signal of different path (victim) will also change. because of these changes, if both the signal change in same direction then origional victim signal change faster and delay of the signal become lesser. and if both the signal change in opposite direction then origional victim signal change slower and delay of the signal become higher.
	
STA will taken in accout these delays for calculation. 
	
<img width="214" alt="image" src="https://user-images.githubusercontent.com/123488595/220586029-3ff9c3c6-a745-406e-8116-5997ddabbc9f.png">

### Noise
In some cases, the victim signal is not changing due to aggressor signal. but here also coupling capacitor is available. so, due to coupling capacitor, in victim signal, one glitch will create and this glitch is known as noise. 

<img width="276" alt="image" src="https://user-images.githubusercontent.com/123488595/220586630-d1c30f1e-a530-4cec-a044-c680576c98d4.png">

STA observe this glithces and make sure that this glitches are less than the thresold voltages.
	
## <h4 id="header-4_2">Operting modes and other variation</h4>
Chip is made by physical process and this process has global  process variation. this variations are in term of one wafer to another wafer or within the wafer two dies can have variations.
	
<img width="163" alt="image" src="https://user-images.githubusercontent.com/123488595/220587954-60e522ba-eb6b-44da-92b9-2b5415b0bd3c.png">

The cause of these variations is different manufacturing delays and different transition times. so, STA has to take this into account.
	
We can have variations within die it self. So, STA has to take this also into account.
	
<img width="167" alt="image" src="https://user-images.githubusercontent.com/123488595/220588866-19f4c37c-d032-4e95-9faf-4f5332396eb8.png">

## <h4 id="header-4_3">Clock getting checks</h4>
Clock getting checks is done when a signal can control the path of the clock at a cell. for example if we have an AND gate and in this one of the input signal is clock and other input one is enable, then clock getting check is done there.

In oreder to clock getting check to heppenes, the signal must be used as clock downstream. the meaning of this is 
<ul>
		<li><a>It should be feed a flop or latch clock pin</a></li>
	</ul>
<ul>
		<li><a>or it should feed to output port.</a></li>
	</ul>
<ul>
		<li><a>or it should feed to generated clocks</a></li>
	</ul>	
The intension of the check is to insure that the transiton on geting pin does not create any unnecessory active edge of the clock in the fanout. Let's understand that using specific cell for which clock geting check is done.
	
We will start with active high clock geting cell which is done on AND gate or NAND gate.
	
<img width="155" alt="image" src="https://user-images.githubusercontent.com/123488595/220592069-84888187-d082-47a5-9a17-9f3da6c32ef6.png">

clock geting check is checked during the setup check that from the rise of the clock pulse and before certai serup time, the enable should be stable. and similarly after the falling eged of clock pulse and after some hold period, enable should be stable. Id enable changes during this time period, our setup and hold time will be violated.
	
Instead of AND or NAND gate, if there will be a OR gate then between the low pulse and before the low pulse came up to setup time and after the low pulse came up to hold time, enable should be stable. 
	
<img width="167" alt="image" src="https://user-images.githubusercontent.com/123488595/220594044-d5202dac-842f-412a-bf09-52dc9f758276.png">

Other then AND, NAND and OR gate, timing tool will say it can't figure out the clock getinh check. and users have to specify that what type of check they want.Command for this check is "set_clock_geting_check".
	
## <h4 id="header-4_4">checks on Async pin</h4>
Async pins typically in the design are "RESET" or "CLEAR" pins. below we are using clear pin as an example but it can be RESEt pin also.

When assertion is happenes, there is no relation with the clock but the de-assertion causes flop to become dependent on clock. So, when we move to synchronisum with clock from asynchronisum,  Timing checks are needed to avoid unknown states.

First step of timing check is recovery time. Recovery time is a period which is between assertion and de-assertion.

<img width="203" alt="image" src="https://user-images.githubusercontent.com/123488595/220596694-c9f2d563-6360-4ef5-95e0-043d6177e630.png">

De-assertion should be happense before the some clock period.assertion can happense anytime.

Second timing check is removel time check. Here de-assertion should be done after some time of the rise clock pulse.

<img width="178" alt="image" src="https://user-images.githubusercontent.com/123488595/220597557-057709b2-addf-42fa-8541-efcee0beb550.png">

## <h4 id="header-4_5">DAY-4 labs</h4>
### Clock gating check
clock Gating check which we shown is "Active high clock check" and now here we see the "Active low clock getting check".
For that commmands are,
<ul>
		<li><a>cd lab6</a></li>
	</ul>
<ul>
		<li><a>leafpad run.tcl</a></li>
	</ul>
<ul>
		<li><a>Run STA by "sta run.tcl –exit | tee run.log"</a></li>
	</ul>
Then analyze the slack on clock gating path which was reported there.
	
### Async pin checks
In this check, there are two primary timing checks are done.
<ul>
		<li><a>Recovery check</a></li>
	</ul>
<ul>
		<li><a>Removal check</a></li>
	</ul>
For this check, command are
<ul>
		<li><a>cd lab6</a></li>
	</ul>
<ul>
		<li><a>leafpad run.tcl</a></li>
	</ul>
<ul>
		<li><a>Run STA by "sta run.tcl –exit | tee run.log"</a></li>
	</ul>
Then analyze the slack reset path which was reported there.
	
# <h5 id="header-5">Section 5- Lactures and labs </h5>	 
## <h5 id="header-5_1">Clock groups</h5>
Clock groups commmands are use to tell the STA tool that in between what clocks we need to  meet the timing and in between what clocks we don't need to meet the timing. sometimes there are no clocks where we need to meet the timing. before going into the details, first we under the synchronous and asynchronous clock.

### synchronous clocks
synchronous clocks are clocks where events happen at a fixed phase relaton. there can be different frequency between them but basically edges are the relationship between them.

<img width="187" alt="image" src="https://user-images.githubusercontent.com/123488595/220602102-1e72f071-70b2-409e-a3c3-638915c9873f.png">

### Asynchronous clocks
Asynchronous clocks are clocks where no fixed phase relationship.means the clocks edges are unrelated.
	
<img width="179" alt="image" src="https://user-images.githubusercontent.com/123488595/220602489-ded44088-a81a-4cce-8c77-b9ebd05f34f6.png">

STA is  focused on only synchronous clocks. STA can not do any analysis of Asynchronous clocks timing paths. for Asynchronous clocks analysis, there are other tools are available like, cross domain analysis tool.

### Logically exclusive clocks
There are additional set of clocks which are known as logiclly exclusive clocks. 
	
<img width="151" alt="image" src="https://user-images.githubusercontent.com/123488595/220603462-7f98e49b-56c7-4608-b0a7-8b13a00f81b8.png">

As shown in above figure, as per the select line of the mux, clock is selected. so,if we maintioned in the STA tools that these are logically exclusive clocks then STA will not time the path between all of them because this clocks will not come at a same time.

### Physically exclusive clocks
There is another set of clocks which is physically exclusive clocks.

<img width="151" alt="image" src="https://user-images.githubusercontent.com/123488595/220604294-a8dc71cc-d569-4b72-92ac-7b0565fb88fa.png">

As we can see in the above figure, these clocks can not ne together in the design at a same time. So,if we maintioned in the STA tools that these are physically exclusive clocks then STA will not time the path between all of them because this clocks will not come at a same time.
	
Bydefault STA will assume that all clocks are syncronous clocks.

Command for to define asyncronous clocks is "set_clock_groups-asyncronous-group(clk1 clk2 clk3)-group(clk4 clk5 clk6)".

This command implies that,
<ul>
		<li><a>clk1 is asyncronous to clk4, clk5 and clk6</a></li>
	</ul>
<ul>
		<li><a>clk2 is asyncronous to clk4, clk5 and clk6</a></li>
	</ul>
<ul>
		<li><a>clk3 is asyncronous to clk4, clk5 and clk6</a></li>
	</ul>
<ul>
		<li><a>No relation can be assumed ammongs clk1,clk2 and clk3</a></li>
	</ul>
<ul>
		<li><a>No relation can be assumed ammongs clk4,clk5 and clk6</a></li>
	</ul>
If only one group is specified like, "set_clock_groups-asyncronous-group(clk1 clk2 clk3)".

So, STA will assume that there is no relation between clk1, clk2 and clk3. and these three clocks will asyncronize with all the other clocks of the design.

## <h5 id="header-5_2">Clock properties</h5>
These are the set of commands which defines the properties of the clocks.
<ul>
		<li><a>set_clock_transition</a></li>
	</ul>
By using this command, we can set the transition time of clock like what is the rise and fall time.

<ul>
		<li><a>set_clock_uncertainty</a></li>
	</ul>
By this command, we can specify the uncertainty of clock by clock skew and clock jitter.
<ul>
		<li><a>set_clock_latency</a></li>
	</ul>
By this command we can set the source and network latency of the path.
<ul>
		<li><a>set_clock_sense-stop_propogation</a></li>
	</ul>
By this command, we can specify the where clock si stoping at perticular point.
<ul>
		<li><a>set_clock_sense-positive</a></li>
	</ul>
Here we can define the positive unit or nagative unit of the clocks.
<ul>
		<li><a>set_ideal_network</a></li>
	</ul>

## <h5 id="header-5_3">Timing exceptions</h5>
There is special set of commands in STA konwn as "timing exception" which can modify the default behavior.
	
Before we goes into the timing exception, we have to understand the path specification of the perticular design.

<img width="129" alt="image" src="https://user-images.githubusercontent.com/123488595/220626465-ae0a6e56-0ade-4c66-9c98-9d74497cfca2.png">

there are multiple paths exist in above network. and if we want to change the default behavior of this timing analysis on the path, we have to specify that on what path we have to change the behavior. To specify this path, any of the timing excaption commands using three option which are gievn below,
<ul>
		<li><a>from</a></li>
	</ul>
It is use for start points(I/O ports, clock pins)
<ul>
		<li><a>to</a></li>
	</ul>
It is typically used for end points.
<ul>
		<li><a>through</a></li>
	</ul>
it is used for nets and nodes(combinational nodes).
	
Now, lets we take one path as given below in the circuit for change the behavior.

<img width="130" alt="image" src="https://user-images.githubusercontent.com/123488595/220628190-e633b2a0-d3cf-45bd-98c8-13b797c994f2.png">

To specify this we have to write "-from F1/ck-to F5/D-through {U1/a}-through {U1/z}". Here through options are ordered options and we have to use this accordingly.

Now, let's see the varies exception commands use for this path specification
to change the default behavior.

#### set_false_path
"-from F1/ck/D through {U1/a} through {U1/z} to F5", meaning of giving this command is don't time this path.

#### set_multicycle_path
"set_multicycle_path-setup 2-from FF1 to FF2", this is the command for set the multicycle path
<img width="191" alt="image" src="https://user-images.githubusercontent.com/123488595/220631910-1d87ad15-bf6e-4c89-8e18-466d86c5db84.png">
	
Here we specify to STA that meet the timing in 2 cycle instead of 1 cycle through this path.

Similarly, hold time is also modified by this command, "set_multicycle_path-hold 1-from FF1 to FF2".
	
### Other exception
<ul>
		<li><a>set_max_delay</a></li>
	</ul>
<ul>
		<li><a>set_min_delay</a></li>
	</ul>
<ul>
		<li><a>set_disable_timing</a></li>
	</ul>

## <h5 id="header-5_4">multiple modes</h5>
The last setup command which is use to define the multiple modes in STC. This command is "set_case_analysis". this command is use to specify a certain portion of the design and specify a constant value that may or may not be constant value in the netlist but we can over write this by using this command.
	
For example, let 2:1 mux have TestCLK and FunctionCLK in the input and select line is "SEL". so if we want to do the analysis of functionCLK. so  we have to give commmand like "set_case_analysis 1 {SEL}".
	
## <h5 id="header-5_5">DAY 5- Labs</h5>
As we done the analysis of slack calculation in the DAY-3 lab, same we have to done here and we get -217.32 slack here in the report which we can see below.
### report
<img width="232" alt="image" src="https://user-images.githubusercontent.com/123488595/220636659-68f88983-e5d9-4e36-bbf1-208a0742c15f.png">

### Circuit design
<img width="226" alt="image" src="https://user-images.githubusercontent.com/123488595/220636769-5f429a70-6817-4b08-bad5-f57e68143213.png">

### CPPR
Full form of CPPR is "common path pessimism removal".
	
<img width="370" alt="image" src="https://user-images.githubusercontent.com/123488595/220637833-8ada7645-3e9d-466a-ba4a-ddcc2f62a2c1.png">

In above circuit, U8 and U9 are common path for launch and capture the data. so when we do the STA, it can be removed.
	
Now first we done STA without CRPR. for that this commands should be run,
<ul>
		<li><a>cd lab4</a></li>
	</ul>
<ul>
		<li><a>sta run.tcl –exit | out.txt</a></li>
	</ul>
<ul>
		<li><a>%report_checks -to F2/D through U5/A1</a></li>
	</ul>
Here we take worst path for this analysis.

So, we get this report,
	
<img width="194" alt="image" src="https://user-images.githubusercontent.com/123488595/220639558-7045b2d4-bdba-4c01-a05f-4f271cfd76d2.png">

So, here we get slack= -398.1.
	
Now if we use CRPR and remove that comman part from this path then we can change the behavior and same time we can reduce the slack. Now as given below in the circuit, "c2" is the node which required CRPR.

<img width="239" alt="image" src="https://user-images.githubusercontent.com/123488595/220640635-9164ec90-1952-4825-997b-7ae1524802a6.png">

Command for that is "set sta_crpr_enabled 1" and the command for getting the report is "%report_checks to F2/D through U5/A1". again here also we select the same path for analysis as what we selected before.
	
Now this is the report what we get here,
	
<img width="273" alt="image" src="https://user-images.githubusercontent.com/123488595/220641398-2876b46e-a993-4955-889d-d03bbbcd450a.png">

As compair to the first report, in this report the reconvergence pessimism is extra added so our required time is increased and due to that the slack is reduced to "-391.43".

### ECO- Engineering change Order
In the Engineering change Order cycle, we perform various analysis one by one for every check which we need to close but not closed till PnR stage.

There are specialized signoff tools that help us to analyze the issue 
and also suggest the changes we need to do in order to close the 
issue. This suggested changes are captured in "eco file". because of these changes, we can fic the setup and Hold violations.
	
For that first we have to run this commands,
	
<ul>
		<li><a>cd lab5</a></li>
	</ul>
<ul>
		<li><a>run.tcl</a></li>
	</ul>

<img width="155" alt="image" src="https://user-images.githubusercontent.com/123488595/220643848-ee034513-cca1-4a0c-814a-c36dbf10f97f.png">

Here we can notice the commands which are used in run.tcl file.
Now Check for description of commands in openSTA pdf document. for that open the verilog file which name is "s27_eco.v" and compair this file with "s27.v".
	
Observe the suggestion in this difference and implement this on the run. then we can check the chnages in the slack in the report by opening the report.

# <h6 id="header-6">References</h6>
<ul>
	<li><a>https://github.com/</a></li>
	</ul>
<ul>
	<li><a>https://github.com/The-OpenROAD-Project/OpenSTA/blob/master/doc/OpenSTA.pdf</a></li>
	</ul>
<ul>
	<li><a>https://people.eecs.berkeley.edu/~alanmi/publications/other/liberty07_03.pdf</a></li>
	</ul>
<ul>
	<li><a>https://www.vlsisystemdesign.com/spef-format-part-1/</a></li>
	</ul>
<ul>
	<li><a>https://github.com/Bharti-Navlani/VSD-IAT-Sign-off-Timing-Analysis_Basics-to-Advance/tree/main/Labs</a></li>
	</ul>

# <h7 id="header-7">Acknowledgement</h7>
I would like to express my special thanks of gratitude to Mr. kunal ghosh (co.-founder of VLSIsystem design (VSD) corp.pvt.ltd.) and mr. Vikas Sachdeva for their guidence and temendous presenting this workshop on STA. The Workshop was excellent and well designed. This workshop taught me a lot of new things about the different types of timing analysis and how to reduce the slack in the design.
