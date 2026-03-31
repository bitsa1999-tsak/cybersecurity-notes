1st question is about how many port are open so i will use nmap -sV to the target
2nd question about apache version can be found from the first answer 
for the gobuster we use : gobuster dir -u *target* -w /location/.../.../etc/...
The hidden directory is the last one
///////////
FOR THE 3RD TASK

From the gobuster we found the /panel so thorugh browser we can upload a php reverse shell(which i found from here:https://github.com/pentestmonkey/php-reverse-shell/blob/master/php-reverse-shell.php),in the first try uploading it we get an error message,so we can rename the file to .php5 and from the /uploads we can see that its succesfully uploaded.(Before we upload the file we need to edit the IP Address and the port)
After this,we need to start a netcat listener in a new terminal that will be listening to the port we edited the .php5 file before
Then we have to go to the /uploads path open the shell,return to the netcat listener terminal and we are in!
We search in the terminal find / -type f -name user.txt 2> /dev/null,we found var/www/user.txt>cat var/www/user.txt and we get the flag

\\\\\\\\\\\\
4TH TASK
We llok for files with SUID Permission using the command : find / -perm -4000 2>/dev/null
Once we found the unusual file we use GTFOBINS for privilege escalation 
We use /usr/bin/python -c 'import os; os.execl("/bin/sh", "sh", "-p")',and using whoami we can see we are logged in as root,we found the flag,cat the flag and room is over!
