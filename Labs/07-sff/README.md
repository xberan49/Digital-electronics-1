# Lab 7: Latches and Flip-flops

## 1. Preparation tasks

   | **clk** | **d** | **q(n)** | **q(n+1)** | **Comments** |
   | :-: | :-: | :-: | :-: | :-- |
   | ↑ | 0 | 0 | 0 | No change |
   | ↑ | 0 | 1 | 0 | Change |
   | ↑ | 1 | 0 | 1 | Change |
   | ↑ | 1 | 1 | 1 | No change |

   | **clk** | **j** | **k** | **q(n)** | **q(n+1)** | **Comments** |
   | :-: | :-: | :-: | :-: | :-: | :-- |
   | ↑ | 0 | 0 | 0 | 0 | No change |
   | ↑ | 0 | 0 | 1 | 1 | No change |
   | ↑ | 0 | 1 | 0 | 0 | Reset |
   | ↑ | 0 | 1 | 1 | 0 | Reset |
   | ↑ | 1 | 0 | 0 | 1 | Set |
   | ↑ | 1 | 0 | 1 | 1 | Set |
   | ↑ | 1 | 1 | 0 | 1 | Toggle |
   | ↑ | 1 | 1 | 1 | 0 | Toggle |

   | **clk** | **t** | **q(n)** | **q(n+1)** | **Comments** |
   | :-: | :-: | :-: | :-: | :-- |
   | ↑ | 0 | 0 | 0 | No change |
   | ↑ | 0 | 1 | 1 | No change |
   | ↑ | 1 | 0 | 1 | Toggle |
   | ↑ | 1 | 1 | 0 | Toggle |



## 2. D latch
### 2.1. VHDL code listing of the process p_d_latch with syntax highlighting
```VHDL
library ieee;
use ieee.std_logic_1164.all;
use ieee.numeric_std.all;

-- Uncomment the following library declaration if using
-- arithmetic functions with Signed or Unsigned values
--use IEEE.NUMERIC_STD.ALL;

-- Uncomment the following library declaration if instantiating
-- any Xilinx leaf cells in this code.
--library UNISIM;
--use UNISIM.VComponents.all;

entity d_latch is
    Port ( 
           en    : in STD_LOGIC;
           arst  : in STD_LOGIC;
           d     : in STD_LOGIC;
           q     : out STD_LOGIC;
           q_bar : out STD_LOGIC);
end entity d_latch;

architecture Behavioral of d_latch is

begin
------------------------------------------------------------------------
-- p_alarm:
-- A combinational process of alarm clock.
------------------------------------------------------------------------
p_d_latch : process(d, arst, en)
begin
    if (arst = '1') then
        q     <= '0';
        q_bar <= '1';
    elsif (en = '1') then
        q     <= d;
        q_bar <= not d;
    end if;
end process p_d_latch;

end Behavioral;

```

