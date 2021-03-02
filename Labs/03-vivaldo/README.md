https://github.com/xberan49/Digital-electronics-1

## 1. Preparation tasks


## 2. Two-bit wide 4-to-1 multiplexer

### Listing of VHDL architecture from source file

**architecture** Behavioral of mux_2bit_4to1 **is
begin**
    f_o <= a_i **when** (sel_i = "00") **else**
           b_i **when** (sel_i = "01") **else**
           c_i **when** (sel_i = "10") **else**
           d_i;       

**end architecture** Behavioral;


### Listing of VHDL stimulus process from testbench file

p_stimulus : **process
    begin**
        -- Report a note at the beginning of stimulus process
        **report** "Stimulus process started" **severity** note;
.
        s_d <= "00"; s_c <= "00"; s_b <= "00"; s_a <= "00"; 
        s_sel <= "00"; **wait for** 100 ns;
.
        s_d <= "10"; s_c <= "01"; s_b <= "01"; s_a <= "00"; 
        s_sel <= "00"; **wait for** 100 ns;
.
        s_d <= "10"; s_c <= "01"; s_b <= "01"; s_a <= "11"; 
        s_sel <= "00"; **wait for** 100 ns;
.
        s_d <= "10"; s_c <= "01"; s_b <= "01"; s_a <= "00"; 
        s_sel <= "01"; **wait for** 100 ns;
.
        s_d <= "10"; s_c <= "01"; s_b <= "11"; s_a <= "00"; 
        s_sel <= "01"; **wait for** 100 ns;
        -- WRITE OTHER TEST CASES HERE
.
.
        -- Report a note at the end of stimulus process
        **report** "Stimulus process finished" **severity** note;
        **wait**;
    **end process** p_stimulus;

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


