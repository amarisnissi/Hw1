1.  Write a MATLAB script, named plotGrowthRate.m, that reads this chain.txt file, and then makes a plot of the fourth column of data (GrowthRate) in this file, that looks like the following,

chainfile = importdata('chain.txt'); 
data = chainfile.data; 
y = data(:,4); 
x = linspace(10^0,10^6,length(data)); 
plot(x,y,'-r','LineWidth',2); 
xlim([10^0 10^5]); 
box on; 
set(gca,'xscale','log');

2.  Write a MATLAB script named, robustWebRead.m that takes an input string containing a web address, then checks if the web address exists or not, if it exists, it returns the content of the web page as the output of the function, otherwise prints a message like the following and exits the function without breaking the MATLAB (e.g., without any abrupt stop).



3.  What is the difference between gca and gcf keywords in MATLAB? (what does each one do?)

The figure gcf returns the current figure handle. The current figure is the target for graphics output. If a particular figure does not exist in MATLAb, then gcf creates a figure and returns to its original handle. You can use the figure handle to alter figure properties.
The axis gca returns the current axes or chart for the current figure, which is oftentimes the last one committed or clicked on. Graphics functions, such as a title or label, target the current axes or chart. Use the ax to access and change properties of the axes or chart. If anytime the axes or charts do not exist, then the gca will create a Cartesian axes.
