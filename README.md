Download Link: https://assignmentchef.com/product/solved-eml5311-control-systems-theory-mechanical-and-aerospace-engineering-hw-7
<br>
<em>You are encouraged to use MATLAB</em><sup> c </sup><em>to verify your answers whenever you can. However, unless specified, do not use MATLAB</em><sup> c </sup><em>to solve a problem.</em>

<strong>Problem 1. </strong>Consider an LTI system described by the following matrices:

(1)

<ol>

 <li>Determine controllability and observability of the system. (Meaning, determine if they are controllable and observable. If not, determine the dimension of the controllable subspace and unobservable subspace.)</li>

 <li>Comment on the relation, if any, between the number of inputs and controllability, and the number of outputs and observability.</li>

</ol>

<em>Hint: If you use the rank test, unless the rank is obvious from inspection, reduce the controllability/observability matrices to row echelon form to determine their rank. Sometimes it is useful to use the fact that rank of a matrix is the same as the rank of its transpose, to first transpose the matrix and then do row reduction. Verify your answer in MATLAB</em><sup> c </sup><em>using </em><em>ctrb, </em><em>obsv and </em><em>rank commands. </em><strong>Problem 2. </strong>Consider the following system

where <em>c</em><sub>1</sub><em>,c</em><sub>2</sub><em>,c</em><sub>3 </sub>are unknown scalars.

<ol>

 <li>Provide an example of values of <em>c</em><sub>1</sub><em>,c</em><sub>2</sub><em>,c</em><sub>3 </sub>for which the system is not observable.</li>

 <li>Provide an example of values of <em>c</em><sub>1</sub><em>,c</em><sub>2</sub><em>,c</em><sub>3 </sub>for which the system is observable.</li>

 <li>Provide a necessary and sufficient condition on the <em>c<sub>i</sub></em>’s so that the system is observable.</li>

</ol>

<strong>Problem 3. </strong>This is a MATLAB<sup> c </sup>-only problem. A Simulink model observer.slx is provided with this homework, with an accompanying MATLAB<sup> c </sup>script RunObserver INCOMPLETE.m. The plant being simulated is stable, with 2 inputs and 1 output. Your task is to complete the MATLAB<sup> c </sup>script so that all the parameters needed by the observer in the Simulink model are defined, and the model executes correctly when called, either from the script directly or by clicking the ’run’ button on the Simulink model.

<ol>

 <li>Show that the observer dynamics <em>x</em>ˆ<sup>˙ </sup>= <em>Ax</em>ˆ + <em>Bu </em>+ <em>L</em>(<em>y </em>− (<em>Cx</em>ˆ + <em>Du</em>)) can be rewritten as</li>

</ol>

or as

<em>Beware: in analyzing an observer we frequenctly replace y with Cx </em>+ <em>Du, but we cannot do it in implementation, since the state x is unknown. When implementing an observer, whether in a simulink simulation or a real system, you have to think of the observer as a dynamic system with state x</em>ˆ<em>, output x</em>ˆ <em>(same as the state), and input </em><em> or </em><em>. Either way of defining the input vector is fine, but you must be consistent. Check the simulink block to see which one I am using; your matlab script will have to be consistent with how I have defined the observer input in the Simulink model.</em>

<ol start="2">

 <li>No need to resubmit the whole script, simply complete the following section of the script (the provided .m file) that needs completion:</li>

</ol>

obsv_poles = ; %choose desired eigenvalues of A-LC ….

L =….

Also submit the plots of the states and state estimates between <em>t </em>= 0 to <em>t </em>= 15. (Plot <em>x<sub>i </sub></em>and <em>x</em>ˆ<em><sub>i </sub></em>in the same figure so the accuracy of the estimate can be visually checked easily.)

<ol start="3">

 <li>Describe your rationale for your choice of the eigenvalues of <em>A </em>− <em>LC</em>. What effect does varying these eigenvalues have on the state estimation accuracy?</li>

</ol>

<em>You have to use duality to design the observer gain L by using the </em><em>place command, since that command is meant for designing K in state feedback control. A frequent mistake here is to forget to use tranposes. Review duality carefully.</em>

