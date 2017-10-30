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
    list = "Please make sure that the directory has a name field and a bytes field";
   end
end

5. Solution:



