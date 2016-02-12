//Indira Askaukar
// pc=rc2poly(rc)
//A function which converts the reflection coefficients to prediction filter polynomial.
//The input here is a vector rc which gives the reflection coefficients
//When rc is between -1 to 1 the filter is said to be stable
// The output is a vector stored as pc which defines the polynomial coefficients
// The first element of pc is always a 1.
//References

function [pc]=rc2poly(rc)
    pc=rc(1)//sets output vector i.e. pc to first element of input rc 
    l=length(rc)
    pc=pc(0:-1:1)//empty matrix 1-by-0
    for i=1:l//loops for all elements of rc
        pc=[pc+pc(i-1:-1:1)*rc(i),rc(i)]
        
    end
    pc=[1,pc]
endfunction







