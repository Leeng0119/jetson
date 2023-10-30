# jetson
#1 "sudo sh install.sh" 명령은 Unix 또는 Linux 기반의 운영 체제에서 사용되는 명령어입니다. 이 명령어를 실행하면 "install.sh"라는 쉘 스크립트를 실행하는 것입니다. "sudo"는 슈퍼 유저 또는 관리자 권한으로 명령어를 실행하라는 것을 나타내며, 이렇게 하면 보통의 사용자 권한으로 실행하는 것보다 높은 권한으로 실행됩니다.

"install.sh"는 쉘 스크립트 파일의 이름입니다. 이 스크립트 파일은 주로 어떤 소프트웨어를 설치하거나 설정을 변경하는 데 사용됩니다. 스크립트 내용과 스크립트가 어떤 작업을 수행하는지에 따라 설치할 소프트웨어나 설정이 다를 수 있습니다.

따라서 "sudo sh install.sh" 명령을 실행하면 "install.sh" 스크립트가 실행되고, 해당 스크립트가 무엇을 하는지는 스크립트 내용에 따라 다를 것입니다. 스크립트를 실행하려면 "install.sh" 파일이 존재하고 실행 가능한 상태여야 합니다.

#2 2장, Jetpack & ROS install
https://drive.google.com/file/d/1HU5F1cwiw2wzuNBdLL9R3Wvpg5AXLzw5/view?usp=sharing 4GB 이미지

1.1. Terminal(=SSH)에서 WiFi 연결하기

# 실행해야할 명령
$ sudo nmcli device wifi list
$ sudo nmcli device wifi connect <ssid_name> password <password>
$ ifconfig

# 명령어 실행 예제
# password가 없는 경우
1, zeta@jp461:~$ sudo nmcli device wifi connect STARTUP_LOUNGE_love
2, ifconfig
# password가 있는 경우
jetson@jp4512G:~$ sudo nmcli device wifi connect U+NetD681 password xxxxxxx

# 연결을 해제할 때
$ sudo nmcli device disconnect wlan0

#명령 실행 로그
jetson@jp4512G:~/catkin_ws$ sudo nmcli device disconnect wlan0
Device 'wlan0' successfully disconnected.

1.2 Cooling Fan
cd Downloads
git clone https://github.com/jetsonworld/jetson-fan-ctl.git  --->ls
cd jetson-fan-ctl

sudo sh install.sh

2.1 ROS Melodic 설치

cd ~/Downloads/
sudo apt update

git clone https://github.com/zeta0707/installROS.git
cd installROS
./install-ros.sh













