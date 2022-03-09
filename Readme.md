The most frequently used SSH commands and their use

CD
Search, navigation and listing
CD

Change directory to a particular directory.

cd : If the command is executed without arguments, it will take us to the user's home directory.

cd ~ : Takes you back to your home directory (the directory you appear in when you first log in to your server).

cd /usr/local/apache : Takes you to the /usr/local/apache/ directory.

cd - : Moves you back to the last directory you were in.

cd .. : Moves you up one level in the directory tree.

#ls
List all files/directories in the current directory.
ls

ls -a : Show all files/directories in the current directory, including hidden files.

ls -l : Show an ordered list of the current directory.

ls -al : Show an ordered list of the current directory, including hidden files.

#du
du

Shows the disk usage of the current directory.

du -h : Displays disk usage, by folder, in the current directory, in a human-readable format.

du -sh : Does not display the size per folder, it only shows the total space used, in a human readable format.

du -la * |sort -n|tail -15: an example of a combined command:

du -la * : Return the size of all files in the given directory.
sort -n : Sort the results by numerical value.
tail -15 : Print only the last 15 results, which means the 15 largest files in a given directory.

#cp Copy, move and delete
zip

Command used to copy a file.

cp /home/path/filename.ext /home/newpath/newfilename.ext : Makes a copy of filename.ext from the /home/path/ directory to the /home/newpath/ directory named newfilename.ext.

cp -R /home/path/* /home/newpath/ : Makes a copy of all files and directories in /home/path/ and puts them in the /home/newpath/ directory.

#mv Command used to move a file – usage is the same as with cp (see above).

################################################### ###################################################

#rm Command used to delete files.

rm filename.ext : Delete filename.ext, ask for confirmation before deleting.

rm -f filename.ext : Delete filename.ext without asking for confirmation.

rm -rf /home/directory/ :Delete the folder in the directory, all files and subdirectories within it, without confirmation. (Be very careful with this command).

Search, locate, view and edit

vi Text editor. Its use is shown here.

vi filename.ext : Opens filename.ext in the vi text editor.

#cat

cat Used to print to screen. (View content of a file)

cat filename : Prints the contents of the file filename to the screen.

cat filename |more : |more spreads the contents of the file over multiple pages (scroll between pages by pressing the space bar, exit by pressing the letter q).

tail

Same principle as with cat but only prints the end of the file. Very often used to see the latest events displayed in a log file.

tail -f /path/filename.txt : To watch the file continuously, even when it is being updated.

tail -100 /path/filename.txt : To print the last 100 lines of a file.

grep

Search for a string within a file.

grep string filename : Prints to the screen the instance in which the string was found in the file filename.

grep -r string * : Prints to the screen the instances in which the string string has been found in the current folder, as well as in the files in its subfolders.

find

File search.

find /path/to/search/ -name filename : Search /path/to/search for a file named filename.

find / -name filename : Find all files named filename anywhere on your server.

find /path/to/search -name "*string*" : Find all files that have 'string' in their filename.

Server security, processor and network monitoring

last

Shows the last connections to the server and when they were made.

last -20 : Show only the last 20 logins.

last -20 -a : Shows only the last 20 logins, with the name of the computer from which the connections were made.

last -20 -ai : The same as above, but shows the IP address instead of showing the computer name.

w

Shows who is currently online and where they are logged in from.

quien

Similar to w but shows only the user, time of the connection and the name of the computer from which the connection was made.

netstat

Shows all current network connections.

netstat -an : Shows all connections to the server, the source and destination IP addresses, as well as the ports.

netstat -rn : Shows the routing table of all IP addresses bound to the server.

top

Shows the processese are running as well as their resource usage in a table, in real time.

Shift + M to sort by memory usage.

Shift + P to sort by CPU utilization. (Press ctrl + c to exit).

ps

Lists the running processes and their PIDs (Process IDs).

ps U username : Shows the processes that are executed by the user username.

ps aux : Shows all running system processes.

ps aux --forest : List and sort all running system processes.

kill

Used to terminate a process.

kill -9 PID : Where PID refers to the process ID number.

Permits and ownership

(Note: You must either be the owner of the file/directory, or be logged in as root before you can run any of these commands.)

chown

Used to change the ownership of a file (two variables: USER - GROUP)

chown root filename.ext : Changes the owner of the filename.ext to the root user.

chown root.apache filename.ext : Change owner to user root and group to apache.

chown -R root /home/folder : Change the owner of everything included (folders and files too) in the /home/folder directory to the root user.

chmod

Used to change the permissions of the file.

chmod 755 filename.ext : Change the file permissions for filename.ext to 755.

Various

ln

Create a link between files, directories and URLs.

ln -s /usr/local/apache/conf/httpd.conf /etc/httpd.conf : You can now edit /etc/httpd.conf instead of /usr/local/apache/conf/httpd.conf.

ln -s /home/www/path domain.com : Makes the domain.com domain point to the /home/www/path directory (don't forget to make another entry with http://www.domain.com!)

touch

Create an empty file.

touch /home/path/filename.html : creates an empty file called filename.html in the /home/path directory (which can then be edited in VI, for example).

toilet

Print the number of words in a file.

wc -l filename.ext : Print the number of lines in filename.ext.

file

tar

Used in combination with arguments to create and extract .tar, .gz and .tar archives.

tar -vxfz filename.tar.gz : Uncompress and extract the files contained in filename.tar.gz

tar -vxf filename.tar : Uncompresses and extracts the files contained in filename.tar

tar -vcf archive.tar directory/ : Takes all the files and folders in /directory/ and archives them in archive.tar

Apache

httpd

httpd -v : Prints the build date and version number of the Apache server.

httpd -l : Lists compiled into Apache modules.

service httpd restart : Restart the Apache web server.

mysql

mysql

mysqladmin processlist : Shows active MySQL connections as well as queries.

mysqladmin drop databasename : Drops (delete) the database named databasename.

mysqladmin -u root -p create databasename : Create a database named databasename.

mysql -u username -p password databasename < databasefile.sql : Restore a MySQL database at databasename from databasefile.sql.

mysqldump -u username -p password databasename > databasefile.sql : Performs a MySQL dump of the database named databasename and sends it to databasefile.sql.
