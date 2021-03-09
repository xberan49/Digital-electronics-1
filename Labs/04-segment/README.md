# Lab 4: Seven-segment display decoder

## 1. Preparation tasks

| **Hex** | **Inputs** | **A** | **B** | **C** | **D** | **E** | **F** | **G** |
| :-: | :-: | :-: | :-: | :-: | :-: | :-: | :-: | :-: |
| 0 | 0000 | 0 | 0 | 0 | 0 | 0 | 0 | 1 |
| 1 | 0001 | 1 | 0 | 0 | 1 | 1 | 1 | 1 |
| 2 | 0011 | 0 | 0 | 1 | 0 | 0 | 1 | 0 |
| 3 | 0010 | 0 | 0 | 0 | 0 | 1 | 1 | 0 |
| 4 | 0101 | 1 | 0 | 0 | 1 | 1 | 0 | 0 |
| 5 | 0100 | 0 | 1 | 0 | 0 | 1 | 0 | 0 |
| 6 | 0111 | 0 | 1 | 0 | 0 | 0 | 0 | 0 |
| 7 | 0110 | 0 | 0 | 0 | 1 | 1 | 1 | 1 |
| 8 | 1000 | 0 | 0 | 0 | 0 | 0 | 0 | 0 |
| 9 | 1001 | 0 | 0 | 0 | 0 | 1 | 0 | 0 |
| A | 1010 | 0 | 0 | 0 | 1 | 0 | 0 | 0 |
| b | 1011 | 1 | 1 | 0 | 0 | 0 | 0 | 0 |
| C | 1100 | 0 | 1 | 1 | 0 | 0 | 0 | 1 |
| d | 1101 | 1 | 0 | 0 | 0 | 0 | 1 | 0 |
| E | 1110 | 0 | 1 | 1 | 0 | 0 | 0 | 0 |
| F | 1111 | 0 | 1 | 1 | 1 | 0 | 0 | 0 |

## 2. Seven-segment display decoder
### 2.1. Listing of VHDL architecture from source file `hex_7seg.vhd`
- p_7seg_decoder : process(hex_i)
- **begin**
- **case** hex_i is
- **when** "0000" =>
- seg_o <= "0000001";     -- 0
- **when** "0001" =>
- seg_o <= "1001111";     -- 1
- **when** "0010" =>
- seg_o <= "0010010";     -- 2
- **when** "0011" =>
- seg_o <= "0000110";     -- 3
- **when** "0100" =>
- seg_o <= "1001100";     -- 4
- **when** "0101" =>
- seg_o <= "0100100";     -- 5
- **when** "0110" =>
- **seg_o** <= "0100000";     -- 6
- **when** "0111" =>
- seg_o <= "0001111";     -- 7
- **whe**n "1000" =>
- seg_o <= "0000000";     -- 8
- **when** "1001" =>
- seg_o <= "0000100";     -- 9
- **when** "1010" =>
- seg_o <= "0001000";     -- A
- **when** "1011" =>
- seg_o <= "1100000";     -- b
- **when** "1100" =>
- seg_o <= "0110001";     -- C
- **when** "1101" =>
- seg_o <= "1000010";     -- d
- **when** "1110" =>
- seg_o <= "0110000";     -- E
- **when others** =>
- seg_o <= "0111000";     -- F
- **end case**;
- **end process** p_7seg_decoder;

### 2.2. Listing of VHDL stimulus process from testbench file `tb_hex_7seg.vhd`
- s_hex <= "0000"; **wait for** 100 ns; 
- s_hex <= "0001"; **wait for** 100 ns; 
- s_hex <= "0010"; **wait for** 100 ns; 
- s_hex <= "0011"; **wait for** 100 ns;
- s_hex <= "0100"; **wait for** 100 ns;
- s_hex <= "0101"; **wait for** 100 ns;
- s_hex <= "0110"; **wait for** 100 ns;
- s_hex <= "0111"; **wait for** 100 ns;
- s_hex <= "1000"; **wait for** 100 ns;
- s_hex <= "1001"; **wait for** 100 ns;
- s_hex <= "1010"; **wait for** 100 ns;
- s_hex <= "1011"; **wait for** 100 ns;
- s_hex <= "1100"; **wait for** 100 ns;
- s_hex <= "1101"; **wait for** 100 ns;
- s_hex <= "1110"; **wait for** 100 ns;
- s_hex <= "1111"; **wait for** 100 ns;

### 2.3. Screenshot with simulated time waveforms
![simulation](https://github.com/xberan49/Digital-electronics-1/blob/main/Labs/04-segment/images/display.PNG)


https://github.com/xberan49/Digital-electronics-1