<strong>Problem 4. </strong>( In this problem you will design a control system for a SISO plant <em>P</em>(<em>s</em>) to meet transient response performance requirements by using state space techniques. You are allowed – and encouraged – to use MATLAB<sup> c </sup>for any calculation needed in this problem.) Consider the following plant <em>P</em>(<em>s</em>) whose input is <em>u </em>+ <em>v</em>, where <em>u </em>is the control command and <em>v </em>is a disturbance, and output <em>y</em>:

(2)

A minimal realization of it the plant is provided below:

)         (3)

(4)

Your job is to design and output feedback controller for this plant by using a state observer and combining it with a state feedback controller (that is, <em>u</em>(<em>t</em>) = −<em>Kx</em>ˆ(<em>t</em>), and ˆ<em>x </em>is an estimate of the state <em>x</em>), and simulate the closed loop. Here are the tasks:

<ol>

 <li>Draw a sketch of the closed loop control system.</li>

 <li>Show that with the output feedback controller, the closed loop system’s state space representation is</li>

</ol>

(5)

where <em>e </em>= <em>x </em>− <em>x</em>ˆ, and <em>A,B,C </em>are the system matrices of the plant <em>P</em>(<em>s</em>) shown in eq. (3)-(4).

<ol start="3">

 <li>Design the control system so that the closed loop transfer function <em>H<sub>yv </sub></em>is BIBO stable and has a 2% settling time less than 1. <em>hint: You have to choose controller poles and observer poles in this step, and then get K,L by using the place command. The choice of these eigenvalues are dictated by the settling time requirement (recall the material on dominant poles and relation of poles of second order underdamped systems and transient response). After that, define the closed loop system by using </em><em>ss and equation </em>(5)<em>, and determine rise time by using </em><em>stepinfo. Verify the results of </em><em>stepinfo by plotting the step response and checking visually.</em></li>

 <li>Construct a SIMULINK model of the closed loop system. Write a MATLAB<sup> c </sup>script to initialize and define all parameters needed by the Simulink model, and also to run the model using the sim Set <em>v</em>(<em>t</em>) to 0 (for all <em>t</em>). Choose a sufficiently long time to see transients die out, use the following initial conditions: <em>x</em>(0) = [1<em>,</em>1<em>,</em>1<em>,</em>1<em>,</em>1]<em><sup>T</sup></em>, ˆ<em>x</em>(0) = 0. Submit: (i) plots of output, (ii) a picture of your simulink block, (iii) a brief description of your design process (not more than 5 sentences). <em>Your simulink model should have the plant, observer, and the state feedback controller, all interconnected. The easiest path to constructing it is to copy the observer model I am providing in the previous problem, remove the external input, add the state feedback controller, and make other necessary changes. My simulink block looks like the picture shown below.</em></li>

</ol>

<strong>Problem 5. </strong>This is a MATLAB<sup> c </sup>only problem. Your task in this problem is to write a MATLAB<sup> c </sup>script to compute the solution of an ODE by “numerical integration.” The ODE is

<em>y</em>¨+ 2<em>y</em>˙ + 5<em>y </em>= <em>f</em>(<em>t</em>)<em>,y</em>(0) = −4<em>,y</em>˙(0) = 5                                 (6)

where the input is <em>f</em>(<em>t</em>) = 2sin(2<em>t</em>) + 5.

<ol>

 <li>First, use matlab’s built in function lsim to compute the solution by doing the following. Express the ODE is state space form, and then use lsim to determine the solution between <em>t </em>= 0 and <em>t </em>= 5, using a time resolution of 0.25 seconds in specifying the input vector (Beware: do not forget to provide the initial condition to lsim.)</li>

 <li>Now write a MATLAB<sup> c </sup>script to compute the solution approximately by using either (i) a first-order Euler forward-difference method<a href="#_ftn1" name="_ftnref1"><sup>[1]</sup></a>, or (ii) discretizing the ODE using the continuousto-discrete conversion covered in class. Either method is fine; they will produce similar results. Plot the solution in the same figure as the solution you get in step 1. Repeat this for three different sampling periods, <em>T<sub>s </sub></em>= 0<em>.</em>5, <em>T<sub>s </sub></em>= 0<em>.</em>25 and <em>T<sub>s </sub></em>= 0<em>.</em> Do all of these “solutions” look right? (Ans: The solution plots you should get are shown in Figure 1.)</li>

 <li>An inexperienced engineer comes to you seeking your guidance in performing simulations of dynamic systems using an Euler approximation. What guidelines would you provide about the choice of sampling period for first order Euler forward-difference approximation?</li>

