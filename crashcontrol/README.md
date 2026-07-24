

## Create Crash dump 
### Ensure kdump installation is present  : systemctl status kdump 

### Ensure /proc/cmdline has the crashkernel=auto 

### Install kdump 
- dnf install kexec-tools  && systemctl enable --now kdump 

### Enable Sysrq for crash 
- echo 1  > /proc/sys/kernel/sysrq 

### Check the path param : in /etc/kdump.conf . disk space 

### Crash Kernel 
echo c > /proc/sysrq-trigger