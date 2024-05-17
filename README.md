VLSI-LAB-EXP-4
SIMULATION AND IMPLEMENTATION OF SEQUENTIAL LOGIC CIRCUITS

AIM:
To simulate and synthesis SR, JK, T, D - FLIPFLOP, COUNTER DESIGN using Xilinx ISE.

APPARATUS REQUIRED:
vivado 2023.2

PROCEDURE
STEP:1 Start the vivado software, Select and Name the New project.

STEP:2 Select the device family, device, package and speed.

STEP:3 Select new source in the New Project and select Verilog Module as the Source type.

STEP:4 Type the File Name and module name and Click Next and then finish button. Type the code and save it.

STEP:5 Select the run simulation and then run Behavioral Simulation in the Source Window and click the check syntax.

STEP:6 Click the simulation to simulate the program and give the inputs and verify the outputs as per the truth table.

STEP:7 compare the output with truth table.

LOGIC DIAGRAM

SR FLIPFLOP

![image](https://github.com/navaneethans/VLSI-LAB-EXP-4/assets/165633628/7f732d5a-1172-4db7-bdd4-53f748bd800c)


JK FLIPFLOP

![image](https://github.com/navaneethans/VLSI-LAB-EXP-4/assets/165633628/6950e63d-8723-4e86-aea4-801392546211)


T FLIPFLOP

![image](https://github.com/navaneethans/VLSI-LAB-EXP-4/assets/165633628/0bb64f16-8857-4022-b7df-f66315df86be)


D FLIPFLOP

![image](https://github.com/navaneethans/VLSI-LAB-EXP-4/assets/165633628/fdfc6f85-9002-4031-919d-45f257cdecda)


COUNTER

![image](https://github.com/navaneethans/VLSI-LAB-EXP-4/assets/165633628/9ba7bbc5-c984-42e3-a1b5-b1714bd3aad1)


VERILOG CODE
SR FLIPFLOP
module srff(clk,j,k,rst,q );

input s,r,clk,rst;

output reg q;

always@(posedge clk)

begin

if(rst==1)

q=1'b0;

else

begin

case({s,r})

2'b00: q=q;

2'b01:q=1'b0;

2'b10:q=1'b1;

2'b11:q=1'bx;

endcase

end

end

endmodule

JK FLIPFLOP:
module jkff(clk,j,k,rst,q );

input j,k,clk,rst;

output reg q;

always@(posedge clk)

begin

if(rst==1)

q=1'b0;

else

begin

case({j,k})

2'b00: q=q;

2'b01:q=1'b0;

2'b10:q=1'b1;

2'b11:q=~q;

endcase

end

end

endmodule

T FLIPFLOP:
module tff(clk,reset,t,q);

input clk,reset,t;

output reg q;

always @(posedge clk)

begin

if(reset==1)

q=0;

else

begin

if(t==0)

q=q;

else

q=~q;

end

end

endmodule

D FLIPFLOP:
module dff(clk,d,rst,q );

input d,clk,rst;

output reg q;

always@(posedge clk)

begin

if(rst==1)

q=1'b0;

else

q=d;

end

endmodule

UPDOWN COUNTER:
module updown(clk,rst,up_down,count);

input clk,rst,up_down;

output reg[3:0]count;

always@(posedge clk)

begin

if(rst==1)

count <= 4'b0000;

else if (up_down == 1'b1)

count <= count + 1'b1;

else

count <= count-1'b1;

end

endmodule

MOD 10 COUNTER:
module mod(clk,rst,count);

input clk,rst;

output reg[3:0]count;

always @(posedge clk)

begin

if(rst==1 | count==4'b1001)

count <= 4'b0000;

else

count <= count +1;

end

endmodule

RIPPLE COUNTER:
module ripplecounter(clk,rst,q);

input clk,rst;

output [3:0]q;

tff tff1(q[0],clk,rst);

tff tff2(q[1],q[0],rst);

tff tff3(q[2],q[1],rst);

tff tff4(q[3],q[2],rst);

endmodule

module tff(q,clk,rst);

input clk,rst;

output q;

wire d;

dff df1(q,d,clk,rst);

not n1(d,q);

endmodule

module dff(q,d,clk,rst);

input d,clk,rst;

output q;

reg q;

always@(posedge clk or posedge rst)

begin

if(rst)

q=1'b10;

else

q=d;

end

endmodule

OUTPUT WAVEFORM
SR Flipflop:
![image](https://github.com/navaneethans/VLSI-LAB-EXP-4/assets/165633628/1c8880b1-0529-4901-983e-84452a3d091a)


JK flipflop:
![image](https://github.com/navaneethans/VLSI-LAB-EXP-4/assets/165633628/21c5273c-9370-4d86-8101-2ad0c2e8aa21)

T Flipflop:
![image](https://github.com/navaneethans/VLSI-LAB-EXP-4/assets/165633628/aecb351f-dd16-44e3-b621-becac8d2bcf0)


D Flipflop:
![image](https://github.com/navaneethans/VLSI-LAB-EXP-4/assets/165633628/2047207a-b639-4cea-ac98-3c9796139494)


Updown counter:
![image](https://github.com/navaneethans/VLSI-LAB-EXP-4/assets/165633628/19888b11-71f6-4688-9838-da73718a3169)


Mod 10 counter:
![image](https://github.com/navaneethans/VLSI-LAB-EXP-4/assets/165633628/911e76b3-193c-48ea-878c-df72dc03ace6)


Ripple counter:
![image](https://github.com/navaneethans/VLSI-LAB-EXP-4/assets/165633628/d0940989-2a32-4ead-a72b-dc56f3538e3d)


RESULT
Thus,the simulation and synthesis of SR,JK,T,D flipflops,counters by using vivado has been successfully excecuted and verified.
