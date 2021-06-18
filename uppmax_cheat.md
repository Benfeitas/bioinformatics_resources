#Uppmax intro and cheat sheet

## To access uppmax you can use one of 2 ways**  
1. Terminal:  
```
ssh YOUR_UPPMAX_ID@rackham.uppmax.uu.se
cd /crex/proj/path/to/your/folder/
```

2. Installing Thinlinc in your computer. Instructions: https://www.uppmax.uu.se/support/user-guides/thinlinc-graphical-connection-guide/  
This is the easy way to run RStudio in uppmax, and you click everywhere with mouse and keyboard as if you were in your own computer. If you login, then you can browse to the same folder with the path above. You probably will not need this since you are developing your code in your own computer, and use Uppmax to run the heavy jobs. I find it easier to use at start though.

## To upload data**
To upload the data to uppmax, the easiest way is with Filezilla. You can also do it with terminal, but it is not as straightforward. Once you have installed Filezilla, please use the following:
```
Host: rackham.uppmax.uu.se
User: [your uppmax username]
Password: [your uppmax password]
Port: [leave as blank]
```

Once you are connected you can paste 
`/crex/proj/path/to/your/folder/`
in “remote site:”. Then you browse normally and drag-and-drop to upload and download data.

Be careful with uploading other things and git: if you upload your code before doing git pull you will find conflicts when you pull. So usually I just use FileZilla to upload data since that is never touched with GitHub.

## To submit jobs
(alternatively to job submission, see running interactive jobs)
Please prepare the R, python or bash scripts that will run in its entirety. If you don’t need to run everything, either comment it or delete it from the given script.  Don’t forget to output the results into files as appropriate. 
You will need to follow the instructions in here. Create a file called “my_job_file.sh” and add the following inside:

```
#!/bin/bash -l
 
#SBATCH -A snicPROJECT-ID
#SBATCH -p core
#SBATCH -n 6
#SBATCH -t 12:00:00
#SBATCH -J some_job_name_as_test
#SBATCH --mail-user your_email@ki.se
#SBATCH --mail-type=ALL
R CMD BATCH /crex/proj/path/to/your/folder/name_of_your_R_script.R
```

Then submit the job from terminal (if you’ve connected with ssh) or command line (if you’re inside Thinlinc) with 

```
sbatch /path/to/the/file/my_job_file.sh
```

## Some notes about job submission
Above I’ve selected 12 hours (-t 12:00:00) and 6 cores (-n 6). Each core has about 6 Gb or ram memory. So this will mean that your job will occupy 6 \* 6Gb = 36Gbs of memory. This may be too much, or it may be not enough. There’s no way in knowing before trying a few times. The less you use for both time and memory, the faster your job will start. But if you don’t use enough, it may not complete. The maximum number of cores you can use is 20.

Don’t worry about messing up things for others. You will not have permissions to do, you only have access to this uppmax directory. But be careful before deleting anything, as it may imply you will have to re-run things.

To check how much memory your job consumed please use jobstats (see the Useful commands below).

## Running interactive jobs
You can run interactive jobs that allow you to debug and edit code as you go, similarly to how you would do in your own computer. See here for more information and options.
```
interactive -A [snicPROJECT-ID] -n [node_number] -t [hours]
```

## Useful commands
You can find some useful commands here: https://nbisweden.github.io/NGScourse/common/images/uppmax-cheat-sheet.png

`jobinfo  -u [username]`                #show running jobs for you
`jobstats -r [job_id]`                      #show job statistics. You can access job_id using jobinfo
`jobstats -p -r [job_id]`        # show the job statistics as a plot. You can then see it using thinlinc 
`scancel [job_id]`        # cancel a running or submitted job
`uquota`            # total disk usage (Gb)
`projinfo`            # total project hours used / allocated


`screen -S [name]`        #create a screen named [name]
`screen -ls`            #list all screens
`screen -r [name]`        #attach to screen
`screen -r -d [name]`        #to for attach to screen

## Using screen
To use screen:
1. `ssh` to uppmax
2. `screen -S some_screen_name`
3. start jobs
4. detach with `Ctrl + A + D` or `screen -r -d some_screen_name`
5. kill with `Ctrl + A + x`
