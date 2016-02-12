//Indira Askaukar

// pc=rc2poly(rc)

//A function which converts the reflection coefficients to prediction filter polynomial.

//The input here is a vector rc which gives the reflection coefficients

//When rc is between -1 to 1 the filter is said to be stable

// The output is a vector stored as pc which defines the polynomial coefficients

// The first element of pc is always a 1.

//Examples:
//a=[0.3090    0.9800    0.0030    0.0082    0.1597]
//x=rc2poly(a)
 //x=   1.    0.6160941    0.9911707    0.1661259    0.1063811    0.1597
//References:
[1]Matlab help document.



function [pc]=rc2poly(rc)

    pc=rc(1)//sets output vector i.e. pc to first element of input rc 

    l=length(rc)

    pc=pc(0:-1:1)//empty matrix 1-by-0

    for i=1:l//loops for all elements of rc

        pc=[pc+pc(i-1:-1:1)*rc(i),rc(i)]
        
    end


    pc=[1,pc]

endfunction







