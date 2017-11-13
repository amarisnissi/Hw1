1. a) function factorial = getFacWhile(n) 
      factorial = 1
         while(n~=1) factorial = factorial * n
            n=n-1
            end 
         end
      end

   b) function factorial = getFacFor(n) 
      factorial = 1
         for i=1:n 
            factorial = factorial * i
            end 
         end
      end

   c) function factorial = getFacVec(n) 
      factorial = prod(1:n)
      end
      
2. function timeFacFuncs(n)
   f = @() getFacWhile(n);
       disp(char(9) 'Average runtime: ', num2str(timeit(f)));
   f = @() getFacFor(n);
     disp(char(9) 'Average runtime: ', num2str(timeit(f)));
   f = @() getFacVec(n);
       disp(char(9) 'Average runtime: ', num2str(timeit(f)));

EXTRA CREDIT

