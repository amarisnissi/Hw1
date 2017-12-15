load('Drand.mat');
global data nSample
data = Drand;
mu = 1;
sigma = 10;
Param = [mu,sigma];
nSample = length(data);
getTotalLogProb(Param)
fminsearch(@getTotalLogProb,Param)
