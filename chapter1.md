# Part One: Getting the Data
 The first difficulty of real data is that it comes from many different sources, which may not be optimized for MATLAB. This part will cover some basic tricks for automatically reading in large amounts of data

## Folder structures

As always start your code with
```Matlab
clear
close all
clc
```
 
% get to where you want to be (cd = change directory)
cd('C:\Users\pkaroly\Google Drive\MATLAB course\Statistics Extension Course')
 
% get info about what's inside a particular folder (directory)
allMyData = dir('MyData');
 
% just print out the name of everything inside the folder
allMyData.name
 
% we can also look at one at a time
allMyData(1).name
allMyData(2).name
allMyData(3).name
 
% lets open the first patient
Patient1 = dir(allMyData(3).name);   
 
% there's nothing there!
 
% need to tell it the root folder as well
folderName = ['MyData/' allMyData(3).name];
Patient1 = dir(folderName);
 
for n = 1:length(Patient1)
   display(['name: ' Patient1(n).name ' size: ' num2str(Patient1(n).bytes/1000) 'kb']);
   % load the third file
   if n == 3
      patientData = xlsread([folderName '/' Patient1(n).name]); 
   end
end


*Challenge One*
```Matlab 
% CHALLENGE ONE
% Use a loop to read in the first file in each folder
% EXTENSION
% use two loops to read in all the files in all the folders
```


## File names

If you're looking for particular file names the functions 'string compare' (*strcmp*) and 'string find' (*strfind*) can be useful!

*Challenge Two*
``` matlab
% CHALLENGE TWO
% Work out the difference between strcmp and strfind
```

If you need to get particular dates, numbers or names from a file name the 'regular expression' function (*regexp*) might help.

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