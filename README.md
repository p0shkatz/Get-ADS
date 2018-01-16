# Get-ADS
Powershell script to search for alternate data streams

This script searches recursively through a specified file system for alternate data streams (ADS). 

The script can search local and UNC paths speciffied by the $path paramenter. All readable files will have the stream
attrubute inspected ignoring the default DATA and FAVICON (image file on URL files) streams. The script use Boe Prox's 
amazing Get-RunspaceData function and other code to multithread the search. The default number of threads is the
number of logical cores plus one. This can be adjusted by specifiying the $threads parameter. Use with caution as 
runspaces can easily chomp resources (CPU and RAM). 

Once the number of file system objects (files and folders) is determined, they are split into equal groups of objects
divided by the number of threads. Then each thread has a subset of the total objects to inspect for ADS.
