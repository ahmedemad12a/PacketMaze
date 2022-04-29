# PacketMaze

# Challenge Details :

## Tools :
-  [Wireshark](https://www.wireshark.org/download.html)
-  [CyberChef](https://gchq.github.io/CyberChef/)
-  [VirusTotal](https://www.virustotal.com/gui/home/upload) 
-  [AbuseIPDB](https://www.abuseipdb.com/)
-  [Whois](https://www.whois.com/whois/)
-  [MAC Address Lookup](https://dnschecker.org/mac-lookup.php)
    
# Challenge Solve :

**Q1** : What is the FTP password?

S1 : filter packet by write (ftp) to show the data traffic then you see in info password (AfricaCTF2021)  

![Detection](Pictures/1.png)

----------------------------------------------------------
**Q2** : What is the IPv6 address of the DNS server used by 192.168.1.26? (####::####:####:####:####)

S2 : show MAC of this ip 192.168.1.26 

![Detection](Pictures/2.png)

then Write this filter (eth.addr == ca:0b:ad:ad:20:ba && ipv6) IPv6 is in source 

![Detection](Pictures/3.png)


----------------------------------------------------------------------------
**Q3** : What is the duration of the capture?

S3 :  From Capture File Properties look for Elasped under Time.

![Detection](Pictures/4.png)

-----------------------------------------------------------------------------
**Q4** : What is the most active computer at the link level?

S4 : To view Ethernet, go to Statistics > Endpoints > Ethernet. Click Packets to sort the packets by descending .

![Detection](Pictures/5.png)

![Detection](Pictures/6.png)

-----------------------------------------------------------------------------

**Q5** : Manufacturer of the NIC of the most active system at the link level?

S5 : Or use a MAC address lookup online. Copy your answer from the previous question and search it on DNSChecker.org .

![Detection](Pictures/7.png)

-----------------------------------------------------------------------------

**Q6** : Where is the headquarters of the company that manufactured the NIC of the most active computer at the link level?

S6 : Using Google search engine, the results show the headquarters address of Hewlett Packard .

![Detection](Pictures/8.png)

-----------------------------------------------------------------------------

**Q7** : The organization works with private addressing and netmask /24. How many computers in the organization are involved in the capture?

S7 : To view the IPv4 addresses, go to Statistics > Endpoints > IPv4 (Answer = 3)

![Detection](Pictures/9.png)

-----------------------------------------------------------------------------

**Q8** : What is the name of the most active computer at the network level?

S8 : DHCP traffic can be used to identify the host information such as MAC Address, IP Address, and Hostname. Since I already know the MAC address, I used it to filter the packets to only display the dhcp traffic from the MAC address 00:08:02:1c:47:ae. 
write in wireshark to filter taffic use this command = eth.addr==00:08:02:1c:47:ae && dhcp ,

Select the first frame and expand Dynamic Host Configuration Protocol and Option (12).

![Detection](Pictures/10.png)

-----------------------------------------------------------------------------

**Q9** : What is the IP of the organization’s DNS server?

S9 : Enter in search bar DNS to filter packets and write IP in Destination Show in first frame (10.4.10.4)

![Detection](Pictures/11.png)

-------------------------------------------------------------------------------

**Q10** : What domain is the victim asking about in packet 204?

S10 : use this command to filter packets to show packet 204 (frame.number==204)
Expanding the Domain Name System and Queries will show the domain that the victim is accessing.

![Detection](Pictures/12.png)

------------------------------------------------------------------------------------

**Q11** : What is the IP of the domain in the previous question?

S11 : add = 217.182.138.132


![Detection](Pictures/13.png)
