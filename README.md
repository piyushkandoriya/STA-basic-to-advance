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
contais the design information
<ul>
		<li><a>SDC or Constrain file</a></li>
	</ul>
It comtains all information about what you want the time
<ul>
		<li><a>Logic Libraries</a></li>
	</ul>
It contains all the information about delays of logic cells and tansition time of those cells.
