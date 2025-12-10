find / -perm -4000 -type f 2>/dev/null | grep -v '^/proc\|^/run\|^/sys\|^/snap' #Find all SUID binaries (clean output)
find / -perm -2000 -type f 2>/dev/null | grep -v '^/proc\|^/run\|^/sys\|^/snap' #Find all SGID binaries (clean output)
find / -type d -writable 2>/dev/null | grep -v '^/proc\|^/run\|^/sys\|^/snap'   #Find writable directories for your current user
find / -user root -writable -type f 2>/dev/null | grep -v '^/proc\|^/run\|^/sys' #Find files owned by root but writable by you
find / -perm -2 -type f 2>/dev/null | grep -v '^/proc\|^/run\|^/sys' #Find world-writable files
getcap -r / 2>/dev/null | grep -v '^/snap\|^/proc\|^/sys' #Find files with capabilities (very powerful for privesc)
find / -type f -name "*.sh" -user root 2>/dev/null | grep -v '^/proc\|^/run\|^/sys' #Find scripts executed by root (common privesc path)
find / -type f \( -name "*.bak" -o -name "*.old" -o -name "*~" \) \
2>/dev/null | grep -v '^/proc\|^/run\|^/sys' #Find backup files that may contain credentials
find / -type f -name ".*" 2>/dev/null | grep -v '^/proc\|^/run\|^/sys' #Find hidden files (often contain sensitive content)
crontab -l 2>/dev/null
ls -al /etc/cron* 2>/dev/null #cronjobs
grep -Ri "password" /etc 2>/dev/null #sensitive strings
