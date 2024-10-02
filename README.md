# ROS 

## bashrc 설정

sudo apt install 명령으로 설치한 ros pkg가 /opt/ros/humble에 저장됌 따라서 pkg를 불러와서 사용해야함

처음에 ros2 키워드 사용 시 안먹음 --> bashrc 설정 안해줘서

```
vi ~/.bashrc 안에
echo "ROS2 humble is activated!"
source /opt/ros/humble/setup.bash
```
이후 터미널에 soruce ~/.bashrc  설정해주면 ros2 키워드 바로 먹힘

하지만 우리는 ros2만 사용하는 것이 아니기 때문에 alias 키워드를 통해 따로 설정해줌

```
vi ~/.bashrc 안에
alias humble="source /opt/ros/humble/setup.bash; echo \"ROS2 humble is activated!\""
```

설정 및 저장해주고 터미널에 humble 입력 시 설정됌

<br/>
## ros_domain_id 설정

ros2에서 내가 주고받는 데이터만 확인하기 위해 ID를 정의해주는데 마찬가지로 bashrc에서 설정

```
alias ros_domain="export ROS_DOMAIN_ID=13; echo \"ROS_DOMAIN_ID=13\""
alias humble="source /opt/ros/humble/setup.bash; ros_domain; echo \"ROS2 humble is activated!\""
--> humble에다가 ros_domain을 호출하도록 넣어줌
```

---

## node

ros에서 실행가능한 최소한의 단위

#### ros2 run <pkg_name> <node_name>

#### ros2 node list, ros2 node info <node_name> 로 정보 확인가능

<img width = "50%" img src ="https://github.com/user-attachments/assets/713d29bd-06db-4607-938a-3d1616985e19">


<br/><br/>

---

## service

<img width = "30%" img src ="https://github.com/user-attachments/assets/d057b388-2ab6-4b23-b89f-5abe0e486509">

서비스는 AUTOSAR의 서비스 생각하기 , 말그대로 서비스개념임

#### ros2 service list를 통해 service list확인가능
```
/clear
/kill
/reset
/spawn
/turtle1/set_pen
/turtle1/teleport_absolute
/turtle1/teleport_relative
/turtlesim/describe_parameters
/turtlesim/get_parameter_types
/turtlesim/get_parameters
/turtlesim/list_parameters
/turtlesim/set_parameters
/turtlesim/set_parameters_atomically
```

이때 그 service의 type (C언어의 자료형)을 확인하기위해

#### ros2 service type < > 을 통해 확인가능

```
ros2 service type /turtle1/teleport_absolute 
결과 --> turtlesim/srv/TeleportAbsolute
```
<img width = "60%" img src ="https://github.com/user-attachments/assets/e183ae40-b64d-499e-ba43-3c33eeba6fb4">

<br/><br/>

<img width = "55%" img src ="https://github.com/user-attachments/assets/996147c6-dd0c-4ead-b7c0-332af0daae5b">

서비스에서 service definition이 필요함 (Type정의) 이것이 .srv 파일에 정의되어있음

구분자 (---)를 기준으로 위는 Request, 아래는 Response


#### ros2 interface show < > 명령어로 터미널에서 확인가능

<img width = "60%" img src ="https://github.com/user-attachments/assets/e66d6134-5937-4e25-ac57-830db7e058fb">


+) ros는 degree보다 radian단위를 좋아함(파이꼴)


#### ros2 service call <service_name> <service_type> "{arg}" 로 service를 부를 수 있음

<img width = "75%" img src ="https://github.com/user-attachments/assets/894335f1-d4ce-4d33-898b-1f6d92b128d1">


이때 <service_name>은 service list로 확인하고 , <service_type>은 service type으로 확인하고 , {arg}는 interface show로 확인한다.




#### namespace

<img src="https://github.com/user-attachments/assets/70092aaf-317b-4a69-a18d-be516d4de0ea">

처음에 ros2 service list하면 나오는 것들 중 /turtle1/~~~ 도 있고, /turtlesim/~~~도 있는데 이게 뭘까?? 했더니 

--> namespace다 !! 라는것

이후 spawn을 통해 godveryday라는 거북이를 소환하고 다시 service list를 보면 /godveryday/~~~가 생긴것을 확인가능함

---

## Topic 





