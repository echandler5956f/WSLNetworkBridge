# WSLNetworkBridge
A simple package containing the files I used to dynamically bridge network ports on WSL2. Tested with Windows 11 running ROS Melodic on a Turtlebot3.

Place the .exe and .dll files somewhere in your windows directory, and put the .sh anywhere you feel comfortable calling it from.
You will have to edit the .sh to tell the program where your .exe is located.

After that, you will want to add the following line to your ~/.profile in WSL2, replacing the "{Your IP}" with your IP address.
Note that this will prompt you for your password each time you login. 
There are probably better ways to do this, but it works:
kfc="$(sudo ifconfig eth0:1 {Your IP} netmask 255.255.255.192 up)"

Now, whenever you want to connect to something that requires dynamic port bridging (i.e. connecting to another machine running ROS), you can simply run the .sh script. 
Note that running the bash script isn't necessary when running ROS locally- only when connecting to external machines like a Turtlebot.

# Disclaimer: 
Credits for the main executable and .dll go to CzBix from https://github.com/CzBiX/WSLHostPatcher. 
More information about WSL network problems and solutions can be found here: https://github.com/microsoft/WSL/issues/4150#issuecomment-1018524753
