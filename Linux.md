# ==================   Linux   ==================  
Detail:  
http://linux.vbird.org/linux_basic/

## System Service
<details>
<summary>view subjects</summary>

- Connect to the remote server. (ps: Need to provide the public key first.)
```shell
ssh userName@10.1.3.51
```

- Reboot the VM
```shell
sudo reboot
```

- Check CentOs/redhat/ubuntu version
```shell
cat /etc/centos-release
cat /etc/redhat-release
cat /etc/os-release
```

- Check Linux  by 'uname' command.
```shell
# List all info.
uname -a
# List the kernel-release.
uname -r
```

- Mount commands.
```shell
# Show all mount detail
mount
# Mount all devices in /etc/fstab
sudo mount -a
# Umount all devices in /etc/fstab
sudo umount -a
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

- List all ip tables config
```shell
sudo iptables -A INPUT -j ACCEPT # Accept all input link.
sudo iptables -L INPUT --line-numbers # Show all config with line number.
sudo iptables -A INPUT -p tcp --dport 22 -s 192.168.1.100 -j ACCEPT # Accept 192.168.1.100 connect with 22 port.
sudo iptables -D INPUT 5 # Remove line number 5 ip config.
```

- List all running processes. (ps: `-e` and `ax` are completely equivalent)
```shell
ps aux # Brief info and different layout
ps -ef # Process info, PID, user, usage
```

- Run the process in background / foreground
```shell
# 'Ctrl + z' to stop it first and get the number
# Run at background
bg %1
# Run at foreground
fg %1
```

- Run the command at the background.
```shell
# Run the script at background.
nohup /root/test.sh &
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

- Kill the unresponsive process by PID
```shell
kill -9 123
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

- Show the cpu detail
```shell
cat /proc/cpuinfo
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
ss -tunapls
```

- Check the date time, NTP sync detail
```shell
timedatectl
```

- Firewall check status, add/remove port, restart service.
```shell
firewall-cmd --list-all
firewall-cmd --add-port=[portNumber]/tcp --permanent
firewall-cmd --remove-port=[portNumber]/tcp  --permanent 
firewall-cmd --reload
```
</details>

## Download Commands
<details>
<summary>view subjects</summary>

- Download the package to the directory without install it. (For CentOS)
```shell
sudo yum install --downloadonly --downloaddir=/root/xxx <package_Name>
```

- Download the package and install it. (For Debian OS)
```shell
apt-get install <package_Name>
```

- Directly crawl the data back and save the response.
```shell
curl http://www.google.com > response.html
```

- Download files directly.
```shell
wget http://www.google.com/xxx.tar.gz
```
</details>

## Permission
<details>
<summary>view subjects</summary>

- Change to other user.
```shell
su [userName]
```

- Change the file's owner.
```shell
chown root:root /var/log/file
```

- Change the file's permission.
```shell
chmod 755 [testfile.txt]
```

- Modify the user's data.
```shell
usermod -l [newname] [username]
usermod -p [password] [username]
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

- Locate the file path, usually find in 'ENVIRONMENT_VARIABLE $PATH'.
```shell
which [packageName]
```

- Check the content different between two files.
```shell
diff fileName1 fileName2
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
