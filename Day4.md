# Day4: Gate-Level Simulation (GLS), Blocking vs. Non-Blocking in Verilog, and Synthesis-Simulation Mismatch

## Lab1: 

```
module ternary_operator_mux (input i0, input i1, input sel, output y);
  assign y = sel ? i1 : i0;
endmodule

```

```
iverilog ternary_operator_mux.v tb_ternary_operator_mux.v
./a.out
!gtkwave tb_ternary_operator_mux.vcd
```

<img width="1918" height="893" alt="image" src="https://github.com/user-attachments/assets/2ac2c234-9abc-42f4-a3ef-c7a29fd87bff" />


## Lab2: 

<img width="1919" height="906" alt="image" src="https://github.com/user-attachments/assets/b86c7aa4-1ca7-456c-be1c-1d5e39da44e1" />

## Lab 3: GLS of ternary_operator_mux

```
iverilog ../my_lib/verilog_model/primitives.v ../my_lib/verilog_model/sky130_fd_sc_hd.v ternary_operator_mux_net.v tb_ternary_operator_mux.v
./a.out
gtkwave tb_ternary_operator_mux.vcd
```
<img width="1919" height="907" alt="image" src="https://github.com/user-attachments/assets/f6ad30d6-9349-4328-a7a3-bfce5fe2ba32" />

## Lab4: Bad Mux

<img width="1919" height="896" alt="image" src="https://github.com/user-attachments/assets/ae04b740-7658-4915-8a1f-b00abb948a47" />

## Lab5: GLS of Bad Mux

<img width="1919" height="910" alt="image" src="https://github.com/user-attachments/assets/de961c6d-ed10-4fb5-9985-b692ce0125b0" />

## Lab6: blocking_caveat

```
module blocking_caveat (input a, input b, input c, output reg d);
  reg x;
  always @ (*) begin
    d = x & c;
    x = a | b;
  end
endmodule

```

    The order of assignments causes d to use the old value of x—not the newly computed value.
    Best Practice: Assign intermediate variables before using them.


Corrected order:
```
always @ (*) begin
  x = a | b;
  d = x & c;
end
```

<img width="1919" height="910" alt="image" src="https://github.com/user-attachments/assets/8ef4fc5f-9123-45a7-ba5c-945c3024d970" />

## Lab7: blocking_caveat synthesis

<img width="1919" height="898" alt="image" src="https://github.com/user-attachments/assets/149716c7-6e2a-4ba8-aaf6-514bcbf0007e" />








