Important Information:
- If something doesn't work, check the end for troubleshooting. 

## Set up Ubuntu
1. Log in to Ubuntu
2. Make sure you are in home yinlab directory (text should say `yinlab@DESKTOP-SAB32EL:~$`). If there is anything after it, type `cd /home/yinlab/` and hit enter. 

To run data, you have two options: 

___

## Run Default
This will run data with minimal parameters. To do so:

1. On Windows, move ***ONE*** set of files with a common sample (E756, Undetermined, etc.) to **`C:/DefaultRunFolder`**. Cellranger can only run one sample set at a time (as far as I am aware). 
2. On Ubuntu, type **`make default sample=SAMPLE_HERE`** and replace **`SAMPLE_HERE`** with the sample of the files you are using. 
3. Files will run, and output should be in **`C:/DefaultOutput`**
4. To run more files, remove all files from **`C:/DefaultRunFolder`** and replace with new ones. I am not sure if leaving files in `C:/DefaultOutput` will delete everything in there after running again, so the best practice will be to move files out of there also before running again. 

*What the command should look like:*
```
make default sample=E756
```

___

## Run Custom
This will run data with custom parameters. To do so:
1. On Windows, find the directory of files to run. We will call this **`DIR`**. 

>[!WARNING]
>Make sure that each sample is separated into its own directory. Cellranger can only run one sample set at once. 

2. Choose an output directory to put data in. We will call this **`OUT`**. 
3. Pick a sample set to run. We will call this **`SAMPLE`**. 
4. On Ubuntu, type **`make run path=DIR output=OUT sample=SAMPLE`**. 
5. This will run that sample set once. Repeat for each sample set. 

*What the command should look like:*
```
make run path=D/Fastq_Files/Concatenated output=C/OutputFiles sample=E756
```

___

# Issues
## No such file or directory
- If you receive an error that says the following: 
```
error: Invalid value for '--fastqs <PATH>...': No such file or directory (os error 2)
```
Possible Fixes:
1. Type `make dir prefix=PREFIX` where **`PREFIX`** is the drive letter names that you are using (most likely C or D). Should look like: 
```
make dir prefix=C
make dir prefix=D
```
2. Make sure that you are typing in directories correctly. 
3. Make sure that directories do not contain spaces. 
## Argument requires a value, but none was supplied
Possible Fixes: 
1. An argument was omitted, make sure all have been filled out correctly. 

If you still have an issue or there is an issue not in here, contact me at adamllryan@gmail.com. 
