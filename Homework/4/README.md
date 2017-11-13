1. 
a) WHILE LOOP

function convert = convertTempWhile(InVec,statement)
convert = zeros(1,length(InVec));
if(strcmp(statement,'C2F')==1)
    i=1;
    while(i~=length(InVec)+1)
        convert(1,i) = 1.8*InVec(1,i)+32;
        i=i+1;
    end
elseif(strcmp(statement,'F2C')==1)
     i=1;
    while(i~=length(InVec)+1)
        convert(1,i) = 5*(InVec(1,i)-32)/9;
        i=i+1;
    end
else
    error('Input must be C2F or F2C');
end
end

b) FOR LOOP

function convert = convertTempFor(InVec,statement)
convert = zeros(1,length(InVec));
if(strcmp(statement,'C2F')==1)
    for i=1:length(InVec)
        convert(1,i) = 1.8*InVec(1,i)+32;
    end
elseif(strcmp(statement,'F2C')==1)
    for i=1:length(InVec)
        convert(1,i) = 5*(InVec(1,i)-32)/9;
    end
else
    error('Input must be C2F or F2C');
end
end

c) VECTORIZATION

function convert = convertTempVec(InVec,statement)
convert = zeros(1,length(InVec));
if(strcmp(statement,'C2F')==1)
    i = 1:length(InVec);
    convert(1,i) = 1.8*InVec(1,i)+32;
elseif(strcmp(statement,'F2C')==1)
  	i = 1:length(InVec);
    convert(1,i) = 5*(InVec(1,i)-32)/9;
else
    error('Input must be C2F or F2C');
end
end

2. starterdata = [-20, -15, -10, -5, 0, 5, 10, 15, 20, 25, 30, 35, 40];
>> tic, convertTempFor(starterdata,'C2F') ,toc
ans =
    -4     5    14    23    32    41    50    59    68    77    86    95   104
Time duration is 0.003072 seconds.
>> tic, convertTempWhile(starterdata,'C2F') ,toc
ans =
    -4     5    14    23    32    41    50    59    68    77    86    95   104
Time duration is 0.002207 seconds.
>> tic, convertTempVec(starterdata,'C2F') ,toc
ans =
    -4     5    14    23    32    41    50    59    68    77    86    95   104
Time duration is 0.001674 seconds.

As shown, Vectorization is faster than a while condition, which is faster than a for loop. 
This is because rather than looping, it uses converts the input array into a column vector,
hence allows it to perfrom an operation to all elements in the vector at once.

3. function statement = extractLetter(cellofchars)
if(isa(cellofchars,'cell'))
    arr = [];
    length = size(cellofchars);
    for i=1:length(2)      
        arr = [arr cellofchars{i}];
    end
 statement = strjoin(arr,''); 
        %elementlength = size(List{i})
        %for j=1:elementlength(2)
        %disp(char(statement(i
else
    error('Input must be a cell array');
end
end

4. The code takes the number 2.0 and takes its square root. Then it squares the result which is now the output.
It then takes the number 2.0 and takes its takes its square root two times and  squares the result two times, which is the output.
This process repeats until it takes the number 2.0, square roots it n times and then squares the result n times.

**The result is due to a precision-roundoff issue.**

When the code is run, it starts by taking the square root of 2. Since the square root of 2 is irrational, its exact value has infinitely many digits,
but sqrt is a double method which restricts its size to 8 bytes(16 decimal places after a one digit number) which involves rounding that value. When that value is squared, again it must round once more.
This value is very close but slightly off the number 2, giving 2.000000000000004 instead.

So, when it takes the square root twice and then squares it twice the result is even more deviated from the original number, giving 1.9999999999999996. After many iterations when it square roots 51
times and then squares 51 times the answer is 1.6487212645509468. But on the 52nd iteration when it square roots the number '2' 52 times it gets the number '1', so when it squares '1' 52 times it is
still '1'. Essentially after square rooting too many times then answer is so close to '1' that
when it gets cut off due to the size limit of the double variable type, it displays '1'.

5. In this code the only way 1.0 ~= 1.0 + eps could be false is if eps = 0. 
But in the code, in each iteration eps is divided by 2, so eps starts out at 1 and becomes 0.5,
then 0.25, then 0.125 and so on. Eventually eps is so small (1.1102e-16) that when its added to '1.0'
and that value is truncated to a certain number of decimal places (because a double precision
variable is only 8 bytes or 16 decimal places after a one digit number), the result is just
1.0000000000000000, and that value is equivalent to 1.0, so it breaks out of the while loop 
and displays the final value for the variable eps.

6. function largest = getLargestprime(number)
for i = number: -1 :1
    if isprime(i)
        largest = i;
        break;
    end
end

7. 
a) function fib()
    n = input('Please enter a non-negative integer or type stop: ','s');
    if strcmp(n,'stop')
        return
    else
        n = str2double(n);
        if isreal(n)
            if n>=0 && round(n)==n
                disp(['fib(',num2str(n),') = ',num2str(getFib(n))]);
                f = @() getFib(n);
                disp([ char(9) 'average runtime: ' num2str(timeit(f))]);
                fib()
                return
            end
        end
        disp('The input argument is not a non-negative integer!');
        fib()
    end
    function fib = getFib(n_int)
        if n_int == 0
            fib = 0;
        elseif n_int == 1
            fib = 1;
        else
            fib = getFib(n_int-1) + getFib(n_int-2);
        end
    end
end


b) function fibloop()
    n = input('Please enter a non-negative integer or type stop: ','s');
    if strcmp(n,'stop')
        return
    else
        n = str2double(n);
        if isreal(n)
            if n>=0 && round(n)==n
                disp(['fib(',num2str(n),') = ',num2str(getFib(n))]);
                 f = @() getFib(n);
                disp([ char(9) 'average runtime: ' num2str(timeit(f))]);
                fibloop()
                return
            end
        end
        disp('The input argument is not a non-negative integer!');
        fib()
    end
    function fib = getFib(n_int)
        firstnum = 0;
        secondnum = 1;
        for i = 2:n_int
            fib = firstnum+secondnum;
            firstnum=secondnum;
            secondnum=fib;
        end
    end
end

c)

