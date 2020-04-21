# aws-connect
## aws ec2, RDS 생성 및 연결

사용환경: ec2 리눅스<br> 
<h5>3/12-</h5> 나는 window환경을 사용하므로 'putty' 라는 프로그램 사용하여 aws 연결 성공. <br>
        출처:https://blog.naver.com/zion830/221353353266<br>
        aws의 데이터베이스는 Mysql으로 생성. mysql Workbench로 생성한 aws DB에 접속하려 했으나, 자꾸 오류남.<br>
        (연결이 안되면 보안그룹 문제라고들 하는데, 같은 보안그룹으로 ec2 인스턴트 연결은 잘되어서 본인의 workbench 사용 미숙으로 알고 다른 방법 모색함.<br>
        진짜 이걸로 3~4시간 가까이 씨름한듯.)<br>
<br>
### 사용했던 putty를 이용하여 aws에 연결을하고 ec2 인스턴트에 직접 mysql 설치를하여 mysql 접속 성공.<br>
        putty를 사용하여 aws에 접속한 후, putty의 CLI 터미널 창에서 mysql 설치함. 리눅스 입력 커맨드와 같음.<br>
        putty 사용 안해도 CLI를 통해 해당 키 파일이 있는 위치에서 해당 ec2의 접속명령어 사용하여 접속 가능.<br>
        1. mysql -v 입력하여 해당 인스턴트에서 mysql 설치 확인.<br>
        2. 설치가 안되어있다면 sudo yum install mysql 입력하여 mysql 설치.<br>
        3. mysql -u [마스터 사용자 이름] -p -h [RDS 인스턴스 엔드포인트] 입력하여 생성한 RDS에 연결.<br>
        4. RDS 생성시 설정한 비밀번호 입력 후 RDS의 mysql에 로그인.<br>
## aws ec2 자바, 톰캣 설치, 파일 업로드
### (리눅스사용 기반)aws의 우분투에서 sudo apt-get install openjdk-8-jre 로 자바 설치(apt-get안된다면 yum사용)<br> 
               (jre설치후 우분투에서 java -version 입력하여 설치 및 버전 확인.<br>
               aws 우분투에서 sudo apt-get install tomcat8 입력하여 톰캣 설치.<br>
               sudo ufw allow (톰캣 포트번호)/tcp 로 방화벽에서 톰캣의 외부접속을 허용한다.<br>
               sudo service tomcat8 start 로 톰캣 실행.<br>
               인스턴스의 /var/lib/tomcat8/webapps 경로에 스프링 war파일 넣어야기에 우분투에서 해당 경로에 권한 부여 해야함. <br>
               실행시킨 상태에서 fileZilla나 winscp로 aws ec2생성시 받은 개인키로 파일 업로드.<br>
               후에 https://aws인스턴스ip:8080/프로젝트명 을 웹 주소창에 쓰면 본인 결과물 배포완료.<br>
               (8080은 톰캣 기본 ip이므로 본인 인스턴트의 톰캣 ip
               참고: https://windosakacastle.tistory.com/17?category=691705
