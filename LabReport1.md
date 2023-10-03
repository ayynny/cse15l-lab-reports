1. ![image](https://github.com/ayynny/cse15l-lab-reports/assets/61796361/800c0dca-158b-4f34-bf73-b4236183fa07)
   
For cd + no arguments, nothing happens because the cd is searching for a directory & in this case, there isn't anything to search. For cd + directory, the prompt changes to which directory the terminal is now in. For cd + file, there's an error because the terminal doesn't allow that because cd searches for directories. To avoid this error, input a directory (typically a folder) to successfully use cd to manuever through your files.

2. ![image](https://github.com/ayynny/cse15l-lab-reports/assets/61796361/79a8ab04-5196-4fe1-900d-a1cad759ed3e)
   
For ls + no arguments, the terminal prints the folders available in the workspace (in this case, lecture1 is the only folder so the terminal prints lecture1). For ls + directory (lecture1) as an argument, the terminal prints out the files found in the directory. For ls + file (.txt file), there's an error because terminal doesn't allow that because ls is searching for files or directory within itself. To avoid this error, we should search for folders instead of files.

3. ![image](https://github.com/ayynny/cse15l-lab-reports/assets/61796361/77153182-a09f-4400-ae79-647b1f77db2c)
   
For cat + no argument, nothing prints. For cat + directory (lecture1), the terminal prints "cat: lecture1: is a directory". I `cd lecture1` to get into lecture1 directory. I tried to cat lecture1 again, but it says no file or directory because a lecture1 file or directory doesn't exist in the lecture1. For cat + file (Hello.java), the directory prints out the conetnt of the file. 
