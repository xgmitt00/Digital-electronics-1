# CV 8

https://github.com/xgmitt00/Digital-electronics-1

## Preparation tasks
### Completed state table

| **Input P** | `0` | `0` | `1` | `1` | `0` | `1` | `0` | `1` | `1` | `1` | `1` | `0` | `0` | `1` | `1` | `1` |
| :-- | :-: | :-: | :-: | :-: | :-: | :-: | :-: | :-: | :-: | :-: | :-: | :-: | :-: | :-: | :-: | :-: |
| **Clock** | ![rising](Images/eq_uparrow.png) | ![rising](Images/eq_uparrow.png) | ![rising](Images/eq_uparrow.png) | ![rising](Images/eq_uparrow.png) | ![rising](Images/eq_uparrow.png) | ![rising](Images/eq_uparrow.png) | ![rising](Images/eq_uparrow.png) | ![rising](Images/eq_uparrow.png) | ![rising](Images/eq_uparrow.png) | ![rising](Images/eq_uparrow.png) | ![rising](Images/eq_uparrow.png) | ![rising](Images/eq_uparrow.png) | ![rising](Images/eq_uparrow.png) | ![rising](Images/eq_uparrow.png) | ![rising](Images/eq_uparrow.png) | ![rising](Images/eq_uparrow.png) |
| **State** | A | A | B | C | C | D | A | B | C | D | B | B | B | C | D | B |
| **Output R** | `0` | `0` | `0` | `0` | `0` | `1` | `0` | `0` | `0` | `1` | `0` | `0` | `0` | `0` | `1` | `0` |

### Figure with connection of RGB LEDs on Nexys A7

| **RGB LED** | **Artix-7 pin names** | **Red** | **Yellow** | **Green** |
| :-: | :-: | :-: | :-: | :-: |
| LD16 | N15, M16, R12 | `1,0,0` | `1,1,0` | `0,1,0` |
| LD17 | N16, R11, G14 | `1,0,0` | `1,1,0` | `0,1,0` |

## Traffic light controller
### State diagram
### Listing of VHDL code of sequential process p_traffic_fsm
### Listing of VHDL code of combinatorial process p_output_fsm
### Screenshot(s) of the simulation

## Smart controller
### State table
| **Current state** | **Direction South** | **Direction West** | **Delay** | **No Cars** | **Cars to West** | **Cars to South** | **Cars both directions** |
| :-- | :-: | :-: | :-: | :-: | :-: | :-: | :-: |
| `STOP1`      | red    | red | 1 sec | `OPTION1` | `OPTION1` | `OPTION1` | `OPTION1` |
| `WEST_GO`    | red    | green | 4 sec | `WEST_GO` | `WEST_GO` | `WEST_WAIT` | `WEST_WAIT` |
| `WEST_WAIT`  | red    | yellow | 2 sec | `STOP2` | `STOP2` | `STOP2` | `STOP2` |
| `STOP2`      | red    | red | 1 sec | `OPTION2` | `OPTION2` | `OPTION2` | `OPTION2` |
| `SOUTH_GO`   | green  | red | 4 sec | `SOUTH_GO` | `SOUTH_WAIT` | `SOUTH_GO` | `SOUTH_WAIT` |
| `SOUTH_WAIT` | yellow | red | 2 sec | `STOP1` | `STOP1` | `STOP1` | `STOP1` |
| `OPTION1` | red | red | 0 sec | `WEST_GO` | `WEST_GO` | `SOUTH_GO` | `WEST_GO` |
| `OPTION2` | red | red | 0 sec | `SOUTH_GO` | `WEST_GO` | `SOUTH_GO` | `SOUTH_GO` |
### State diagram
### Listing of VHDL code of sequential process p_smart_traffic_fsm
