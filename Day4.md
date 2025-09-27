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
