# ==================   Linux   ==================  

http://linux.vbird.org/linux_basic/

## System Service
- Check CentOs version
```shell
cat /etc/centos-release
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
## Permission
- change owner
```shell
chown root:root /var/log/imm
```
- change file permission
```shell
chmod 755 testfile.txt
```

## General Command
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
## VI & VIM
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
## Compression
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