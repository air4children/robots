# Software 

## 1. Cloning air4children project
### 1.1 Quick access with the use of a ZIP project
Download main.zip or the relevant branch:  
* https://github.com/air4children/robots/archive/refs/heads/main.zip
* https://github.com/air4children/robots/archive/refs/heads/otto-humanoid.zip

### 1.2 Clone GitHub project.
Open a terminal (GNU/Linux) or GitBash (in windows) 
```
mkdir -p ~/repositories/air4children
cd ~/repositories/air4children
git clone https://github.com/air4children/robots.git
```
Example of the output
```
$ git clone https://github.com/air4children/robots.git
Cloning into 'robots'...
remote: Enumerating objects: 225, done.
remote: Counting objects: 100% (225/225), done.
remote: Compressing objects: 100% (174/174), done.
remote: Total 225 (delta 59), reused 211 (delta 46), pack-reused 0
Receiving objects: 100% (225/225), 46.09 MiB | 4.19 MiB/s, done.
Resolving deltas: 100% (59/59), done.
```

## 2. Installation of Blocky
### 2.1 Windows 10x64
1. Download API here: https://github.com/OttoDIY/blockly/releases/tag/v1.4.0   
	Other versions will work but have not being tested: https://github.com/OttoDIY/blockly/releases   
2. Unzip and install.
3. Open the example for Humanoid.
4. Connect your Otto robot.
5. Select Arduino nano, USB port where Otto is connected.
6. Check the code.
7. Upload!


### 2.2 Ubuntu 18.04x64, 20.04x64
#### Dependencies (nodejs, npm)
* Uncomment lines that correspond to your Ubuntu version
```
cd
#curl -sL https://deb.nodesource.com/setup_10.x -o nodesource_setup.sh #ubuntu-18-04
#curl -sL https://deb.nodesource.com/setup_15.x -o nodesource_setup.sh #ubuntu-20-04
sudo bash nodesource_setup.sh
sudo apt install -y nodejs
#nodejs -v #ubuntu-18-04
#node -v #ubuntu-20-04 #> v15.14.0 on  Sun 15 Aug 02:16:57 BST 2021
```
* Update node
``` 
npm install -g npm@8.1.1
```


See the following links to install node-js on [ubuntu-18-04](https://www.digitalocean.com/community/tutorials/how-to-install-node-js-on-ubuntu-18-04) or [ubuntu-20-04](https://www.digitalocean.com/community/tutorials/how-to-install-node-js-on-ubuntu-20-04).

#### Clone Blocky repository in the branch `versionlinux`
* Clone repository
```
cd ~/repositories/air4children
git clone --single-branch --branch versionlinux https://github.com/ottodiy/blockly
#or: `git clone https://github.com/ottodiy/blockly && git checkout linuxversion`
cd blockly
npm install
sudo chown -R $USER:$(id -gn $USER) /home/$USER/.config
npm start #to test app
npm run compiler #To compile
```
* Setting up permission to the usermod and ports

check USB connection
``` 
ls -l /dev/ttyUSB*
```
terminal output   
```
$ ls -l /dev/ttyUSB*
crw-rw---- 1 root dialout 188, 0 Aug 15 10:49 /dev/ttyUSB0
```

setting up permissions    
``` 
sudo usermod -a -G dialout $USER
sudo chmod a+rw /dev/ttyUSB0
```

_**NOTE.** You need to reboot your machine for the group changes to take effect._

#### Cleaning blocky node project
``` 
rm -rf dist/ && rm -rf node_modules/ && rm -rf package-lock.json
```


## 3. Usage Instructions
1. Open a terminal and run: 
```
cd ~/repositories/air4children/blockly
npm start #to test app
 ```
2. Connect your robot to an avaible USB post and 
3. In the OttoBlockly choose: 
	Board: Arduino Nano;    
	Port:/dev/ttyUSB0   


## 4. References
* GNU/Linux version: 
   * branch `versionlinux`: [README](https://github.com/mxochicale/blockly/tree/versionlinux#otto-blockly-for-gnulinux-os) 
   * blocklyLinux: https://github.com/OttoDIY/blocklyLinux   
* See [EXTRAS](EXTRAS.md) notes for issues and other notes  
* Issue related to the linux installation https://github.com/OttoDIY/blockly/issues/38 
* dialout group permissions: https://www.arduino.cc/en/Guide/Linux  
