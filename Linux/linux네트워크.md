## 리눅스 네트워크

### 네트워크 관련 명령어
#### nmtui
- 네트워크와 관련된 대부분의 작업을 이 명령어에서 수행
  - 자동 ip 주소 또는 고정ip주소 사용 결정
  - ip주소, 서브넷 마스트, 게이트웨이 정보 입력
  - DNS 정보 입력
  - 네트우크 카드 드라이버 설정
  - 네트워크 장치의 설정
- 텍스트 기반으로 작동함

#### systemctl < strat/stop/restart/status > Network Manager
- 네트워크의 설정을 변경한 후에, 변경된 내용을 시스템이 적용시키는 명령어

#### ifup <장치이름> 및 ifdown <장치이름>
- 네트워크 장치를 on 또는 off 시키는 명령어
#### ifconfig <장치이름>
- 장치의 Ip주소 설정 정보를 출력

#### nslookup
- dns 서버의 작동을 테스트하는 명령어
#### ping <ip주소 또는 url>
- 해당 컴퓨터가 네트워크상에서 응답하는지를 테스트하는 간편한 명령어

### 네트워크 설정 주요 파일
#### /etc/sysconfig/nework
- 네트워크의 기본적인 정보가 설정되어 있는 파일
#### /etc/sysconfig/newwork-scripts/ifcfg-ens160
- ens32 장치에 설정된 네트워크 정보가 모두 들어 있는 파일
#### /etc/resolv.conf
- DNS 서버의 정보 및 호스트 이름이 들어 있는 파일
- 컴퓨터를 재시작하거나 네트워크 장치를 리부팅할 때마다 ifcfg-ens160에서 dns정보를 복사 해옴
#### /etc/hosts
- 현 컴퓨터의 호스트 이름 및 FQDN이 들어 있는 파일

------------------
### 파이프, 필터 , 리디렉션
#### 파이프(pipe)
- 두개의 프로그램을 연결해주는 연결통로의 의미
- `|`을 사용함
- /# ls -l /etc | more
#### 필터(filter)
- 필요한 것만 걸러 주는 명령어
- grep, tail, sort, grep, wak, sed 등
- 주로 파이프와 같이 사용
- /# ps -ef | grep bash
#### 리디렉션 (redirection)
- 표준 입출력의 방향을 바꿔 줌
- /# ls -l > list.txt // list.txt에 출력내용이 저장됨.

--------------
### 프로세스, 데몬
- 정의
  - 하드디스크에 저장된 실행코드(프로그램)가. 메모리에 로딩되어 활성화 된것.
- Foreground Process
  - 실행하면 화면에 나타나서 사용자와 상호작용을 하는 프로세스
  - 대부분의 응용프로그램
- Background Process
  - 실행은 됐지만. 화면에는 나타나지 않고 실행되는 프로세스
  - 백신 프로그램 ,서버 데몬 등
- 프로세스 번호
  - 각각의 프로세스에 할당된 고유번호
- 작업 번호
  - 현재 실행되고 있는 백그라운드 프로세스의 순차번호
- 부모 프로세스와 자식 프로세스
  - 모든 프로세스는 부모 프로세스를 가지고 있음
  - 부모 프로세스를 kill하면, 자식 프로세스도 자동으로 kill 됨
- 프로세스 관련 명령어
  - `ps` : 현재 프로세스의 상태를 확인하는 명령어
    - ps -ef | grep <프로세스 이름>을 주로 사용
  -`kill` : 프로세스를 강제로 종료하는 명령어
    - kill -9 <프로세스 번호> : 강제 종료
  - `pstree`
    - 부모 프로세스와 자식 프로세스의 관계를 트리 형태로 보여줌.
  - `&` : 실행을 하돼 백그라운드로 실행되서 프로그램을 동시에 사용할 수 있다.
    - /# gedit &
  
-------------
### 서비스와 소켓
#### 서비스
- 시스템과 독자적으로 구동되어 제공하는 프로세스.
  - 웹 서버(httpd), DB서버(mysqld), FTP서버(vsftpd) 등이 있다.
- 실행 및 종료는 대개 `systemctl start/stop/restart 서비스이름`으로 사용된다.
- 서비스의 실행 스크림트 파일은 `/usr/lib/systemd/system/디렉터리`에 `서비스이름.service`라는 이름으로 확인 가능하다.
#### 소켓
- 서비스는 항상 가동되지만, 소켓은 외부에서 특정 서비스를 요청할 경우에 systemd가 구동시킨다. 그리고 요청이 끝나면 소켓도 종료된다.
- 소켓으로 설정된 서비스를 요청할 때는 처음에 연결되는 시간이 서비스와 비교했을 때 약간 더 걸릴 수 있다.
- systemd가 서비스를 새로 구동하는 데 시간이 소요되기 때문이다. ex) 텔넷 서버
- 소켓과 관련된 스크립트 파일은 `/usr/lib/systemd/system/디렉터리`에 `소켓이름.soket`이라는 이름으로 존재한다.