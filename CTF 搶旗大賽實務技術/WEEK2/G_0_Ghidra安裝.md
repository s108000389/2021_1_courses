# Ghidra 
```
Ghidra is a software reverse engineering (SRE) suite of tools 
developed by NSA’s Research Directorate in support of the Cybersecurity mission.

Ghidra is open-source.
```
# 撰寫 run ghidra.sh
```
Ghidra Installation on Ubuntu |18.04, 16.04, 14.04
Posted on March 26, 2019 by Yılmaz Cemalettin
https://www.ylmzcmlttn.com/2019/03/26/ghidra-installation-on-ubuntu-18-04-16-04-14-04/
```
```
mkdir Ghidra
cd Ghidra
wget https://ghidra-sre.org/ghidra_9.0.1_PUBLIC_20190325.zip
unzip ghidra_9.0.1_PUBLIC_20190325.zip
cd ghidra_9.0.1
sudo add-apt-repository ppa:openjdk-r/ppa 
sudo apt update 
sudo apt install openjdk-11-jdk 
sudo apt install openjdk-11-jre-headless
chmod +x ghidraRun
./ghidraRun
```
```
OK

```