### 2.2. Listing of VHDL reset and stimulus processes from the testbench tb_d_latch.vhd file with syntax highlighting and asserts
```VHDL
----------------------------------------------------------------
    -- Reset generation process
    --------------------------------------------------------------------
    --- WRITE YOUR CODE HERE
 p_reset_gen : process
    begin
        s_arst <= '0';
        wait for 40 ns;
        
        -- Reset activated
        s_arst <= '1';
        wait for 50 ns;

        s_arst <= '0';
        wait;
    end process p_reset_gen;
 --------------------------------------------------------------------
    -- Data generation process
    --------------------------------------------------------------------
    --- WRITE YOUR CODE HERE
    p_stimulus : process
    begin
        report "Stimulus proces started" severity note;
       s_d  <= '0';
       s_en <= '0';
       
       assert(s_q = '0' and s_q_bar = '0')
       report "asda" severity error;
       
       --d sekv
       wait for 10 ns;
       s_d  <= '1';
       wait for 10 ns;
       s_d  <= '0';
       wait for 10 ns;
       s_d  <= '1';
       wait for 10 ns;
       s_d  <= '0';
       wait for 10 ns;
       s_d  <= '1';
       wait for 10 ns;
       s_d  <= '0';
       --/d sekv
       assert(s_q = '0' and s_q_bar = '0')
       report "asda" severity error;
       
       s_en <= '1';
       
          --d sekv
       wait for 10 ns;
       s_d  <= '1';
       wait for 10 ns;
       s_d  <= '0';
       wait for 10 ns;
       s_d  <= '1';
       wait for 10 ns;
       s_d  <= '0';
       wait for 10 ns;
       s_d  <= '1';
       wait for 10 ns;
       s_en <= '0';
       wait for 100 ns;
       s_d  <= '0';
       --/d sekv
       
       s_en <= '1';
       
          --d sekv
       wait for 10 ns;
       s_d  <= '1';
       wait for 10 ns;
       s_d  <= '0';
       wait for 10 ns;
       s_d  <= '1';
       wait for 10 ns;
       s_d  <= '0';
       wait for 10 ns;
       s_d  <= '1';
       wait for 10 ns;
       s_d  <= '0';
       --/d sekv
       
       s_en <= '1';
       
        report "Stimulus process finished" severity note;
        wait;
    end process p_stimulus;
    
```
### 2.3. Screenshot with simulated time waveforms
![simulation](https://github.com/xberan49/Digital-electronics-1/blob/main/Labs/07-sff/images/D_latch.PNG)

## 3.Flip-flops
### 3.1. VHDL code listing 
#### 3.1.1. of the processes p_d_ff_arst
```VHDL
entity d_ff_arst is
  Port ( 
           clk     : in STD_LOGIC;
           arst  : in STD_LOGIC;
           d     : in STD_LOGIC;
           q     : out STD_LOGIC;
           q_bar : out STD_LOGIC
           );
end d_ff_arst;

architecture Behavioral of d_ff_arst is

begin
p_d_ff_arst : process(arst, clk)
begin
    if (arst = '1') then
        q     <= '0';
        q_bar <= '1';
        
    elsif rising_edge(clk) then
        q     <= d;
        q_bar <= not d;
    end if;
end process p_d_ff_arst;

end Behavioral;

```
#### 3.1.2. of the processes jk_ff_rst

```VHDL
entity jk_ff_rst is
Port ( 
           clk   : in STD_LOGIC;
           rst   : in STD_LOGIC;
           j     : in STD_LOGIC;
           k     : in STD_LOGIC;
           q     : out STD_LOGIC;
           q_bar : out STD_LOGIC
           );
end jk_ff_rst;

architecture Behavioral of jk_ff_rst is
    signal s_q :std_logic;
begin
p_jk_ff_rst : process(clk)
begin
    if rising_edge(clk) then
        if (rst = '1') then
            s_q <= '0';
        else 
        
            if (j = '0' and k = '0') then
                s_q <= s_q;
                
            elsif (j = '0' and k = '1') then
                s_q <= '0';
                
            elsif (j = '1' and k = '0') then
                s_q <= '1';
                
            elsif (j = '1' and k = '1') then
                s_q <= not s_q;
            
            end if;
            
        end if;
        
     end if;
 
end process p_d_ff_arst;

q <= s_q;
q_bar <= not s_q;

end Behavioral;


```

### 3.2. Listing of VHDL clock, reset and stimulus processes from the testbench files
#### 3.2.1. p_d_ff_arst
```VHDL
--------------------------------------------------------------------
    -- Clock generation process
    --------------------------------------------------------------------
    p_clk_gen : process
    begin
        while now < 750 ns loop         -- 75 periods of 100MHz clock
            s_clk_100MHz <= '0';
            wait for c_CLK_100MHZ_PERIOD / 2;
            s_clk_100MHz <= '1';
            wait for c_CLK_100MHZ_PERIOD / 2;
        end loop;
        wait;
    end process p_clk_gen;
   
    --------------------------------------------------------------------
    -- Reset generation process
    --------------------------------------------------------------------
    --- WRITE YOUR CODE HERE
     p_reset_gen : process
     begin
        s_arst <= '0';
        wait for 28 ns;
        
        -- Reset activated
        s_arst <= '1';
        wait for 13 ns;
        -- Reset activated
        s_arst <= '0';
        wait for 17 ns;
        
        s_arst <= '1';
        wait for 33 ns;
        
        s_arst <= '0';
        wait for 666 ns;
        
        s_arst <= '1';
        
        wait;
    end process p_reset_gen;
    --------------------------------------------------------------------
    -- Data generation process
    --------------------------------------------------------------------
    --- WRITE YOUR CODE HERE
    p_stimulus : process
    begin
        report "Stimulus proces started" severity note;
       s_d  <= '0';
       
       --d sekv
       wait for 14 ns;
       s_d  <= '1';
       wait for 10 ns;
       s_d  <= '0';
       
       wait for 6 ns;
       assert()
       report"";
       
       wait for 4 ns;
       s_d  <= '1';
       wait for 10 ns;
       s_d  <= '0';
       wait for 10 ns;
       s_d  <= '1';
       wait for 10 ns;
       s_d  <= '0';
       --/d sekv
       
       --d sekv
       wait for 14 ns;
       s_d  <= '1';
       wait for 10 ns;
       s_d  <= '0';
       wait for 10 ns;
       s_d  <= '1';
       wait for 10 ns;
       s_d  <= '0';
       wait for 10 ns;
       s_d  <= '1';
       wait for 10 ns;
       s_d  <= '0';
       --/d sekv
       
       
        report "Stimulus process finished" severity note;
        wait;
    end process p_stimulus;
    
```
#### 3.2.2. jk_ff_rst
  ```VHDL
  p_clk_gen : process
    begin
        while now < 750 ns loop         -- 75 periods of 100MHz clock
            s_clk_100MHz <= '0';
            wait for c_CLK_100MHZ_PERIOD / 2;
            s_clk_100MHz <= '1';
            wait for c_CLK_100MHZ_PERIOD / 2;
        end loop;
        wait;
    end process p_clk_gen;
   
    --------------------------------------------------------------------
    -- Reset generation process
    --------------------------------------------------------------------
    --- WRITE YOUR CODE HERE
     p_reset_gen : process
     begin
        s_rst <= '0';
        wait for 28 ns;
        
        -- Reset activated
        s_rst <= '1';
        wait for 13 ns;
        -- Reset activated
        s_rst <= '0';
        wait for 17 ns;
        
        s_rst <= '1';
        wait for 33 ns;
        
        s_rst <= '0';
        wait for 666 ns;
        
        s_rst <= '1';
        
        wait;
    end process p_reset_gen;
    --------------------------------------------------------------------
    -- Data generation process
    --------------------------------------------------------------------
    --- WRITE YOUR CODE HERE
    p_stimulus : process
    begin
        report "Stimulus proces started" severity note;
       s_j  <= '0';
       s_k  <= '0';
       
       --d sekv
       wait for 40 ns;
       s_j  <= '0';
       s_k  <= '0';
       assert (s_q = '1' and s_q_bar = '0') 
       report "x" severity note;
       
       wait for 10 ns;
       s_j  <= '0';
       s_k  <= '1';
       assert (s_q = '0' and s_q_bar = '1') 
       report "x" severity note;
       
       wait for 10 ns;
       s_j  <= '1';
       s_k  <= '0';
       assert (s_q = '1' and s_q_bar = '0') 
       report "x" severity note;
       
       wait for 10 ns;
       s_j  <= '1';
       s_k  <= '1';
       assert (s_q = '1' and s_q_bar = '0') 
       report "x" severity note;
       
       --/d sekv
       
       
        report "Stimulus process finished" severity note;
        wait;
    end process p_stimulus;
```
    
### 3.3.Screenshots with simulated time waveforms
#### 3.3.1. d_ff_arst
![simulation](https://github.com/xberan49/Digital-electronics-1/blob/main/Labs/07-sff/images/d_ff_asrt.PNG)

#### 3.3.2. jk_ff_rst
![simulation](https://github.com/xberan49/Digital-electronics-1/blob/main/Labs/07-sff/images/jk_ff_rst.PNG)
