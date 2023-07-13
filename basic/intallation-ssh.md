# openssh-server 설치 하기

> sudo apt update

> sudo apt install -y openssh-server

> servicectl status openssh

> sudo ufw allow ssh

접속 시도 -> 오류 발생 한다.

* ubuntu@192.168.64.6: Permission denied (publickey).

접속 권한을 안주어서 문제. ssh 접속지 password 도 가능하게 설정을 바꾼다

해결 방법 



## 설정 변경 하기
sudo nano /etc/ssh/sshd_config

![image](https://github.com/matin03/study-linux/assets/3805205/d4dc8aee-2ed7-427e-b8e4-0628f1b8ec5e)
