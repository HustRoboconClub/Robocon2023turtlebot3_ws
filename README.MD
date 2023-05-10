Huong dan: 
Yêu cầu : - Ubuntu 22.04
		   - Cài đặt ROS2 Humble

Mở Terminal và chạy các lệnh sau:
----------Cài đặt và cấu hình Workspace-------------
- Source cấu hình Ros vào layer làm việc (Câu lệnh sẽ ghi thêm vào file .bashrc)
	~$ echo "source /opt/ros/humble/setup.bash" >> ~/.bashrc
- Cài đặt vcs-tool:
	~$ sudo apt install python3-vcstool
- Clone lại workspace trên github của CLB:
	~$ git clone https://github.com/HustRoboconClub/Robocon2023turtlebot3_ws.git
- Truy cập vào thư mục src của ws vừa clone về :
	~$ cd Robocon2023turtlebot3_ws/src
- Cài đặt gói turtlebot3:
	~/Robocon2023turtlebot3_ws/src$  vcs import . < turtlebot3.ros2.repos
- Quay lại thư mục chính của ws: 
 	~/Robocon2023turtlebot3_ws/src$ cd ~/Robocon2023turtlebot3_ws 
- Chạy lệnh build các packages của ws:
	~/Robocon2023turtlebot3_ws$ colcon build
	-Cần cài đặt Gazebo: 
	-sudo apt install gazebo
	-udo apt install ros-humble-gazebo-ros-pkgs
- Source ws vào layer làm việc (mỗi terminal mới đều phải chạy lại lệnh này, nếu muốn lệnh này luôn chạy thì ghi vào file .bashrc)
	~/Robocon2023turtlebot3_ws$ source install/setup.bash

----------Chạy Mô phỏng TurtleBot--------------
- Chạy lệnh export robot (mỗi terminal mới đều phải chạy lại lệnh này, nếu muốn lệnh này luôn chạy thì ghi vào file .bashrc)
	~/Robocon2023turtlebot3_ws export TURTLEBOT3_MODEL=waffle
- Tại thư mục ws chạy lệnh launch:
	- gazebo   ( Can bat gazebo thu cong bang tay ) 
	~/Robocon2023turtlebot3_ws ros2 launch turtlebot3_gazebo turtlebot3_world.launch.py
	
+ Điều khiển Robot:
1. Sử dụng gói điều khiển robot bằng bàn phims:
	~/Robocon2023turtlebot3_ws ros2 run turtlebot3_teleop teleop_keyboard 
2. Điều khiển bằng tay cầm (Hiện tại đang cấu hình cho tay cầm ps4, các tay cầm khác có thể không hoạt động ):
	~/Robocon2023turtlebot3_ws ros2 launch teleop_twist_joy teleop-launch.py

+ Chạy Yolo bằng cam robot mô phỏng
 ~/Robocon2023turtlebot3_ws ros2 run yolo_pkg detect_note
 
 

sudo apt install python3-vcstool

sudo apt install ros-humble-gazebo-*
sudo apt install ros-humble-navigation2
sudo apt install ros-humble-nav2-bringup
sudo apt install ros-galactic-slam-toolbox

---Cai dat goi turtlebot3--
vcs import . < turtlebot3.ros2.repos

---export model. Co the ghi them vao file .bashrc---
export GAZEBO_MODELPATH=$GAZEBO_MODEL_PATH:~/turtlebot3_ws/src/turtlebot3/turtlebot3_simulations/turtlebot3_gazebo/models
export TURTLEBOT3_MODEL=waffle
