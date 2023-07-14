# openssh-server 설치 하기

흔히 ubuntu 를 사용하게 되면 gui 보다 terminal 로 작업을 하는게 수월 하다.
그러다 보니 ssh 를 많이 사용 하게 되니, docker 나 multilink 등 성치를 하고 나면 꼭 ssh 를 사용 하자. 

특히 docker 나 원격 개발을 하기 위해서는 Intellij / vscode 에서 ssh 개발을 지원하니 설치해서 사용 하면 아주 좋다. 


1. 언제나 습관 처럼... apt update!
<pre>
$ sudo apt update
</pre>

2. openssh-server 설치
<pre>
$ sudo apt install -y openssh-server
</pre>

설치 완료후 서비스 상태도 확인을 해야지... 못믿을 놈의 컴퓨터놈들...
<pre>
$ servicectl status openssh  
</pre>

3. 방화벽에서 포트를 열어 준다. ssh 는 22번을 사용한ㄷ.
<pre>
$ sudo ufw allow ssh  
</pre>


자 모든 준비가 끝났다. 


다른 컴퓨터에서 접속 해보자...

<pre>
$ ssh ubuntu@아이피.넣어주자 
</pre>

<strong>오류가 발생한다.</strong>
<pre>
ubuntu@192.168.64.6: Permission denied (publickey).  
</pre>



## 설정 변경 하기

다시 ubuntu 에서 설정을 바꿔 준다.

에디터로 설정 파일을 열어서..
<pre>
$ sudo nano /etc/ssh/sshd_config  
</pre>

![요렇게 고쳐주자](https://github.com/matin03/study-linux/assets/3805205/d4dc8aee-2ed7-427e-b8e4-0628f1b8ec5e)

<em>
  PasswordAuthentication yes
</em>

이 항목을 yes 로 수정 했으면 이제 ssh 서비스를 재시작 해주자

<pre>
$ sudo systemctl restart ssh
</pre>

