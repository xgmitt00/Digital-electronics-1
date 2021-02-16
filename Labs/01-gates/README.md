# CV 1

### Links

https://www.edaplayground.com/x/VC9Z

https://github.com/xgmitt00/Digital-electronics-1

### Source code

```vhdl
architecture dataflow of gates is
begin
    f_o  <= ((not b_i) and a_i) or ((not c_i) and (not b_i));
    f_nand_o <= (a_i nand (not b_i)) nand ((not b_i) nand (not c_i));
    f_nor_o <= (a_i nor (not c_i)) nor b_i;

end architecture dataflow;
```

### De Morgan's law simulation


