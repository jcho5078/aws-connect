# aws-connect
### aws ec2, RDS 생성 및 연결

사용환경: ec2 리눅스<br> 
<h5>3/12-</h5> 나는 window환경을 사용하므로 'putty' 라는 프로그램 사용하여 aws 연결 성공.<br>
        aws의 데이터베이스는 Mysql으로 생성. mysql Workbench로 생성한 aws DB에 접속하려 했으나, 자꾸 오류남.<br>
        (연결이 안되면 보안그룹 문제라고들 하는데, 같은 보안그룹으로 ec2 인스턴트 연결은 잘되어서 본인의 workbench 사용 미숙으로 알고 다른 방법 모색함.<br>
        진짜 이걸로 3~4시간 가까이 씨름한듯.)<br>
<br>
<h5>3/13-</h5> 사용했던 putty를 이용하여 aws에 연결을하고 ec2 인스턴트에 직접 mysql 설치를하여 mysql 접속 성공.<br>
        putty를 사용하여 aws에 접속한 후, putty의 CLI 터미널 창에서 mysql 설치함. 리눅스 입력 커맨드와 같음.<br>
        1.mysql -v 입력하여 해당 인스턴트에서 mysql 설치 확인.<br>
        2.설치가 안되어있다면 sudo yum install mysql 입력하여 mysql 설치.<br>
        3.mysql -u [마스터 사용자 이름] -p -h [RDS 인스턴스 엔드포인트] 입력하여 생성한 RDS에 연결.<br>
        4.RDS 생성시 설정한 비밀번호 입력 후 RDS의 mysql에 로그인.
