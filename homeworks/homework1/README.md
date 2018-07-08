# CS510 RUST Programming
# Homework 1
# Sunanth Sakthivel

## What I did:
A calculator program was made to take in command line arguments to perform sum, product, gcd or lcm functions depending on what the first argument was passed. IMPLEMENTATION: the command line arguments were loaded into vectors. Using these vectors, the correct number of arguments was checked (ensure that at least one argument is given in the command line). Depending on the command or function given in the command line (sum, product, gcd, or lcm) then that respective function is called with the passed in numeric values (which were loaded onto a vector). If no numeric functions are provided after a chosen function then the program will still exit successfuly. 

Function implementations (detailed comments provided in source code):
1. check_length(): this function was made to check if zero arguments were given in the command line (not including calc) and panic if needed.
2. calculate(): this function was designed using a series of if statements to carry out the desired function based on what command is passed in. If no numerical arguments are given and a valid command is passed in the we still exit sucessfully.
3. sum(): The sum of all numbers in the passed in vector is stored and returned. The initial result is initialized as 0.
4. product(): The product of all numbers in the passed in vector is stored and returned. The intial result is intialized as 1.
5. gcd_two(): Function takes two u64 integer arguments and firstly ensures that none of these arguments is 0 (gcd can't be calculated with 0). Next a while loop is made to continually subtract the smaller value of the two from the bigger until both values are the same and then the value is returned as the gcd.
6. gcd(): This function uses the gcd_two() function in a for loop in order to find the gcd of more than 2 numbers. The for loop iterates through all the values in the passed in vector. 
7. lcm_two(): This function takes two u64 integer arguments and will use the value of gcd_two() using the two arguments to then find the lcm using the fact that lcm = (one x two)/gcd.
8. lcm(): this function uses the lcm_two() function in a for loop in order to find the gcd of more than 2 numbers. The for loop iterates through all the values in the passed in vector.

## How it went:
One obstacle that I came across while doing this assignment was effectively loading up the command line arguments and seperating out the first argument as a string and parsing the rest of the arguments as integers. What seemed to work well was first collecting the entire command line as a vector of strings and then using another for loop to push the remaining arguments as u64 integers into another u64 vector. Another tricky aspect of this assignment was simply realizing the fact that by finding the gcd of two values we can iteratively use this function to find the gcd of more than two values; likewise, this same concept also applies to lcm. Lastly, the original implementation didn't use panics and instead relied on displaying in stderr and exiting with status code 1. I realized that unit testing for specific exit codes wasn't possible because these exit statuses aren't returned back for unit testing. Moreover, by instead using panics it was much more convenient and straightforward to test various test cases.  

## How I tested it:
1. sum_test(): this test will test the sum of more than 2 values, 2 values and 1 value.
2. product_test(): this test will test the prodcut of more than 2 values, multiple values (w/ 0) , 2 values and 1 value.
3. gcd_test(): this test will test the gcd of more than 2 values, 2 values and 1 value.
4. lcm_test(): this test will test the lcm of more than 2 values, 2 values and 1 value.
5. zero_gcd(): this test will ensure that the gcd function panics when 0 is included in the computation.
6. zero_lcm(): this test will ensure that the lcm function panics when 0 is included in the computation.
7. zero_args(): this test will ensure that check_length() function panics when zero arguments are given in command line (not including calc).
8. wrong_command(): this test will ensure the calculate function panics when an incorrect command is used in the command line
9. one_arg(): this test ensures that when no arguments are given beyond an existing command function, it will exit w/ success.

