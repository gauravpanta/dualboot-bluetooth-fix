# dualboot-bluetooth-fix
Fix for pairing devices across dual boot config

- Pair your device on Windows and Ubuntu
- Boot to Ubuntu
- Copy your Windows pairing keys by following these commands, mount your windows volume to ubuntu and open a terminal in this folder
  - cd /[WindowsSystemDrive]/Windows/System32/config
  - sudo apt-get install chntpw
  - chntpw -e SYSTEM
  - cd ControlSet001\Services\BTHPORT\Parameters\Keys
  - ls
  - cd [your bluetooth mac address]
  - ls
  - hex [001ex2ds5a78] <- your bluetooth device you connected mac address
   => :00000 XX XX XX XX XX XX XX XX XX XX XX XX XX XX XX XX ...ignore..chars..
- Copy the xx stuff and ignore others ( the xx stuff is the pairing key that bluetooth uses to pair device, we will replace this into our ubuntu)
- exit this terminal and you can unmount the drive
- Open a new terminal and do the following:
  -  sudo -i
  -  cd /var/lib/bluetooth
  -  ls
  -  cd [your bluetooth mac address]
  -  ls
  -  cd [your device bluetooth mac address]
  -  nano info
   [LinkKey]
   Key=XXXXXXXXXXXXXXXXXXXXXXXXX 
  - Replace the link key without spaces
  - CTRL+X [save and exit]
  - sudo systemctl restart bluetooth 
- DONE!!!
  