fib()
Please enter a non-negative integer or type stop: 10
fib(10) = 55
	average runtime: 2.3984e-05
Please enter a non-negative integer or type stop: 15
fib(15) = 610
	average runtime: 0.0001547
Please enter a non-negative integer or type stop: 20
fib(20) = 6765
	average runtime: 0.0013825
Please enter a non-negative integer or type stop: 25
fib(25) = 75025
	average runtime: 0.014347
Please enter a non-negative integer or type stop: 30
fib(30) = 832040
	average runtime: 0.14569
Please enter a non-negative integer or type stop: 35
fib(35) = 9227465
	average runtime: 1.6679
Please enter a non-negative integer or type stop: stop

fibLoop()
Please enter a non-negative integer or type stop: 10
fib(10) = 55
	average runtime: 7.7406e-06
Please enter a non-negative integer or type stop: 15
fib(15) = 610
	average runtime: 6.3455e-06
Please enter a non-negative integer or type stop: 20
fib(20) = 6765
	average runtime: 5.8015e-06
Please enter a non-negative integer or type stop: 25
fib(25) = 75025
	average runtime: 6.0212e-06
Please enter a non-negative integer or type stop: 30
fib(30) = 832040
	average runtime: 5.9943e-06
Please enter a non-negative integer or type stop: 35
fib(35) = 9227465
	average runtime: 6.3273e-06
Please enter a non-negative integer or type stop: stop

The fibLoop is faster and more efficient because it doesn't use recursion. 
When fib runs the getFib method, it is using a recursive call to the getFib
for a number one less than it, and it keeps on going until it reaches n = 2.
Then it calculates fib(2) to send back to fib(3) and so on, until it finally
calculates all the fib values needed to get fib(n-1) and fib(n-2) so that it 
can calculate fib(n). The recursive process is wasting time by going all the
way back to the base case and then relaying the information back. The fibLoop
is faster because it starts at the base case and increments as it goes along
until it reaches n, which avoids unnecessary back and forth information relaying.

8.
a)
function output = timeFib(n)
if(~ischar(n)&&isreal(n)&&n>=0&&round(n)==n)
output = struct;
f = @() getFib(n);
output(1).n = n;
output(1).fib = getFib(n);
output(1).runtime = timeit(f);
else
    error('The input argument is not a non-negative integer!');
end

    function fib = getFib(n_int)
        if n_int == 0
            fib = 0;
        elseif n_int == 1
            fib = 1;
        else
            fib = getFib(n_int-1) + getFib(n_int-2);
        end
    end
end

function output = timeFibLoop(n)
if(~ischar(n)&&isreal(n)&&n>=0&&round(n)==n)
output = struct;
f = @() getFib(n);
output(1).n = n;
output(1).fib = getFib(n);
output(1).runtime = timeit(f);
else
    error('The input argument is not a non-negative integer!');
end

    function fib = getFib(n_int)
        firstnum = 0;
        secondnum = 1;
        for i = 2:n_int
            fib = firstnum+secondnum;
            firstnum=secondnum;
            secondnum=fib;
        end
    end
end

b)
function fibrecur = writeFibResult()

    n = 1;                              
     numbers = {};
    while(~strcmp(n,'stop'))
        n = input('Please enter a non-negative integer or type stop: ','s');
        if strcmp(n,'stop')
          break;
        else
          n = str2double(n);
          length = size(numbers);  
          numbers{1,length(2)+1}=n; %#ok<*AGROW>
        end
    end 

b = size(numbers);          
disp(numbers);
%disp(class());
for i = 1:b(2)
    fibrecur(i) = timeFib(cell2mat(numbers(i))); 
    fibloop(i) = timeFibLoop(cell2mat(numbers(i)));
end

myarray1 = [fibrecur.n;fibrecur.fib;fibrecur.runtime];
fileID = fopen('fibOutput.txt','w');
fprintf(fileID,'%6s %11s %17s\n','n','fib','runtime(s)'); 
fprintf(fileID,'%6d %11d %16.5d \n',myarray1); 
fclose(fileID);
myarray2 = [fibloop.n;fibloop.fib;fibloop.runtime];
fileID = fopen('fibLoopOutput.txt','w');
fprintf(fileID,'%6s %11s %17s\n','n','fib','runtime(s)');
fprintf(fileID,'%6d %11d %16.5d \n',myarray2);
fclose(fileID);
end
