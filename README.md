Linux Essential 과정 정리 

제 01장. Linux Command
제 02장. 디렉토리 추가 관리

hostnamectl set-hostname (이름)

ip설정창 불러오기
nm-connection-editor

ip 설정창의 이더넷 목록에서 디바이스를 아래 맥주소로 선택해야한다.
왜냐하면 이것은 기존 main을 스냅샷 한것이기 때문에 다른 맥주소를 사용해야 오류가 없다.

적용 후, nmcli connection up ens 33으로 최종 적용한다.

-명령어 메뉴얼로 탐색
man -k calendar = 캘린더의 키워드 메뉴얼
man -k는 다음 명령어가 뭔지 기억이 안날때 쓰면 좋음

man -f passwd = 패스워드와 관련된 매뉴얼 탐색
번호는 메뉴얼 세션 번호. 각 세션마다 정보가 다름. 책번호 라고 생각하면 편하다

# man ls /* 명령어나 파일의 이름으로 검색하는 경우 */ 
# man -k calendar /* keyword로 검색하는 경우 */
# man -f passwd (# whatis passwd) 
# man 1 passwd /* section번호로 검색하는 경우, man -s 1 passwd *

■ Linux Manual Section --------------------------------------------------------- 
Section 1 : 사용자 명령(실행가능한 명령 및 쉘 프로그램) 
Section 2 : 시스템 호출(사용자 공간에서 호출된 커널 루틴) 
Section 3 : 라이브러리 기능(프로그램 라이브러리에서 제공)
Section 4 : 특수 파일(예: 장치 파일) 
Section 5 : 파일 형식(많은 구성 파일 및 구조의 경우)
Section 6 : 게임(오락 프로그램용 섹션) 
Section 7 : 범례, 표준 및 기타(프로토콜, 파일시스템) 
Section 8 : 시스템 관리 및 권한 명령(유지 보수 작업) 
Section 9 : 리눅스 커널 API(내부 커널 호출)
 ---------------------------------------------------------

ctrl+shift+t = 탭형태로 새로 띄우기
ctrl+shift+n = 윈도우 형태로 새창 띄우기

암호변경: passwd 변경할 사용자 이름
원격 접속: ssh 사용자이름@localhost

시스템 기본 정보 확인
uname
date
cal

cat 명령어 = cat etc/ ~~ 식으로 경로를 검색하여 해당경로의 문서를 쉘로 확인

uname 
Linux server1.example.com 4.18.0-240.el8.x86_64 #1 SMP Fri Sep 25 19:48:47 UTC 2020 x86_64 x86_64 x86_64 GNU/Linux

리눅스 레드헷에 대한 정보들을 모아두는 사이트
Red Hat Enterprise Linux - Red Hat Customer Portal
ㄴ centos의 정보를 확인할 때, 사용한다.

새창 띄우기 crtl+shift+n

사용자 디렉토리 이동 

이전 디렉토리 이동=  cd -
옆에 있는 디렉토리로 이동= cd ../옆디렉토리
상위 디렉토리 이동= cd ..
디렉토리 이동 cd /이동을 원하는 하위 디렉토리
cd = 홈디렉토리 이동

디렉토리 관리 명령어
ㄴ 리눅스에서 관리라는 말이 붙는다는것은 변경 삭제 추가가 가능하는 뜻을 말한다


ls 명령어 - 목록을 보여주는 명령어
ls -l = 해당 디렉토리 안에 있는 폴더들의 권한과 정보를 표시해준다
ld -ld =현재 디렉토리의 권한과 최종 사용된 시간을 표현해준다.
ㄴ권한에 대한 설명
  rwx 읽고, 쓰고 ,실행하는 권한을 뜻함. 명령어로 표현될 때는 rwx r__ _w_ 식으로     지원하지 않는것도 _로 표현해준다.
ㄴ 여기서 ls 의 -l을 붙여주면 더 많은 정보를 표현해준다.
ld - lR = 현재 디렉토리 안에 모든 파일의 권한과 정보를 표시 함
ls -al = .으로 시작하는 숨겨진 디렉토리도 표현하여 표기해준다.
ls -i  = 각 파일의 인덱스 넘버를 출력해주는 역할을 수행한다.
ls - li = 디렉토리의 식별번호를 표시해준다.
ls -lh = 디렉토리의 용량 단위를 환산 할 때 , 자동으로 단위를 편하게 보기 위해 보정해줌


[실무예]  실무에서 많이 사용하는 cmd
cd /Log_dir                    ls- -altr

[참고]  alias   (선언) alias ls = ‘ls -l | grep “^-”’   (확인) alias   (해제) # unalias ls 



파일 또는 디렉토리만 출력
일반적으로 리눅스에서 명령어를 만들어서 사용하기도 한다.



mkdir 명령어
mkdir -p dir3/dir2/dir1 
ㄴ 아래 -p를 추가해준다면 상위에서 하위 디렉토리를 한번에 생성

rmdir 명령어
폴더가 비워져 있는 경우에는 지울 수 있는 명령어 이다. 잘 사용 x
rm -rf dir1 = -rf는 지울때 파일마다 한번씩 재확인을 받는데 그것을 방지하고 디렉토리를 삭제해주는 명령어이다.

파일/디렉토리 삭제를 주의 해야함!!!!



