# scilab_sptb
//Indira Askaukar
//lsp=lpc_lsp(a)
//A function which converts prediction polynomial
//to line spectral frequencies

//Input variable is vector A which defines the prediction polynomial
//coefficients
//A should have all its roots inside unit circle.
//A should not include any complex terms.
//The function also normalises A if its 1st element is not 1.
//beacuse A(1) should be 1 before the conversion takes place.
//Output variable lsp is a vector giving the line spectral frequencies.
//Reference


function lsp= lpc2lsp(a)
//check if polynomial has complex coefficients.
a=a(:)
if ~isreal(a)
    error('Line spectral frequencies are not defined for complex polynomials')
end

//normalise to make A(1)=1
if a(1) ~= 1.0;
    a=a./a(1)
end

//check if roots are inside unit circle
if (max(abs(roots(a)))>=1.0)
error('The polynomial must have all the roots inside of the unit circle')
end





 l=length(a)
 P=zeros(l)
 Q=zeros(l)
 P(1)=1
 Q(1)=1
 if(modulo((l-1),2)==0)

   for i=2:l
   P(i)=(a(i)-a(l+2-i))
   Q(i)=(a(i)+a(l+2-i))
   end
   //removing the +1 zero from P and -1 from Q
   for i=2:l
     P(i)=P(i)+P(i-1)
     Q(i)=Q(i)-Q(i-1)
    
     end

else
     P(1)=1
     Q(1)=1
     for i=2:l
   P(i)=(a(i)-a(l+2-i))
   Q(i)=(a(i)+a(l+2-i))
     end
   P=[P;1]
   Q=[Q;1]
   
   P(1)=P(1)
   P(2)=P(2)
   //to remove zeros at +1 and -1 from P
   for i=3:l
   P(i)=P(i)+P(i-2)
   Q = Q
   end
   P(l+1)=0
    
end
r1=roots(P)
r2=roots(Q)
thetaP=zeros(l-1)
thetaQ=zeros(l-1)
for i=1:l-1
    
thetaP(i)=(atan(imag(r1(i)),real(r1(i))))
thetaQ(i)=(atan(imag(r2(i)),real(r2(i))))
end
l=l-1;
phase=zeros(l)
for i=1:l/2
phase(i)=thetaP(i*2)
phase(i+(l/2))=thetaQ(2*i)
end
phase=-phase
if(modulo (l,2)==0)
    phase=phase
    else
phase=[phase;thetaQ(l)]
end
//sort in ascending order
lsp=gsort(phase,'g','i')
