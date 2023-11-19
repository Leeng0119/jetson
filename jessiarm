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

~/catkin_ws까지 만들어집니다. 지금까지 작업하면 폴더는 아래와 같을 것입니다.

2.2 .bashrc 수정

PC, Jetson에 작업을 편리하게 할 환경을 .bashrc에서 추가해줍니다. alias 명령어추가, PC ↔ Jetson remote 환경을 설정합니다.
# mirco USB 케이블 연결을 사용할 경우
192.168.55.1: Jetson IP
192.168.55.100: PC IP
(하지만 후에 알기로는 IP를 넣은 코드를 베시에 넣는 다면 코드가 엉켜버려 후에 뺴버렸다.) 

2.4 ROS 동작 확인(Option)
설치 후 제대로 되었는지 turtlesim으로 확인할 수 있습니다. 세 개의 창에 하나씩 아래 명령어를 실행해주세요. 두가지 방법으로 실행 가능합니다.
. ROS remote 환경
. PC에서 VNC로 Jetson에 접속, 또는 Jetson에 TV를 연결
# 터미널 #1
jetson@jp4512G:~/catkin_ws$ roscore
# 터미널 #2
jetson@jp4512G:~/catkin_ws$ rosrun turtlesim turtlesim_node
# 터미널 #3
jetson@jp4512G:~/catkin_ws$ rosrun turtlesim turtle_teleop_key

Teleop by keyboard
원래는 조이스틱도 할려고 했지만 시간상에 관계로 패스 하였습니다 
할수 없이 키보드에 젯슨을 연결하여 진행하였습니다.

1.  teleop_keyboard 키 사용 방법
실행했을때 message입니다.
Control Your Robot!
---------------------------
Moving around:
        w
   a    s    d
        x

w/x : increase/decrease linear velocity (~ 1.2 m/s)
a/d : increase/decrease angular velocity (~ 1.8)

space key, s : force stop

CTRL-C to quit
이를 실행 시키기 위한 코드로는 
# terminal #1
$ roslaunch jessicar_control keyboard_control.launch

# terminal #2
$ roslaunch jessicar_teleop jessicar_teleop_key.launch

사용법으로는 W는 전진 X는 후진 S는 정지를 담당한다

W,X를 단계 별로 누를떄마다 속도가 빨라지며 4단계 까지 있다

터미널 #3, CV Magic, Bind Ball with Pixel Value
requires load parameter at first
jetson@jp4612GCv346Py37:/catkin_ws$ rosparam load src/jessiarm/jessiarm_control/config/find_ball.yaml jetson@jp4612GCv346Py37:/catkin_ws$ rosrun jessiarm_cv find_ball.py

터미널 #4, Blob Point to Twist
$ rosrun jessiarm_control chase_the_ball.py

터미널 #5, PWM Control node
$ rosrun jessiarm_control blob_chase.py

11장, Yolo4 PicknPlace 1.1 darknet_ros 설치 sudo apt-get install -y ros-melodic-image-pipeline

cd ~/catkin_ws/src git clone --recursive https://github.com/Tossy0423/yolov4-for-darknet_ros.git 1.2 darknet_ros 수정 yolov4 → yolov4-tiny로 수정, 그리고 custom dataset에 해당하는 config, weights 적용

cd ~/catkin_ws/src/yolov4-for-darknet_ros/darknet_ros git clone https://github.com/zeta0707/darknet_ros_custom.git cp -rf darknet_ros_custom/* darknet_ros/ package가 준비 되었으므로 빌드합니다.

zeta@zeta-nano:/catkin_ws/src$ cd .. zeta@zeta-nano:/catkin_ws$ cma 2. darknet_ros 실행 2.1 coco 객체 PicknPlace #terminal #1, object detect using Yolo_v4 jetson@jp4612GCv346Py37:~$ roslaunch darknet_ros yolo_v4.launch

#terminal #2, camera publish, object x/y -> robot move jetson@jp4612GCv346Py37:~$ roslaunch jessiarm_control yolo_chase.launch










