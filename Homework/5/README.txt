1.  Creating random 3-member student groups for the semester project.

>> function output = Rand3Group()
rng(131313);    % Initializes the seed so the number regenereates every time. %
triples = randperm(99);  % The array of numbers 1-99 is randomized. %
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

>> function fetchDataFromWeb()       % Part A %
data = webread('http://www.shahmoradi.org/ICP2017F/homework/5-problems/triggers.txt');
data = strsplit(data,'\n');
dataDir = '.swift/';
mkdir(dataDir);
missingCounter = 0;
for i=1:length(data)
                                  % Part B %
    try
       dataRepository = 'http://www.shahmoradi.org/ICP2017F/homework/5-problems/swift/'; 
       filename = ['GRB', data{i}, '_ep_flu.txt'];
       dataURL = [dataRepository,filename];
       fileID = fopen([dataDir,filename],'w');
       fprintf(fileID, '%s',webread(dataURL));
       fclose(fileID);
    catch
       missingCounter = missingCounter + 1;
       disp(['Requested file not found. Leaving ...', num2str(missingCounter)]);
    end
    
end
  disp(['There are ' , num2str(missingCounter), ' missing files.'])
end

                                  % Part C %

>> function plotDataFromFile()
directory = dir('C:\Users\amarisnissi\OneDrive\Documents\MATLAB\.swift');
success = 0;
data = [0,0];
     for i = 3:size(directory)
         if (directory(i).bytes>0)
             currentdata = readtable(['.swift/',directory(i).name]);
             try 
                 currarr = table2array(currentdata);
                 if (all(currarr(:,2)<0.0)) 
                     data = [data ; table2array(currentdata)];
                     success = success+1;
                 end
             catch
                 disp(['Could not recognize at', directory(i).name]);
             end
         end
     end
    
    scatter(exp(data(:,2)), data(:,1), 1,'red','filled','MarkerFaceAlpha',.1,'MarkerEdgeAlpha',.1);       % Check for the negativity of files here. %
   
    title('Plot of E_peak vs. Fluence for 650 Swift GRB events');       % Top label: main %
    xlabel('Fluence [ergs/cm^2]');        % Bottom label, main %
    set(gca,'xscale','log');
    xlim([1.0000e-08 1.0000e-02]);    % x-axis value limit %
    xticks([ 1.0000e-8 1.0000e-6 1.0000e-4 1.0000e-2]);       % x-axis values %
    
   
    ylabel('E_peak');             % Left label: main %
    set(gca,'yscale','log');   
    ylim([1.0000e0 1.0000e04]);   % y-axis value limit and value set %
    disp(num2str(success));
end 

3.  Simulating a fun Monte Carlo game. 

>> rng('shuffle');
winCounter = 0;    
nExperiments = 100000;
data = [0,0];
    for iExperiments = 1:nExperiments
        doors = [1,2,3];
        doorCar = randi(3);
        myChoice = randi(3);
        hostChoice = doors(doors~=doorCar);
        hostChoice = hostChoice(hostChoice~=myChoice);
        hostChoice = hostChoice(randi(length(hostChoice))); 
        mynewChoice = 6-hostChoice-myChoice;
        if(mynewChoice == doorCar)
           winCounter = winCounter + 1;
           data = [data ; [iExperiments winCounter/iExperiments]];
        end
    end
      scatter((data(:,1)), data(:,2),1);
      disp (['The winning percentage due to switching is', num2str(winCounter/nExperiments)]);
    end
end

4.  Monte Carlo approximation of the number ππ. 

>> function montypi()
n = 5000000;     % Let n be the number of points. %
points = rand(n,2);
circle = zeros(n,2);
pos = 1;
for i = 1:n
        dist = sqrt(points(i,1)^2+points(i,2)^2);
       if(dist<=1)
           circle(pos,1) = points(i,1);
           circle(pos,2) = points(i,2);
           pos = pos + 1;
       end
end
circle = circle(1:pos,1:2);
disp(['pi is ' num2str(4*length(circle)/(n)) ' for ' num2str(n) ' points']);
  c = [244,223,65];  %shade of preffered yellow
  c = c/255;
  scatter(circle(:,1),circle(:,2), 3, c, 'filled');
  title(['pi is ' num2str(4*length(circle)/(n)) ' for ' num2str(n) ' points']);
end
