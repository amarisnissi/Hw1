1.  Creating random 3-member student groups for the semester project.

function output = Rand3Group()
rng(131313);    %Initializes the seed so the number regenereates every time.%
triples = randperm(99);  %The array of numbers 1-99 is randomized.%
fileID = fopen('students.csv');
mytable = readtable('students.csv');
output = cell(33,3);
row = 1;
col = 1;
for i = 1:99
  output{row,col} =  cell2mat(mytable{triples(i),2});
  if(row == 33)
    row = 1;
    col = col + 1;
  else
    row = row + 1;
  end
end
fclose(fileID);
xlswrite('groups.xlsx',output);
end

2.  Reading scientific data from web using MATLAB.

3.  Simulating a fun Monte Carlo game. 

4.  Monte Carlo approximation of the number ππ. 
