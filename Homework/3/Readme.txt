1.  The bell-shaped Gaussian probability density function,

      f(x)=12π−−√σexp[−12(x−μσ)2]
      f(x)=12πσexp⁡[−12(x−μσ)2]

is one of the most widely used functions in science and technology. The parameters of the function (μ∈[−∞,+∞]μ∈[−∞,+∞], σ>0σ>0) are prescribed real numbers. Write a MATLAB script for evaluating this function when μ=0μ=0, σ=2σ=2, x=1x=1. Verify your answer by getting the same result from Wolfram Alpha mathematical search engine, also by using MATLAB’s builtin function normpdf(xx,μμ,σσ).

Answer:
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

2.  As an egg cooks, the protein molecules in the egg first denature and then coagulate. When the temperature exceeds a critical point, reactions begin and proceed faster as the temperature increases. In the egg white, the proteins start to coagulate for temperatures above 63∘C63∘C, while in the yolk the proteins start to coagulate for temperatures above 70∘C70∘C. For a soft boiled egg, the white needs to have been heated long enough to coagulate at a temperature above 63∘C63∘C, but the yolk should not be heated above 70∘C70∘C. For a hard boiled egg, the center of the yolk should be allowed to reach 70∘C70∘C. The following formula expresses the time tt it takes (in seconds) for the center of the yolk to reach the temperature Ty (in Celsius degrees):

      t=M2/3 c ρ1/3Kπ2 (4π/3)2/3 ln[0.76T0−TwTy−Tw]
      t=M2/3 c ρ1/3Kπ2 (4π/3)2/3 ln⁡[0.76T0−TwTy−Tw]

where MM is the mass of egg, ρρ is the density, cc is the specific heat capacity, and KK is thermal conductivity. Relevant values are M=47 [g]M=47 [g] for a small egg and M=67 [g]M=67 [g] for a large egg, ρ=1.038 [g cm−3]ρ=1.038 [g cm−3], c=3.7 [J g−1 K−1]c=3.7 [J g−1 K−1], and K=5.4×10−3 [Wcm−1K−1]K=5.4×10−3 [Wcm−1K−1]. Furthermore, TwTw is the temperature (in C degrees) of the boiling water, and T0T0 is the original temperature (in C degrees) of the egg before being put in the water. Implement the formula in a MATLAB program, set Tw=100∘CTw=100∘C and Ty=70∘CTy=70∘C, and compute tt for a large egg taken from the fridge (T0=4∘CT0=4∘C) and from room temperature (T0=20∘CT0=20∘C). (Hint: Note that for this problem you will need to use MATLAB’s builtin function log(), and the predefined variable pi.)

Answer:
>> Tw=100;
>> Ty=70;
>> T0=4;
>> Tr=20;
>> answer = (67^(2/3))*3.7*(1.038^1/3)*log(0.76*(4-100)/(70-100))/(5.4*10^(-3)*pi*pi*(4*pi/3)^2/3);
>> disp(strcat('From the fridge it is ', num2str(answer), 'seconds'));
      From the fridge it is 60.2107 seconds
end
