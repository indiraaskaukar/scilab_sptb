# scilab_sptb
rc2poly
The function converts reflection filter coefficients to prediction polynomial coefficients.

syntax
pc=rc2poly(rc)

Description:

input: 
Vector rc defining the reflection coefficients of filter.

output:
Vector pc which gives the prediction filter polynomial coefficients.

function:
pc=rc2poly(rc)
The reflection coefficients specified by vector rc are converted to the polynomial coefficients .
The Levinson's recursion algorithm is used to calculate the output.

Examples:
a=[0.3090    0.9800    0.0030    0.0082    0.1597]
x=rc2poly(a)
 x=   1.    0.6160941    0.9911707    0.1661259    0.1063811    0.1597

References:
[1]Matlab help document.






lpc2lsp
The function converts prediction filter coefficients to line spectral frequencies.
syntax
lsp= lpc2lsp(a)
Description:
input: 
vector a which defines the coefficients of prediction polynomial.
All the roots of a should be inside the unit circle.
Vector a is normalized if first element of a is not 1.
output: 
vector lsp ,which defines the line spectral frequencies.
function:
lsp=lpc2lsp(a) 
Generates two polynomials P and Q using a, where P is anti symmetric and Q is a symmetric polynomial.
If m is the order of polynomial a;
For m even: Q has zero at -1 and P has at +1
For m odd:  P has zero at +1 and -1.
The order reduction is done by removing these zeros.
The roots of new P and Q is calculated.
The phase angles of r1 and r2 gives the line spectral frequencies.
Examples:
a=[1.0000  -1.5419  1.3523  -0.7197  0.3206]
lsp=lpc2lsp(a)
lsp= 0.5288239  
    0.7817111  
    1.3209563  
    1.8529858  
References:
[1] SPEECH CODING ALGORITHMS Foundation and Evolution of Standardized Coders by WAI C. CHU. 
[2]Matlab help document.

