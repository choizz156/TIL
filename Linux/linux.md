# Linux (CentOS 8)
## 리눅스란?
- pc를 비롯한 다양한 컴퓨터 환경에서 사용 가능한 unix에서 비롯된 운영체제.
- 리눅스 토발즈를 중심으로 인터넷 상의 많은 개발자의 참여로 kernel이 개발됨.
- 전 세계의 수많은 사람들에 의해 테스트되고 개선, 발전됨.
- Free software
- GNU(Gneral Public License)에 따라 공개로 배포.
- 모든 프로그램의 소스 또한 공개
    - 원하는 사람은 소스를 변경하여 사용 가능.
    - GNU 정신에 따라 변경한 내용도 공개해야 함.
    - 사용자를 위한 다양한 공개 문서 및 지원 사이트 존재.

## 필수 개념
### 시작과 종료
- 종료하는 방법 : `shutdown -P now`, `halt -p` , `init 0`
- 시스템 재부팅 : `shutdown -r now`, `reboot` , `init 6`
- 로그아웃 : `logout`(사용자 로그아웃), `exit`(터미널 꺼짐)

### 가상 콘솔
- 쉽게 '가상의 모니터'라 생각하면 됨. CentOS는 총 5~6의 가상 콘솔 제공.
- 단축키 : ctrl + Alt + (F3 ~ F6) , ctrl + alt + F2는 x윈도우 모드
- 여러 명의 사용자가 동시 접속이 가능하다.
<br/>
shutdown -h +3 : 3분후에 꺼진다.
<br/>
 shutdown -k +5 : 5분후에 꺼진다고 다른 사용자에게 경고를 보내지만 실제로 꺼지지는 않는다.

### 런 레벨(Runlevel)
- 0 : power off - 종료 모드
- 1 : rescue - 시스템 복구 모드 
- 3 : mulit-user - 텍스트 모드의 다중 사용자 모드
- 5 : graphical - 그래픽 모드의 다중 사용자 모드
- 6 : reboot : - 재시작
- 런레벨 모드를 확인하려면 /lib/systemd/system/runlevel?.target을 확인.
- 런레벨 바꾸기 : ln -sf /lib/systemd/system/multi-user.target default.target
    - 디폴트를 멀티유저모드로 바꾼다.