touch 명령어
touch 명령어는 폴더 내에 bin 파일을 생성
touch file1 /* file1 이라는 파일을 하나 생성한다.
touch -t 08301300 file1 = file1의 시간정보를 변경한다.

cp 명령어 =copy 명령어
cp file1 file2 = file1 파일내용을 file2로 생성
cp file1 dir1 = file1 파일내용을 dir1 디렉토리에 file1으로 생성
cp -r dir1 dir2 = -r을 추가하여 dir1을 디렉토리 안에 있는 파일까지 똑같이 복사하여 dir2라는 폴더명으로 복사하여 생성
ㄴ 옵션: -r, -i, -f
echo 'linux200' > file1

cp file1 dir1 = file1을 dir1에 file1이라는 이름으로 똑같이 표현 
linux200이라는 내용을 가진 file1을 생성

실무예 - 설정파일을 백업하는 경우
cp -p httpd.conf httpd.conf.orig
`	cp -a

    실무예 - 로그파일 비우기 
   # cp /dev/null file.log
   	# cat /dev/null > file.log
   	# > file.log 

와일드카드 문자
ls file* = file~라는 파일들을 모두 검색


mv 명령어
mv file1 file3  = 현 디렉토리 내에 file1을 file3로 이름을 변경한다.
mv fire* dir1 = file~ 라고 시작하는것들을 모두 dir1 디렉토리에 넣는다.
mv dir 1 dir2 =dir1을 dir2라고 하고 복사해서 넣는다.
옵션: -i, -f


rm 명령어
rm -rf = 묻지않고 바로 삭제하는 방법, 주로 이 방법을 사용한다.
실무예: 지운 파일 복구하기

rm f

cat
	cat -n file1
	cat file1 file2 > file3 = 파일 3에 1, 2의 내용을 모두 집어넣음
	cat /etc/services | more = 긴 출력문을 페이지 단위로 보게 해주는 코드




more cmd
	cmd | more
	ps -ef | more
cat /etc/serveices | more
netstat -an | more
systemctl list-unit-files

head cmd
	 head /etc/passwd= 길게나옴
	head -5 /etc/passwd = 5줄 까지만 출력
	
alias pps='ps -ef | head -1 ; ps -ef | grep $1'

tail cmd
	tail -f /val/log/massages
	top
	tail -f /val/log/massages | egrep -i '(warn|fail|error|crit|alert|emerg)'


ssh 사용자 이름 = 원격접속 명령어
telnet 서비스 기동하기
yun install telnet telnet-server
systemctl enable —now telnet.socket
ㄴ 텔넷서버 시스템을 설치하고 바로 기동
–now 을 붙여주면 부팅이랑 스타트 둘다 해줌

systemctl start telnet.socket = 시작하고
(--now를 써주면 x) systemctl enable telnet.socket= 부팅시에도 기동

wc cmd = 워드카운트 wc -c 문자수, -l = 라인수, -w = 단어수
 cat /etc/passwd | wc -l

추가= rpm = 레드헷에서만 쓰는 소프트웨어 관리자 (설치된거 보여줌)
	ps -ef 프로세스 정보를 표시
추가= df 명령어= 디스크의 남은공간 위주로 정보를 출력해준다
참고 = 데이터 수집( data gathering)
	ps -ef | tail -n +2 | wc -l
	cat /etc/passwd | wd -l
	rpm -pq | wc -l
	cat /val/log/messges | grep ‘jan 19’ | grep ‘started Telnet server’ | wc-l   = 서버가 몇명씩 사용하고 있는지 파악하는 용도
	    라인카운트로 사용자별 한줄인걸로 파악

su cmd = 사용자 전환 == su 사용자 이름 
su 와 su - 의 차이점 : 이전 사용자가 사용하고 있던 환경변수가 그대로 오는가 
ㄴ 스위칭을 할 때는, 기본적으로 su - 사용자이름 식으로 사용하는것이 좋다.

sudo cmd(/etc/sudoers, /etc/sudoers.d/*)
sudo  su - 사용자 이름
	sudo -l = 목록 확인
	sudo -i  = 관리자 계정으로 임시접속
	sudo 명령어들 = 권한을 임시적으로 가져와 권한필요 명령어 수행

su와 sudo의 차이점: su는 완전히 계정을 변환하는것이고, sudo는 임시로 가져오는것으로 보안 상, sudo를 사용하는것이 보안상 좋다.

추가 = usermod =사용자의 대한 수정

id , groups 명령어는 기억만 해두자
ㄴ 다른사용자로 전환하게 되면 한번씩 해주자. 
용어 = pts/0 –  가상서버/ 0번째

last cmd ** = 보안상으로 중요한 cmd 접속기록!!
	last -i
	last -f /val/log/wtmp.20230128
	lastlog(/val/log/lastlog) = 사용자의 마지막 로그인 시간을 알려줌
	내 서버에 존재하는 계정중에서 1년동안 접속하지 않은 계정을 찾고 
	싶다! 식으로 사용자를 구별하여 처리할때 검색

lastb cmd = 사용자들의 마지막 로그인 했는 기록 목록을 보여준다.
	lastb (val/log/btmp)= 로그인에 실패한 기록들을 저장

who cmd ** = 사용자가 사용한 명령어를 보여줌
	who = 현재 서버에 접속중인 모든 사용자
	ㄴ (/val/run/utmp) = 참조 파일경로




w cmd = 로그인 된 사용자들이 사용하는 명령어를 확인
	while true ***** (반복 실행문)
	do		cmd		sleep 2		donecle
	참고- watch cmd

파일 종류

	
링크파일
	하드링크파일 = ln에서 특별한 링크 없이 실행
 dd if=/dev/zero of=/home/file1 bs=1M count=500 –500메가생성
ln으로 링크를 걸어 새로운 파일234를 생성
다른걸 지워도 용량을 그대로 차지한다.
즉, 링크를 걸어둔 파일1을 지워도 링크된 234중 하나라도 살아있다면 용량을 그대로 차지한다.


심볼릭 링크 파일 = 심볼링크가 더 많이 사용
	용어+ 마이그레이션=파일 이동

-장치 — 장치 드라이버 —-/—운영체제
운영체제에서 장치 드라이버를 통해 장치에 접근이 가능하다
장치를 제어하기 위해 운영체제 내에 /dev/장치이름 식으로 장치에 대한 정보와 이름을 저장하여 이 파일을 통해 장치를 제어,접근한다.
즉 운영체제에서 장치로 바로 접근이 가능한것이 아니라 관문에 역할을 수행하는 장치 드라이버를 설치하여 접근이 가능하다.

** 안에 파일을 볼 수 있는 명령어 : ll 링크 이름이나 그냥 ll 사용!!!
	tty: 가상터미털과 번호를 볼 수 있다.
	ㄴ ll /dev/sda 

***----ls -l |grep '^b' ==b로 시작하는것만 검색하기!!!








===============================
—-----------7장 파일의 속성관리—---------
===============================

—-----------   rw-r--r-- 1 root root 1945  6월 11 14:13 file1   —--------------
File Type       	: 변경 불가능
Permission Mode: chmod 
Link Count     	: ln 
Owner              	: chown 
Group              	: chgrp 
File Size       	:
Mtime              	: touch -t
File Name       	: mv  

chown cmd =파일의 권한,소유권을 바꾸기 위해 사용한다.
chown user01 file1
# chown user01.other file1     (# chown user01:other file1)
# chown .other file1    	   (# chown :other file1)
# chown -R user01 dir1 = -R은 회귀적으로 하는 뜻! 많이 사용된다.
# chown -R user01:other dir1
ls -l file1= 파일1의 권한정보와 생성 날 확인
	# chown -R fedora:fedora /home/fedora

chgrp cmd= 파일의 사용자 그룹을 바꾼다. (c
hown으로도 변경가능)

-chmod cmd = 파일의 접근 권한변경(퍼미션 변경)
ㄴ 하나의 문자가 명령어들을 대표해서 표현하는것
        
심볼릭모드 == chmod u(사용자의 약자들 확인) + r (권한)file1(파일이름)
옥탈모드(8진수모드) ***** (주로 옥탈모드 사용!)
chmod 744(u_g_o) file1 - 유저 그룹 기타 (4_2_1)
ㄴ rwx (- - -)                 (ll로 권한확인)



***** 디렉토리의 rwx에 대해
r= (ls -l) 목록을 볼 수 있는 권한
	w= (디렉토리 안에 폴더,파일에 대한 수정 권한 , 파일이 속한 상단폴더에 w권한이 있으면 o
	x= (cd) =디렉토리에 들어갈 수 있는가?
	– 디렉토리는 r이나 w 권한을 위해서 반드시 x권한이 필요하다
* 명령어 외우기! : touch = 파일 생성 mkdir = 폴더 생성 chmod 권한 부여


umask cmd =파일 디렉토리 생성시, 기본 적용 권한인 디폴트 퍼미션을 조정하는 명령어
	ㄴ 이걸 설정해주면 처음 디렉토리가 생성되면 설정한대로 생성된다
 	umask 022 == 기본 권한 = 755 umask가 클수록 보안이 좋아짐
	** umask는 실무에서 왠만하면 바꾸지마라
      경로 = /etc/bashrc(관리자)    $HOME/bashrc(사용자)

mac= 잘 알려진 서비스를 위해 할당하는 포트 번호
	ex)ssh(22).telnet(23),smtp(25) 등
ip=호스트를 구분하는 번호		포트번호=서비스를 구분하는 번호
집을 ip라고 한다면 포트번호를 가족 구성원으로 보고 1호집의 아빠,누나 이런식으로 구분가능


===============================
—-----------8장 VI 편집기—---------
===============================
생성, 수정 = vi 파일 이름
i,o,O,h = 입력모드		esc= esc모드 사용 
삭제= x,dd 			저장/종료: 쉬프트+: -코드입력모드- wq! 입력시 종료
ㄴ 설정에 따라서 방향키나 딜리트키 가 먹지 않을 수 있기 때문에 알자!

: / 검색할 단어 ,      : 검색할 줄 숫자
줄넘버 표시: set number
단어 단위 이동: w,b	첫라인,끝라인 이동: 0^, $ (esc모드)	
페이지단위 이동: 컨+f, 컨+B		(페이지)G, 그냥 G는 막페이지(esc모드)
vi 편집기 모드 종류: 명령모드,입력모드,최하위모드

vi 편집기의 삭제 기능
페이지를 검색하고 지우면 검색한줄의 워드만 지워진다
dd 누르면 그 줄 삭제, 3dd 누르면 3줄 지워짐 
라스트라인 모드에서  11,15d 로 입력하면 11~15줄 없어짐
esc모드에서 d1G누르면 현재커서부터 입력줄까지 삭제
vi 편집기의 입력 기능
i: 현재커서에서 입력		- I:현재커서 있는 행 처음에 입력
a:현재커서 이후에 입력		-A: 현재커서가 있는행 마지막부터 시작
o:현재커서 아래행부터		-O: 현재커서의 위 행 부터 시작

그 밖의 유용한 기능들
뒤로가기 : u(escmod)		-앞으로가기: ctrl+r 
현재커서 줄 복사: yy		-붙여넣기:p (P는 현재커서 위로 붙)
yy: 커서로부터 3줄 복사		-1,3 co 5: 1~3줄 복사 18줄 아래로 붙
1,3 m 5: 1~3줄을 5줄 아래로 이동
5,10s/^(첫줄부터라는뜻)/#/ : 5~10줄 주석처리
5,10s/^/    /:앞에 4줄 띄어쓰기 추가       –ZZ: 저장하고 나가기(escmod)

Vi 편집기 환경설정
$HOME/ .vimrc(run commend)
set nu
set ai
set ts=4
번호보이기:set number

[참고] vim 확장자: 예제화일


===============================
—---------9장 사용자통신명령어—-------
===============================

mail cmd: 메일관련 cmd
mail 받는사람
ctrl+d 누르면 보냄
mail -u 유저이름 = 관리자 계정에서 다른 사용자의 메일 탐색가능
외부메일보내기
ㄴ mail -s “제목” 이메일주소 < /etc/hosts

wall < /etc/MESS/work.txt: txt 파일 안에 글을 접속 사용자에게 공지함

[참고] touch /etc/nologin(새로운 사용자 접속 금지함)
	wall < /etc/MESS/work.txt
	….
	fuser -cu /home
	fuser -ck /home
	-작업들 진행-
	rm -f /etc/nologin(사용자들의 로그인을 다시 허용

talk

wall: 서버 내에 로그인 되어 있는 사용자에게 동시에 메시지를 전송
wall “메시지”


===============================
—---------10장 유용한 명령어—-------
===============================

cmp/diff cmd: 파일을 비교할 때 사용한다. 두개파일이 다르면 다른 부분의 
	              줄과 틀린 부분의 용량을 알려준다.

cmp 비교파일1 비교파일2 : 틀린 줄이랑 용량만 출력
diff 비교파일1 비교파일2 : 틀린 부분까지 출력해줌
diff -c 비교파일1 비교파일2 : 파일1,2 전체를 보여줘 비교
diff -r 디렉1 디렉2= 디렉토리 내에 다른이름의 파일을 알려줌
diff httpd.conf httpd.conf.OLD 를 입력한다면 수정된 점 표시

[실무 예] 설정파일 비교
	diff httpd.conf httpd.conf.OLD
[실무 예] 디렉토리 마이그레이션 종료 후 비교
	diff -r /wal1 /wal2


sort cmd : 정렬 명령어
	-sort 파일이름 -r 내림차순
	-sort 파일이름 -k 3(3번째 필드부터) -n(숫자정렬): 필드 지정 정렬
	ㄴ 3번째 필드부터 (uid 구분으로)
	-sort를 활용한 정렬방식
	ㄴ ps -ef | head | sort -k 3(숫자정령), -원하는 영문
	   ㄴ sort -k 3 = 3번째 필드를 중심으로 파일을 정렬( -n=숫자, -nr 반대)
	[실무예] 용량 확인하기!
	ㄴ du -sk * | sort -nr = 용량이 큰 순으로 보기


file cmd
[cmd] file /etc/passwd 파일의 확장자,종류를 알려줌
ㄴ# file /etc/hosts /etc  = 여러개 파일 지정
[업무에서의 경우]
ㄴ 확장자가 변경되는 예에 대해서 다른종류의 운영체제 간의 파일 전송이 많은경우, 파일의 확장자가 변하는 경우가 종종 있다.
=리눅스.txt ->윈도우.txt = 이렇게 반복하다보면 확장자가 사라지기도함

[깨알코드[ = 이름 변경: mv 변경할 파일 변경후 이름
-파일 압축하기: zip file.zip 압축할 파일들 이름
-파일 압축해제: unzip 압축파일.zip 

-l	(-l : list files) 패턴이 있는 파일이름만을 출력한다.
-n	(-n : number line) 패턴을 포함하는 줄을 출력할 때 줄번호와 함께 출력한다.
-v	(-v : inVerse, except) 패턴을 포함하는 줄을 제외하고 출력한다.
-c	(-c : count) 패턴을 찾은 줄의 수를 출력한다.
-i	(-i : ignore case, 대문자/소문자) 패턴을 찾을 때 대소문자를 구분하지 않는다.



grep cmd
	grep option ‘pattern’ file1
options: -i,-l,-v,-r,-n,--color, -A
pattern: * . ^root  root$ [abc]   [a-c]    [^a](a가 아니면 띄움)
	
cmd | grep root
	ㄴ cat /etc/passwd

[실습예] cat /var/log/messages | egrep -i '(warn|err|fail|crit|alert|emerg)' 
	ㄴ 메시지 로그에서 egrep으로 여러개의 키워드를 같이 검색!








=alias 등록 코드 =
#!/bin/bash

if [ $# -ne 1 ] ; then
    echo "Usage: $0 <logfile>"
    exit 1
fi

export LANG=C
RE1=$(date +'%b')
RE2=$(date +'%d')
if [ $RE2 -le 9 ] ; then
   RE2=$(echo $RE2 | cut -c2-)
   RE2=" $RE2"
fi
cat $1 | egrep "$RE1 $RE2" | egrep -i --color 'warn|errror|fail|crit|alert|emerg' 

-find cmd
■ 자주 사용되는 find 명령어 형식들
------------------------------------------------------------------------------
(형식1) # find / -name core -type [f|d]    (# find / -name "*oracle*" -type f)
(형식2) # find / -user user01 -group class1 
(형식3) # find / -mtime [-7|7|+7] 
(형식4) # find / -perm [-755|755] 
(형식5) # find / -size [-300M|300M|+300M]
(형식6) # find / -name core -type f -exec rm -f {} \;
------------------------------------------------------------------------------
-find .(.은 현재 폴더 아래에 대해서) , /(상위폴더에 대해)
find . -mtime 3 -type f (수정일이 3일전 파일 검색)
find . -mtime -3 -type f (수정일이 3일일 안된 파일)
find . -mtime +3 -type f(수정일이 3일이 지남)

find . -perm -400 -type f -ls
ㄴ 권한을 -400 이하로 가진 애들 불러오기
find . -perm 400 -type f -ls
ㄴ 권한이 400인 퍼미션 파일 찾기

[실무예] 오래된 로그 파일 삭제
# find /Log_Dir1 -name "*.log" -type f -mtime +30 -exec rm -f {} \;
# find /Log_dir2 -name "*.log" -type f -mtime +60 -exec rm -f {} \;

[실무예] 파일시스템이 갑자기 풀(Full) 나는 경우 예
# find /var -mtime -2 -size +1G -type f 
# find /var -mtime -2 -size +512M -type f 
	ㄴ 양일간에 수정된 파일들 중에서 용량이 1기가 이상인것
	   ㄴ 안나오면 반으로 줄여서 한 번 더 검색. 이런식으로 줄여가며!

/var/server/log/file.log - 이런식으로 검색해서 용량이 큰 파일이 나오면!
ㄴ lsof(list open file) 
# lsof | grep /var/server/log/file.log = 어떤 프로세스가 이 파일을 잡고 있는지 확인한다 !

[실무예] 에러 메세지 검색
(소스코드가 존재하는 경우)
소드코드O: find /src -type f -exec grep -l ‘server Error’ {} \;
ㄴ 수많은 파일 중 서버 에러라고 뜨는걸 찾아라
소스코드X: 구글검색으로 site:redhat.com “Server Error” 식으로 검색찾기!
===============================
—---------12장 압축과 아카이빙—-------
===============================

압축 (효율 gzip<bzip<xz)
[gzip/gunzip cmd]
	-gunzip -c file1.gz (-c는 파일 잠깐 풀어서 안을 확인함, -d는 압축해제)
	-gzip -v file2( -v는 중간에 압축하는걸 텍스트로 출력)
	-gzip file1 = file1을 압축
	-gunzip file1 = 압축해제 

	[zcat] zcat file1.gz 파일을 잠시 열어서 확인해서 안깨짐
	ㄴ 압축파일을 원래 cat으로 확인하면 깨진다

[bzip2/bunzip2 cmd]
	-bzip2 file1 =압축
	-bunzip2 -c file1.bz2 =압축해제1
	-bzip2 -d file1.bz2  =압축해제2
	
[xz/unxz cmd]
	-xz file1 = 압축
	-unxz -c file1.xz =압축파일 확인
	-unxz file1.xz = 압축 해제

아카이빙
tar cvzf file.tar.gz file1 file2
tar tvzf file.tar gz
tar xvzf file.tar gz
tar cvjf file.tar.gz file1 file2
tar tvjf file.tar gz
tar xvjf file.tar gz
tar cvJf file.tar.gz file1 file2
tar tvJf file.tar gz
tar xvJf file.tar gz

(실무 예) 인터넷상에 받은 파일 압축 해제 방법
file.gz			---- gzip -----> # gunzip file.gz        	(# gzip -d file.gz)
file.bz2 		---- bzip2 ----> # bunzip2 file.bz2      	(# bzip2 -d file.bz2)
file.xz     	---- xz -------> # unxz file.xz          	(# xz -d file.xz)
file.tar.gz		---- tar/gzip -> # tar xvzf file.tar.gz  	(# tar xvf file.tar.gz)
file.tgz
file.tar.bz2	---- tar/bzip2-> # tar xvjf file.tar.bz2 	(# tar xvf file.tar.bz2)
file.tbz
file.tar.xz    	---- tar/xz ---> # tar xvJf file.tar.xz  	(# tar xvf file.tar.xz)
file.txz 
file.zip		---- zip ------> # unzip file.zip
file.jar        	---- jar ------> # jar xvf file.jar

===============================
—---------13장 배시쉘특성—-------
===============================

–리다이렉션–
	입력 리다이렉션 -wall < /etc/MESS/work.txt
	출력 리다이렉션 -ls -l

[특수문자의미] >의 갯수에 따른 의미차이!
CMD  2>  filename 변경			
CMD  2>> filename 내용추가해서 변경해줌


에러 리다이렉션
[cmd] ls -l /test /nodir > dirfilename1 
	ㄴ정상적인 출력 결과를 파일로 새로 만들어서 저장
# ls /test /nodir > dirfilename 2>&1
ㄴ dirfilename1에 정상출력결과와 에러출력결과를 같이 저장

[실습예] 스크립트 로그 파일 생성
# ./script.sh > script.log 2>&1

[실습예] 출력 내용이 긴 명령어 수행 시, 출력 화면 분석
# configure > config.log 2>&1
ㄴ 긴 config 출력문을 config.log에 넣어서 확인

[실습예] 일반사용자가 명령 수행시 에러 메세지를 지우는 경우
$ find / -name core -type f > 2>/dev/null
ㄴ 일반사용자가 볼 경우 에러가 많이 뜰 수 있으니 에러는 빼고 검색!

–파이프 = 명령어를 가공 시 사용. 추가 명령어!--
■ Pipe(|) 기호가 많이 사용되는 형식
# CMD | more
# CMD | grep rsyslogd
# CMD | CMD | …

[실무예] 모니터링 구문 + 데이터 수집 (cmd | tee -a httpd.cnt)
while true
do
	ps -ef | gerp httpd | wc -l | tee -a httpd.cnt
	sleep
done

[실습예] 여러 터미널 화면을 공유하는 경우
	#script -a /dev/null | tee /dev/pts/1 | tee /dev/pts/2
               스크립트 공유       터미널 1 경로     터미널2 경로  (tty로 확인)



–배시쉘 기능–
# set -o	/* 쉘 자체의 기능 전체 목록 확인 */
# set -o vi 	/* 쉘 자체의 기능 중 vi 기능을 ON */
# set +o vi 	/* 쉘 자체의 기능 중 vi 기능을 OFF */
[깨알코드] txt 파일에 문자를 바로 넣어서 생성
ㄴ echo 1111(내용) > 만든 문서의 이름

–변수– 
지역변수 - export를 안쓰면 지역변수
환경변수 - export로 전역 설정을 해주면 환경변수
특수변수 - $$	$?	$!	$1,2	$#	$*
   변수의 선언방법
    ㄴ export VAR=5
	ㄴ echo $VAR
	    ㄴ unset VAR

[시스템/ 쉘 환경변수(set/env)]
	PS1 변수: export PS1=’[\u@\h \w]$ ’      home/.bashrc
	명령어 마지막에 \을 사용하면 다음줄로 넘어가서 이어서 쓰면 됨.
	보통 명령어가 너무 길어서 확인이 힘들때 다음줄로 추가 명령 입력
	PATH 변수: export PATH=$PATH:/root/scripts ($home/.bash_profile)
	HOME 변수
	PWD 변수
	USER 변수
	LOGNAME 변수
	UID 변수
	TERM: export TERM=vt100
	LANG: export LANG=ko_LR.UTF-8


–메타캐릭터–
“”	‘’ 	``	\	;

–cmd 히스토리– 
 	HISTSIZE=512 크기 지정
	HISTFILE=$HOME/.BASH_HISTORY = 경로지정
	HISTFILESIZE=

–엘리어스– = 줄임말로 만들기!*****
alias aa='cd /test && rm -rf /test/*' =aa를 테스트폴더 비우기로 사용 




–환경파일– 				
/etc/profile
	
root		                   user01		    user02
	
	~/.bash_profile	~/.bash_profile		~/. bash_profile	
	~/.bashrc		~/.bashrc			~/.bashrc

-/etc/profile		- ~/.bash_profile		-~/.bashrc

===============================
—---------14장 프로세서 관리—-------
===============================

