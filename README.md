# network_subnetting
first of all, all the information here is taken from the  NetPractice project of 1337/42 shcool and the perpos is just simplefy the project for others and refrech the project consipte to batter understand

what you will know here:
what is the ip
what is the mac
what is the router
what is the switch
what is the subneting
what is the type of netwoks
and o lot of things to check out on your self

what is the ip address:
IP -> standes for internet protocol means is an internet address witch mean's without it we can not access the internet
and we have to defrent type of the ips (ipv4, ipv6), here we will talk about the ipv4 as is must used in these days
the ipv4 save two types also, privet ip and the public ip address, lats talk what is the perpose of each one in a quick
the prived ip address is a unique address in the LAN(local erea netwok) and with it we can accress all the devices in the LAN
as i sayed just for the LAN that mean's we can not use it to access the internet, bunos -> the ip address have 5 calsses needs to know
you have a range of classes you can use based on the number of LAN devices if you have more then 256 divece you will not use the class C
i forget to tell you guys the callasses sorry
the 5 classes:
Class A  -> 10.0.0.0/8
Class B  -> 172.0.0.0/16
Class C  -> 192.168.0.0/24  this is the famouse one used in HOME LAN
Class D  -> NOT USED (reserved)
Class E  -> NOT USED (reserved)

the (class a) can give use a range of 2^24(24 number of free bit to use ^2(based on the binary 0 and 1)) will give use 16,777,216 millon device and i a huge number for a HOME LAN that why is not famous as the (Class C) 
the (class b) can give use a range of 2^16 = 65536 ip use can use it for a Medume LAN
the (class c) can give use a range of 2^8 = 256 devices on the LAN network and that what we see in the HOME netwok a small range will 256

last's talk about the getway and the breadcast of the ip address(ipv4)
you can say why is not 255 and 256?
this is just a singe that the first one is 0 is not couted and we add 1 to conted the 0 of the first ip address what why.
what is the brodcast:
imagen we have a protocal(Like; ARP("you can lean about this protocol if you need")) that every time needs to get a MAC address of other device
and this protocal to get a mac address of other device he have one info about the device, it's a LAN IP address and the protocal needs to get the MAC address(what is the MAC I will expline it more, from know just take it as an address of a device like the IP)
and the ARP protocal they don't know the exacte location or the path to get send the message to a specifec device to get it's MAC address that why we have the broadcast address and i the last ip we can use just for the broadcast and we can not use it to eidentify a device with this ip address.
and this is the broadcast ip address usege send message to every one in the netwok for get information and configuration stuff

what is the netwok address and the getaway?
last talk first about the netwok address, imagen we have a loot of netwok before you specify the ip address of the device distination we have to get the network address of the destination because we have a lot of networks in the LAN(to better understanding, look at the picture and you will know what am talking about


https://d1tzxux72fvryy.cloud![M34d23a861cb6354e6673806eaf0246541719481544005](https://github.com/user-attachments/assets/4079912a-53aa-4818-96ae-24129b5c777b)

picuter from -> https://mockflow.com/flowchart-examples/cisco-network-diagram-example-network-address-translation
