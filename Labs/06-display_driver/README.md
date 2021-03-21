# Lab 6: Driver for multiple seven-segment displays

## 1. Preparation tasks


## 2. Display driver
### 2.1. Listing of VHDL code of the process p_mux with syntax highlighting

### 2.2. Listing of VHDL stimulus process from testbench file `tb_hex_7seg.vhd`
´´´VHDL
p_mux : process(s_cnt, data0_i, data1_i, data2_i, data3_i, dp_i)
    begin
        case s_cnt is
            when "11" =>
                s_hex <= data3_i;
                dp_o  <= dp_i(3);
                dig_o <= "0111";

            when "10" =>
                s_hex <= data2_i;
                dp_o  <= dp_i(2);
                dig_o <= "1011";

            when "01" =>
                s_hex <= data1_i;
                dp_o  <= dp_i(1);
                dig_o <= "1101";

            when others =>
                s_hex <= data0_i;
                dp_o  <= dp_i(0);
                dig_o <= "1110";
        end case;
    end process p_mux;
    ´´´

### 2.3. Screenshot with simulated time waveforms
![simulation](https://github.com/xberan49/Digital-electronics-1/blob/main/Labs/04-segment/images/display.PNG)


https://github.com/xberan49/Digital-electronics-1