[프로세서 정보]  (/proc/PID/*) 에 프로세서에 대한 정보가 있음
	프로세스의 정보는 /proc/*에 존재
	정밀 검색 시, ps -ef |grep 파일이름 으로 검색

[프로세서 관리]
프로세스 관리1
1.프로세스 실행
-fg) # gedit
-bg) # gedit & (띄운상태로 명령어 입력 가능)

2. 프로세스 확인
-ps -f =- f(full listing)는 더 많은 인자, 옵션을 확인 할 수 있게 해준다.
-ps -e= e(every)옵션은 특정 터미널이 아닌 데몬 프로세서도 출력

3. 프로세스 종료 (kill pid입력)
# kill - 1|-2|-9|-15 PID PID

1 	SIGHUP	프로세스 재시작(HangUp), 터미널의 제어 프로세스 종료를 보고하는 데 사용한다. 또한 프로세스를 종료하지 않고 다시 초기화(설정 재로드)하는 데에도 사용한다.
(EX): # kill  -1 450
2 	SIGINT 	키보드 인터럽트(Interrupt, <Ctrl + C>), 프로그램이 종료된다. 차단하거나 처리할 수 있다. 
(EX): # kill -2 450
3	SIGQUIT	키보드 종료(CTRL + \), SIGINT와 유사하지만 종료할 때 프로세스 덤프가 발생된다. 
(EX): # kill -3 450
9	SIGKILL	강제 종료(force exit signal), 갑작스럽게 프로그램이 종료된다. 차단, 무시 또는 처리할 수 없다. 항상 치명적이다.
(EX): # kill -9 450
15 	SIGTERM	정상 종료(exit), 기본 시그널, 프로그램이 종료된다. SIGKILL과 달리 차단, 무시 또는 처리 할 수 있다. 프로그램 종료를 정중치 요청하는 방법이다. 자체 클린업(cleanup)이 가능하다.   
(EX): # kill -15 450)
18	SIGCONT	프로세스가 중지된 경우 재개하기 위해 전송된다. 차단할 수 없다. 처리하더라도 항상 프로세스가 재개된다.
(EX): # kill -18 450
19	SIGSTOP	프로세스를 일시 중지한다. 차단 또는 처리할 수 없다.
(EX): # kill -19 450
20	SIGTSTP	키보드 중지, SIGSTOP와 달리 차단, 무시 또는 처리할 수 있다. SUSP 키 조합(CTRL + Z)을 사용한다.


프로세스 (잡, job) 관리2
• 잡 실행
fg) # ls 
bg) # ls &
• 잡 확인
# jobs

# fg %1
# bg %1
• 잡 종료
# kill %1

[프로세서 모니터링]
# lsof    (# lsof -P) = 내 프로세서가 열고 있는 모든 화일을 보여줌

# lsof <파일이름>   
	# lsof /usr/sbin/sshd
	# lsof /tmp
	# lsof /dev
	# lsof /home/user01

# lsof -c <데몬명>
	# lsof /usr/sbin/sshd
# lsof -c sshd   (# lsof | grep '^sshd')

# lsof -p <PID번호>
	# lsof -p 450

# lsof -i 
	# lsof -i 		(# netstat -antup)
	# lsof -i TCP	(# netstat -antp)
	# lsof -i UDP	(# netstat -anup)


   ===============================
—---------15장 원격접속과 파일전송—-------
   ===============================

[파일전송]
	scp cmd
	# scp file1 server2:file2 =보내기
# scp server2:/tmp/file2 /test/file1 =가져오기
# scp -r dir1 server2:/tmp

	sftp cmd
	#

[원격접속]
	ssh cmd

  
  
  
   ===============================
	  -----1장 디렉토리구조—-------
   ===============================
   
   디렉토리 목적
/	모든 디렉토리의 가장 상위 디렉토리이다. Root 파일 시스템이라고도 불린다. 모든 파일 시스템의 마운트 포인트가 존재한다. 

/usr	설치된 소프트웨어, 공유 라이브러리 포함된 파일 및 읽기 전용 프로그램 데이터, 중요한 하위 디렉토리에는 다음이 포함된다.
	• /usr/bin   	: 사용자 명령
	• /usr/sbin  	: 시스템 관리 명령
	• /usr/local 	: 로컬 사용자 지정 소프트웨어
	(EX) (Win)Program Files

/etc	설정에 관련된 파일들이 존재, 시스템 고유의 구성 파일이 존재한다. 
	• OS 부팅시 설정 정보
	• 서비스 설정 파일
	• 보안, 기타 여러가지 설정 파일들이 존재
	(EX) (Win)제어판

/var	재부팅 후에도 유지는 시스템 고유의 가변 데이터가 존재한다. 동적으로 변경되는 파일(예: 데이터베이스, 캐시 디렉토리, 로그파일, 프린터로 전송된 문서, 웹 사이트 콘텐츠)은 /var에 존재할 수 있다.
	• /var/log/*	: 로그 디렉토리

/run	마지막 부티 이후 시작된 프로세스의 런타임 데이터이다. 여기에는 프로세스 ID 파일과 잠금 파일 등이 포함된다. 디렉토리 내용은 재부팅하면 다시 생성된다. 이 디렉토리는 이전 버전의 CentOS에 있던 /var/run, /var/lock을 통합한다.
	• {/var/run|/var/lock} -> /run

/home	일반 사용자의 홈 디렉토리이다. 일반 사용자의 개인 데이터 및 구성 파일을 저장하는 디렉토리이다.
	(EX) (Win)C:\Users\soldesk\

/root	root 사용자 홈 디렉토리이다.

/tmp	어디에서나 쓸 수 있는 임시파일용 공간이다. 10일동안 엑세스, 변경 또는 수정되지 않은 파일은 이 디렉토리에서 자동으로 삭제된다. 다른 임시 디렉토리는 /var/tmp에 존재한다. 30일 이상 엑세스, 변경 또는 수정되지 않은 파일은 자동으로 삭제된다. 
	(EX) (Win)TMP=C:\Users\soldesk\AppData\Local\Temp

/boot	부팅 프로세스를 시작하는 데 필요한 파일들이 존재한다.
	• Boot Loader(GRUB)
	• 커널(Kernel)
	• 램파일시스템(initrd)

/dev	시스템에서 하드웨어에 엑세스 하는 데 사용되는 특수 장치 파일을 포함한다.
	(EX) (Win)장치관리자
	
media/	usb 같은 임시 마운트 포인트로 사용되는것
mnt/ ""


   ===============================
	-----2장 장치인식과 파티션작업—-------
   ===============================
   
  -----------------[Git 사용법 *****]-----------------
  GIT 사이트 : https://github.com/
  1) git 계정 생성
  2) github repository 생성
  3) 올릴 파일 준비
	+ .gitignore = 공개를 하지 않은 파일,디렉토리를 지정
	+ README.md
	+ bin/*.sh
	+ doc/*.hwp
	+ env/*.bashrc.txt
  4) 파일 올리기: https://github.com/shb003/01_LinuxEssential.git
	------------------------------------------------
	echo "# 01_LinuxEssential" >> README.md
	git init = 현재 폴더 아래 git와 연동할 로컬폴더를 생성
	git add README.md = 파일을 git 설정에 추가 (저장해줘야함)
	git commit -m "first commit"
	git branch -M main -초기구성
	git remote add origin https://github.com/shb003/01_LinuxEssential.git
		ㄴ 나의 원격 저장소에 이름을 붙인다. -초기구성
	git push -u origin main
	
	브런치랑 리모트 설정이 끝났다면
	git add README.md -파일추가
	git commit -m "first commit" - 파일에 대한 설명 추가 (필수)
	git push -u origin main - git사이트에 내가 입력한 파일 정보들을 입력
	
	------------------------------------------------------

	branch(가지)name : git config --global init.defaultBranch <name>
				      git config --global user.name "shb003"
					  git config --global user.email "dodoto999@gmail.com"
	(*) 로그인이 안된다면 토큰방식으로 변경해야한다
	[token 만들기]
	git 사용자 접속 - 디벨로퍼 셋팅 - 개인 접속 코인 - 토큰(클래식)
	ㄴ shb003 Token = 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
	 ㄴ token push 작업
		- git push -u origin main
	-------------------------------------------------------------
	[새로운 파일 추가]
	touch addfile.txt -텍스트 파일 추가
	git add .  - 폴더 아래에 모든 파일 git 임시등록
	git commit -m "2nd commit"	-설명추가
	git push origin main  -github로 연동
	----------------------------------------------------------------
	cd /test
	git clone https://github.com/shb003/01_LinuxEssential.git
	
#######################
제 2장 장치 관리(디스크 장치 관리)
#######################

	# ls /
	[참고] 파일시스템 구조/ 디렉토리 용도 확인 CMD
	# man 7 hier
	# man 7 file-hierachy
	
장치관리(ex: 디스크 장치 관리)
	
	디스크 장착
	* 장치 인식 작업
	* 파티션 작업
	* 파일 시스템 작업
	* 마운트 작업
	
1. 장치 인식(device reconfiguration)
	(선수지식)
	디스크s 구조: sector- track - cylinder - parition - disk
	디스크 종류: IDE(SATA), SCSI(SAS), SSD
	디스크 이름 체계
		* IDE DISK: /dev/hda, /dev/hdb, dev/hdd
		* SCSI DISK: /dev/sda, /dev/sdb, /dev/sdc, /dev/sdd .....
		* Virtual DISK: /dev/vda, /dev/vdb, /dev/vdc .....	
	
		
	(장치인식 작업)
	디스크 추가
	* poweroff
	* 디스크 장착
	* poweron
	* lsblk --fs -p
	
2. 파티션 작업
(1) 선수 지식
	파티션 종류
		* BIOS F/N - MBR 파티션 형식
		* UEFI F/W - GPT 파티션 형식
	파티션 이름 체계 (MBR 체계)
		* primary partition(1-4)
		* Extended partition
			-Logical partition(5-15)
	파티션 이름 체계 (GPT 파티션 형식)
		*partition(1~128)

(1) 파티션 작업
	
		파티션 작업 툴
		* fdisk CMD - 2TB 이하 (2TB 이하의 작업에서만 사용)
		---------------------
		* gdisk CMD - 2TB 초과
		* parted CMD - 2TB 초과
		
		파티션 작업 순서
		1. fdisk /dev/sdb
		2. p= 파티션 확인, n = 파티션 생성, d = 파티션 제거, w=저장하고 종료
		3. 저장 삭제 후, partprobe로 마무리
		
		fdisk 확장 파티션
		1. 확장 파티션 생성
		ㄴ n - p - 원하는 파티션 번호 - enter - 원하는 용량
		2. 이미 확장 파티션 안에서 만들 수 있음. n를 입력하면 번호 지정 없이 바로 나머지를 물어봄
		3. 시작점 설정 건너뛰고 두번째 용량만 원하는 용량으로 설정
		4. 나머지는 기호에 따라 추가
		
		확장파티션(Extended Partition), 논리파티션(Logical partition)은 왜 존재하는 것인가?
		ㄴ 1기가를 4개의 파티션으로 나눠서 작업한다면 primary 파티션으로 나눠줄 수 있지만,
		  4개 이상이라면 확장파티션으로 논리 파티션 분리 작업을 해주는것이 좋다.
		  
		[gdisk 작업]
		- gdisk partition id (Hex code) - 외워둬야 하는 타입의 헥스 코드
	   * 8200 : Linux swapml
   	   * 8300 : Linux filesystem
	   * 8e00 : Linux LVM
	   * fd00 : Linux RAID
	   
	    - fdisk partition id (Hex code)
		82 : linux swap
		83 : linux
		
		[parted 작업]
		1. parted /dev/sdc
		2. mklabel 라벨타입
		3. mkpart
		4. 이름은 아무거나 ex: data1
		5. 시스템 타입은 보통 ext4
		6. 시작용량과 끝 용량 설정. 남은 용량 다채우는 거면 end를 100%로 설정
		
		+ parted로 용량을 딱 맞게 설정하여 작업 시, 용량을 어느정도 여유롭게 잡아줘서 실제로 200M를
		  잡았다면 190M정도면 파티션을 잡아준다.

		3. 파일 시스템 작업
		(1) 선수 지식
			- 파일시스템 정보 확인
			# man -k ext4|xfs
			# man 5 fs
			
			- 파일시스템 종류
			* ext3/ext4, xfs 
			
			- 파일시스템 구조 (ex: ext4)
			* DISK 
				--------------------(10)
				MBR
				----------(5)
				BOOT SECTOR
+-->			--------------------(10)
|				SUPER BLOCK
|				----------
				GROUP 0
ext4			*Backup super block
				*Gloup Descriptor table
|					-block bitmap, inode bitmap
|					-inode table, data block
|				
|				GROUP 1
|				*Gloup Descriptor table
|					-block bitmap, inode bitmap
|					-inode table, data block
|				
|				GROUP 2
|				*Backup super block
|				*Gloup Descriptor table
|					-block bitmap, inode bitmap
|					-inode table, data block
|				....
+-->			--------------------(10)
				Super block
				-----------
				GROUP 0
				GROUP 1
				GROUP 2
				....
				
				
			# dumpe2fs /dev/sdb1 (# tune2fs -l 
			# xfs_info /dev/sdb1
		(2) 파일 시스템 작업
		
5. 기타 마운트 관리
	(1) cd/dvd 마운트
		(자동마운트)
		ㄴ Automount
		# cd /run/media/$USER/$LABEL ; ls
		# cd ; umount /run/media/$USER/$LABEL
		(수동마운트)
		# mkdir -p / mnt/cdrom ; mount -t iso9660 -o ro /dev/cdrom /mnt/cdrom
		# cd ; umount /mnt/cdrom
	
		
#######################
제 3장 파일시스템 점검과 모니터링
#######################
파일시스템 점검
	fsck CMD
		# fsck /dev/sbd1
		# fsck -y /dev/sbd1
		
		# fsck /dev/sbd1
		# fsck ext4 /dev/sbd1
		# fsck -l ext4 /dev/sbd1
		
		(ext4) # fsck ext4 /dev/sbd1
		(xfs) xfs_repaire /dev/sbd1
		
		[실무예] "fsck -y /dev/sdb1" 사용하는 경우의 로그 생성된다
		# fsck -y /dev/sdb1 2>&1 | tee -a tsck.log/*
		
		[실무예] 슈퍼블록 복구
		(자동) # fsck -y /dev/sdb1
		(수동) # dumpe2fs /dev/sdb1 | grep -i superblock
			  # fsck -b 32768 /dev/sdb1
			  
		[실무예} bad block
		배드블럭(bad block)의 종류
		- 물리적인 배드블럭(Physical badblock)
		- 논리적인 배드블럭(Logical  badblock)

		# badblocks -v /dev/sdb1       /* 상당히 오랜 시간이 걸림 */
		# e2fsck -c -p -f -v /dev/sdb1 (# e2fsck -cpfv /dev/sdb)
		
		alias df='df -h -T'
		
		
	5. 기타 마운트 관리
		(2) iso 이미지 파일 관리
		mkisofs -o /이름/가져올 경로
		# mkisofs -o linux.ios /etc/sysconfig/*
		# mkdir -p /mnt/iso ; mount -t(type지정) iso9660 -o ro,loop /test/linux.iso /mnt/iso
		 [깨알 상식] lsblk --fs = 파일 구조와 안에 내용들을 트리 형식으로 저장
		 
		(3) usb 메모리 마운트
		FAT32
		(자동마운트)
		automount
			# cd /run/media/$USER/&LABEL ; ls
			# cd ; umount /run/media/$USER/&LABEL
		
		(수동마운트)
			# mkdir -p /mnt/usb ; mount -t vfat /dev/sde2 /mnt/usb	
			# cd /mnt/usb ; ls
			# cd ; umount /mnt/usb
		
		NTFS
			# yum -y install epel-release
			# yum install ntfs-3g
		(자동마운트)
		automount
		# cd /run/media/$USER/&LABEL ; ls
		# cd ; umount /run/media/$USER/&LABEL
		(수동마운트)
		# mkdir -p /mnt/ntfs ; mount.ntfs /dev/sde2 /mnt/ntfs
		# cd /mnt/ntfs
		
		-RAM 디스크 마운트
		(수동마운트)
		# mkdir -p /mnt/ram ; mount -t tmpfs -o size=5g none /mnt/ram
		# cd /mnt/ram ; ls
		# cd ; umount /mnt/ram
		
		- NFS 원격 마운트
		  [전제조건] 원격서버에 공유설정이 되어 있어야한다
		  
		(수동마운트)
		# mkdir -p /mnt/nfs ; mount -t nfs 
		# systemctl restart nfs-server
		# 
		
		(6) cifs 원격 마운트
		# mkdir -p /mnt/cifs
		# mount -t cifs //자신의 ip/공유될 폴더 /mnt/cifs -o username=soldesk
		# cd /mnt/cifs = 사용할 폴더로 이동
		# cd ; umount /mnt/cifs = 사용 종료 후, 마운트 종료
		

#######################
-----제 5장 LVM 관리------
#######################

■ LVM 작업 순서

• Partition System ID 변경(fdisk CMD) 
-> PV 생성(pvcreate CMD) 
	t-L-가이드를 보고 원하는 타입으로 변경 : ex: 8e
	# pvcreate /dev/sda1 
	# pvcreate /dev/sda1 /dev/sdb1 /dev/sdc1 
	# pvcreate /dev/sd[abc]1 
	# pvcreate /dev/sda /dev/sdb /dev/sdc 
-> PV 제거
	# pvremove /dev/sda1 
	# pvremove /dev/sda1 /dev/sdb1 /dev/sdc1 
	# pvremove /dev/sd[abc]1 

-> PV 생성 시, 확인법
	# fdisk -l | grep LVM  	# 생성 가능한 PV 목록 확인
	# pvs                    	# 생성된 PV 목록 확인
	# pvcreate CMD			# PV 생성
	# pvdisplay /dev/디스크 선택 = 자세한 확인

-> VG 생성(vgcreate CMD) 
	# vgcreate vg1 /dev/sdc1 /dev/sdd1 /dev/sde1 
	# vgcreate vg1 /dev/sd[cde]1 
	# vgcreate vg1 /dev/sd[cde]1 -s 16M		/* PE Size : 16MB */ -사이즈 단위 안주면 4M단위로 나옴!

-> VG 삭제
	# vgremove vg1 
	# vgremove /dev/vg1 

-> VG에 디스크 추가/제거
	# vgextend vg1 /dev/sdf1 
	# vgreduce vg1 /dev/sdf1 

-> VG 이름 변경
	# vgrename /dev/vg1 /dev/vg1_backup
	# vgrename vg1 vg1_backup

-> VG 정보 확인
	# vgs
	# vgdisplay   (# vgdisplay vg1)
	# vgscan



-> LV 생성(lvcreate CMD)
	# lvcreate -L 10G vg1            	/* LV 이름 자동 생성 : lvol#(용량 10G) */
	# lvcreate -L 1500M -n lv1 vg1
	# lvcreate -L 1500 -n lv1 vg1    	/* 용량 단위가 없으면 MB */
	# lvcreate -l 60%VG -n lv1 vg1
	# lvcreate -l 100%FREE -n lv1 vg1
	
	■ LV 삭제
# lvremove /dev/vg1/lv1

-> LV 이름 변경
	# lvrename /dev/vg1/lv1 /dev/vg1/lv2
	# lvrename vg1 lv1 lv2           	/* vg1(lv1 -> lv2) */
-> LV 공간 늘리기/줄이기
	# lvextend -L 12G /dev/vg1/lv1   	/* lv1 용량을 12G로 맞춤 */
	# lvextend -L +1G /dev/vg1/lv1   	/* lv1 용량을 1G 만큼 추가 */
	# lvextend -l +100%FREE /dev/vg1/lv1

	# lvreduce -L 3G /dev/vg1/lv1
	# lvreduce -L -3G /dev/vg1/lv1
	# lvreduce -l -3 /dev/vg1/lv1    	/* lv1 용량을 3 LE(Logical Extend)만큼 감소 */

-> LV 정보 확인
	# lvs 
	# lvdisplay 	(# lvdisplay /dev/vg1/lv1)
	# lvscan 

[질문] 초기 vm 구성 후 리눅스 설치 시에 / 용량을 60G로 늘릴 수 있는가?
/dev/cs/root(39G) -> /dev/cs/root(60G)
 답 = #lvextend -l 100%FREE /dev/cs/root
 

-> F/S 생성(mkfs CMD)
-> 마운트(mount CMD, /etc/fstab)


[구성 순서]
1. 디스크 8e로 lvm 설정, 개인파티션 디스크 구성
2. pvcreate로 만들기
3. vg로 만들어둔 pv들 다 묶기

-작업계획
	1. DISK 준비 (추가 및 인식)
	2. 파티션 작업

parted /dev/sdc mklabel media
fdisk /dev/sdc
/dev/sdc1
partition id:8e
#######################
-----제 6장 RAID------
#######################

- RAID 7
	리얼타임을 따로 사용해서 안정성이 높음 하지만 스토리지 가격이 높음
	
#######################
-----제 7장 SWAP------
#######################

-SWAP 이란?
디스크내에 존재하는 가상적인 메모리 공간, 물리적인 메모리(RAM) 
연장 공간처럼 쓰이는 공간

■ 스왑 관련 이슈(SWAP Issue)?
- 언제 스왑을 추가하는가?
- 스왑 공간의 크기?
	(초기 설치시)
	(운영시)
- 스왑을 추가하면 성능이 좋아지는가?
	ㄴ 그렇지않다. 하지만 운영체제가 멈추는것을 방지하기 위해 추가 하는것이다.

-SWAP 관리
	* SWAP FILE 형태로 추가/삭제하기
		# mkdir -p /swap
		# dd -if=/dev/zero of=/swap/swapfile bs=1M count=10240
		# mkswap /swap/swapfile
		# swapon swap/swapfile
		# vi /etc/fstab
		# rm -f /swap/swapfile
		
	* SWAP Partition 형태로 추가/삭제하기
		# fdisk /dev/sdb (t=82)
		# mkswap /dev/sdb1
		# swapon /dev/sdb1
		# vi /etc/fstab
		
		# swapoff /dev/sdb1
		# vi /etc/fstab
		
	* swap LV 형태로 추가/삭제하기
		#fdisk /dev/sdb (t=8e)
		#pvcreate /dev/sdb1
		#vgcreate cs /dev/sdb1
		#lvcreate cs -n swap2 -L 10G
		#mkswap /dev/cs/swap2
		#swapon /dev/cs/swap2
		#vi /etc/fstab
		
		#swapoff /dev/cs/swap2
		#vi /etc/fstab
		
############################
-----제 8장 소프트웨어 관리------
############################

rpm cmd
	#rpm -qa | grep openssh
		[참고] 인터넷 - rpm 파일 
	ㄴ rmpfind.net
	 ㄴ rpm.pbone.net
	
	-설치
	#rpm -ivh|Fvh|Uvh [--nodeps] [force] PKG.rpm
	     설치 업데이트 업그레이드(선호!)
	#rpm -qa | grep PKG = 전체 패키지 확인 옵션
	   
	#rpm -e PKG
	
	#rpm -qf /usr/bin/php-cli
	
	-삭제
	#rpm -e [--nodepes](호환성무시) PKG
yum/dnf cmd
	
	-설치명령어
	# yum [-y] install pkg
	# yum [-y] update pkg
	# yum [-y] localinstall pkg.rpm
	# yum download pkg
	
	#yum list (확인명령어)
		# yum list installed  = 설치된 패키지 목록 확인
		# yum list installed [--downloadonly] = 경로아래 다운로드만 해둠
		# yum list avalable 
		# yum search php
		# yum list 'php-7.2.24*'
		# yum provide '*/httpd.conf'
		
		- yum history
		# yum history = 설치,삭제 내역 확인
		# yum histoty info (번호) = 그 번호에 대한 로그기록
		# yum history redo 20
		# yum history undo 43 
		# yum history rollback 41
		

	# yum [-y] remove pkg =삭제명령어

	[참고] yum update
	# yum check-update 2>&1 | tee rpm.log ( 업데이트 확인하고|그 내용을 로그로 따로 저장)
	[2(오류출력)>&1(정상출력)의 뜻] =file.log에 정상적인 출력결과 외에도 넣는다는 뜻 
	# yum update
	
	- yum repository 관리
	# yum repolist ,all
	# yum-config-manager --disable epel = 목록에서 제외
	# yum-config-manager --enable epel = 목록에 추가
	
	[참고] /etc/yum.repo.d/*.repo 만들기
	(ㄱ) 자동으로 생성하기 (yum-config-manager)
		# yum-config-manager --add-repo file:///mnt/cdrom/BaseOS
		# yum-config-manager --add-repo file:///mnt/cdrom/AppStream
	(ㄴ) 수동으로 생성하기
		# yum /etc/yum.repo.d/CD.repo
		-----------------------------
		[MYCDBaseOS]
		name= CentOS Stream 8 -BaseOS
		baseurl=file:///mnt/cdrom/BaseOS
		enabled=1
		
		[MYCDAppStream]
		name=CentOS Linux - AppStream
		baseurl=file:///run/media/root/CentOS-8-3-2011-x86_64-dvd/AppStream
		enabled=1
	
	-yum group cmd
		# yum group install <gpkg>
		# yum group update <gpkg>
		
		# yum group list
		# yum group list hidden | egrep -i 'security|development'
		# yum group info <GPKG>
		
		# yum group remove <gpkg>
		
		사용리눅스 커널 버전: 4.18.0-408.el8.x86_64

source code

	#cd /test ; rm -rf * = 사용 x
	#cd /test && rm -rf * = 있어야만 지우기 때문에 안전!!
	
	#cd /test && wget http://www.example.com/httpd.tar.gz
	#tar xvzf http.tar.gz -C /usr/local/src
	#cd /usr/local/src $$ comfigure --prefix=/usr/local/apache2 && make && make install
	# /usr/local/apache2/bin/apachect1 start
	
	[참고] 퍼블릭 키 값: FE1AA336F722C534B40466F1D7F385BF5C0F4E5C
		ㄴ 키 보는 명령어 # gpg --list-key
		
rpm 선행설치 필요파일들
rpm -Uvh php-cli-7.2.24-1.module_el8.2.0+313+b04d0a66.x86_64.rpm
php-common-7.2.24-1.module_el8.2.0+313+b04d0a66.x86_64.rpm

크롬실행명령어 -----chrome &--------

############################
-----제 9장 부팅 과정------
############################

[리눅스 부팅 과정]
-F/W 단계
-부트 로드(Boot Loader) 단계
-커널(Kernel) 단계 
-systemd 단계

1. 부팅 과정
■ 1 단계 : F/W 단계
	- post
	- 부팅매체(floppy -> disk -> cd -> net)
■ 2 단계 : 부트 로드(Boot Loader) 단계
	- /boot/grub2/grub.cfg
	- kernel 
	- initramfs
■ 3 단계 : 커널(Kernel) 단계 
	-kernel -> initramfs(systemd)
■ 4 단계 : systemd 단계\

■ 서비스 제어
# systemctl start httpd.service
# systemctl stop httpd.service
# systemctl restart httpd.service
# systemctl status httpd.service
# systemctl enable httpd.service
# systemctl disable httpd.service

# systemctl status httpd - 현재 구동중인지 확인
# systemctl is-active httpd	=> # systemctl status httpd
# systemctl is-enabled httpd	=> # systemctl list-unit-files | grep httpd.service
*** # systemctl is-failed httpd	=> # systemctl --failed --type=service
	ㄴ fail이 발생한 부분을 확인한다.
	
- 그래픽, 멀티모드 설정하기
# systemctl get-default – 부팅시 모드 표시
# systemctl set-default graphical.target – 재부팅 시 모드 설정

-부팅과정에서 text ctl 모드에서 설정변경 (e로 edit 모드 들어가기)
(ㄱ) /dev/cl/root --> /sysroot(ro)   ==> "rd.break"
                                        # mount -o remount,rw /sysroot
                                        # chroot /sysroot
(ㄴ) /dev/cl/root --> /(ro)          ==> "init=/bin/bash"
                                        # mount -o remount,rw /
(ㄷ) /dev/cl/root --> /(ro), 시스템 초기화   ==> "systemd.unit=emergency.target"
                                        # mount -o remount,rw /
(ㄹ) /dev/cl/root --> /(rw), 시스템 초기화, 나머지 파일시스템 마운트 ==> "systemd.unit=rescue.target"

(5) 장애처리(ex:안전모드)
(ㄱ) rd.break
	reboot -> GRUB menu -> 적당한 커널 선택 -> e -> linux 라인 선택
	<end><space> -> rd.break
	# mount –o remount,rw /sysroot
	# chroot /sysroot
	# passwd root
	# toucg /.autorelabel -> exit exit
	
(ㄴ) init=/bin/bash
	reboot -> GRUB menu -> 적당한 커널 선택 -> e -> linux 라인 선택
	<end><space> -> init=/bin/bash
	# mount –o remount,rw /sysroot
	# chroot /sysroot
	# passwd root
	# toucg /.autorelabel -> 재부팅
	
(ㄷ) systemd.unit=emergency.target
	reboot -> GRUB menu -> 적당한 커널 선택 -> e -> linux 라인 선택
	<end><space> -> systemd.unit=emergency.target
	# mount –o remount,rw /
		장애처리 -etc 파일 오류 시 사용
	# exit

(ㄹ) systemd.unit=rescue.target
	reboot -> GRUB menu -> 적당한 커널 선택 -> e -> linux 라인 선택
	<end><space> -> systemd.unit=rescue.target - 마운트가 이미 되어있음
		장애처리 -etc 파일 오류 시 사용
	# exit

질문 – 오랜 linux vm 이미지를 기동했는데 root 암호를 모르는경우?
답변 – root 암호를 복구한다.
	# reboot
	GRUB menu 적당한 커널 -> e -> linux 시작하는 라인 -> <end><space> -> re.break -> <ctrl+x>
	# mount –o remount,rw /sysroot
	# chroot /sysroot
	# passwd root
	# (selinux on 시) touch /.autorelabel
	#exit; exit
	
[실습] (systemd phase) /etc/rc.local (/etc/rc.d/rc.local) 파일을 사용한 부팅시 실행명령 등록
# vi /etc/rc.d/rc.local
# chmod +x /etc/rc.d/rc.local - 로그인 바로 직전에 실행되게 됨

[실습2] (bootload phase) GRUB2 암호 설정하기
# grub2-setpassword
=> /boot/grub2/user.cfg

[실습3] (systemd phase) 새로운 서비스 등록
# vi /usr/lib/systemd/system/new.service
# systemctl daemon-reload
# systemctl enable --now new

[실습4] (grub phase) GRUB가 깨진 경우
CD 부팅
# df -h =mnt/sysroot가 마운트 되어 있어야해서 확인하는것! # mount -o rw /mnt/sysroot
# chroot /mnt/sysroot
	# lsblk --fs -p
	# fdisk -l /dev/sda
# grub2-install /dev/sda (#grub2-mkconfig -o /boot/grub.cfg)
# exit ; exit

[실습5] (systemd phase) /etc/fstab 파일 잘못된 설정의 예
root 암호 입력
# mount -o remount,rw /
# vi /etc/fstab
-> 적당한 설정
# systemctl daemon-reload
# exit

- systemd 데몬 = 모든 시스템의 부모 프로세서

############################
-----제 10장 사용자그룹관리------
############################

용어: 인증(authentication), 인가(Authorization), 역할(role)

사용자 관리
	사용자 정보 파일
		/etc/passwd
		/etc/shadow
	사용자 관리 파일
		useradd cmd
			# useradd user01
			# useradd -M /oracle oracle - 홈폴더 생성x( #chown -R oracle:oinstall /oracle)
			# passwd user01
			# useradd -e 2023-03-08 user04 - 계정에 기간을 추가
			# useradd -D -g 10 - 유저 생성 기본값 변경
			# useradd -D -b /users  ''
			# useradd -D -s /bin/sh ''

		usermod cmd
			# usermod -u 2000 user01 - uid change
			# usermod -s /bin/sh user01 - shells 경로 변경
			# usermod -c '적당한 내용' user01
		userdel cmd
			# userdel user01 = 검색상 정보만 삭제
			# userdel -r user01 = 정보와 자원 모두 삭제
그룹관리
	그룹 정보 파일
		/etc/group
	그룹 관리 명령
	groupadd CMD
		# groupadd class1
		# useradd -aG class1,class2 user01  - 유저에게 서브그룹 추가
	groupmod CMD
		# groupmod -g 3000 class1 
	groupdel CMD
		#groupdel class1

암호관리
	chage CMD
		# chage -l user01
		# chage -M 90 -W 7 user 01
		# chage -E 2023-12-31 user01
		
		[실무예] 사용자 계정에 대한 exfiere date 설정하기
		추가 - # useradd -e 2023-12-31 user01
		변경 - # usermod -e 2023-12-31 user01 (# chage -E 2023-12-31 user01)
		
		[실무예] Max Days + Warn Days
		전역 - /etc/login.defs (PASS_MAX_DAYS=30, PASS_WARN_AGE=7)
		개인 - # chage -M 30 -W 7 user01
		
############################
-----제 11장 스케줄링------
############################

at CMD (atd.service)
	# at 1300 -설정
	# at -l	(#atq) -확인
	# at -r N (#atrm N) -취소

crontab CMD
■ 작업 선언
	# crontab -e 	(-e : Edit, # vi /var/spool/cron/<사용자이름>)

■ 작업 확인
	# crontab -l 	(-l : List, # cat /var/spool/cron/<사용자이름>)

■ 작업 삭제
	# crontab -r 	(주의) (-r : Remove, # rm /var/spool/cron/<사용자이름>)
	
[반복출력문 시간마다 출력]
#!/bin/bash

ps u | awk '{print $7}' | grep pts/ | sort -u > /root/bin/pts.list
cat pts.list | while read BTS
do
cat /etc/MESS/CoffeeTime.txt > /dev/$BTS
done

	

	[실무예] 매월 첫번째 주 일요일 날 /root/bin/backup.sh 스크립트 실행하고 싶다
	* crontab CMD + script.sh
	# crontab -e(edit)
	0	3	*	*	0	/root/bin/script.sh	
	# vi script.sh
	------------------------------------------
	#!/bin/bash
	
	DAY=$(date +%d)
	if [ &DAY -le 7 ] ; then
		/root/bin/backup.sh
	fi
	-------------------------------------------


[실무예] wasuser, oracle 사용자만 crontab 명령어를 수행하도록 하고 싶다.
	# cd /var/spool/cron 
	# ls 
		backupuser   user01

	# vi /etc/cron.allow 
		backupuser 
		user01
		wasuser
		oracle


[실무예] 고객의 물음(?)
[고객의 질문] 일반적인 서비스(EX: httpd)는 설정 파일(EX: httpd.conf)을 수정하고 나면 데몬을 재기동하는데, 
crontab 서비스는 설정 파일을 수정한 다음에 데몬을 재기동하는가?


(복원) /etc/cron.allow 파일을 삭제하고 /etc/cron.deny 파일 편집한다.
	# rm -f /etc/cron.allow 
	# > /etc/cron.deny 
	-> user01 삭제

	[실무예] 관리자 스케줄링 설정
	(ㄱ) crontab -e => /var/spool/cron/root/$USER
	(ㄴ) # vi /etc/crontab
	(ㄷ) # vi /etc/cron..{hourly,daily,weekly,monthly}/*

############################
-----제 12장 백업과 복구------
############################

로컬 백업/복구
	tar CMD
		[참고] 상대경로/절대경로 (되도록 상대경로)
		ㄴ 상대경로는 경로로 직업 들어가서 카피를 해줘야하지만
		  절대경로는 뒤에 .이 아니라 /home 으로 절대 경로를 
		  정해줘서 직접 안해도 된다.
		 # cd /home
		 # tar cvzf /backup/home.tar.gz .
		 # tar tvzf /backup/home.tar.gz
		 # cd /home ; tar xvzf /backup/home.tar.gz
		 
		 ㄴ 한번에 복구가 되어서 편하지만 데이터가 넘 많이 쌓인다
		 
		 Full Backup + Difference Backup
		 # cd /home
		 # tar -g /backup/backup.time -czf /backup/home_full.tar.gz .
		 # tar -g /backup/backup.time -czf /backup/home_inc1.tar.gz .
		 
		 - 풀때
		 # cd /hoem
		 # tar -g /backup/backup.time -xzf /backup/home_full.tar.gz
		 # tar -g /backup/backup.time -xzf /backup/home_inc1.tar.gz
		 
		 
	-----------------------중요!!!----------------------------
	***** cp -r /test1/* /test2 = cp로 복사 시, 문제 점
	ㄴ *는 .으로 시작하는 설정파일은 cp 하지않고, 시간 또한 다르게 저장된다
	  그리고 오너와 그룹도 모두 실행자의 오너그룹으로 변경된다. 권한들 또한 
	  새로 만들어져 보안설정 또한 다르게 설정된다.
	  
	[해결법] 
	# cd /test1
		   cf(v는 보여주기 출력이기때문에 빼도 됨)
	# tar cvf - . | (cd /test2 ; tar xvf -)
	     file.tar로 받아라           file.tar를 풀어라
	- 에 file.tar로 지정해두면 안되는 이유
	ㄴ -는 바로 압축파일을 넘기는것이지만, file.tar로 지정하면 압축한것을 
		경로에 놔야하는데 용량이 두배로 든다. 만약 압축경로에 용량이 없다면 -로
		바로 압축해제 경로에 풀어버릴 수 있다.
	---------------------------------------------------------
	
	- 해제한 파일을 서로 비교해서 다른 점을 찾는다.
	(단순비교)
	# find /test1 | wc -l 
	# find /test2 | wc -l 
	(정밀비교) 
	# diff --recursive /test1 /test2 
	
	--로컬백업--
	[EX] 운영체제 전체백업 - 다른 용도로도 사용가능( --exclude)
	- 전체의 백업은 쉽지만 , 선택한 부분만 한번에 백업 받는것은 어렵다.
      그렇기 때문에 이 방법을 사용하여 제외 디렉토리를 지정하여 선택받기가 가능하다
	 # tar cvzf /backup/test.tar.gz \
		> --exclude=/test/dir1 \
		> --exclude=/test/dir6 \
		> --absolute-name /test
		- 절대경로 형식이라 최상위 폴더로 가서 풀어줘야한다
			[운영체제 백업본 만들기]
			# mkdir -p /RootBackup 
			# time tar cvzf /RootBackup/full.tar.gz \
				--exclude=/proc \
				--exclude=/tmp \
				--exclude=/media \
				--exclude=/sys \
				--exclude=/run \
				--exclude=/mnt \
				--exclude=/RootBackup \ - 이거 안해주면 압축파일을 계속만들어서 full난다.
				--absolute-name /

	[Ex5] 일부 복원/ 전체 복원
-복원위치
	백업 (절대경로) -> 복원 (cd /)
	백업 (상대경로) -> 복원 (cd /home)
-복원데이터
* (전체 복원) # tar xvzf /backup/backup.tar
* (일부 복원) # tar xvzf /backup/backup.tar user01 user02/ .bashrc
--
(1)	백업 데이터 생성
├── dir1
│   ├── dir2
│   │   ├── dir3
│   │   │   └── file1
│   │   └── file2
│   └── file3
├── dir4
│   └── file4
├── dir5
│   └── file5
├── dir6
│   ├── dir7
│   │   └── file6
│   └── file7
└── file8
--------------------------------
# cd /test
# tar cvf /backup/test.tar .
2-전체복원
# rm –rf /test/*

# tar tvf /backup/test.tar | head –확인
# tar -xvf /backup/test.tar  - ./으로 시작하는 상대결로여서 test로 들어가서 해줌

3-일부복원
# cd /test && rm –rf dir1
# tar -tvf /backup/test.tar | grep dir1
# tar -tvf /backup/test.tar | head  === 절대경로인지 상대경로인지 확인!! (.으로 시작하면 상대)

# cd /test
# tar -xvf /backup/test.tar ./dir1 ./file8 -- ./복원할 디렉토리, 파일 이름


	원격 백업/복구
	rsync CMD
		L /backup1 -> L /backup2
			#rsync -a --delete /backup1/ /backup2
		L /backup  -> R main:/backup/server1
			#rsync -az --delete -e ssh /backup/ main:/backup/server1
		R main:/backup/server1 -> L /backup
			#rsync -az --delete -e ssh main:/backup/server1/ /backup
		
		[참고] $HOME/ .bashrc
		alias RS='rsync -az --delete -e ssh'
		alias LS='rsync -a --delete'

	
	rsync 서버/클라이언트
	
	[네트워크 확인]
	# netstat -a(all)n(new)tup(proc,pid) | grep :검색번호
	
	(rsync server)
	# yum install rsync-daemon rsync
	# vi /etc/rsyncd.conf 
	----------------------------------------
	uid=nobody 			/* 사용자 아이디 */
	gid=nobody 			/* 그룹 아이디 */
	use chroot=no 			/* yes : 지정된 경로 이외에 다른 경로로 접속 못하게 함 */ 
	max connections=5 		/* 최대 접속자 수 : 0은 무제한을 나타냄 */
	timeout=60 			/* Client의 접속이 idle상태일 때 접속을 끊어버릴 초 단위 시간 */ 

	[Backup] 			/* rsync 서비스명 */
	comment=Rsync Backup Server 	/* rsync 서비스에 대한 설명 */
	path=/backup1 			/* 미러링될 데이터의 경로 (대상파일경로) */
	read only=no 
	----------------------------------------
	# systemctl enable --now rsyncd.socket
	
	(rsync client)
	# rsync -avz --delete -e ssh server::Backup /mirror


    
    
  리눅스 네트워크 /서비스/보안 과정

*****************************************
------------1장 네트워크 설정----------------
*****************************************

주소종류
* MAC (Media Access Control Address)
네트워크 세그먼트의 데이터 링크 계층에서 통신을 위한 
네트워크 인터페이스에 할당된 고유 식별자이다.
- 이더넷 상에서 통신 할 때 사용하는 주소
# ip link == 00:0c:29:45:93:63

* IP Address
컴퓨터 네트워크에서 장치들이 서로를 인식하고 통신을 하기 위해서 
사용하는 특수한 번호이다.
	-ipv4: 32bit 4byte 4octet 10진수 - 192.168.10.10
	-ipv6: 128bit 16byte 8octet 16진수 - fe80::20c29ff:fea5:1263
* Port Address
포트 주소는 소프트웨어에서는 네트워크 서비스나 특정 프로세스를 식별하는 논리 단위이다.
포트는 번호로 구별되며 이 번호를 포트 번호라고 한다. 포트 번호는 
IP 주소와 함께 쓰여 해당하는 프로토콜에 의해 사용된다.
예를 들어, ftp://000.000.000.000:21 라는 URL 에서 
맨 마지막에 있는 21이 포트 번호
 
NetworkManager?

- ens33(변경가능)= 네트워크 커넥션 번호 = 안에 네트워크 정보들이 들어있다.
* Network interface
* connection/profile

네트워크 관련 설정 파일들
	* /etc/hosts
		아이피(IP)와 호스트 이름(hostname) 또는 
		도메인 이름(Domain Name)을 맵핑(Mapping)하는 역할을 가진다. 
	* /etc/hosts.conf
		이름 요청(도메인 요청, Naming Service Request)시 
		도메인/이름 검색 순서를 나타낸다.
	* /etc/resolv.conf
	* /etc/sysconfig/network-scripts/ifcfg-*
네트워크 관련 명령어들
	* cthtool ens33
	* ip addr
	* ip route
	* cat /etc/resolv.conf
	* netstat -nr == ip 게이트웨이 확인
네트워크 설정 관련 툴
	* nmcli CMD
	* nmcli 툴
	nm-connection-editor 툴
	nmcli general permissions : 네트워크 권한을 총괄적으로 봄
	
	네트워크 시나리오 작업
		* ip 변경 작업
		* nic 추가 작업
		* 호스트 이름 변경
		* 팀 구성, 본딩 구성
			(ㄱ) team0
				# nmcli connection add \
				type team 
				ifname team0 
				con-name team0 
				team.runner activebackup
			(ㄴ) team0 (team0-portl, team0-port2)
				nmcli connection add \
				type etherner \
				slave-type team \
				ifname ens33 \
				con-name team-port1 \
			master team0
			(ㄷ) team0
				nmcli connection modify team0 \
				ipv4.method manual \
				ipv4.addresses 192.168.10.100/24 \
				ipv4.gateway 192.168.10.2 \
				ipv4.dns 168.126.63.1 \
				ipv4.dns-search example.com 
			(ㄹ) team0
				nmcli connection up team0
			
			(그밖)
			# nmcli connection add \
			type team \
			ifname team0 \
			con-name team0 \
			config'{"runner": {"name": "activebackup"}}'
	
			nmcli connection add \
			type etherner \
			slave-type team \
			ifname ens36 \
			con-name team-port1 \
			master team0
			
		[네트워크 복원] network 설정을 작업하기 전 상태로 돌리기(ens33,36)
		* ens33 : ip(192.168.19.20/24), gw(192.168.10.2), dns(168.126.63.1)
		* ens36 : connection/profile => x
			
		COMMON_OPTIONS:
            type <type>
            ifname <interface name> | "*"
            [con-name <connection name>]
            [autoconnect yes|no]
            [save yes|no]
            [master <master (ifname, or connection UUID or name)>]
            [slave-type <master connection type>]
		
		team:[config <file>|<raw JSON data>]

		team-slave:master <master (ifname, or connection UUID or name)>
                  [config <file>|<raw JSON data>]
				  
		IP_OPTIONS:
                  [ip4 <IPv4 address>] [gw4 <IPv4 gateway>]
                  [ip6 <IPv6 address>] [gw6 <IPv6 gateway>]
	


*****************************************
------------2장 SELinux관리----------------
*****************************************

SELINUX?
SELINUX 모드
	* enforcing
	* permissive
	* disabled
	
disabled <-> permissive,enforcing
	* disabled -> enforcing
		# vi /etc/selinux/config
		SELINUX=enforcing
		# reboot
	* enforcing -> disabled
		# vi /etc/selinux/config
		SELINUX=disabled
		# reboot
	* enforcing -> permissive
		# setenforce 0
		# vi /etc/selinux/config
		SELINUX=permissive

SELINUX Context
	# semanage fcontext -l
	# semanage fcontext -a -t http_sys_contene_t '/virtual(/.*)?'
	# restorecon -Rv /virtual
SELINUX Boolean
	# semanage boolean -l
	# semanage boolean -l -C = 초기 구성상태와 비교해 다른 점을 알려줌
	# setsebool -P httpd_enable_httpd on
SELINUX port
	# semanage port -l = 확인
	# semanage port -a -t http_port_t -p tcp 8888 = 추가
SELINUX Troubleshooting
	(ㄱ) 문제 원인 파악
	# cat /var/log/messages | grep -i preventing
	# sealert -l UUID == 안에 해결 방법이 있음
	or
	# cat /var/log/audit/audit.log | grep -i 'avc:	denied'
	# sealert -a /var/log/audit/audit.log
	(ㄴ) 문제해결 방법 - 이 중에서 문제가 있을 수 있다.
	* SELINUX context 문제 해결
	* SELINUX boolean 문제 해결
	* SELINUX port 문제 해결
	
*****************************************
-------------3장 방화벽 관리----------------
*****************************************

[firewalld?(nftables)]
firewalld는 동적 방화벽 관리자로 nft 명령을 
사용하는 nftables 프레임워크에 대한 프론트엔트이다.

	(CLI) firewall-cmd CMD (alias fwcmd)
	(GUI) firewall-config (firewall-config 패키지(다운로드))
	
	firewall-cmd CMD
		# firewall-cmd --permanent --add-service=http --add-service=https
		# firewall-cmd --permanent --add-port=1521/tcp
		# firewall-cmd --reload (alias fwreload)
	
	[리치 규칙]
	간단한 방화벽 설정은 앞에 fwcmd 로 등록하면 되지만 여러가지 설정이 필요하다면
	리치 규칙을 사용하여 설정하는것이 유리하다.
	# firewall-config 로 설정하는것이 좋다.
	
*****************************************
-------------4장 DNS Server--------------
*****************************************


- dns 서버의 역할 = 이름과 ip를 매칭시켜주는 역할을 수행한다.
- 다이나믹 dns = 원격서버에서 nsupdate를 통해 dns 설정을 원격으로 바꾸는것
- 캐싱= 정보를 임시로 보관하는것

* 프로그램: bind. bind-urills
* 데몬 & 포트.프로토콜: named(53/tdp, 53/tcp)
* 설정파일: /etc/named,conf/ (/etc/named.rfc1912.zones)
* 서비스 설정파일 : /var/named*

[실습] 초기 도메인 관리 -/etc/hosts

도메인 설정시 문제 확인

cat /etc/resolv.conf 의 ip주소 확인
	1. nameserver의 ip가 다른경우 nmtui로 eth0의 dns ip주소를 바꾼다
방화벽 리스트로 확인
systemctl status named로 확인

dnssec : 데이터의 위변조를 방지하기 위한 수단으로 사용되는것
ㄴ 사용하는 기술: 공개키 암호화 , 서명방식
	
	누락
	
	
[관리] DNS 모니터링
	* dnsgraph
-------------------------------------------------------------------

*****************************************
----------5장 Apache web Server----------
*****************************************

- 웹서버: 정적 컨텐츠를 제공 (jpg,ntw) ex= apache httpd
- Web Application Server: 동적 컨텐츠 제공 ( .jsp , .asp) =tomcat
-------------------------------------------------
	■ 프로그램: httpd, mod_ssl
	■ 데몬 & 포트 & 프로토콜: httpd(80/tcp, 443/tcp)
	■ 설정 파일: /etc/httpd/conf/httpd.conf
	■ 하위 설정 파일: /etc/httpd/conf.d/*.conf
	■ 서비스: httpd.service
--------------------------------------------------

1. 패키지 설치
	# yum install httpd mod_ssl
2. 서비스 구설
	# vi /etc/httpd/conf/httpd.conf
	# vi /etc/httpd/conf.d/*.conf
	# echo 'MyServer' > /var/www/html/index.html
3.서비스 기동
	#systemctl enable --now http.service
4. 방화벽 등록
	# firewall-cmd --permanent --add-service={http,https}
	# fwreload
--------------------웹서버 사용---------------------
[실습] 초기 웹서버 설정 점검
	# firefox https://www.example.com = https로 불러와서 인증서 과정을 거침
	# curl -k http://www.example.com  = 터미널로 불러와서 확인 -k는 
						인증서가 없어 발생하는 위험을 감수하고 실행한다는 명령문
	# curl -I http://www.example.com = 헤더정보만 확인하기 위한 명령어

[실습] 관리자 웹서버 구축(www.example.com)
	* /etc/httpd/conf/httpd.conf{ServerAdmin, ServerName}

[실습] 클라이언트 프로그램 사용
	*curl, firefox 링크로 사용
	
[실습] CGI 사용 =• 웹서버와 클라이언트간에 필요한 정보 교환을 가능하게 해주는 웹인터페이스.

[실습] 사용자 웹서버 구축(www.example.com/~user01)
	# vi /etc/httpd/conf.d/userdir.conf(UserDir public_html)
	$ chmod 711 /home/user01/ = user01에 권한을 변경해줘야 밖에서 봄
	$ mkdir /home/user01/public_html
	$ echo 'User01WebPage' > /home/user01/public_html/index.html

[실습] 사용자 웹서버 구축2(www.example.com/~user01)
	# /etc/httpd/conf/http.conf(Alias /user01 /home/user01/public_html)
	
(*) Apache Web Server 실행
(현재) # systemctl start|stop|restart|status httpd.service 
(부팅) # systemctl enable|disable httpd.service

[실습] CGI 설정 - bash shell 사용
	* /etc/httpd/conf.d/vhost.conf(scriptAlias /cgi-bin/ /vhost.conf)

[실습] CGI 설정 - perl 사용
	# yum install mod_perl(epel-release)
	* /etc/httpd/conf.d/perl.conf

[실습] PHP 사용
	# yum -y install php
	* /etc/httpd/conf.d/php.conf

[실습] .htaccess - 웹페이지 보호
	* /etc/httpd/conf.d/vhost.conf(AllowOverride AuthConfig
	* /www1/cgi-bin/.htaccess
	* htpasswd -c /etc/httpd/passwd webmaster

[실습] 가상호스트 (virtual Hosting) -하나의 웹서버에 여러개의 웹서버를 만드는것
	(ㄱ) 이름 기반 가상 호스팅(Name-based Virtual Hosting)
	(ㄴ) 포트 기반 가상 호스팅(port-based Virtual Hosting)	
	(ㄷ) IP 기반 가상 호스팅 (IP-based Virtual Hosting)

[실습] 웹서버 정보/상태/통계 모니터링
	* 1) 정보 => http://www.example.com/server-info
	* 2) 상태 => http://www.example.com/server-status
	* 3) 통계 => http://www.example.com/usage
		* webalizer (/etc/webalizer.conf)
		* /etc/httpd/conf.d/webalizer.conf

[실습] 웹 스트레스 툴 = webstress tool	

웹서버의 정보를 확인하는 사이트 : https://sitereport.netcraft.com/

[실습] 버전 장버/OS 정보 숨기기
	* /etc/httpd/conf.d/default.conf(servertoken prod)
	
[실습] ATJM(Apache + tomcat + hsp +MariaDB)
	  Apache|nginnx|IIS - Tomcat|JBoss - MYSQL/MariaDB/PostgreSQL

[보안]
	* 웹 방화벽 (WAF)
		* modsecurity
		# yum install mod_security
		# yum install mod_security_crs
		# systemctl restart httpd
	* 웹 취약점 무료 점검 서비스
	
[참고] Apache - Tomcat 왜 연동하는가?
	(ㄱ) 부하 분산
	(ㄴ) 클러스터(세션 클러스터) - 장애처리
	(ㄷ) 아파치 웹서버의 보안 기능 및 추가 기능 사용



-------------------[참고] 클라이언트 쪽에서 확인 방법 --------------------
	# ping 192.168.10.30 -c 1			-> server2 alive 확인
	# nmap -p 80,443 192.168.10.30		-> server2 firewall 설정
	# firefox http://192.168.10.30	-> httpd.service 기동/설정
	# curl http://www.example.com	-> dns 설정
------------------------------------------------------------------

아파치 HTTP 웹서버 설정 및 변경과 NGINX 설정 및 구성 
https://access.redhat.com/documentation/en-us/red_hat_enterprise_linux/8/html/deploying_different_types_of_servers/setting-apache-http-server_deploying-different-types-of-servers

**********************************
----------6장 FTP Server----------
**********************************
-----------------------------------------------------------------------
	■ 프로그램: vsftpd, ftp
	■ 데몬 & 포트 & 프로토콜: /usr/sbin/vsftpd, 21/tcp, 20/tcp, 1024/tcp 이상
	■ 주 설정 파일: /etc/vsftpd/vsftpd.conf
	■ 하위 설정 파일: /etc/vsftpd/{user_list, ftpusers}
	■ 서비스: vsftpd.service
-----------------------------------------------------------------------

■ vsftpd 관련 파일들

파일 종류	설명
/etc/vsftpd/vsftpd.conf	= vsftpd 프로그램의 주 설정 파일
/etc/vsftpd/ftpusers	= vsftpd 서버에 접속할 수 없는 사용자 정의
/etc/vsftpd/user_list	= vsftpd 서버에 접속할 수 없는 사용자 정의
/var/ftp				= Anonymous FTP 사용자를 위한 디렉토리

--------------ftp 서버구성절차--------------------------
1. 패키지 설치
	# yum install vsftpd ftp
2. 서비스 구성
	# vi /etc/vsftpd/vsftpd/conf
	# vi /etc/vsftpd/(ftpusers,user_list)
	# echo 'MyServer' > /var/www/html/index.html
3.서비스 기동
	#systemctl enable --now vsftpd.service
4. 방화벽 등록
	# firewall-cmd --permanent --add-service=ftp
	# fwreload
----------------------------------------------------
[실습] 초기 ftp 서버 설정 점검
[실습] vsftpd FTP server 구축
[실습] ftp 서버 사용자 접근 제어
	*/etc/vsftpd/{ftpusers,user_list}
[실습] 클라이언트 프로그램
[실습] 세션 타임 아웃 설정
	* idle_session_timeout=9000
	* data_connection_timeout=9000
[실습] 일반 사용자 chroot 구성
	* chroot_local_user=YES
	* allow_writeable_chroot=YES
	* chroot_list_enable=YES
	* chroot_list_file=/etc/vsfrpd/chroot list
	* echo 'root' >> /etc/vsfrpd/chroot list
[실습] 익명 ftx enable=YES
	anonymos enable=YES
	
[실습] 익명 ftp 업로드 기능 설정
	* /var/ftp/pub/incoming(603)
	3  --- 졸아서 이 부분 필기 못함---
	
[보안] FTP 보안
	* 접근 제어
		* 호스트 접근 제어 -> firewalld
		* 사용자 접근 제어 -> /etc/vsfrpd/{user_list. ftpusers}
			*userlist_deny=NO, /etc/vsfrpd/user_list
	* 자원 제어
		* max_clients, max_per_ip
		* idle_session_timeout , data_connection_timeout
	* 패키지 업데이트/패치
		* yum update vsfrpd
	* chroot 구성
	* ftp -> sftp/ftps
	* ftp 포트
----------------------------------------------------

* ftp 포트
	-active mode				
	-Passive Mode
* ftp 로그
	확인 명령어: tail -f /var/log/xferlog -다운로드에 대해
			  tail -f /var/log/secure - 인증에 대해
			  

**********************************
----------7장 Mail Server----------
**********************************

* 용어:
	* MTA , MUA
	* SMTP/ESMTP(메일 보낼때) / POP3, IMAP4 (메일 받을때)
-----------------------------------------------------------------------
MAIL(sendmail) Server
	■ 패키지: sendmail
	■ 데몬 & 포트 & 프로토콜: /usr/sbin/sendmail, 25/tcp, 465/tcp
	■ 주 설정 파일: /etc/mail/sendmail.cf
	■ 서브 설정 파일: /etc/mail/*, /etc/aliases
	■ 서비스: sendmail.service

	POP3/IMAP4(dovecot) Server
 	■ 패키지: dovecot
	■ 데몬 & 포트 & 프로토콜: /usr/sbin/dovecot, 110/tcp, 143/tcp, 995/tcp, 993/tcp
	■ 설정 파일: /etc/dovecot/dovecot.conf
	■ 스크립트: dovecot.service


--------------POP3/IMAP(postfix) Mail(sendmail) 서버구성절차--------------------------
------Mail(sendmail)------
1. 패키지 설치
	# yum install sendmail mailx
2. 서비스 구성
	# vi /etc/mail/sendmail.cf
	# vi /etc/mail/*
3.서비스 기동
	#systemctl enable --now sendmail.service
4. 방화벽 등록
	# firewall-cmd --permanent --add-service={smtp,smtps}
	# fwreload
	
---POP3/IMAP(postfix)------
1. 패키지 설치
	# yum install sendmail dovecot
2. 서비스 구성
	# vi /etc/dovecot.conf
	# vi /etc/dovecot/conf.t
3.서비스 기동
	#systemctl enable --now dovecot
4. 방화벽 등록
	# firewall-cmd --permanent --add-service={pop3,pop3s,imap,imaps}
	# fwreload
----------------------------------------------------
[실습] 초기 mail (sendmail) 서버 설정 점검
[실습] 초기 POP3/IMAP(dovecot) 서버 설정 점검	  


(1) (main) example.com 메일 클라이언트 프로그램(EX: evolution 사용)
• 192.168.10.10에서 설정한다.
• (주의) root 사용자로 테스트 하지 않고, 일반 사용자(EX: user01)로 테스트 한다.
-> Evolution 프로그램을 통해 설정한다.

① 프로그램 설치
# yum install evolution

② 프로그램 실행
Linux Pannel > Application > Office > Email 
or
# export LANG=ko_KR.UTF-8 
# evolution & 

③ evolution 설정 작업 (GUI)
--------------------------------------------------
Evolution Setup Assistant user01 사용자 설정 방법
--------------------------------------------------
■ Welcome 화면
   -> Next 
■ Restore from backup 화면
   -> Next 
■ Identity 화면
   -> Required Information
      Full Name : user01 
      Email Address : user01@example.com 
   -> Next 
■ Receiving Email 화면
   -> Server Type: POP
   -> Configuration
      Server: mail.example.com
      Username: user01
   -> Next 
■ Receiving Options 화면
   -> Next 
■ Sending Email 화면
   -> Server Type: SMTP
   -> Server : mail.example.com 
   -> Next 
■ Account Summary 화면
   -> Next 
■ Done 화면
   -> Apply


에볼루션(evolution) > 편집(Edit) > 기본 설정(Preferences) > 메일 계정(Mail Account)
	사용자 순서 변경: 
		[v] user01@example.com [v]기본값
		[v] 이 컴퓨터
		[v] 검색폴더
		
[실습] Squirrelmail (다람쥐 메일)
	웹서버의 형식으로 메일을 보내고 받을 수 있게 보여주는것이지 직접 동작하는것이 아니다.
	
* [실습x] Anti-SPAM(spamassessin)
* [실습x] Anti-Virus

파일 바이러스 확인: https://www.virustotal.com/gui/home/upload


**********************************
----------8장 NFS Service----------
**********************************

--------------------------------------------------------------------
NFS 버전: NFSnv, NFSv4(4/0, 4.2)
NFS 데몬: nfs, mountd
NFS 파일: (server) /etc/exports / (client) /etc/fatab
NFS 명령 (server) exportfs CMD / (Client)showmount ,CMD mount CMD

-------------------NFS V4 server--------------------------------------
	■ 프로그램: nfs-utils
	■ 데몬 & 포트 & 프로토콜:nfs(2049/tcp)
	■ 주 설정 파일: /etc/exports
	■ 하위 설정 파일: /etc/exports.d/*.exports
	■ 서비스: nfs-server.service
-----------------------------------------------------------------------
-NFS server
1. 패키지 설치
	# yum install nfs-utils
2. 서비스 구성
	# vi /etc/exports
	# vi /etc/exports.d/*.exportfs
3.서비스 기동
	#systemctl enable --now nfs-server
4. 방화벽 등록
	# firewall-cmd --permanent --add-service={nfs,rpc-bind,mountd}
	# fwreload
-----------------------------------------------------------------------
[실습] 초기 NFS 서버 설정 점검
[실습] 
-----------------------------------------------------------------------
	




**********************************
-------9장 SMB/CIFS Server------
**********************************

* CIFS = SMB + NetBIOS
* SMB 관련 명령: (Server) (Client) SMB client CMD
--------------------------------------------------------------------
■ 프로그램: samba, samba-clinet, cifs-utils
■ 데몬 & 포트 : smbd(139/tcp, 445/tcp), nmbd(137/udp, 138/udp)
■ 주 설정 파일: /etc/samba/smb.conf
■ 서비스: smb.service, nmb.service, winbind.service
-----------------------------------------------------------------------
-samba 서버 구성 절차
1. 패키지 설치
	# yum install samba samba-client cifs-utils
2. 서비스 구성
	# vi /etc/samba/smb.conf
3.서비스 기동
	#systemctl enable --now smb nmb
4. 방화벽 등록
	# firewall-cmd --permanent --add-service=samba
	# fwreload
-----------------------------------------------------------------------
# testparm = 삼바의 conf 설정파일을 보여준다 (/etc/smb/smb.conf)
	# testparm -v = 좀 더 자세히 출력! 기본값을 확인 할 때 사용한다.   
		# testparm -s -v = -s는 중간에 엔터를 치는 과정을 생략함! 주로 이거 씀!!
		# testparm -sv | sed '/homes/,$d'
		# testparm -sv | sed '/homes/,$d'| grep -i 'read only'
• valid users = 공유디렉토리에 접근 할 수 있는 사용자 목록
• write list  = 공유 디렉토리에 rw 권한이 가능한 사용자 목록

# mount.cifs 
# umount.cifs 

----------------------smb 사용자 만들기---------------------------
	# useradd -M -s /sbin/nologin smbuser1 
	# useradd -M -s /sbin/nolgoin smbuser2 

	(SMB 사용자 추가/삭제)  # smbpasswd -a|-x smbuser1
	(SMB 사용자 활성/비활성)# smbpasswd -e|-d smbuser1
--------------------리눅스에서 윈도우로 파일 공유 확인----------------------------
(두번째 방법) 바탕화면에서 확인하기
-> "root's Home" 아이콘 더블클릭
-> 새로 뜬 'root' 창에서 'Other Locations' 부분 선택
-> "Connect to Server" 부분의 'Enter server address...' 다음을 입력
	smb://192.168.10.202/
-> 공유된 자원이 보일것이다.
   공유된 자원 중 samba_share 선택하고 우클릭 하고 mount 선택

[정리]
(ㄱ)	리눅스 공유(/samba) ------mount------ 윈도우 마운트
*임시마운트: 
		<win + E> 파일 탐색기 열어서 위 주소창에 \\상대주소 를 입력하면 접속 됨.
		ㄴ 이는 재부팅 하면 날라가는 임시적인 방편
		*영구마운트:
		상대 주소로 접속하여 공유 폴더를 우클릭 하여 네트워크 파일 공유를 선택해준다

(ㄴ)	윈도우 공유(/samba) ------mount------ 리눅스 마운트
	*임시마운트: 
	
# smbclient //192.168.10.20/share –U smbuser1
Or	
# mount –p /mnt/server ; mount.cifs //상대주소/share /mnt/server –o user=soldesk

		*영구마운트:
		# mkdir –p /mnt/share
		# vi /etc/fstab
		# //192.168.10.202/samba_share     /mnt/server     cifs    credentials=/root/cred  0  0
		# mount a
		
② 그룹 추가 및 공유 디렉토리 설정
# groupadd -r marketing 

# mkdir -p /smbshare
# chgrp marketing /smbshare
# chmod 2775 /smbshare

# ls -ld /smbshare

(선행 작업)
① 패키지 설치
# yum install samba-client cifs-utils

&& smbclient -L 192.168.10.20 -U smbuser4 
	ㄴ 마운트 확인! Test1이 있어야한다!
----------------------------------------------------	
[실습] 초기 smb/cifs 서버 설정 점검
[실습] 리눅스 공유 서버에 윈도우 클라이언트 접근
[실습] 윈도우 공유서버에 리눅스 클라이언트 접근
[실습] 리눅스 공유 서버에 리눅스 클라이언트 접근
----------------------------------------------------

**********************************
-------10장 Log server------
**********************************

-------------------------------------------------------------------
* 자원 / 로그 모니터링
* 시스템 기본 로그 파일들
	* OS 기록: /var/log/messages 
			  /var/log/secure, 
			  /var/log/boot.log
			  /var/log/{wtmp,btmp}
	* 서비스 기록 :
		dns	  /var/log/messages
		web	  /var/log/httpd/*
		ftp	  /var/log/xferlog
		
* rsyslog 체계 (/etc/rsyslog.conf) - 리눅스가 기록을 남기는 체계

--------------------------------------------------------------------
-Log server
■ rsyslog 서버에 대해서
● 패키지: rsyslog
● 데몬 & 포트 & 프로토콜: rsyslogd(514/tcp, 514/udp)
● 주 설정 파일: /etc/rsyslog.conf
● 부 설정 파일: /etc/rsyslog.d/*.conf
● 서비스: rsyslog.service
---------------------------------------------------------------------
-log server 서버 구성 절차
1. 패키지 설치
	# yum install rsyslog
2. 서비스 구성
	# vi /etc/rsyslog.conf
	# vi /etc/rsyslog.d/*.conf
3.서비스 기동
	#systemctl enable --now rsyslog
4. 방화벽 등록
	# firewall-cmd --permanent --add-port={514/tcp,514/udp}
	# firewall-cmd --permanent --add-service=syslog-tls
	# fwreload
--------------------------------------------------------------------
[실습] 초기 로그 서버 설정 점검
[실습] 기본 로그 파일(인증로그 기록, /var/log/secure)
[실습] 기본 로그 파일(메일로그 기록, /var/log/maillog)
[실습] 기본 로그 파일(스케줄러 기록, /var/log/cron)
[실습] 새로운 로그 파일(/var/log/file.log)
	* 쉘 스크립트를 사용한 로그 생성
	* rsyslog 체계를 사용한 로그 생성 (logger CMD)
[실습] 로그 서버 구축 1/2
[실습] visutl syslog 서버 설치
[실습] evenrlog-to-syslog 설치
[실습] graylog server 설치
	* graylog server 
	* Elasticsearch
	* mongoDB
[실습] 로그 파일 관리
	* OS 기록 (로그 파일이름이 고정되어 있는 경우) -> logrotate
	* 서비스 기록 (로그 파일이름이 고정되어 있지 않은 경우) -> find + crontab
[실습] 로그 파일 분석	
	* 메세지의 난이도 별로 확인이 가능하다.
	ㄴ cat file.log | egrep -i '(warn|error|fail|crit|alert|emerg)
	* 메시지 시간 ( cat file.log | egrep 'Feb 21 1[0-2]:')
	* 메시지 생성 주체
	* 메시지 생성 서버
	* 단어 검사
	....
[실습] system journal
	/etc/systemd/journald.conf
	-> /run/log/journal
	-> /var/log/journal
	journalctl CMD
		# journalctl -p warning
		# journalctl --since ... until ...
		# journalctl -u named -f
		# journalctl -o verbose
	* 저널 영구 저장 설정
		# vi /etc/systemd/journal.conf
		Storage=p
--------------------------------------------------------------




---------------------------------------------------------------------
29페이지 하다 맘
Enter Password: admin
8c6976e5b5410415bde908bd4dee15dfb167a9c873fc4bb8a81f6f2ab448a918

[root@main ~]# pwgen -N 1 -s 96
5OPoSXI9YoyzGWAez7kXa4ud3uKPpFAhWQa9e2jmLY8qnlSS8qtC4V4ENcJNo3looiaLFAPfwakvz4xmeBIJt9PWq4uR3sAX
-------------------------------------------------------------------------



**********************************
-------11장 DHCP Server------
**********************************

---------------------------------------------------------------------
dhcp 동작 원리: DORA (Discover , offer , request, ack)
--------------------------------------------------------------------
DHCP Server
● 패키지: dhcp-server , dhcp-client
● 데몬 & 포트 & 프로토콜: dhcpd(67/udp)
● 주 설정 파일: /etc/dhcp/dhcpd.conf
● 서비스: dhcpd.service
------------------------------------------------------------------------------------------------------------------------------------------
-dhcp server 서버 구성 절차
1. 패키지 설치
	# yum -y install dhcp-server dhcp-client
2. 서비스 구성
	# vi /etc/dhcpd.conf
3.서비스 기동
	#systemctl enable --now dhcpd
4. 방화벽 등록
	# firewall-cmd --permanent --add-port={dhcp,dhcp-client,dhcpv6}
	# fwreload
--------------------------------------------------------------------
[실습] 초기 서버 설정 점검
[실습] DHCP 서버 구성
[실습] DHCP 클라이언트 리눅스 (동적 ip)
[실습] DHCP 클라이언트 윈도우 (동적 ip)
[실습] DHCP 클라이언트 리눅스 (고정 ip)

**********************************
-------12장 OpenSSH Server------
**********************************

--------------------------------------------------------------------
SSH Server
■ 프로그램: openssh, openssh-clients, openssh-askpass, openssh-server 
■ 데몬 & 포트 & 프로토콜: sshd(22/tcp)
■ 주설정 파일: /etc/ssh/sshd_config(sshd), /etc/ssh/ssh_config(ssh CMD)
■ 서비스: sshd.service 
■ sshd(22) : ssh/scp/sftp
------------------------------------------------------------------------------------------------------------------------------------------
-dhcp server 서버 구성 절차
1. 패키지 설치
	# yum -y install openssh openssh-server
2. 서비스 구성
	# vi /etc/sshd_config
3.서비스 기동
	#systemctl enable --now sshd.service
4. 방화벽 등록
	# firewall-cmd --permanent --add-port=ssh
	# fwreload
--------------------------------------------------------------------

[실습] root 사용자에 대한 password authentication
	* /etc/ssh/sshd_config
	-permitRootLogin yes
	-passwordAuthentication yes
[실습] 


누락


**********************************
-------13장 OpenSSH Server------
**********************************

--------------------------------------------------------------------
NTP Server
● 패키지: chrony
● 데몬 & 포트 & 프로토콜: chronyd(123/udp)
● 주설정 파일: /etc/chrony.conf
● 서비스: chronyd.service
------------------------------------------------------------------------------------------------------------------------------------------
-dhcp server 서버 구성 절차
1. 패키지 설치
	# yum -y install chrony
2. 서비스 구성
	# vi /etc/chrony.conf
3.서비스 기동
	#systemctl enable --now chronyd.service
4. 방화벽 등록
	# firewall-cmd --permanent --add-port=ntp
	# fwreload
--------------------------------------------------------------------
[실습] 초기 서버 설정 점검
[실습] NTP 서버 구성 - main
[실습] NTP 클라이언트 구성 -server1
[실습] NTP 클라이언트 구성 -server2
[실습] 시간 동기화 실습
--------------------------------------------------------------------




**********************************
-------14장 MariaDB 데이터베이스------
**********************************

--------------------------------------------------------------------
MariaDB Server
● 패키지: mariaDB, mariaDB-server
● 데몬 & 포트 & 프로토콜: mtsqld(3306/tcp)
● 주설정 파일: /etc/my.cnf
● 서브 설정 파일: /etc/my.cnf.d/*.cnf
● 서비스: mariadb.service
------------------------------------------------------------------------------------------------------------------------------------------
-dhcp server 서버 구성 절차
1. 패키지 설치
	# yum install mariadb-server mariadb
2. 서비스 구성
	# vi /etc/my.cnf
3.서비스 기동
	#systemctl enable --now mariadb.service
4. 방화벽 등록
	# firewall-cmd --permanent --add-service=mysql
	# fwreload
5. 초기 보안 설정
	# mysql_secure_installation
	# mysql -u root -p
6. SELinux(?)
--------------------------------------------------------------------
[실습] 초기 서버 설정 점검
[실습] DB 관리
[실습] Table 관리
[실습] DB TABLE 관리
---------------------------------------------------------------------


**********************************
----ISCSI Target/Initiator-------
**********************************
-------------------------용어 정의----------------------------
● (질문1) 개별 iSCSI 대상(target) 및 이니시에이터(initiator)를 
         식별하기 위한 고유한 이름은 무엇인가? IQN

● (질문2) 개별 파이버 채널(Fibre Channel) 포트 및 노드를 
         식별하기 위한 고유한 번호는 무엇인가? WWN

● (질문3) iSCSI 서버의 스토리지 리소스는 무엇인가? 타겟

● (질문4) iSCSI 서버의 스토리지 리소스 블록 장치는 무엇인가? LUN

● (질문5) 소프트웨어 또는 하드웨어에 구현된 iSCSI 클라이언트는 무엇인가? Initiator

● (질문6) 단일 iSCSI 이니시에이터 또는 대상은 무엇인가? node

● (질문7) 이니시에이터와 대상의 단일 IP 연결 주소는 무엇인가? 포탈
-------------------------------------------------------------
ISCSI Target
● 패키지: targetcli
● 데몬 & 포트: iscsid(3260/tcp)
● 주설정 파일: /etc/target/saveconfig.json
● 서브 설정 파일: /etc/iscsi/initiatorname.iscsi (이니시에이터의 이름들)
● 서비스: target.service

ISCSI Initiator
● 패키지: iscsi-initiator-utils
● 데몬 & 포트: iscsid
● 주설정 파일: /etc/iscsi/iscsi.conf
● 서브 설정 파일: /etc/iscsi/initiatorname.iscsi (이니시에이터의 이름들)
● 서비스: iscsid.service
-------------------------------------------------------------
**ISCSI Target Configuration

-ISCSI Targe 서버 구성 절차
1. 패키지 설치
	# yum install targetcli
2.서비스 기동
	#systemctl enable --now targetcli.service
3. 서비스 구성
    자원생성
	#targetcli
	>exit
4. 방화벽 등록
	# firewall-cmd --permanent --add-service=iscsi-target
	# fwreload
5. SELinux(?)

**ISCSI Initiator Configuration

-ISCSI Initiator 서버 구성 절차
1. 패키지 설치
	# yum install iscsi-initiator-utils
2.서비스 기동
	# vi /etc/iscsi/initiatorname.iscsi
	# systemctl enable --now iscsid.service
3. 검색
	# iscsiadm -m discovery -t st -p 192.168.10.20
4. 로그인
	# iscsiadm -m node -T IQN -p PORTAL -l
5. 작업
	# lsblk
	적당한 작업
6. SELinux(?)
---------------------------------------------------------------
-targetcli을 통한 마운트 구성 구조
/dev/sdf
파티션
파일시스템
마운트

/dev/sdg, /dev/sdh
파티션
PV->VG->LV
파일시스템
마운트


-------쉘스크립트 실습환경 구축----------


**********************************
---------배시 쉘 프로그래밍-----------
**********************************

1) 선수 지식

2) 명령어
	grep CMD
		# grep OPTIONS PARRERNS file1
		OPTIONS: -i, -v ,-l , -n, -r, -w
		PARRERNS: * . ^root root$ [abc] ....
	sed CMD
		p cmd) # sed -n '1,3p' /etc/host
		d cmd) # sed ;'1,3d' /etc/host
		s cmd) # sed -i '/main/s/192.168.10.10/192.168.10.20/' /etc/host
		
	awk CMD
		# awk 'statement {action}' 파일이름
		# awk -F: '$3 >= 1000 && $3 <= 60000 {print $1}' /etc/passwd
		# df -h / | tail -1 | awk '{print $6}' | awk -F% '{print $1}'
		# ifconfig eth0 | grep inet | grep -v inet6 | awk '{print $2}' | awk -F: '{print $2}'
		# ps -elf | awk '$2 == "Z" {print $0}'	
	+
	CMD(cut cmd ...)
	정열(sort)
	정열 - 중복된것을 하나로만 표시
		# sort -u file1  
	정열 - 중복되는 것만 표시
		# sort file1 | uniq -d 
	정열 - 중복되 않는것만 표시
		# sort file1 | uniq -u
		
	cut 명령어 - 필드를 잘라내는 역할로 많이 사용
		# cut -c1-5 /etc/hosts - 문서 각 줄의 앞 1~5자리만 표현
		# cat /etc/hosts | tr '[a-z]' '[A-Z]'
			ㄴ 소문자를 대문자로 바꿔서 출력
		# cat /etc/hosts | egrep -v '(^$|^#)' | cut -f 1 
		# cut -d ":" -f 1 /etc/passwd 		(# awk -F: '{print $1}' /etc/passwd)
		# ifconfig eth0 | grep 'inet addr:' | awk '{print $2}' | cut -d":" -f2 
		
	paste 명령어 - 다수의 파일을 한번에 볼때 옆으로 정렬해서 출력
		# paste file1 file2  
		
	wc 명령어
		# wc /etc/passwd

3) 쉘의 특성
	● 리다이렉션(Redirection) 		: <  <<  >  >>  2>  2>>
		# cat < /etc/passwd - 내용을 출력
		# cat > file1 - 파일의 내용을 직접 입력하여 생성 (마지막 ctl+d)
		
	● 파이프(pipe)            		: |
		파이프 명령어 형식
		# CMD | more
		# CMD | grep rsyslogd
		# CMD | CMD
	● 셀 자체의 기능(bash function)  	: set -o vi
	● 변수(Variable)                 	: export VAR=5
		변수의 종류
		- 지역변수(# VAR=5)
		- 환경변수(# export VAR=5)
		- 특수변수($$, $?, $!, $*, $1, $2, ....)
		
		변수 선언 방법(env/set)
		(선언) # VAR=5     (# export VAR=hello)
			 # export VAR 
		(확인) # echo $VAR (# printf $VAR)
			
		$$ : 현재 쉘의 PID 번호 저장(EX: 임시 파일 생성, /tmp/.tmp.$$)
		$! : 바로 이전 수행된 백그라운드 프로세스의 PID 번호 저장
		$? : 바로 이전 수행된 명령어의 return value 저장(0 ~ 255)
		$* : 모든 인자($* == $@)
		$# : 인자의 개수
		$0 : 프로그램 이름
		$1 : 프로그램에 대한 첫번째 인자
		$2 : 프로그램에 대한 두번째 인자
		$3 : 프로그램에 대한 세번째 인자
			(해제) # unset VAR 
	● 함수 - alias와 같이 선언하여 명령어 처럼 사용함!
	(선언) # a() { ls; date; cal; }   or   function a { ls; date; cal; }
	(실행) # a 
	(확인) # typeset -f 
	(해제) # unset -f a 
	[참고] CMD -> alias -> function -> script
	● 그룹화(Grouping) 
		( ls ; pwd ; date ) > outputfile 
	● 조건 연산자 ( && , || )
	● 메타캐릭터(Metacharacter)		: ''  ""  ``  ;
	● 히스토리(History)				: history	
	● 환경파일(Environment Files)		: /etc/profile, ~/.bash_profile, ~/.bashrc

5) 쉘 스크립트 작성

	1. 프로그램 작성과 실행
		# bash -x script.sh
		# . ~/.bashrc
		# vi script.sh ' chmod +x script.sh ; ./script.sh
		
	2. 주석관리
		* 한줄 처리 - #
		* 여러 줄 처리 - : << EOF ~ EOF
	3. 입력과 출력
		출력 : echo CMD, printf CMD
		입력 : read CMD
		
#!/bin/bash

#svc.sh start sshd
# -> systemctl enable sshd
# -> systemctl restart sshd
# -> systemctl status sshd

#svc.sh stop sshd
# -> systemctl disable sshd
# -> systemctl stop sshd
# -> systemctl status sshd


-------------continue를 사용하여 문제를 확인하는 예제----------------

#!/bin/bash

egrep -i '(warn|fail|error|crit|alert|emerg)' /var/log/messages > /tmp/.tmp1
ㄴ 안좋은 단어를 검색함 (30초 전 파일)

while true - 참일때
do
    sleep 30 - 30초 쉬고
    egrep -i '(warn|fail|error|crit|alert|emerg)' /var/log/messages > /tmp/.tmp2
		ㄴ 30초 뒤에 파일을 다시 검사하여 tmp1 과 2의 차이점을 비교함
	diff /tmp/.tmp1 /tmp/.tmp2 > /tmp/.tmp3 && continue
		ㄴ 결과값이 저장된 tmp 파일들을 서로 비교해 같으면 continue!
    mailx -s "[WARN] Log Mail Check" root < /tmp/.tmp3
		ㄴ 결과값이 달라 아래로 내려와서 관리자에게 메일을 보내게 함 
    egrep -i '(warn|error|crit|alert|emerg)' /var/log/messages > /tmp/.tmp1
		ㄴ 다시 반복해서 검사하여 내용을 tmp1에 넣음
done

(기능)
목적: 로그 파일을 모니터링 하는 프로그램 작성
기능: 
● 로그 파일의 추가된 내용을 확인
● 로그 파일의 추가된 내용이 존재한다면 메일로 전송(To: root)
● 이 프로그램은 종료되면 안된다.(EX: Daemon)
● 사용하는 명령어: egrep -i '(warn|fail|err|crit|alert|emerg)' /var/log/messages
● 30초에 한번씩 로그 파일의 내용에 추가된 내용을 확인한다.

* diff 명령어 사용: diff file1 file2 = 파일1과 파일2의 차이점 비교


---------------FTP 사용 예제------------------------
#!/bin/bash
HELP(){
cat << EOF
Commands may be abbreviated.  Commands are:

!		debug		mdir		sendport	site
$		dir		mget		put		size
account		disconnect	mkdir		pwd		status
append		exit		mls		quit		struct
EOF
}

ERROR(){
    [ "$CMD" ] && echo "[WARN]Invalid command"
}

while true
do
    echo -n "ftp> "
    read CMD
    case $CMD in
        'quit'|'bye') break ;;
        'help') HELP ;;
        *) ERROR ;;
    esac
-------------------------------------------------

*) IO 리다이렉션 자식 프로세스
	for LINE in $(cat file1)
	do
		echo $LINE
	done > file2
	----방법2(권장)---
	cat file1 | while read LINE
	do
		echo $LINE
	done > file2

*) 시그널 제어
	*시그널무시
	*시그널 받으면 개발자가 원하는 동작

*) 디버깅
	* bash -x script.sh
	* bash -xv script.sh
*) 옵션 처리
	getopts CMD + while CMD + case CMD
	(예) # ssh.sh -p 80 192.168.10.20
	while getopts p: options
	do
		case $options in
			p ) P_ACTION ;;
			\?) Usage    ;;
			* ) Usage    ;;
		esac
	done


-----------서버 체크 파일--------------------
#!/bin/bash
#   # ./check_service.sh 192.168.10.10 192.168.10.20
#   ------------------
#   192.168.10.10
#   ------------------
#   svc1    active
#   svc2    active
#
#   ------------------
#   192.168.10.20
#   ------------------
#   svc3    active
#   svc4    active
#   ....

if [ $# -ne 2 ] ; then
    echo "Usage: $0 <IP1> <IP2>"
    exit 1
fi
export FIRST_IP=$1
export SECOND_IP=$2
export BASEDIR=/root/bin

ServiceList() {
# input: str        # ServiceList main
# output: file      # ServiceList main -> main.txt
# functions:  
SERVER=$1   
ssh $SERVER systemctl -t service | sed -n '1,/^LOAD/p' \
                                 | sed '$d' \
                                 | awk '{print $1, $3}' > $BASEDIR/$SERVER.txt
}

ServiceList $FIRST_IP
ServiceList $SECOND_IP

FSERVER=$BASEDIR/$FIRST_IP.txt
SSERVER=$BASEDIR/$SECOND_IP.txt

cat << EOF
##############################
"$FIRST_IP"
##############################
$(diff $FSERVER $SSERVER | fgrep '<' | cut -c3-)

##############################
"$SECOND_IP"
##############################
$(diff $FSERVER $SSERVER | fgrep '>' | cut -c3-)

EOF

----vscode 자동으로 켜지도록 설정------
* crontab + vskill.sh

kill $(ps -ef | grep -w code \
         | grep -v 'grep --color' \
         | awk '{print $2}' \
         | sort \
         | head -1)
---------------------------------

fdisk -l | grep LVM | awk '{print $1}' > pv1.txt
pvs | tail -n +2 | awk '{print $1}' > pv2.txt

ENV1.sh : 환경설정
	* $HOME/.bashrc
ENV2.sh : 필요한 패키지 설치
	* 패키지 설치 (gcc, php, vscode)
ENV3.sh : 서버 세팅
	텔넷 서버 - telnet-server
	ftp 서버 - vsftpd ftp
	ssh 서버 - openssh-server openssh-clients openssh-clients
	nginx 웹 서버 - yum -y install nginx
				  echo "Nginx webserver > /usr/share/nginx/html/index.html
				  systemctl enable --now nginx.server


cat << EOF > /etc/yum.repos.d/vscode.repo
[code]
name=Visual Studio Code
baseurl=https://packages.microsoft.com/yumrepos/vscode
enabled=1
gpgcheck=1
gpgkey=https://packages.microsoft.com/keys/microsoft.asc" 
EOF

yum install code
sudo rpm --import https://packages.microsoft.com/keys/microsoft.asc

sudo sh -c 'echo -e "[code]\nname=Visual Studio Code\nbaseurl=https://packages.microsoft.com/yumrepos/vscode\nenabled=1\ngpgcheck=1\ngpgkey=https://packages.microsoft.com/keys/microsoft.asc" > /etc/yum.repos.d/vscode.repo'
yum install code

https://www.google.co.kr/chrome/thank-you.html?brand=YTUH&statcb=0&installdataindex=empty&defaultbrowser=0#

wget https://dl.google.com/linux/direct/google-chrome-stable_current_x86_64.rpm -O /root/bin/

yum localinstall google-chrome-stable_current_x86_64
      
      
      
      


  
  
  
  
