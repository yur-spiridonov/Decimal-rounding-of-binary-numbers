
There is a well-established opinion that decimal rounding is necessary only when outputting the results of binary calculations (float, double, etc.) to a decimal string. Suppose after some calculations we got a float: 1.00011101100011011100010e-9= 2.1786023862659931182861328125E-3. The question arises, how many digits in this number can be trusted? Or, to what the number of significant digits should our number be rounded so that all the digits are correct. We know that float allows you to represent a decimal number with 7 decimal digits of the mantissa. Let's round the mantissa of our number when outputting to a string to 7 digits and get the number 2.178602E-3.At the same time, the number 2.1786023862659931182861328125E-3 will be stored in the processor memory.  Therefore, if in the next step we multiply this number by 10E6, then we will get 2178602.3862659931182861328125E-3, while the correct result will be 2.178602E-3*10E6 = 2178602E-3. To minimize the calculation error, we must store the binary equivalent of the decimal 2.178602E-3 in memory. This decimal number is float 1.00011101100011011100000E-9. Which is equal to decimal 2.178601920604705810546875E-3. The number 1.00011101100011011100000E-9 will be called a properly-rounded binary number. We will write this number into the processor's memory.
I propose a C++ test code for proper decimal rounding of binary numbers, based on the concept of arithmetic of binary equivalents of decimal numbers. The theoretical justification for this code is given in my work, the preprint of which can be found at https://www.techrxiv.org/articles/preprint/The_arithmetic_of_binary_equivalents_of_decimal_numbers/19294511/1 .
