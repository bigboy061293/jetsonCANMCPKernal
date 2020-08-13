# jetsonCANMCPKernel

Connect first MCP251x chip to SPI1 on 40-pin, use CS0 pin, connect INT on Pin 31 (GPIO Z.0)  
Connect second MCP251x chip to SPI2 on 40-pin, use CS0 pin, connect INT on Pin 32 (GPIO V.0)  
Copy mcp251x.ko on target under /lib/modules/4.9.140-tegra/kernel/drivers/net/can/spi/  
Copy tegra210-p3448-0000-p3449-0000-a02-mcp251x.dtbo under /boot/  
Copy tegra210-p3448-0000-p3449-0000-a02.dtb under /boot/dtb/  
Run /opt/nvidia/jetson-io/jetson-io.py  
Select Configure Jetson for compatible hardware  
Select MCP251x CAN Controller  
Save and reboot  
Make CAN0 and CAN1 inerface up on network:  
ip link set can0 up type can bitrate 500000  



To make the CAN-interface permanent, add the following lines to /etc/network/interfaces  

auto can0  
iface can0 can static  
    bitrate 500000  


For JSNN / Radar  
sudo apt-get install python-pip -y  
sudo apt-get install libxml2-dev libxslt-dev python-dev -y  
sudo pip install pymavlink  
sudo pip install python-can  
