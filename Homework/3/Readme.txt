1. Solution:
>> x=1;
>> mu=0;
>> sigma=2;
>> Y=normpdf(x,mu,sigma)            %% Y=normpdf(x) uses the standard normal deviation (mu=0, sigma=1) %%
Y =
    0.1760
    Or the long way: 
>> Y=(1/(sqrt(2*pi)*sigma))*(exp(-0.5*((x-mu)/(sigma))^2))
Y =
    0.1760
>> disp('For the values you entered here is the result of the gaussian probability density function');
For the values you entered here is the result of the gaussian probability density function
>> disp(Y);
    0.1760
end

2. Solution:
>> Tw=100;
>> Ty=70;
>> T0=4;
>> Tr=20;
>> answer = (67^(2/3))*3.7*(1.038^1/3)*log(0.76*(4-100)/(70-100))/(5.4*10^(-3)*pi*pi*(4*pi/3)^2/3);
>> disp(strcat('From the fridge it is ', num2str(answer), 'seconds'));
      From the fridge it is 60.2107 seconds
end

3. Solution:
%% The function getPolar(inputCartesianStruct). %%
function polar = getPolar(inputCartesianStruct)
if(isfield((inputCartesianStruct),'x') && isfield((inputCartesianStruct),'y'))
    r = sqrt((inputCartesianStruct.x)^2 + (inputCartesianStruct.y)^2);
    phi = acos(inputCartesianStruct.x/r);
    polar = struct;
    polar.r = r;
    polar.phi = phi;
else
    polar = "Be sure that the input is a structure with fields 'x' and 'y'";
end
%% The function getCart(inputPolarStruct). %%
>> function cartesian = getCart(inputPolarStruct)
if (isfield((inputPolarStruct),'r') && isfield((inputPolarStruct),'phi'))
    x = inputPolarStruct.r*cos(inputPolarStruct.phi);
    y = inputPolarStruct.r*sin(inputPolarStruct.phi);
    cartesian = struct;
    cartesian.x = x;
    cartesian.y = y;
else
    cartesian = "Be sure that the input is a structure with fields 'r' and 'phi'";
end

4. Solution:
function list = getList(directory)
   if(isfield((directory),'name') && isfield((directory),'bytes'))
     length = size(directory);
     for i = 1:length
      disp( [directory(i).name ' has ' num2str(directory(i).bytes)  ' bytes of storage']);
     end
 
   else
    list = "Be sure that the directory has a name field and a bytes field";
   end
end

5. Solution:
function runner = fib()
flag = false;
while (flag == false)
    prompt = 'Enter a non-negative integer or a type stop:';
    number = input(prompt);
    if(isa(number,'numeric'))
        if(number < 0)
            disp('The input argument is not a non-negative integer.');
        else
            disp(strcat('fib(',num2str(number),') = ', num2str(getFib(number))));
        end
    elseif(strcmp(number,'stop')==1)
        flag = true;
    elseif (number == 1)
        runner = 'This is just a redundant code so that runner has some output';
    else
        disp('The input argument is not a non-negative integer!');
    end
end
function f = getFib(n)
 if (n==0)
     f = 0;
    % disp(699);
 elseif (n == 1)
     f = 1; 
     %disp(f);
 else
     f = getFib(n-1) + getFib(n-2);   
     %disp(f);
 end
end

6. Solution:
function trianglearea = getTriangleArea(vertices)   
    if(isfield((vertices),'x') && isfield((vertices),'y'))
        x1 = vertices(1).x;
        x2 = vertices(2).x;
        x3 = vertices(3).x;
        y1 = vertices(1).y;
        y2 = vertices(2).y;
        y3 = vertices(3).y;
        %For convenience of actual function readibility
        trianglearea = 0.5*abs(x2*y3-x3*y2-x1*y3+x3*y1+x1*y2-x2*y1);
    else
        trianglearea = 'It is not an appropriate input';
    end
end

7. Solution:
function prime = isPrime(number)
   if(number == 2)           % An easy base case
       prime = true;
   elseif(number<2 || mod(number,2)==0)  % Another easy base case
       prime = false;
   else
       prime = isdivisibleby(number,round(number/2));  % Most useful line of code for this function
end
function divisible = isdivisibleby(number,factor) %This function uses the recursion principle
    if (factor == 1) % base case
        divisible = true;
    elseif(mod(number,factor)==0)
        divisible = false;
    else
        divisible = isdivisibleby(number,factor-1);
    end
end

8. Solution:
function general = genFunc(varargin)
    arr = cell2mat(varargin);
    if(isnumeric(arr(1)) == false)
         error('Dude, these arguments are not real numbers');
    elseif(size(arr,2)==0)
        a = 0; b = 0; c = 0;
    elseif(size(arr,2)==1)
        a = arr(1); b = 0; c = 0;
    elseif(size(arr,2)==2)
        a = arr(1); b = arr(2); c = 0;    
    elseif(size(arr,2)==3)
        a = arr(1); b = arr(2); c = arr(3);
    else
        error('Dude, thats too many inputs');
    end
    general = @evalfunc;

   function y = evalfunc(x)
       y = a*x*x + b*x + c;
      
   end

end
