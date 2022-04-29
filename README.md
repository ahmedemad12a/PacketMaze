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
**Q3** : What domain is the user looking up in packet 15174?

S3 :  use this filter to get packet 15174 (frame.number == 15174)
then extend Domain name system then Queries , you show domain name is (www.7-zip.org)  

![Detection](Pictures/4.png)

-----------------------------------------------------------------------------
**Q4** : How many UDP packets were sent from 192.168.1.26 to 24.39.217.246?

S4 : Filter packets by using (ip.src== 192.168.1.26 && ip.dst == 24.39.217.246 && udp) and then count packets will be (10 packets)

![Detection](Pictures/5.png)

-----------------------------------------------------------------------------

**Q5** : What is the MAC address of the system being investigated in the PCAP?”

S5 : use ftp to filter packet and show mac address of source in Ethernet 

![Detection](Pictures/6.png)

-----------------------------------------------------------------------------

**Q6** : What was the camera model name used to take picture 20210429_152157.jpg ?

S6 : write (ftp-data) to filter packets select first packet

![Detection](Pictures/7.png)

then use follow tcp stream and select Show data as and select (Raw)

![Detection](Pictures/8.png)

then click on save as and save data in JPG 

![Detection](Pictures/9.png)

then click Right on pictures click in properties and seclect details then you show name of camera in camera model

![Detection](Pictures/10.png)

-----------------------------------------------------------------------------

**Q7** : What is the server certificate public key that was used in TLS session: da4a0000342e4b73459d7360b4bea971cc303ac18d29b99067e46d16cc07f4ff?

S7 : use this filter to get certificate (tls.handshake.session_id == da:4a:00:00:34:2e:4b:73:45:9d:73:60:b4:be:a9:71:cc:30:3a:c1:8d:29:b9:90:67:e4:6d:16:cc:07:f4:ff)

![Detection](Pictures/11.png)

then you get pubkey in 

![Detection](Pictures/12.png)

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
