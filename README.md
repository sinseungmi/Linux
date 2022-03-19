> # Linux 
> ### 기본 개념 및 명령어 정리 
> <br>
> 
> ##### YUM(Yellow Dog update Modified) - 프로그램(패키지) 설치 관리 도구
> ```
> yum [옵션] [명령] [패키지명]    
> ```
> 1. YUM 패키지 설치/삭제 명령
> ```
> yum install 패키지명 // 패키지 설치
> yum remove 패키지명 // 패키지 삭제
> ```
> 2. 패키지 모듈을 update하는 명령. (단, 설치되어 있지 않으면 but not installed 메시지가 뜹니다.)
> ```
> sudo yum update lrzsz
> ```
> 3. apt remove, purge, autoremove 명령어 <br>
> #### apt-get remove
> - remove 명령어는 패키지를 삭제하지만 환경설정은 삭제하지 않습니다.
> ```
> sudo apt-get remove openjdk*
> sudo apt remove openjdk*
> ```
> 
> <br>
> 
> #### sudo su : root 권한주기
> - sudo는 root가 아닌 사용자가 root에 준하는 능력으로 sudo 다음에 나오는 명령을 실행하게 하는 명령어입니다.  <br>
> su는 root 패스워드가 필요하지만 sudoer에서 사용을 허락한 사용자는 모두 패스워드와 관계없이 쓸 수 있습니다. sudo는 슈퍼유저, 관리자 권한을 가지지만 근본적으로는 해당 사용자가 내리는명령입니다.  
> - sudo su는 일시적으로 그 명령은 root가 내리는 명령입니다. 예를 들어 sudo로 작업하면서 디스크에 쓰기를 해야하면 소유자가 지금 사용자로 나옵니다만, sudo su로 작업하면 소유자가 root가 됩니다.
