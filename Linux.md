==================   Linux   ==================
http://linux.vbird.org/linux_basic/

>> Find file name
find /etc -iname 'Network'

>> Check CentOs version
cat /etc/centos-release 

>> change owner
chown root:root /var/log/imm

>> change file permission
chmod 755 testfile.txt

>> List all the services
systemctl

>> Restarting and Reloading
sudo systemctl restart application.service

>> Live checking the log file in latest line.
tail -f fileName

>> Show the last 100 lines.
tail -100f fileName