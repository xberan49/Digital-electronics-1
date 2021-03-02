https://github.com/xberan49/Digital-electronics-1

## 1. Preparation tasks


## 2. Two-bit wide 4-to-1 multiplexer

### Listing of VHDL architecture from source file

1. **architecture** Behavioral of mux_2bit_4to1 **is begin**
2. f_o <= a_i **when** (sel_i = "00") **else**
3. b_i **when** (sel_i = "01") **else**
4. c_i **when** (sel_i = "10") **else**
5.         d_i;       
6.
7. **end architecture** Behavioral;


### Listing of VHDL stimulus process from testbench file

1. p_stimulus : **process begin**
2.   
3.     -- Report a note at the beginning of stimulus process
4.    **report** "Stimulus process started" **severity** note;
5.
6.     s_d <= "00"; s_c <= "00"; s_b <= "00"; s_a <= "00"; 
7.   s_sel <= "00"; **wait for** 100 ns;
8.
9.     s_d <= "10"; s_c <= "01"; s_b <= "01"; s_a <= "00"; 
10.  s_sel <= "00"; **wait for** 100 ns;
11.
12.    s_d <= "10"; s_c <= "01"; s_b <= "01"; s_a <= "11"; 
13.  s_sel <= "00"; **wait for** 100 ns;
14.
15.     s_d <= "10"; s_c <= "01"; s_b <= "01"; s_a <= "00"; 
16.     s_sel <= "01"; **wait for** 100 ns;
17.
18.     s_d <= "10"; s_c <= "01"; s_b <= "11"; s_a <= "00"; 
19.     s_sel <= "01"; **wait for** 100 ns;
20.     -- WRITE OTHER TEST CASES HERE
21.
22.
23.     -- Report a note at the end of stimulus process
24.       **report** "Stimulus process finished" **severity** note;
25.       **wait**;
26. **end process** p_stimulus;

### Screenshot with simulated time waveforms
![Simulated time waveforms](https://github.com/xberan49/Digital-electronics-1/blob/main/Labs/03-vivaldo/multiplexer-images/V%C3%BDst%C5%99i%C5%BEek.PNG)


## 3. Vivado tutorial
![1.](https://github.com/xberan49/Digital-electronics-1/blob/main/Labs/03-vivaldo/Vivaldo_manual/1..PNG)
![2.](https://github.com/xberan49/Digital-electronics-1/blob/main/Labs/03-vivaldo/Vivaldo_manual/2..PNG)
![3.](https://github.com/xberan49/Digital-electronics-1/blob/main/Labs/03-vivaldo/Vivaldo_manual/3..PNG)
![4.](https://github.com/xberan49/Digital-electronics-1/blob/main/Labs/03-vivaldo/Vivaldo_manual/4..PNG)
![5.](https://github.com/xberan49/Digital-electronics-1/blob/main/Labs/03-vivaldo/Vivaldo_manual/5..PNG)
![6.](https://github.com/xberan49/Digital-electronics-1/blob/main/Labs/03-vivaldo/Vivaldo_manual/6..PNG)
![7.](https://github.com/xberan49/Digital-electronics-1/blob/main/Labs/03-vivaldo/Vivaldo_manual/7..PNG)
![8.](https://github.com/xberan49/Digital-electronics-1/blob/main/Labs/03-vivaldo/Vivaldo_manual/8..PNG)
![9.](https://github.com/xberan49/Digital-electronics-1/blob/main/Labs/03-vivaldo/Vivaldo_manual/9..PNG)
![10.](https://github.com/xberan49/Digital-electronics-1/blob/main/Labs/03-vivaldo/Vivaldo_manual/10..PNG)
![11.](https://github.com/xberan49/Digital-electronics-1/blob/main/Labs/03-vivaldo/Vivaldo_manual/11..PNG)


