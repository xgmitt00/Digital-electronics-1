# CV 5

https://github.com/xgmitt00/Digital-electronics-1

### Connection table

| **Name** | **Port** |**Function** |
| :-: | :-: | :-: | 
| J15 | SW | L=0V, H=3,3V | 
| P17 | RESET | L=0V, H=3,3V |
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

### Table with calculated values

| **Time interval** | **Number of clk periods** | **Number of clk periods in hex** | **Number of clk periods in binary** |
| :-: | :-: | :-: | :-: |
| 2&nbsp;ms | 200 000 | `x"3_0d40"` | `b"0011_0000_1101_0100_0000"` |
| 4&nbsp;ms | 400 000 | `x"6_1a80"` | `b"0110_0001_1010_1000_0000"` |
| 10&nbsp;ms | 1 000 000 | `x"f_4240"` | `b"1111_0100_0010_0100_0000"` |
| 250&nbsp;ms | 25 000 000 | `x"17d_7840"` | `b"0001_0111_1101_0111_1000_0100_0000"` |
| 500&nbsp;ms | 50 000 000 | `x"2fa_f080"` | `b"0010_1111_1010_1111_0000_1000_0000"` |
| 1&nbsp;sec | 100 000 000 | `x"5f5_e100"` | `b"0101_1111_0101_1110_0001_0000_0000"` |

## Bidirectional counter
### Listing of VHDL code
```vhdl
architecture behavioral of cnt_up_down is
    signal s_cnt_local : unsigned(g_CNT_WIDTH - 1 downto 0);
begin
    p_cnt_up_down : process(clk)
    begin
        if rising_edge(clk) then       
            if (reset = '1') then 
                s_cnt_local <= (others => '0'); 
            elsif (en_i = '1') then    
            if (cnt_up_i = '1') then
                s_cnt_local <= s_cnt_local + 1;      
            elsif (cnt_up_i = '0') then
                s_cnt_local <= s_cnt_local - 1;                
             end if;
            end if;
        end if;
    end process p_cnt_up_down;
end architecture behavioral;
```
### VHDL reset process from testbench
```vhdl
    p_reset_gen : process
    begin
        s_reset <= '0';
        wait for 12 ns;
        s_reset <= '1';
        wait for 73 ns;
        s_reset <= '0';
        wait;
    end process p_reset_gen;
```
### VHDL stimulus process from testbench
```vhdl
   p_stimulus : process
    begin
        report "Stimulus process started" severity note;
        s_en     <= '1';
        s_cnt_up <= '1';
        wait for 230 ns;
        s_cnt_up <= '0';
        wait for 230 ns;
        s_en     <= '0';
        report "Stimulus process finished" severity note;
        wait;
    end process p_stimulus;
```
### Screenshot with simulated time waveforms

![Sim](Images/1.PNG)

## Top level
### Listing of VHDL code
```vhdl
library IEEE;
use IEEE.STD_LOGIC_1164.ALL;
entity top is
    Port ( CLK100MHZ : in STD_LOGIC;
           BTNC : in STD_LOGIC;
           SW : in STD_LOGIC_VECTOR (1-1 downto 0);
           LED : out STD_LOGIC_VECTOR (4-1 downto 0);
           CA : out STD_LOGIC;
           CB : out STD_LOGIC;
           CC : out STD_LOGIC;
           CD : out STD_LOGIC;
           CE : out STD_LOGIC;
           CF : out STD_LOGIC;
           CG : out STD_LOGIC;
           AN : out STD_LOGIC_VECTOR (8 - 1 downto 0));
end top;

architecture Behavioral of top is
    signal s_en  : std_logic;
    signal s_cnt : std_logic_vector(16 - 1 downto 0);
begin
    clk_en0 : entity work.clock_enable
        generic map(
            g_MAX => 100000000
        )
        port map(
            clk     => CLK100MHZ,
            reset   => BTNC,
            ce_o    => s_en
        );   
    bin_cnt0 : entity work.cnt_up_down
        generic map(
            g_CNT_WIDTH => 4
        )
        port map(
             clk     => CLK100MHZ,
            reset   => BTNC,
            en_i    => s_en,
            cnt_up_i    => SW(0),
            cnt_o   => s_cnt
        );
    LED(3 downto 0) <= s_cnt;
    hex2seg : entity work.hex_7seg
        port map(
            hex_i    => s_cnt,
            seg_o(6) => CA,
            seg_o(5) => CB,
            seg_o(4) => CC,
            seg_o(3) => CD,
            seg_o(2) => CE,
            seg_o(1) => CF,
            seg_o(0) => CG
        );
    AN <= b"1111_1110";
end architecture Behavioral;
```
### Image of the top layer including both counters

![Sim](Images/2.png)