### 자동완성(tab)과 history
- 화살표 상하키를 이용하여 이전에 입력한 명령어를 나타낼 수 있다.
- histroy : 지금까지 쳤던 명령어를 순서대로 보여줌.
- histroy -c : 지금까지 쳤던 명령어를 clear함.
- tab : 자동완성.
<<<<<<< Updated upstream
=======
### gedit,vi 사용
- 터미널 창에서 gedit을 입력하면 메모장 같은 것이 실행 됨.
- vi editor 
  - 터미널에서 vi를 입력하고 enter
  - i or a를 입력하면 insert모드로 들어가서 문서작업을 할 수 있다.
  - esc를 누르면 ex모드로 들어가서 :을 입력하고 저장(w), 종료(q), 취소(i) 등을 수행한다.
    - `vi 파일명` = 파일 열기
    - `w 파일명` = 그 파일명으로 저장.
    - `:wq` = 저장 후 나가기
    - `:q!` = 수정한 파일을 저장하지 않고 나가기
    - 저장하지 않고 터미널을 종료시켰을 때 : .file1.txt.swp(저장하지 않고 그냥 종료한 파일)을 찾아서 삭제하면
    다시 그 파일에서 수정할 수 있다.
  [vi 단축키](https://iamfreeman.tistory.com/entry/vi-vim-%ED%7E%B8%EC%A7%91%EA%B8%B0-%EB%AA%85%EB%A0%B9%EC%96%B4-%EC%A0%95%EB%A6%AC-%EB%8B%A8%EC%B6%95%ED%82%A4-%EB%AA%A8%EC%9D%8C-%EB%AA%A9%EB%A1%9D)
  
### 도움말, mount, cd/dvd 및 usb 메모리 연결
- man : 명령어를 입력하면 도움말이 출력된다.
     
      man command_name
      man -k(keyword) keyword_0f_command
- man의 결과 화면 보는 법
  - 숫자 : (1) command, (2) system call, (3) library function
  - [] : option
  - FILE : 이곳에다 파일이름을 쓰세요.
  - ... : 반복
----
- mount : 물리적인 장치를 특정한 위치(디렉터리)에 연결시켜주는 과정
  - cd/dvd mount : `mount dev/cdrom(대부분의 리눅스에서 cd를 연결시켜주는 링크)`
  - cd/dvd mount 해제 : 디렉토리를 사용자 디렉토리로 옮기고(cd 입력) `umount /dev/cdrom`을 입력하여 마운트 해제
  - usb mount : `mount /dev/sdb0(리눅스에서 usb장치 이름) /media/usb(직접만든 디렉토리)/`
  - usb mount 해제 : 디렉토리를 사용자 디렉토리로 옮기고 `umount /dev/sdb0(usb이름)`

## 리눅스 경로
- 파일명 및 경로명
  - 파일명
    - 대소문자 구분.
    - .으로 시작되는 파일명은 시스템 파일이 많기 때문에 사용하지 않는 것이 바람직하다.
  - 경로명
    - 절대 경로 : 루트 디렉토리(/)부터의 파일 위치.
      - /root/uesr/...
    - 상대 경로 : 현재 디렉토리로부터의 파일 위치.
      - `.` : 현재 디렉토리 .
      - `..` : 부모 디렉토리.
## 기본 명령어
### pwd(print working Directory)
- 현재 작업 디렉토리를 출력.
### cat(concatenate)
- 표준 입력(키보드) 또는 파일로 부터 입력 받아 이를 표준 출력(화면)에 표시한다.
- 리다이렉션(>)을 통해 파일 생성에 사용할 수 있다.

      cat [-n(출력에 줄 번호 표시)] FILE
> cat > file1 // 표준 입력을 file1에 저장
> <br/>
> abdf
> <br/>
> ^d

> cat -n file1
> <br/>
> 1 abdf
### control C
- 프로세스의 종료.
  - 작업 완료 이전에 프로세스를 강제로 종료시킴.
### control D
- 입력 완료.
### ls (list segment)
- 디렉토리 목록을 리스트 해줌.

  
    ls [-adlR] FILE or DIRECTORY
    ls 뒤에 파일명을 적으면 그 파일에 대한 정보만 보여주고 디렉토리를 적으면 디렉토리 내의 파일들을 보여줌.

     - a : 숨겨진 파일 나열.
     - d : 디렉토리 자체의 정보.
     - l : 허가, 소유, 최종변경일자를 포함하는 긴 목록 제공.
     - R : 디렉토리의 내용과 그 서브 디렉토리의 내용을 재귀적으로 제공(나열).
### cd(chage directory)

    cd DIRECTORY(절대경로,상대경로)
    디렉토리를 입력하지 않는 경우 사용자의 홈 디렉토리로 이동
### mkdir(make directory)

    mkdir DIRECTORY
- 절대 경로를 사용하지 않을 경우 현재 디렉토리에 하위 디렉토리가 만들어짐.

### head/tail
- head : 파일의 처음 n줄을 출력

      head [-n(n 번째 라인까지 출력,디폴트는 10)] FILE
- tail : 파일의 마지막 n 줄부터 출력

      tail [-n(마지막 줄에서 부터 n번째 라인의 줄부터 출력] FILE

### mv(move)
- 파일의 이름 변경 및 이동

      mv [-i(새로운 파일 이름이 이미 존재하는 경우를 위한 확인 프로프트 생성)] OLD_FILE NEW_FILE // 이전 파일을 새로운 파일로 이름변경
      mv [-i] FILE DIRECTORY // 파일을 디렉토리로 이동
      mv [-i] OLD_DIR NEW_DIR // 이전 디렉토리를 새로운 디렉토리로 이름 변경
- 경로 적으면 경로 이동을 하면서 이름도 변경할 수 있음.

### cp(copy)
- 파일 복사

        cp [-i(이미 존재하는 경우를 위한 확인)] OLD_FILE NEW_FILE
        cp [-r] OLD_DIRECTORY NEW_DIRECTORY
        -r : 이전 디렉토리에 있는 모든 파일과 서브디렉토리를 재귀적으로 새로운디렉토리에 복사.
### rm(remove)
- 파일 삭제

      rm [-fir] FILE
      -f : 어떤 에러 메시지나 지시 사항도 나타내지 않는다
      -r : 서브 디렉토리를 포함한 모든 내용을 삭제한다.
      -i : 파일 삭제 전 사용자에게 확인 요구

### rmdir(remove directory)
- 디렉토리 제거
          
        rmdir DIRECTORY
        디렉토리내가 비어있어야 디렉토리가 제거된다.
        rm -r DIRECTORY
        디렉토리 안의 모든 내용을 함께 삭제한다.

-----------
## 사용자와 그룹
- 리눅스는 다중 사용자 시스템(Multi-User System)임.
- 기본적으로 root라는 이름을 가진 수퍼유저(superuser)가 있으며, 모든 작업을 할 수 있는 권한이 있다.
- 모든 사용자는 하나 이상의 그룹에 소속돼 있음.
- 사용자는 /etc/passwd 파일에 저장돼 있음
> 사용자이름:암호:사용자id:사용자가 소속된 그룹:전체 이름:홈 디렉터리:기본셀 
- 사용자 비밀번호는 /etc/shadow에 있음
- 그룹은 /etc/group
- 처음에 group을 만들면 기본값으로 사용자명으로 그룹이 만들어 진다.
> 그룹명:비밀번호:그룹id:그룹에 속한 사용자명

### 사용자와 그룹 관련 명령어
- `useradd` : 새로운 사용자를 추가 /# useradd user1
- `passwd` : 사용자의 비밀번호를 지정하거나 변경 /# passwd uer1
- `uermod` : 사용자의 속성을 변경 /#usermod -g root user1
- `userdel` : 사용자를 삭제 /# userdel user1
- `chage` : 사용자의 암호를 주기적으로 변경하도록 설정 /# chage -m 2 user1
- `groups` : 현재 사용자가 속한 그룹을 보여줌 /# groups
- `groupadd` : 새로운 그룹 생성 /# groupadd newgroup
- `groupmod` : 그룹의 속성을 변경 /# gruopmod -n new group mygroup
  - 사용자 생성시 옵션
    - -u : id 지정
    - -g : 그룹 지정
    - -d : 홈 디렉터리 지정
    - -s : 셀 지정
-------------
## 파일과 디렉터리의 소유와 허가권
### 파일의 리스트와 파일 속성
> -|rw-r--r--|1|root|root|0|11월 11:33|test.txt
  
`파일 유형`|`파일 허가권`|`링크수`|`파일 소유자 이름`|`파일 소유그룹 이름`|`파일크기`|`마지막 변경 날짜/시간`|`파일이름`

- 파일 유형
  - 디렉터리는 `d`, 일반적인 파일은 `-`가 표시.
- 파일 허가권
  - rwx/r--/r-- 3개씩 끊어서 읽음(r = read, w = write, x = execute)
  - user/group/other 의 파일 접근 권한
  - 숫자로 표시 가능
    - User : `r` `w` `-` = `4` `2` `0` = `6`
    - group : `r` `-` `-` = `4` `0` `0` = `4`
    - other : `r` `-` `-` = `4` `0` `0` = `4`
- chmod 명령
  - 파일 허가권 변경 명령어 /# chmod 777(rwxrwxrwx) test.txt
- 파일 소유권
  - 파일을 소유한 사용자와 그룹
- chown/chgrp
  - 파일의 소유권을 바꾸는 명령어/# chown centos text.txt/#chgrp centos test.txt

### 링크([블로그 정보](https://www.leafcats.com/141))
- 파일의 링크에는 하드링크(hard link)와 심볼릭 링크(symbolic link or soft link) 2가지가 있음.
  - 하드 링크를 생성하면 '하드링크파일'만 하나 생성되며 원본파일과 같은 inode1을 사용 /# ln 링크대상파일이름 링크파일이름
  - 심볼릭 링크를 생성하면 새로운 inode2를 만들고, 데이터는 원본 파일을 연결하는 효과/# ln -s 링크대상파일이름 링크파일이름
-------------
## 패키지 설치
- DNF(Dandified dnf) 개념
  - rpm 명령의 패키지 의존성 문제를 완전하게 해결함.
  - 인터넷을 통하여 필요한 파일을 저장소(Repository)에서 자동으로 모두 다운로드해서 설치하는 방식.
  - CentOS 7은 YUM, CentOS 8은 YUM이 개선된 DNF명령을 사용.
  - 저장소 : `/etc/yum.repos.d/`

- dnf 기본적인 사용법
  - 기본 설치 : `dnf install 패키지이름`
    - -y옵션은 사용자의 확인을 모두 yes로 간주하고 설치를 진행
- rpm 파일 설치 : `dnf install rpm파일이름.rpm`
- 삭제 : `dnf remove 패키지이름`
- 정보 확인 : `dnf info 패키지이름`
- dnf 추가 사용법
  - 패키지 그룹 설치 : `dnf groupinstall "패키지그룹이름"`
  - 패키지 리스트 확인 : `dnf list 패키지이름`
  - GPG키 검사 생략
    - `dnf install --nogpgcheck rpm파일이름.rpm`
    - centos8에서 인증되지 않은 패키지를 강제로 설치할 때 사용
   - 기존 저장소 목록 지우기 : `dnf clean all`
---------------
## 파일 압축과 묶기
- 압축과 묶기가 나누어져 있다.
### 파일 압축
  - xz, bz2, gz, zip, Z 등
  - xz, bz2 압축률이 더 좋음
- 관련 명령어
  - xz : /# `xz 파일명`, `xz -d 파일명.xz`(삭제)
  - bzip2 : /# `bzip2 파일명`, `bzip2 -d 파일명.bz2`
  - gzip : /# `gzip 파일명`, `gzip -d 파일명.gz`
  - 압축이 되면 보통 압축한 파일이 없어진다. (zip제외, zip은 윈도우 호환성)
### 파일 묶기
  - 명령어도 tar이고 묶인 파일 확장명도 tar이다.
- 명령어
  - tar : tar로 묶음 파일을 만들어 주거나 묶음 파일을 압축한다.
    - 동작 : c(묶기), x(풀기), t(경로 확인)
    - 옵션 : f(파일), v(과정 보이기),J(tar+xz), z(tar+gzip), j(tar+bzip2)
  - 묶기 : /# tar cvf my.tar /etc/sysconfig 
  - 묶기 + 압축 : /# tar cvfJ my.tar.xz 묶고압축할파일이름(폴더이름)
  - 풀기 : /# tar xvf my.tar
  - 압축해제 + 묶기 풀기 : /# tar xvfJ mytar.xz 폴더이름
### 파일 위치 검색
- 기본 파일 찾기 : find [경로] [옵션] [조건] [action]
  - 옵션 : -name, -user(소유자), -newer(전,후), -perm(허가권), -size(크기)
  - action : -print(디폴트), _exec(외부명령실행)
    - /# find /home -name "*.swp" `-exec(시작) rm(외부명령) {(여기에 앞에 찾은 파일이 들어감}) \:(끝)`
  - which [실행파일이름] : PATH에 설정된 디렉터리만 검색
  - whereis [실행파일이름] : 실행 파일, 소스, man페이지 파일까지 검색
  - loacte [파일이름] : 파일 목록 데이터베이스에서 검색

--------------
## 시스템 설정
- 네트워크 설정 : `nmtui`
- 방화벽 설정 : `firewall-config`
- 서비스 설정 : `ntsysv`
### cron과 at
- cron
  - 주기적으로 반복되는 일을  자동적으로 실행될 수 있도록 설정
  - 관련된 데몬(서비스)은 crond, 관련 파일은 /etc/crontab
    - /# 01**** root run-parts /etc/cron.hourly : 매 시간 1분에 /etc/cron.hourly. 디렉터리 안에 있는 명려을 자동으로 실행
    - /# 01**** root run-parts /etc/cron.monthly
    - /# 01**** root run-parts /etc/cron.daily
    - /# 01**** root run-parts /etc/cron.weekly
    
- at
  - cron은 주기적으로 반복되는 작업을 예약하는 것이지만 at은 일회성 작업을 예약
    - 예약 : /# at <시간>
      - /# at # 3:00 am tomorrow -> 내일 새벽 3시
      - /# at now + 1hours -> 한시간 후 
    - at> 프롬프트에 예약 명령어 입력 후 엔터키
    - 완료되면 ctrl d 
  - 확인 : at -l
  - 취소 : atrm <작업번호>