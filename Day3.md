# Day3: Combinational and sequential optmizations

Lab 1: Verilog code
```
module opt_check (input a , input b , output y);
	assign y = a?b:0;
endmodule

```

```
yosys> read_liberty -lib ../my_lib/lib/sky130_fd_sc_hd__tt_025C_1v80.lib
yosys> read_verilog opt_check.v
yosys> synth -top opt_check
yosys> opt_clean -purge
yosys> abc -liberty ../my_lib/lib/sky130_fd_sc_hd__tt_025C_1v80.lib 
```

<img width="1908" height="921" alt="image" src="https://github.com/user-attachments/assets/5a3702a4-b088-472d-b719-ddd42de17847" />

Lab 2: Verilog code

```
module opt_check2 (input a , input b , output y);
	assign y = a?1:b;
endmodule
```

```
yosys> read_liberty -lib ../my_lib/lib/sky130_fd_sc_hd__tt_025C_1v80.lib
yosys> read_verilog opt_check2.v
yosys> synth -top opt_check2
yosys> opt_clean -purge
yosys> abc -liberty ../my_lib/lib/sky130_fd_sc_hd__tt_025C_1v80.lib 
```

<img width="1919" height="918" alt="image" src="https://github.com/user-attachments/assets/c07866da-6538-4637-9ea2-b1bb034a2be1" />

Lab 3: Verilog Code

```
module opt_check3 (input a , input b, input c , output y);
	assign y = a?(c?b:0):0;
endmodule
```

```
yosys> read_liberty -lib ../my_lib/lib/sky130_fd_sc_hd__tt_025C_1v80.lib
yosys> read_verilog opt_check3.v
yosys> synth -top opt_check3
yosys> opt_clean -purge
yosys> abc -liberty ../my_lib/lib/sky130_fd_sc_hd__tt_025C_1v80.lib 

```

<img width="1919" height="917" alt="image" src="https://github.com/user-attachments/assets/ba90c4f7-c90b-4be8-91c7-614cc32f38b5" />


Lab 4: Verilog Code

```
module opt_check4 (input a , input b , input c , output y);
 assign y = a?(b?(a & c ):c):(!c);
 endmodule
```

```
read_liberty -lib ../my_lib/lib/sky130_fd_sc_hd__tt_025C_1v80.lib
read_verilog opt_check4.v
synth -top opt_check4
opt_clean -purge
abc -liberty ../my_lib/lib/sky130_fd_sc_hd__tt_025C_1v80.lib 

```
<img width="1919" height="920" alt="image" src="https://github.com/user-attachments/assets/488a0298-1f3c-438c-bf3e-f854d8e02aa1" />

Lab 5: Verilog Code
```
module dff_const1(input clk, input reset, output reg q);
always @(posedge clk, posedge reset)
begin
	if(reset)
		q <= 1'b0;
	else
		q <= 1'b1;
end
endmodule
```

```
read_liberty -lib ../my_lib/lib/sky130_fd_sc_hd__tt_025C_1v80.lib
read_verilog dff_const1.v
synth -top dff_const1
opt_clean -purge
abc -liberty ../my_lib/lib/sky130_fd_sc_hd__tt_025C_1v80.lib 

```

<img width="1919" height="915" alt="image" src="https://github.com/user-attachments/assets/d4858503-bcb8-4b64-8ab9-08641df17147" />


Lab 6: Verilog Code
```
module dff_const2(input clk, input reset, output reg q);
always @(posedge clk, posedge reset)
begin
	if(reset)
		q <= 1'b1;
	else
		q <= 1'b1;
end
endmodule
```

```
read_liberty -lib ../my_lib/lib/sky130_fd_sc_hd__tt_025C_1v80.lib
read_verilog dff_const2.v
synth -top dff_const2
opt_clean -purge
abc -liberty ../my_lib/lib/sky130_fd_sc_hd__tt_025C_1v80.lib 

```
<img width="1919" height="881" alt="image" src="https://github.com/user-attachments/assets/093489c9-b86a-49b9-9b67-aeaaf909d1d1" />