</ol>

<strong>Problem 6. </strong>Consider an LTI system given by

<ol>

 <li>Compute the transfer function from <em>i<sup>th </sup></em>input to the output of the system.</li>

 <li>Are the eigenvalues of <em>A </em>the same as the poles of the transfer function?</li>

 <li>Is the system BIBO stable? Is the system stable in the sense of Lyapunov? Is the system asymptotically stable in the sense of Lyapunov?</li>

</ol>

<em>Hint/answer key: this is an example of a pole-zero cancellation; the poles will be a strict subset of the eigenvalues.</em>

<strong>Problem 7. </strong>(This is a MATLAB<sup> c </sup>problem) An incomplete C code control<em>.</em>c written for a particular hardware platform<a href="#_ftn2" name="_ftnref2"><sup>[2]</sup></a> to implement the following controller:

is given below. Use MATLAB<sup> c </sup>to determine the numerical values that should be in the incomplete statements in the code (i.e., use MATLAB<sup> c </sup>’s c2d function to compute the discrete-time <em>A </em>and <em>B </em>matrices of the controller).

0             2              4             6              8             10                     0             2              4              6             8            10

Figure 1: Comparison of numerical ODE solution from MATLAB<sup> c </sup>’s lsim and first order Euler approximation with various sampling periods.

/********************* control.c **********************************/

<table width="557">

 <tbody>

  <tr>

   <td colspan="2" width="275">#include “brtenv.h”</td>

   <td width="283">/* basic real-time environment */</td>

  </tr>

  <tr>

   <td width="145">#define TS</td>

   <td width="130">1.25e-3</td>

   <td width="283">/* Sample period, in sec */</td>

  </tr>

  <tr>

   <td width="145">#define TMR0</td>

   <td width="130">0</td>

   <td width="283">/* Use timer0 for exec-time trace */</td>

  </tr>

  <tr>

   <td width="145">float r,y,e,u; float a11= float a12= float a21= float a22= float b11= float b21= float c11= float c12=</td>

   <td width="130"></td>

   <td width="283">/* input/output variables */</td>

  </tr>

 </tbody>

</table>

float d =

float x1 = 0; float x2 = 0; float u_max = 10; float u_min = -5;

/* timer0 interrupt service routine */ isr_t0() {

<table width="535">

 <tbody>

  <tr>

   <td width="229">ds1102_ad_start();</td>

   <td width="305">/* start DS1102 ADCs */</td>

  </tr>

  <tr>

   <td width="229">r = ds1102_ad(1);</td>

   <td width="305">/* read input r(t) from ADC channel 1 */</td>

  </tr>

  <tr>

   <td width="229">y = ds1102_ad(2);</td>

   <td width="305">/* read input y(t) from ADC channel 2 */</td>

  </tr>

 </tbody>

</table>

e = r-y; /* compute tracking error */

x1next = a11*x1 + a12*x2 + b11*e; x2next = a21*x1 + a22*x2 + b21*e; u = c11*x1 + c12*x2 + d*e;

/* clip the control command if it exceeds actuator ability */ if (u&gt;u_max)

u_final = u_max; else { if (u&lt;u_min)

u_final = u_min;

else

u_final = u;

}

ds1102_da(1,u_final);                                              /* write output to DAC channel 1*/

/* dont forget the next step*/ x1=x1next; x2=x2next;

}

main() {

init();                                                                    /* initialize hardware */

start_isr_t0(TS);                                                   /* initialize sampling clock timer */

}

/********************* end of control.c **********************************/

<em>Problems 8,9,10 are on one theme.</em>

