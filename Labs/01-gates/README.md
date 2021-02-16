## Verification of De Morgan's laws ##

### Listing of VHDL code ###

1. library IEEE;
2. use IEEE.std_logic_1164.all;
3. 
4. ------------------------------------------------------------------------
5. -- Entity declaration for basic gates
6. ------------------------------------------------------------------------
7. entity gates is
8.   port(
9.  c_i     : in  std_logic;         -- Data input
10. b_i     : in  std_logic;         -- Data input
11. a_i     : in  std_logic;         -- Data input
12. f_o     : out std_logic;         -- OR output function
13. fnand_o : out std_logic;         -- AND output function
14. fnor_o  : out std_logic          -- XOR output function
15. );
16. end entity gates;
17.
18. ------------------------------------------------------------------------
19. -- Architecture body for basic gates
20. ------------------------------------------------------------------------
21. -- Usage of De Morgan laws on function f using nands and nors
22. architecture dataflow of gates is
23. begin
24.    f_o  <= ((not b_i) and a_i) or ((not c_i) and (not b_i));
25.    fnand_o <= not(not((not b_i) and a_i) and not((not c_i) and (not b_i)));
26.    fnor_o <= not(b_i or (not a_i)) or not(c_i or b_i);
27.
28. end architecture dataflow;

### Screenshot with simulated time waveforms ###
![Screenshot with simulated time waveforms](https://github.com/xberan49/Digital-electronics-1/blob/main/Labs/01-gates/images/De_Morgans.png)

[EDA Playground example](https://www.edaplayground.com/x/8KYY)



## Verification of Distributive laws ##

### Listing of VHDL code ###

1. library IEEE;
2. use IEEE.std_logic_1164.all;
3.
4. ------------------------------------------------------------------------
5. -- Entity declaration for basic gates
6. ------------------------------------------------------------------------
7. entity gates is
8. port(
9. z_i     : in  std_logic;         -- Data input
10. y_i     : in  std_logic;         -- Data input
11. x_i     : in  std_logic;         -- Data input
12. f1_o    : out std_logic;                
13. f2_o    : out std_logic;       
14. f3_o    : out std_logic; 
15. f4_o    : out std_logic
16.  );
17. end entity gates;
18.
19. ------------------------------------------------------------------------
20. -- Architecture body for basic gates
21. ------------------------------------------------------------------------
22. -- Usage of De Morgan laws on function f using nands and nors
23. architecture dataflow of gates is
24. begin
25. f1_o <= (x_i and y_i) or (x_i and z_i);
26. f2_o <= x_i and (y_i or z_i);
27. f3_o <= (x_i or y_i) and (x_i or z_i);
28. f4_o <= x_i or (y_i and z_i);
29.
30. end architecture dataflow;

### Screenshot with simulated time waveforms ###
![Screenshot with simulated time waveforms](https://github.com/xberan49/Digital-electronics-1/blob/main/Labs/01-gates/images/Distributive.png)

[EDA Playground example](https://www.edaplayground.com/x/FLfZ)

