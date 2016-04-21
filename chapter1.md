# Part One: Getting the Data
 The first difficulty of real data is that it comes from many different sources, which may not be optimized for MATLAB. This part will cover some basic tricks for automatically reading in large amounts of data

## Folder structures
In MATLAB you navigate between files using strings

```Matlab
% Strings are defined using apostrophes
string = 'Goodbye Cruel World';

% File names are defined using strings
file_name = 'MyData';
```

The function `cd` stands for 'change directory', and is used to set the current workspace. 
The function `dir(file_name)` returns a list of files inside the folder called `file_name`.

```Matlab 
% get to where you want to be
cd('C:\Users\pkaroly\Google Drive\MATLAB course\Statistics Extension Course');
 
% get info about what's inside a particular folder (directory)
allMyData = dir('MyData');
```

The variable `allMyData` is a structure with information about the different files inside the folder 'MyData'. For instance, we can now see the file names and sizes. We can loop through these file names to sequentially load in lots of different data files.

```Matlab 
% just print out the name of everything inside the folder
allMyData.name
 
% we can also look at one at a time
allMyData(1).name
allMyData(2).name
allMyData(3).name
```


### *Challenge One*
```Matlab 
% CHALLENGE ONE
% Use a loop to read in the first file in each folder
% EXTENSION
% use two loops to read in all the files in all the folders
```


## File names

If you're looking for particular file names the functions 'string compare' (`strcmp`) and 'string find' (`strfind`) can be useful!

Dealing with strings is not as easy as working with numbers. For instance, you cannot simply use `==` to tell you if two strings are the same. Try typing the following commands into MATLAB to see why.

```Matlab
'hello' == 'hello'
'hello' == 'goodbye'
strcmp('hello','hello')
```

We can use `strcmp` to only load certain files, or to find the index of a particular file
```Matlab
file_number = find(strcmp({Data.name},'patient1.xls'))
```


###*Challenge Two*
``` matlab
% CHALLENGE TWO
% Work out the difference between strcmp and strfind
```

If you need to get particular dates, numbers or names from a file name the 'regular expression' function (`regexp`) might help. For instance, let's say you only want to load data from measurments that were taken after a certain day. Using `strcmp` that would require an `if` statement that listed every possibility:


```Matlab
% looping through lots of files
for n = 1:1000

  % get the file name
  file_name = Data(n).name
  
  % using strcmp check if the file is one that we want
  if strcmp(file_name,'Day15.xls') || strcmp(file_name,'Day16.xls') ...
   || strcmp(file_name,'Day17.xls') || ... 
                   % this could go on forever .....
    
    % load the file
    load(file_name)
    
  end
  
end
```

Instead, we can use `regexp` to just pick out the part of the name we are interested in  - i.e. the number. In MATLAB format strings numbers are represented by `\d`.
```Matlab
[first,last] = regexp(file_name,'\d')
```
This command will just return the first and last indices in the string `file_name` that contain a number. This makes it easier to write a simple `if` statement that works for every file name:

```Matlab
% looping through lots of files
for n = 1:1000

  % get the file name
  file_name = Data(n).name;
  [first,last] = regexp(file_name,'\d');
  day_number = file_name(first:last)
  
  % using strcmp check if the file is one that we want
  if day_number >= 15
    load(file_name)
  end
  
end
```
NB: to keep numbers together using `regexp` use `'\d+'` instead of just `'\d'`. Try it out to see the difference:

```Matlab
regexp('Patient104','\d')
```
 or
```Matlab
regexp('Patient104','\d+')
```

###*Challenge Three*
```Matlab
% CHALLENGE THREE
% Can you use regexp to find:

% 1) The index at the at start of the word 'cat' in the sentence 'the cat sat on the mat'

string = 'the cat sat on the mat';
pattern = 
regexp(string,pattern)

% 2) The indices at the start of the words 'cat' and 'mat'

pattern = 
regexp(string,pattern)

% 3) The words that start with 'c' and end in 't' in the following list

word_list = {'cat', 'mat', 'hat', 'cot'};
pattern = 
regexp(word_list,pattern)


% EXTENSION
% Can you write code that only extracts the day (as a number) from the following list of patient files

file_list = {'Pt1Day14', 'Pt12Day102', 'Pt009Day9'}
pattern = '(?<=Day)\d+'
regexp(file_list,pattern)


```
###*Challenge Four*

```Matlab
% CHALLENGE
% loop through the files and read in the four excel datasheets
% save each dataset as a matlab file called HousingPrices_01,
% HousingPrices_02, etc in chronological order (ie you will need
% to read and use the date from the file name)

% HINT: the function datenum is very useful for sorting dates into
% chronological order
```


## Converting Data


###*Challenge*
```matlab
% CHALLENGE
% the variables in HousingPrices need to be converted to something we can
% work with
% the column called 'Sold at Auction' contains variations of yes and no and
% n/a. It is sometimes blank (which is the same as n/a). Convert this
% variable into 0 = no, 1 = yes and -1 = n/a.
```