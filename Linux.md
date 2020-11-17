# ==================   Linux   ==================  
Detail:  
http://linux.vbird.org/linux_basic/

## System Service
<details>
<summary>view subjects</summary>

- Reboot the VM
```shell
sudo reboot
```
- Check CentOs/redhat version
```shell
cat /etc/centos-release
cat /etc/redhat-release 
```
- Set up **cron job**
```shell
# Edit the file
crontab -e
# At 00:05 in August will run the test.py job
5 0 * 8 * /use/bin/python3 /home/test.py
# Check the crontable jobs.
crontab -l
```
- List all processes
```shell
ps -a
```
- Run the process in background / foreground
```shell
# 'Ctrl + z' to stop it first and get the number
# Run at background
bg %1
# Run at foreground
fg %1
```
- Keep the session alive to run the job when disconnect
```shell
# Need to install the dependency first
yum install screen
# Use 'screen'
screen
# Keep it alive
# "Ctrl + a" + "d"
```
- Kill the process by PID
```shell
kill 123
```
- List all the services
```shell
systemctl
```
- Restarting and Reloading
```shell
sudo systemctl restart test.service
```
- Show the command history
```shell
history
```
- Check the CPU usage
```shell
top
```
- Check the disk volume the usage
```shell
df -h
```
- Check the file size
```shell
du -h /tmp.log
```
- Check the memory usage
```shell
free -h
```
- Check the IP services
```shell
netstat -at
```
</details>

## Package Commands
<details>
<summary>view subjects</summary>

- Download the package to the directory without install it.
```shell
sudo yum install --downloadonly --downloaddir=/root/xxx <package_Name>
```

- Directly crawl the data back and save the response.
```shell
curl http://www.google.com > response.html
```
</details>

## Permission
<details>
<summary>view subjects</summary>

- change owner
```shell
chown root:root /var/log/file
```
- change file permission
```shell
chmod 755 testfile.txt
```
</details>

## General Command
<details>
<summary>view subjects</summary>

- Copy the file to other VM
```shell
scp /path/file1 user@192.168.0.1:/path/
```
- Find file name
```shell
find /etc -iname 'KEYWORD'
```
- Live checking the log file in latest line.
```shell
tail -f fileName
```
-  Show the last 100 lines.
```shell
tail -100 testfileName
```
-  Show the first 50 lines.
```shell
head -50 testfileName
```
-  Replace the X to Y in testfilename.txt (space need to escape ```'\ '```)
```shell
sed -i 's/XXX/YY\ YY/g' testfilename.txt
```
-  Read and parse the file and do the custom command.
```shell
# Split by ':' and print variables "$1 tab $7"
cat /etc/passwd | awk -F ':' '{print $1"\t"$7}'
```
</details>

## VI & VIM
<details>
<summary>view subjects</summary>

- Highlight and choose the line
```shell
# V for choose all line, v for single word.
<normal mode> V 
```
- Copy what you select
```shell
<normal mode> y
```
- Delete what you select
```shell
<normal mode> d
```
- Paste what you select
```shell
<normal mode> p
```
- Undo the command
```shell
<normal mode> u
```
- Show code line.
```shell
<normal mode> :set number
```
- Search keyword
```shell
# **/** for search frontward, **?** for search backward.
# **n** for next match, **N** for previous.
<normal mode> /keyword
```
- Search the keyword and save it
```shell
grep "1111" /tmp/catalina.out.2018-08-20 > 123321.log
```
</details>

## Compression
<details>
<summary>view subjects</summary>

- tar / untar
```shell
tar cvf FileName.tar DirName
tar xvf FileName.tar
```
- zip / unzip
```shell
zip -r file.zip directory_name
unzip file.zip
```
- gzip / gunzip
```shell
gzip FileName
gunzip FileName.gz
```
- rar / unrar
```shell
rar a FileName.rar DirName
rar e FileName.rar
```
</details>
