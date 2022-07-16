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