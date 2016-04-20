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



```Matlab
'hello' == 'hello'
'hello' == 'goodbye'
strcmp('hello','hello')
```
For instance to load a data file for one particular patient we can use `strcmp`

```Matlab

file_number = find(strcmp({Data.name},'patient1.xls'))
load(Data

```


*Challenge Two*
``` matlab
% CHALLENGE TWO
% Work out the difference between strcmp and strfind
```

If you need to get particular dates, numbers or names from a file name the 'regular expression' function (`regexp`) might help.

*Challenge Three*
``` matlab
% CHALLENGE THREE
% Can you use regexp to find:

% 1)

% 2)

% 3)
```
*Challenge Four*
```matlab
% CHALLENGE
% loop through the files and read in the four excel datasheets
% save each dataset as a matlab file called HousingPrices_01,
% HousingPrices_02, etc in chronological order (ie you will need
% to read and use the date from the file name)
% HINT: the function datenum is very useful for sorting dates into
% chronological order
```


## Converting Data

*Challenge*
```matlab
% CHALLENGE
% the variables in HousingPrices need to be converted to something we can
% work with
% the column called 'Sold at Auction' contains variations of yes and no and
% n/a. It is sometimes blank (which is the same as n/a). Convert this
% variable into 0 = no, 1 = yes and -1 = n/a.
```