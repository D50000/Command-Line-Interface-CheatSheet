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

- Show the cpu detail
```shell
cat /proc/cpuinfo
```

- Check CentOs/redhat/ubuntu version
```shell
cat /etc/centos-release
cat /etc/redhat-release
cat /etc/os-release
```

- Check Linux information by 'uname' command.
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
# Check the crontab jobs.
crontab -l
```

- Ip tables config.  
`-A`: **append** rule at end  
`-I`: **insert** rule at start  
`-L`: **list** out the rules  
`-p`: **protocol** type  
`-s`: **source** ip  
`-j`: **job** ACCEPT or REJECT  
`-D`: **delete** the rule  
```shell
sudo iptables -A INPUT -j ACCEPT # Accept all input link.
sudo iptables -L INPUT --line-numbers # Show all config with line number.
sudo iptables -A INPUT -p tcp --dport 7001:7005 -s 192.168.1.100 -j ACCEPT # Accept 192.168.1.100 connect with 7001 ~ 7005 port.
sudo iptables -D INPUT 5 # Remove line number 5 ip config.
```

- Firewall check status, add/remove port, restart service.
```shell
firewall-cmd --list-all
firewall-cmd --add-port=[portNumber]/tcp --permanent
firewall-cmd --remove-port=[portNumber]/tcp  --permanent 
firewall-cmd --reload
```

- List all running processes. (ps: `-e` and `ax` are completely equivalent)
```shell
ps aux # Brief info and different layout
ps -ef # Process info, PID, user, usage
```

- Check the details of process by its `PID`.
```shell
ps -p PID -f  # Process Status command.
lsof -p PID   # List Open Files command.
ss -pl | grep PID   # Socket Statistics command.
```

- Run the process in background / foreground (**Kill** when ssh disconnect)
```shell
# First run the run.sh file. `Ctrl + z` to stop it and keep into background.
sh run.sh
# Show all the sh process. "1" will be the process id number.
jobs
[1]+ Stopped sh run.sh
# Run at foreground
fg %1
# Run at background
bg %1
###############################
# Run the script at background.
sh run.sh &
# Run in background with log. (2: stderr, 1: stdout)
sh run.sh > output.log 2>&1 &
```
<img src="https://github.com/D50000/Command-Line-Interface-CheatSheet/blob/master/assets/process_work_flow.png" alt="process work flow" width="550px">  

- Run the command at the background **even disconnect from server**.
```shell
# Run the script at background.
nohup /root/test.sh &
# Run in background with log. (2: stderr, 1: stdout)
nohup /root/test.sh > output.log 2>&1 &
```

- Keep the session alive to run the job when disconnect
```shell
# Need to install other package first
yum install screen
# Use 'screen'
screen
# Keep it alive
# "Ctrl + a" + "d"
```

- Kill the process by it's PID
```shell
# Signal '9' forcefully terminates the process without giving it a chance to clean up.
kill -9 12345
# Signal '15' (default) for a graceful shutdown.
kill 12345
# Gracefully kill all the match process PID.
ps -ef | grep xxx.jar | awk '{print $2}' | xargs kill

# Find and kill the process name
pkill -f myApp.jar
# Avoid miss matching process name
pkill -f myApp.jar || true
```

- **systemctl** commands
```shell
systemctl                            # List out all system detail service
systemctl list-units --type=service  # Show only service info
sudo systemctl start test.service    # Run
sudo systemctl stop test.service     # Stop
sudo systemctl restart test.service  # Rerun
sudo systemctl reload test.service   # Refresh and won't stop
sudo systemctl enable test.service   # Server reboot will auto run
sudo systemctl disable test.service  # Turn off auto run
sudo systemctl status test.service   # Check info
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
ss -tunapls
```

- Check the date time, NTP(Network Time Protocol), RTC(Real-Time Clock) sync detail
```shell
timedatectl status
cat /etc/ntp.conf  # ntp configuration
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

- Copy the file to other machine.
```shell
scp /path/file1 user@192.168.0.1:/path/
```
</details>

## Permission
<details>
<summary>view subjects</summary>

- Switch user commands.
```shell
su [userName] # Switch to user with "current state".
su - [username] # Switch to user and "simulate with it state".
su [username] -c "[command]" # Use user to execute the command without login.
```

- Change owner the file's owner, and file's user group.
```shell
chown root:root /var/log/file
```

- Change user group.
```shell
chgrp groupname testfile.txt
```

- Change mode the file's permission.
```shell
chmod 755 [testfile.txt]
```

