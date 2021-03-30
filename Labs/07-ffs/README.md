# CV 7

https://github.com/xgmitt00/Digital-electronics-1

## Characteristic equations and completed tables for flip-flops

### Table for D
| D | Qn | Q(n+1) | Comments |
| :-: | :-: | :-: | :-- |
| 0 | 0 | 0 | |
| 0 | 1 | 0 | |
| 1 | 0 | 1 | |
| 1 | 1 | 1 | |

### Table for JK
| J | K | Qn | Q(n+1) | Comments |
| :-: | :-: | :-: | :-: | :-- |
| 0 | 0 | 0 | 0 | No change |
| 0 | 0 | 1 | 1 | No change |
| 0 | 1 | 0 | 0 | Reset |
| 0 | 1 | 1 | 0 | Reset |
| 1 | 0 | 0 | 1 | Set |
| 1 | 0 | 1 | 1 | Set |
| 1 | 1 | 0 | 1 | Inverter |
| 1 | 1 | 1 | 0 | Inverter |

### Table for T
| T | Qn | Q(n+1) | Comments |
| :-: | :-: | :-: | :-- |
| 0 | 0 | 0 | Memory |
| 0 | 1 | 1 | Memory |
| 1 | 0 | 1 | Inverter |
| 1 | 1 | 0 | Inverter |

## D latch
### VHDL code listing of the process p_d_latch
```vhdl
p_d_latch : process (d, arst, en)
begin
    if (arst = '1') then
        q <= '0';
        q_bar <= '1';
    elsif(en = '1') then
        q <= d;
        q_bar <= not d;
    end if;
end process p_d_latch;
```
### Listing of VHDL reset and stimulus processes from the testbench 
```vhdl
 p_reset_gen : process
    begin
        s_arst <= '0';
        wait for 40 ns;        
        s_arst <= '1';
        wait for 150 ns;
        s_arst <= '0';
        wait;
    end process p_reset_gen;    
    ---------------------------------------------      
    p_stimulus : process
    begin
        report "Stimulus process started" severity note;       
        s_d <= '0';
        s_en <= '0';             
        wait for 10 ns;
        s_d <= '1';
        wait for 10 ns;
        s_d <= '0';
        wait for 10 ns;
        s_d <= '1';
        wait for 10 ns;
        s_d <= '0';
        wait for 10 ns;
        s_d <= '1';
        wait for 10 ns;
        s_d <= '0';
        wait for 10 ns;
        s_d <= '1';
        wait for 10 ns;
        s_d <= '0';
        wait for 10 ns;
        s_d <= '1';        
        s_en <= '1';       
        wait for 10 ns;
        s_d <= '1';
        wait for 10 ns;
        s_d <= '0';
        wait for 10 ns;
        s_d <= '1';
        wait for 10 ns;
        s_d <= '0';
        wait for 10 ns;
        s_d <= '1';
        wait for 10 ns;
        s_d <= '0';
        wait for 10 ns;
        s_d <= '1';
        wait for 10 ns;
        s_d <= '0';
        wait for 100 ns;
        s_d <= '1';       
        s_en <= '0';        
        wait for 10 ns;
        s_d <= '1';
        wait for 10 ns;
        s_d <= '0';
        wait for 10 ns;
        s_d <= '1';
        wait for 10 ns;
        s_d <= '0';
        wait for 10 ns;
        s_d <= '1';
        wait for 10 ns;
        s_d <= '0';
        wait for 10 ns;
        s_d <= '1';
        wait for 10 ns;
        s_d <= '0';
        wait for 10 ns;
        s_d <= '1';        
        report "Stimulus process finished" severity note;    
    end process p_stimulus;
```
### Screenshot with simulated time waveforms

## Flip-flops
## VHDL code listing of the processes
