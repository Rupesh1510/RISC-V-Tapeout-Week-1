# Day 1 Lab: Simulating a 2-to-1 Multiplexer

# Labs using iverilog and gtkwave

## Step 1: Clone the Workshop Repository
~~~
git clone https://github.com/kunalg123/sky130RTLDesignAndSynthesisWorkshop.git
cd sky130RTLDesignAndSynthesisWorkshop/verilog_files
~~~

## Step 2: Simulation Files

verilog_files dir contains all the required verilog file for this wwek

~~~
cd sky130RTLDesignAndSynthesisWorkshop/verilog_files
ls
~~~

<img width="1732" height="442" alt="image" src="https://github.com/user-attachments/assets/eb2725c7-c1f4-4fff-bc53-74340079ed27" />



## Step 3: Simulate the Design

Compile the design and testbench:
~~~
iverilog good_mux.v tb_good_mux.v
~~~

<img width="1732" height="442" alt="image" src="https://github.com/user-attachments/assets/850e10ac-981e-4623-9eb4-0b2d79c55fc1" />


Run the simulation:

```
./a.out
```
<img width="1732" height="77" alt="image" src="https://github.com/user-attachments/assets/4f8b445d-4314-4568-87d0-500d9dc463e8" />


View the waveform:

```
gtkwave tb_good_mux.vcd
```
<img width="1732" height="234" alt="image" src="https://github.com/user-attachments/assets/bf80bc3f-91a6-4e4b-b218-f49ab8879125" />


<img width="1920" height="891" alt="image" src="https://github.com/user-attachments/assets/fd2b39cd-683e-4485-96e8-e3a25371cd70" />

## Design File 

```

module good_mux (input i0 , input i1 , input sel , output reg y);
always @ (*)
begin
        if(sel)
                y <= i1;
        else
                y <= i0;
end
endmodule

```

## testbench file

```
`timescale 1ns / 1ps
module tb_good_mux;
        // Inputs
        reg i0,i1,sel;
        // Outputs
        wire y;

        // Instantiate the Unit Under Test (UUT)
        good_mux uut (
                .sel(sel),
                .i0(i0),
                .i1(i1),
                .y(y)
        );

        initial begin
        $dumpfile("tb_good_mux.vcd");
        $dumpvars(0,tb_good_mux);
        // Initialize Inputs
        sel = 0;
        i0 = 0;
        i1 = 0;
        #300 $finish;
        end

always #75 sel = ~sel;
always #10 i0 = ~i0;
always #55 i1 = ~i1;
endmodule

```

# Labs using yosys and SKY130 PDK RTL to Netlist creation

<img width="1092" height="579" alt="image" src="https://github.com/user-attachments/assets/2d419285-37a5-4ac9-b329-b6da6dbfa407" />


<img width="359" height="535" alt="image" src="https://github.com/user-attachments/assets/20be9a6a-e85d-4904-a2c5-fbd3939a1245" />


## Read Liberty File

```
read_liberty -lib ../my_lib/lib/sky130_fd_sc_hd__tt_025C_1v80.lib
```

<img width="1615" height="310" alt="image" src="https://github.com/user-attachments/assets/1575d913-5d49-49c4-bf8f-dca5417ab47d" />

## Read Verilog File

```
read_verilog good_mux.v
```

<img width="1615" height="198" alt="image" src="https://github.com/user-attachments/assets/b5cb00ab-eaf0-4553-a035-1aaea9c52030" />

## Synthesize

```
synth -top good_mux
```

<img width="1615" height="806" alt="image" src="https://github.com/user-attachments/assets/d838f867-66b9-4529-8612-58843748297d" />

## Generate RTL report

```
abc -liberty ../my_lib/lib/sky130_fd_sc_hd__tt_025C_1v80.lib 

```
<img width="1615" height="229" alt="image" src="https://github.com/user-attachments/assets/d72455bd-d83b-4176-9f8b-90ee24b54515" />

<img width="1912" height="665" alt="image" src="https://github.com/user-attachments/assets/200afbfd-7427-46c0-9e9c-261785dcc892" />