- Modify the user's login name.
```shell
usermod -l [newName] [oldUserName] # -l means "login name"
```

- User login password command.
```shell
sudo passwd -S [username] # Check user account status. (ps: p: password enable, L: locked, NP: No password setup)
# user1 P 2025-01-04 0 99999 7 -1 (Password set, user can log in)
# user1 L 2025-01-04 0 99999 7 -1 (Password locked, user cannot log in)
# user1 NP 2025-01-04 0 99999 7 -1 (No password set)

sudo passwd -u [username] # Unlock the user account.
sudo passwd [username] # Update or reset the user login password
```
</details>

## General Command
<details>
<summary>view subjects</summary>

- Find file name
```shell
find /etc -iname 'KEYWORD'
```

- Locate the file path, usually find in 'ENVIRONMENT_VARIABLE $PATH'.
```shell
which [packageName]
```

- Print out the text.
```shell
echo Hello World
echo -e  # Print compile the special character.
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

-  **Stream Editor** replace the X with Y in testFile.txt and backup old file.  
(ps: space need to escape ```'\ '``` and `-i`: in-place, `.bak`:backup the file, `s`: substitute, `g`: global replace, `i`: capital case insensitive)
```shell
sed -i.bak 's/XXX/YY\ YY/gi' testFile.txt
```

-  AWK (Alfred Aho, Peter Weinberger, Brian Kernighan):  
Print, parse and manipulate the file with custom command.
```shell
# Print element_#2 in example.txt file.
awk '{ print $2 }' example.txt

# Print element_#1 when element_#2 > 25 in example.txt file.
awk '$2 > 25 { print $0 }' example.txt

# "-F" mean split by ':' and print variables "element_#1" + "tab" + "element_#7"
awk -F ':' '{print $1"\t"$7}' /etc/passwd
```

- SNMP (Simple Network Management Protocol) for checking device status by UDP.
```shell
snmpget -V # Show version.
// TODO:
```

- Ping for test connection to other host.
```shell
ping -V # Show version.
ping www.google.com # Ping domain.
ping -c 5 10.1.2.3 # Ping for 5 data count.
ping -l 10 10.1.2.3 # Ping for 10 size count.
ping -w 200 10.1.2.3 # Ping for 200ms timeout size count.
ping -4 10 10.1.2.3 # Ping with IPv4.
```

- Test network to other server by TCP (**Default port: 23 and in macOS not build-in cmd**).
```shell
telnet [domain_or_ip] [port] # Test hostName with port.
# Success
Connected to 192.168.1.1.
Escape character is '^]'.
# Fail
telnet: Unable to connect to remote host: Connection refused

# Input and to exit.
Ctrl + ]
quit
```
</details>

## VI & VIM
<details>
<summary>view subjects</summary>

- vim/vi file with readonly mode.
```shell
# It will pop up error it modify the file.
vim -R [filename]
```

- Highlight and choose the line
```shell
# Toggle into <visual mode> and press "V" for select whole line, "v" for single word.
<normal mode> V 
# Select whole file content.
<normal mode> gg  # Move to top.
<normal mode> v   # Switch to <visual mode>.
<normal mode> G   # Move to bottom.
<normal mode> y   # Copy select content.
# Vim need to enable the +clipboard, can check with "vim --version"
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
# "/" for search forward, "?" for search backward.
# n for next match, N for previous.
# For escape character search use /api\/vi
<normal mode> /keyword
```

- Setup hight-light search result
```shell
:set hlsearch  # Enable
:noh           # Disable
```

- Truncate the log file and save as new file.
```shell
# Search the keyword and save it
grep "1111" /tmp/catalina.out.2018-08-20 > 123321.log
# Save log file line number 'x' to 'y'.
100,1000w new_log.log
```
</details>

## Compression
<details>
<summary>view subjects</summary>

- tar / untar
```shell
tar cvf FileName.tar DirName
tar xvf FileName.tar  # untar
tar Jxvf FileName.tar.xz  # untar
```

- zip / unzip
```shell
zip -r file.zip directory_name
unzip file.zip
# unzip into specific path
unzip filename.zip -d /path/to/directory
```

- gzip / gunzip
```shell
gzip FileName
gunzip FileName.gz
# Keep the gz file and gunzip it
gunzip -k FileName.gz
```

- rar / unrar
```shell
rar a FileName.rar DirName
rar e FileName.rar
# Keep the rar file and unzip rar
rar x FileName.rar
```
</details>
