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

## 필수 개념과 명령어
### 시작과 종료
- 종료하는 방법 : `shutdown -P now`, `halt -p` , `init 0`
- 시스템 재부팅 : `shutdown -r now`, `reboot` , `init 6`
- 로그아웃 : `logout`(사용자 로그아웃), `exit`(터미널 꺼짐)

### 가상 콘솔
- 쉽게 '가상의 모니터'라 생각하면 됨. CentOS는 총 5~6의 가상 콘솔 제공.
- 단축키 : ctrl + Alt + (F3 ~ F6) , ctrl + alt + F2는 x윈도우 모드
- 여러 명의 사용자가 동시 접속이 가능하다.
- tip) shutdown -h +3 : 3분후에 꺼진다.
<br />
  shutdown -k +5 : 5분후에 꺼진다고 다른 사용자에게 경고를 보내지만 실제로 꺼지지는 않는다
d
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
- man 명령어를 입력하면 도움말이 출력된다.
- mount : 물리적인 장치를 특정한 위치(디렉터리)에 연결시켜주는 과정
  - cd/dvd mount : `mount dev/cdrom(대부분의 리눅스에서 cd를 연결시켜주는 링크)`
  - cd/dvd mount 해제 : 디렉토리를 사용자 디렉토리로 옮기고(cd 입력) `umount /dev/cdrom`을 입력하여 마운트 해제
  - usb mount : `mount /dev/sdb0(리눅스에서 usb장치 이름) /media/usb(직접만든 디렉토리)/`
  - usb mount 해제 : 디렉토리를 사용자 디렉토리로 옮기고 `umount /dev/sdb0(usb이름)`
>>>>>>> Stashed changes
