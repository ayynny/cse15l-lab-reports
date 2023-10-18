1. ![image](https://github.com/ayynny/cse15l-lab-reports/assets/61796361/800c0dca-158b-4f34-bf73-b4236183fa07)
   
For cd + no arguments, it seems like nothing is happening, but the working directory is the home directory (thus the terminal appears like nothing is happening). If the user was in another directory, and simply put "cd", the working directory becomes the home directory. For example, if the working directory was [user@sahara ~/lecture1], and I type "cd" into the terminal, the working directory becomes [user@shara ~] which is the home directory in this case.

For cd + directory, the prompt changes to which directory the terminal is now in. In this case, entering "cd lecture1" the working directory becomes [user@sahara ~/lecture1], which works as intended.

For cd + file, there's an error because the terminal doesn't allow that because cd searches for directories. To avoid this error, input a directory (typically a folder), rather than a file, to successfully use cd to manuever through your files. The working directory I used for this test was [user@sahara ~/lecture1/messages]. 

2. ![image](https://github.com/ayynny/cse15l-lab-reports/assets/61796361/b5d42889-dffe-4149-a78e-7321e06838d3)
For ls + no arguments, the terminal prints the folders available in the working directory. In this case, the only folder available in the working directory, which is [user@sahara ~], is lecture1.

![image](https://github.com/ayynny/cse15l-lab-reports/assets/61796361/acd39e16-2f51-48d6-98a4-baf2262d8f7d)
For ls + directory as an argument, the terminal prints out the files found in the directory. In this case, "ls lecture1" prints out the names of the 4 files found in the lecture1 folder.  However, we can only use directories that are only 1 child away from the parent folder without having to cd into another folder. For the following examples, the working directory is [user@sahara ~] (parent folder). We are able to ls the home directory (the working directory), or ls the child folder of the home directory (home/lecture1). If we ls the child folder, the terminal will list out the files found in 'lecture1'. However, if we try to access a child folder 2 folders from the parent directory (such as home/lecture1/messages), we recieve an error stating "there is no such file or directory". 

![image](https://github.com/ayynny/cse15l-lab-reports/assets/61796361/81410d93-f0cd-422f-a8b3-b85532e6ea18)
For ls + file, if our current directory does not contain any files, the terminal prints "no such file or directory" (current directories used: [user@sahara ~], [user@sahara ~/lecture1]). This error occurs because we need to be in a directory where there are files. However, if we go into a folder that has a file, then it will return the file name (current directory: [user@sahara ~/lecture1/messages].

3. ![image](https://github.com/ayynny/cse15l-lab-reports/assets/61796361/77153182-a09f-4400-ae79-647b1f77db2c)
   
For cat + no argument, nothing prints. 

For cat + directory (lecture1), the terminal prints "cat: lecture1: is a directory". I `cd lecture1` to get into lecture1 directory. I tried to cat lecture1 again, but it says no file or directory because a lecture1 file or directory doesn't exist in the lecture1. 

For cat + file (Hello.java), the directory prints out the conetnt of the file. 
