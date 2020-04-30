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
- Check CentOs version
```shell
cat /etc/centos-release
```
- List all processes
```shell
ps -a
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
- Check the memory usage
```shell
free -h
```
- Check the IP services
```shell
netstat -at
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
scp /path/file1 user@192.168.0.1:/path/file2
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
tail -100f testfileName
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