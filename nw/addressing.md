# Addressing

IANA internet assigned number authority
regional organizations called RIR
RIRs allocate smaller blocks to ISPs
The ISPs rent the @IP to the users

# Routing

Gateway: 0.0.0.0 没有必要经过路由器 目的地在本地
![alt text](image-7.png)
Router's routing table
![alt text](image-9.png)
检查是不是在一个网络中
![alt text](image-10.png)
check the destination is on one of its networks, first do AND and get
longest match lookup 255.255.255.255
second match lookup 255.255.255.0

# Terminal

route -n
sudo tcpdump -i lo
ping
