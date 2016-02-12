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
