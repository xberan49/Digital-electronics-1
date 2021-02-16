## Verification of De Morgan's laws ##

### Listing of VHDL code ###

1.    f_o  <= ((not b_i) and a_i) or ((not c_i) and (not b_i));
2.    fnand_o <= not(not((not b_i) and a_i) and not((not c_i) and (not b_i)));
3.    fnor_o <= not(b_i or (not a_i)) or not(c_i or b_i);

### Screenshot with simulated time waveforms ###
![Screenshot with simulated time waveforms](https://github.com/xberan49/Digital-electronics-1/blob/main/Labs/01-gates/images/De_Morgans.png)

[EDA Playground example](https://www.edaplayground.com/x/8KYY)



## Verification of Distributive laws ##

### Listing of VHDL code ###

1. f1_o <= (x_i and y_i) or (x_i and z_i);
2. f2_o <= x_i and (y_i or z_i);
3. f3_o <= (x_i or y_i) and (x_i or z_i);
4. f4_o <= x_i or (y_i and z_i);

### Screenshot with simulated time waveforms ###
![Screenshot with simulated time waveforms](https://github.com/xberan49/Digital-electronics-1/blob/main/Labs/01-gates/images/Distributive.png)

[EDA Playground example](https://www.edaplayground.com/x/FLfZ)