<strong>Problem 8 </strong>(unstable pole-zero cancellation)<strong>. </strong>A risky – but at first glance attractive – way of stabilizing an unstable plant is to cancel the unstable poles of the plant with right-half-plane zeros of the controller. This is a bad idea, for at least two reasons. The first reason is modeling uncertainty: since we do not know the precise locations of the plant poles, we will never be able to cancel unstable poles exactly. The second reason is that even if we knew the plant pole locations exactly, pole-zero cancellations only hide the instability but do not remove it. This problem illustrates the second reason. Consider a standard negative feedback loop with three external inputs: reference <em>r</em>(<em>t</em>), disturbance <em>w</em>(<em>t</em>) and noise <em>n</em>(<em>t</em>), with plant and controller given by

As we usually do in such circumstances, the output of the plant is denoted by <em>z</em>(<em>t</em>) and the noisy output that is used for feedback by <em>y</em>(<em>t</em>).

<ol>

 <li>Determine the BIBO stability property of each of the following closed loop transfer functions:</li>

</ol>

<ul>

 <li><em>H<sub>ZR</sub></em>(<em>s</em>)</li>

 <li><em>H<sub>Y R</sub></em>(<em>s</em>)</li>

 <li><em>H<sub>ZW</sub></em>(<em>s</em>)</li>

 <li><em>H<sub>UR</sub></em>(<em>s</em>)</li>

</ul>

<em>Answer key: the first two are BIBO stable, third one is not.</em>

<strong>Problem 9. </strong>Consider a standard feedback loop with a SISO plant and a SISO controller. Suppose a minimal realization of the plant is <em>A<sub>p</sub>,B<sub>p</sub>,C<sub>p</sub>,D<sub>p </sub></em>with state <em>x<sub>p</sub></em>, input <em>u </em>and output <em>y</em>. And, a minimal realization of the controller is <em>A<sub>c</sub>,B<sub>c</sub>,C<sub>c</sub>,D<sub>c</sub></em>, with state <em>x<sub>c</sub></em>, input <em>e </em>and output <em>u</em>. Recall that <em>e </em>= <em>r</em>−<em>y</em>. The only external input to the closed loop system is <em>r</em>, and the output of the closed loop system is the plant output <em>y</em>. Determine a realization of the closed loop system with state by combining the state equations of the plant and the controller and eliminating the internal variables <em>e </em>and <em>u</em>. (Hint: If you have to assume a particular matrix to be invertible, go ahead and assume that.) That is, determine what the matrices <em>A<sub>cl</sub>,B<sub>cl</sub>,C<sub>cl</sub>,D<sub>cl </sub></em>should be in

<em>Note:</em>

<ol>

 <li><em>A frequent mistake is to compute the closed loop transfer function and then compute its realization! Write down a realization of plant and controller separately and then combine them. Also, pay attention that the matrices A<sub>cl</sub>,B<sub>cl</sub>,C<sub>cl</sub>,D<sub>cl </sub>can only be a function of the matrices of the plant and controller’s state space description, they cannot have any time varying functions.</em></li>

 <li><em>Do this one carefully since you are going to use the answer in the next problem, so if you get this wrong you will get the next one wrong too.</em></li>

</ol>

<strong>Problem 10. </strong>Now apply the results of the previous problems to determine the state space realization of the closed loop system with plant and controller.

Assume there are no noise and disturbance; the only external input is <em>r</em>.

<ol>

 <li>Is the closed loop system stable in the sense of Lyapunov?</li>

 <li>Discuss any connection you see between the previous answer and the answer to Problem 8.</li>

</ol>

<em>A frequent error is to compute CP/</em>1 + <em>CP and then determine its minimal realization. That’s WRONG! </em>.

<strong>Problem 11. </strong>[Ungraded problem] Based on the problems in this homework discuss two (or more) advantges of state-space descriptions of linear dynamic systems over transfer function descriptions. For each advantage, mention which problems in the homework illustrate those advantages.

<a href="#_ftnref1" name="_ftn1">[1]</a> You can read about it in the texbook Barooah

<a href="#_ftnref2" name="_ftn2">[2]</a> The platform happens to be dSpace<sup>TM</sup>, but that’s immaterial