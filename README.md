
There is a well-established opinion that decimal rounding of floating-point numbers is necessary only when outputting the results of binary calculations (float, double, etc.) to a decimal string. Let us show that this is not the case. Let's assume that after some calculations we got a float: y = 1.00011101100011011100010e-9. Its decimal value is x = 2.1786023862659931182861328125E-3. Binary y will be written to the processor memory. The question arises, how many digits in the number x can be trusted when outputting x to a string? On the other hand, how many significant digits must x be rounded to for all the digits in the string to be correct?
 We know that float allows you to represent a decimal floating-point number in which the seven decimal digits of the mantissa can be trusted. Let's round the mantissa of our decimal x when outputting to a string to 7 significant digits and get the number X = 2.178602E-3. This rounded float number will be y'=1.00011101100011011100000e-9. The number y' will be the binary equivalent of the number X. The decimal value of binary y' is x' = 2.178601920604705810546875E-3 and is the closest to X. In this case, the number y ≥ y' will be stored in the processor memory. To minimize calculation errors in further arithmetic operations, we must convert the binary y to y' and store the number y' in memory. We call such a reduction correct decimal rounding of a binary number.
At https://github.com/yur-spiridonov/Decimal-rounding-of-binary-numbers/commit/2084c8aeb28a785dee7fc98822b575da09194bbd provides C++ test code for proper decimal rounding of binary numbers, based on the concept of arithmetic of binary equivalents of decimal numbers (ABEDN). The theoretical justification for this code is given in a paper whose preprint can be found at [https://www.techrxiv.org/articles/preprint/Arithmetic_of_binary_equivalents_of_decimal_numbers/21355383/1.]

