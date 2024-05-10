SIMULATION AND IMPLEMENTATION OF MULTIPLIER
**AIM: **
 To simulate and synthesis multiplier using vivado 2023.2.

**APPARATUS REQUIRED:**
vivado 2023.2.
  
**PROCEDURE:**
1. Open Vivado: Launch Xilinx Vivado software on your computer.

2. Create a New Project: Click on "Create Project" from the welcome page or navigate through "File" > "Project" > "New".

3. Project Settings: Follow the prompts to set up your project. Specify the project name, location, and select RTL project type.

4. Add Design Files: Add your Verilog design files to the project. You can do this by right-clicking on "Design Sources" in the Sources window, then selecting "Add Sources". Choose your Verilog files from the file browser.

5. Specify Simulation Settings: Go to "Simulation" > "Simulation Settings". Choose your simulation language (Verilog in this case) and simulation tool (Vivado Simulator).

6. Run Simulation: Go to "Flow" > "Run Simulation" > "Run Behavioral Simulation". This will launch the Vivado Simulator and compile your design for simulation.

7. Set Simulation Time: In the Vivado Simulator window, set the simulation time if it's not set automatically. This determines how long the simulation will run.

8. Run Simulation: Start the simulation by clicking on the "Run" button in the simulation window.

9. View Results: After the simulation completes, you can view waveforms, debug signals, and analyze the behavior of your design.


**Logic Diagram**
2 bit Multiplier

![image](https://github.com/navaneethans/VLSI-LAB-EXP-3/assets/6987778/7713750f-65e6-41c0-8082-5005eac4031c)

**4 Bit Multiplier**

![image](https://github.com/navaneethans/VLSI-LAB-EXP-3/assets/6987778/d95215dd-8cf1-4e08-93cc-96adfdd7fbdc)


**Verilog code**
Multiplier_2bit:
~~~
module ha(a,b,sum,c);

input a,b;

output sum,c;

xor g1(sum,a,b);

and g2(c,a,b);

endmodule

module bitmultiplier(a,b,c);

input [1:0]a,b;

output[3:0]c;

wire w1;

and g1(c[0],b[0],a[0]);

ha ha1(a[0]&b[1],a[1]&b[0],c[1],w1);

ha ha2(a[1] &b[1],w1,c[2],c[3]);

endmodule
~~~

**Output Waveform**
![image](https://github.com/Kirthana-2004/VLSI-LAB-EXP-3/assets/144320880/cfc70ce7-0f5f-4542-ba51-6019deb10449)
![image](https://github.com/Kirthana-2004/VLSI-LAB-EXP-3/assets/144320880/5ee9d304-99e6-40dd-bd79-efa8a334cb29)
Multiplier_4bit:
~~~
module ha(a,b,c,s);

input a,b;

output s,c;

xor g1(s,a,b);

and g2(c,a,b);

endmodule

module fa(a,b,c,s,carry);

input a,b,c;

output s,carry;

wire w1,w2,w3;

xor g1(w1,a,b);

and g2(w2,a,b);

xor g3(s,w1,c);

and g4(w3,w1,c);

or g5(carry,w3,w2);

endmodule

module bitmultiplier(x,y,z);

input[3:0]x,y;

output[7:0]z;

wire [17:1]w;

and g1(z[0],x[0],y[0]);

ha ha1(x[1]&y[0],x[0]&y[1],z[1],w[1]);

fa fa1(x[2]&y[0],x[1]&y[1],w[1],w[5],w[2]);

fa fa2(x[3]&y[0],x[2]&y[1],w[2],w[6],w[3]);
ha ha2(x[3]&y[1],w[3],w[7],w[4]);

ha ha3(w[5],x[0]&y[2],z[2],w[8]);

fa fa3(w[6],x[1]&y[2],w[8],w[12],w[9]);

fa fa4(w[7],x[2]&y[2],w[9],w[13],w[10]);

fa fa5(w[4],x[3]&y[2],w[10],w[14],w[11]);

ha ha4(w[12],x[0]&y[3],z[3],w[15]);

fa fa6(w[13],x[1]&y[3],w[15],z[4],w[16]);

fa fa7(w[14],x[2]&y[3],w[16],z[5],w[17]);

fa fa8(w[11],x[3]&y[3],w[17],z[6],z[7]);

endmodule
~~~
**output waveform**
![image](https://github.com/Kirthana-2004/VLSI-LAB-EXP-3/assets/144320880/e86dcd51-1afd-49a7-b7df-e99ef47dcd81)
![image](https://github.com/Kirthana-2004/VLSI-LAB-EXP-3/assets/144320880/8804957b-f4fa-4ba1-81a0-54ca29df9ac8)






**Result**
Hence the 2 bit multiplier and 4 bit multiplier are simulated and synthesised using Vivado 2023.2.


