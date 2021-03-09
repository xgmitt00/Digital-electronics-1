# CV 4

https://github.com/xgmitt00/Digital-electronics-1

## Table with connection of 7-segment displays on Nexys A7 board

| **Name** | **Port** |**Function** |
| :-: | :-: | :-: | 
| T10 | CA | A | 
| R10 | CB | B |
| K16 | CC | C |
| K13 | CD | D |
| P15 | CE | E |
| T11 | CF | F |
| L18 | CG | G |
| J17 | AN[0] | KAT 1 |
| J18 | AN[1] | KAT 2 |
| T9 | AN[2] | KAT 3 |
| J14 | AN[3] | KAT 4 |
| P14 | AN[4] | KAT 5 |
| T14 | AN[5] | KAT 6 |
| K2 | AN[6] | KAT 7 |
| U13 | AN[7] | KAT 8 |

## Decoder truth table

| **Hex** | **Inputs** | **A** | **B** | **C** | **D** | **E** | **F** | **G** |
| :-: | :-: | :-: | :-: | :-: | :-: | :-: | :-: | :-: |
| 0 | 0000 | 0 | 0 | 0 | 0 | 0 | 0 | 1 |
| 1 | 0001 | 1 | 0 | 0 | 1 | 1 | 1 | 1 |
| 2 | 0010 | 0 | 0 | 1 | 0 | 0 | 1 | 0 |
| 3 | 0011 | 0 | 0 | 0 | 0 | 1 | 1 | 0 |
| 4 | 0100 | 1 | 0 | 0 | 1 | 1 | 0 | 0 |
| 5 | 0101 | 0 | 1 | 0 | 0 | 1 | 0 | 0 |
| 6 | 0110 | 0 | 1 | 0 | 0 | 0 | 0 | 0 |
| 7 | 0111 | 0 | 0 | 0 | 1 | 1 | 1 | 1 |
| 8 | 1000 | 0 | 0 | 0 | 0 | 0 | 0 | 0 |
| 9 | 1001 | 0 | 0 | 0 | 0 | 1 | 0 | 0 |
| A | 1010 | 0 | 0 | 0 | 1 | 0 | 0 | 0 |
| B | 1011 | 1 | 1 | 0 | 0 | 0 | 0 | 0 |
| C | 1100 | 0 | 0 | 0 | 0 | 1 | 1 | 1 |
| D | 1101 | 1 | 0 | 0 | 0 | 0 | 1 | 0 |
| E | 1110 | 0 | 1 | 1 | 0 | 0 | 0 | 0 |
| F | 1111 | 0 | 1 | 1 | 1 | 0 | 0 | 0 |

## Seven-segment display decoder
### VHDL architecture from hex_7seg.vhd

```vhdl
architecture behavioral of hex_7seg is
begin

    p_7seg_decoder : process(hex_i)
    begin
        case hex_i is
            when "0000" => seg_o <= "0000001";
            
            when "0001" => seg_o <= "1001111";
            
            when "0010" => seg_o <= "0010010";
                
            when "0011" => seg_o <= "0000110";
                
            when "0100" => seg_o <= "1001100";
                
            when "0101" => seg_o <= "0100100";
                
            when "0110" => seg_o <= "0100000";
                
            when "0111" => seg_o <= "0001111";
                
            when "1000" => seg_o <= "0000000";
                
            when "1001" => seg_o <= "0000100";
                
            when "1010" => seg_o <= "0001000";
                
            when "1011" => seg_o <= "1100000";
                
            when "1100" => seg_o <= "0110001";
                
            when "1101" => seg_o <= "1000010";
    
            when "1110" => seg_o <= "0110000";     
                
            when "1111" => seg_o <= "0111000";     
        end case;
    end process p_7seg_decoder;

end architecture behavioral;
```

### VHDL stimulus process from testbench



### Simulation

### VHDL code from top.vhd

## LED(7:4) indicators

### Truth table

| Hex | Inputs | LED4 | LED5 | LED6 | LED7 |
| :-: | :-: | :-: | :-: | :-: | :-: |
| 0 | 0000 | 1 | 0 | 0 | 0 |
| 1 | 0001 | 0 | 0 | 1 | 0 |
| 2 | 0010 | 0 | 0 | 0 | 1 |
| 3 | 0011 | 0 | 0 | 1 | 0 |
| 4 | 0100 | 0 | 0 | 0 | 1 |
| 5 | 0101 | 0 | 0 | 1 | 0 |
| 6 | 0110 | 0 | 0 | 0 | 1 |
| 7 | 0111 | 0 | 0 | 1 | 0 |
| 8 | 1000 | 0 | 0 | 0 | 1 |
| 9 | 1001 | 0 | 0 | 1 | 0 |
| A | 1010 | 0 | 1 | 0 | 0 |
| B | 1011 | 0 | 1 | 0 | 0 |
| C | 1100 | 0 | 1 | 0 | 0 |
| D | 1101 | 0 | 1 | 0 | 0 |
| E | 1110 | 0 | 1 | 0 | 0 |
| F | 1111 | 0 | 1 | 0 | 0 |

### VHDL code for LEDs(7:4)

### Simulation
