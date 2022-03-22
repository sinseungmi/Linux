> # Linux 
> ### 기본 개념 및 명령어 정리 
> <br>
> 
> ##### YUM(Yellow Dog update Modified) - 프로그램(패키지) 설치 관리 도구
> ```
> yum [옵션] [명령] [패키지명]    
> ```
> <br>
> 
> 1. YUM 패키지 설치/삭제 명령
> ```
> yum install 패키지명 // 패키지 설치
> yum remove 패키지명 // 패키지 삭제
> ```
> <br>
> 
> 2. 패키지 모듈을 update하는 명령. (단, 설치되어 있지 않으면 but not installed 메시지가 뜹니다.)
> ```
> sudo yum update lrzsz
> ```
> <br>
> 
> 3. apt remove, purge, autoremove 명령어 <br>
> #### apt-get remove
> -remove 명령어는 패키지를 삭제하지만 환경설정은 삭제하지 않습니다.
> ```
> sudo apt-get remove openjdk*
> sudo apt remove openjdk*
> ```
>
> ```
> autoremove : 예전에 다른 패키지의 의존성 때문에 설치되었지만, 지금은 사용되지 않는 패키지를 삭제
>
> sudo apt-get autoremove 
> 
> sudo apt-get remove --auto-remove (package)
>
> sudo apt-get purge --auto-remove (package)
> : remove 또는 purge를 사용할 때 --auto-remove 옵션을 주어 한번에 의존성 패키지를 삭제할 수도 있다.
> purge만하면 삭제가 안된다 그냥 (프로세스)정지 시키는거! 뒤에 옵션까지 줘야지 삭제가 된다.(패키지,환경설정파일까지)
> remove를 해야지 보이는 파일까지 삭제된다. 
> (purge를 했다 해도 remove를 해야지 보이는 파일까지 삭제?)
> ```
>
> <br>
>
> **실행중인 서비스에서 아파치가 실행되고 있는지 확인**
> ```
> $ service --status-all
> ...
> [ + ]  apache-htcacheclean
> [ + ]  apache2
> ...
> ```
>
> ### ps (Process Status) - 현재 실행 중인 프로세스 
>
> **★ps -e 항상 프로세스 확인 먼저!!(실행되는지 안되는지)** <br>
> : 커널 프로세스를 제외한 실행 중인 모든 프로세스를 출력 하는 옵션 <br> <br>
> ★**ps -df** <br>
> : 톰캣이나 아파치 실행 중인거 확인하고 싶을 때 이걸로 확인! <br>
> **-d** : 세션 리더를 제외한 모든 프로세스를 보여줌. <br>
> **-f** : 프로세스에 대한 자세한 정보를 출력. (PPID 확인 가능) <br> <br>
>
> **설치하는 모든 경로 무조건 적어놓기! 왜냐면 나중에 삭제할 때 꼭 필요함** <br>
> **(웬만하면 보편적으로 사용하는 경로를 지정하는게 좋음)**
> ```
> 아파치-톰캣:  /opt/tomcat/apache-tomcat-9.0.60
> 자바: /usr/lib/jvm/default-java
> ``` 
> <br>
> 
> **sudo su** : root 권한주기(제일 처음에 무조건하기) <br>
> -sudo는 root가 아닌 사용자가 root에 준하는 능력으로 sudo 다음에 나오는 명령을 실행하게 하는
명령어입니다.  su는 root 패스워드가 필요하지만 sudoer에서 사용을 허락한 사용자는 모두 패스워드와 관계없이 쓸 수 있습니다. sudo는 슈퍼유저, 관리자 권한을 가지지만 근본적으로는 해당 사용자가 내리는명령입니다. <br>
>
> -sudo su는 일시적으로 그 명령은 root가 내리는 명령입니다. 예를 들어 sudo로 작업하면서
디스크에 쓰기를 해야하면 소유자가 지금 사용자로 나옵니다만, sudo su로 작업하면 소유자가 root가 됩니다. <br> <br>
> 
> **sudo su 정지하고 싶을 땐 그냥 시스템 껐다 켜** <br>
>
> ★★★★★ <br>
>
> **init 0, shutdown -h now 등등 이런 거 절대 쓰지말기! 이거는 프로세스 전부 다 죽이는 거여서 큰일 남. <br>
> 그냥 무조건 exit만 쓰기..이건 콘솔 창 닫는 거..** <br>
>
> ★★★★★ <br> <br>
>
> **cut -f1 -d: /etc/passwd** : 모든 유저 목록 출력(username만) <br>
>
> **cut** : 지정된 파일 또는 파이프 데이터에서 줄의 일부를 잘라내고 결과를 표준 출력으로 인쇄할 수 있는 명령줄 유틸리티입니다. 구분 기호, 바이트 위치 및 문자로 줄의 일부를 자르는 데 사용할 수 있습니다. <br>
>
> **-f**  : 필드를 의미하며 딜리미터로 잘라진 행을 출력 <br>
> **-d** : 딜리미터를 지정 <br> <br>
> **apt-get**  <br>
> -시스템에서 사용 가능한 패키지에 대한 설치, 패키지 검색, 업데이트 및 기타 여러 작업을 수행합니다. 오래된 패키지를 사용하면 시스템에 보안 문제가 발생할 수 있으므로 패키지를 최신 상태로 유지하는 것이 매우 중요합니다. <br>
> 
> -시스템의 핵심 측면을 다루기 때문에 관리 (슈퍼 유저) 권한이 필요하므로 Ubuntu 또는 Ubuntu 기반 배포에서는 sudo, sudo su 사용. <br> <br>
> **apt-get update : 패키지 데이터베이스 업데이트** <br>
>
> -apt-get으로 작업을 시작하기 전에 로컬 데이터베이스 복사본이 최신 상태인지 확인해야 합니다. 이것이 없으면 시스템은 사용 가능한 최신 패키지가 있는지 알 수 없습니다. 업그레이드 또는 dist-upgrade 전에 항상 업데이트를 수행해야 합니다. <br> <br>
>
> ### **파일질라** <br>
> -**SFTP**는 사이트 관리자에서 연결해야함. 빠른 연결 아님. ubuntu 비밀번호 없음. <br> <br>
>
> **FTP** - 파일 전송 프로토콜 <br>
> **vsftpd** - ubuntu FTP 서버 <br>
