# SCUTUM Firewall

Current Version: 2.1 beta

#### Change Log:
1. Fixed Automatic DNS Whitelisting. SCUTUM UDP firewall will now whitelist your DNS automatically. The previous setting was OpenDNS only.

![scutum](https://user-images.githubusercontent.com/21986859/27244999-2f151bd0-52b7-11e7-80e1-47b23364215b.png)


### What is SCUTUM?
<b>Long story short, ARP firewall. It automatically adds gateways to the whitelist on connect and blocks everthing else to avoid potential threat.</b>

SCUTUM is an ARP firewall that prevents your computer from being arp spoofed. Scutum controls "arptables" in your computer so it accepts ARP packets only from the gateway. This way, when people with malicious intentions cannot spoof your arp table. Scutum also prevents other people from detecting your device on LAN if scutum is used with properly configured TCP/UDP firewall.

SCUTUM is also capable of handling tcp/udp/icmp traffic with iptables. You can choose to enable this feature during installation. However, a more professional firewall controller like UFW is recommended. They can handle traffic with more precision.


#
### Usage & Installation
You should run a installation before running it for the first time for setting up configuration files. 
<b>I am not sure if portable version is necessary. If you think this should be changed, raise an issue and I will change it.</b>
#### Installation
~~~~
git clone https://github.com/K4YT3X/SCUTUM.git
cd SCUTUM/
sudo python3 scutum.py --install  # scutum.py deletes itself after installation
cd ../
rm -rf SCUTUM/
~~~~

#### Usage
This should be easy
SCUTUM starts <b>automatically</b> by itself after installation
~~~~
$ sudo scutum # Start SCUTUM
$ sudo scutum -r # Reset SCUTUM (Allow all ARP traffic)
$ sudo scutum -p # Purge SCUTUM logs
$ sudo scutum --install # Run scutum installation wizard and install SCUTUM into system
$ sudo scutum --uninstall # Remove SCUTUM from system completely 
~~~~


#
### SCUTUM Workflow:
#### postconnect
1. Connect to wifi
2. Accept all ARP packets
3. Cache gateway MAC address by establishing a socket connection with a timeout of 0
4. Add Gateway MAC to exception
5. DROP all ARP packets

[Finished]


#### postdisconnect
1. Accept all ARP packets

[Finished]