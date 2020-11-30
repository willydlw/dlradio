# dlradio

Repository for Doodle Lab radio testing and configuration


## Getting Started

Hardware

- 2 Doodle Lab Radios
- 2 Doodle Lab Evaluation Kits 
- 2 Ethernet Cables
- 2 Computers with Ethernet ports (or USB to Ethernet adapters)
- DC power supply (5.5 - 42 V) or batteries or AC adapters
- 2 power cables with 2.5mm jack

The [integration guide](./guides/Smart-Radio-2x2-MIMO-Integration-Guide-V1120.pdf) section, *Setup Information*, walks you through the steps required to test that the radios are communicating via a ping and iperf testing.

Connect the antennas to the radios before supplying power. If testing in close proximity, indoors, use the included attenuator.

Use the ETH0 connection (one farthest to left of power plug) on the evaluation kit's pcb for testing. The ETH1 port has a static ip address that is used only for configuration.<br><br>

### Configure Static IP Address

Each computer must be configured with a unique static IP address on the 10.223.0.0/16 subnet. For simplicity, set the IP address of one computer to 10.223.0.10 and the other computer to 10.223.0.20.

The Ubuntu 18.04 Linux command: `sudo ifconfig 10.223.0.10 eth0` will set the static IP address. This command must be modified to match the name of the computer's ethernet interface. 

Run the command `ifconfig` to view the ethernet interface name. Or use `ip link show`. The ethernet interface name will start with the letter e. Use that name in place of eth0.

Afterward, run the command `ifconfig` again to see that the static ip address has been updated.<br><br>

### Ping Test

After setting the static IP addresses on each computer, check the connection by pinging each computer, using the other computer's static IP address. 

```bash
ping 10.223.0.10
```

If everything is set up properly, each computer should receive a response from the other.<br><br>

### iperf3 Test

Now, run an iperf3 test as detailed in the guide. If this test fails, see the [configuration guide](./guides/Smart-Radio-Configuration-Guide-v1020.pdf) section *Firewall Settings* for ensuring the firewall is setup to allow access on the port 5001.