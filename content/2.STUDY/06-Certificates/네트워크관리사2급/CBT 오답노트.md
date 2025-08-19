# TCP/IP
2025년 5월 25일 기출

TCP를 사용하는 프로토콜로 옳지 않은 것은?
1. FTP
2. TFTP ⇒ UDP
3. Telnet
4. SMTP


ICMP의 Message Type에 대한 설명으로 옳지 않은 것은?
1. 0 - Echo Reply
2. 5 - Echo Request ⇒ 8이 Echo Request, 5는 Redirection
3. 13 - Timestamp Request
4. 17 - Address Mask Request


다음 중 IP 프로토콜의 역할로 올바른 것은?
1. 호스트 간 패킷 전달의 신뢰성을 보장한다.
2. 손실된 패킷의 재전송을 요청할 수 있다.
3. 호스트 간에 패킷 교환에서 흐름 제어를 할 수 있다.
4. MTU(Maximum Transmission Unit) 값보다 큰 Datagram은 단편화(Fragmentation)를 수행한다. ⇒ IP 프로토콜의 특징 - 비신뢰성 & 비연결성(신뢰성 보장 X, 패킷 재전송 및 흐름제어 불가), 데이터그램 단편화하여 전송하는 기능은 수행


TCP/IP protocol stack에서 사용하는 Application 중에 연결 제어와 정보 전송용 포트를 구분하여 사용하는 것은?
1. DNS
2. SMTP
3. TFTP
4. FTP ⇒ 데이터 전송 연결(20)과 제어 연결(21) 구분하여 사용


다음 중 사설 IP 주소로 옳지 않은 것은?
1. 10.100.12.5 ⇒ A Class 사설 IP 주소(10.0.0.0 ~ 10.255.255.255)
2. 128.52.10.6
3. 172.25.30.5 ⇒ B Class 사설 IP 주소(172.16.0.0 ~ 172.31.255.255)
4. 192.168.200.128 ⇒ C Class 사설 IP 주소(192.168.0.0 ~ 192.168.255.255)

---

2025년 2월 23일 기출

IP Address 중 Class가 다른 주소는?
1. 191.234.149.32 ⇒ 128.0.0.0 ~ 191.255.255.255 사이이므로 B Class
2. 198.236.115.33 ⇒ 192.0.0.0 ~ 223.255.255.255 사이이므로 C Class
3. 222.236.138.34 ⇒ 192.0.0.0 ~ 223.255.255.255 사이이므로 C Class
4. 195.236.126.35 ⇒ 192.0.0.0 ~ 223.255.255.255 사이이므로 C Class


OSI 7계층의 통신 계층별 PDU(Protocol Data Unit)의 명칭으로 올바른 것은?
1. 7계층: 세그먼트 ⇒ 7계층: X
2. 4계층: 패킷 ⇒ 4계층: 세그먼트
3. 3계층: 비트 ⇒ 3계층: 패킷
4. 2계층: 프레임


SNMP에 대한 설명으로 옳지 않은 것은?
1. TCP를 이용하여 신뢰성 있는 통신을 한다. ⇒ UDP 사용
2. 네트워크 관리를 위한 표준 프로토콜이다. ⇒ SNMP(Simple **Network Management** Protocol)
3. 응용 계층 프로토콜이다.
4. RFC 1157에 규정되어 있다.


ARP(Address Resolution Protocol)에 대한 설명 중 올바른 것은?
1. 수신측의 논리주소 정보가 없기 때문에 브로드캐스트를 통해 전송한다. ⇒ 수신측의 물리주소(MAC)를 모르기 때문에 알고 있는 논리주소(IP)를 기반으로 브로드캐스트 하는 것
2. 수신측 물리주소와 송신측 물리주소를 검사하여 자신에 대해 물리주소를 요구하는 경우라면 ARP를 전송한다. ⇒ ARP 응답(Reply) 하는 것
3. 각 시스템에 Address Resolution Protocol Cache가 있고 Cache 정보를 보관한다.
4. H/W 주소 기반으로 IP 주소로 변환한다. ⇒ RARP(MAC to IP)

# 네트워크 일반
2025년 5월 25일 기출

Multiplexing 방법 중에서 다중화 시 전송할 데이터가 없더라도 타임 슬롯이 할당되어 대역폭의 낭비를 가져오는 다중화 방식은?
1. TDM(Time Division Multiplexer) ⇒ 
2. STDM(Statistical Time Division Multiplexer)
3. FDM(Frequency Division Multiplexer)
4. FDMA(Frequency Division Multiple Access)


파장분할다중화방식(WDM)의 특징으로 옳은 것은?
1. 선로의 증설 없이 회선의 증설이 어렵다.
2. 광증폭기를 사용해 무중계 장거리 전송이 가능하다. ⇒ 
3. 광학적인 방법에 의해 신호를 시간축에서 다중화하는 방식이다.
4. 각각의 채널은 같은 전송 형식, 전송 속도, 프로토콜 형식을 가진다.


(A)안에 들어가는 용어 중 옳은 것은?

> 
> 지능형(스마트)홈  통신에 사용되는 ( A )은/는 10m 이내의 짧은 거리에 존재하는 컴퓨터와 주변 기기, 휴대폰, 가전제품 등을 무선으로 연결하여 이들 기기간의 통신을 지원함으로써 다양한 응용 서비스를 가능하도록 하는 네트워크 영역을 말하며, UWB, ZigBee, RFID, 블루투스 기술 등이 활용된다.
> 

1. WPAN ⇒ 단거리 통신에 사용되는 개인용 무선 네트워크(블루투스, ZigBee가 대표적), IoT 분야의 핵심 기술
2. LTE-M
3. NB-IoT
4. LAN

---

데이터 흐름 제어(Flow Control)과 관련 없는 것은?
1. Stop and Wait
2. XON/XOFF
3. Loop/Echo ⇒ 디버깅용 기술
4. Sliding Window


다음에서 설명하는 전송 방식은?

>
> LAN의 매체 접근 제어방식 중 버스구조에서 사용하고, 데이터를 전송하려면 채널이 사용 중인지 검사한 후 채널이 사용 중이지 않으면 모든 노드가 채널을 사용할 수 있으며, 동시에 데이터 전송이 이루어지면 충돌이 일어나고 데이터는 폐기되며 일정시간 대기 후 다시 전송한다.
> 

1. Token Ring ⇒ 충돌 X, 링 구조
2. Token Bus ⇒ 충돌 X
3. CSMA/CD
4. Slotted Ring ⇒ 시간 슬롯 기반으로 데이터 전송


다음의 (A)에 들어갈 알맞은 용어는?

> 
> ( A )는 고전적인 네트워크 기술 패러다임이 기지국 기반에서 블루투스와 같이 유연한 애드 혹(Ad hoc) 네트워크로 변화된다. 이러한 애드 혹(Ad hoc) 네트워크는 각각의 구성 장치들 간에 데이터 통신을 하는 주체가 되고, 같은 네트워크 안의 다른 장치들로부터 받은 트래픽을 다른 장치 시스템이다. ( A )의 출발은 미국 군사 기술을 민간용으로 전환한 것으로, ( A ) 기능을 탑재한 무선 LAN AP는 전원 연결만 되면 네트워킹이 가능하므로 설치가 편리하고, 유선망과의 연결 없이 망 확장이 용이하다.
> 

1. Wireless sensor networks
2. Wireless mesh networks ⇒ "무선(Wireless) LAN AP ~ , 유선망과의 연결 없이 망(mesh) 확장이 용이하다."
3. Software defined networks
4. Content delivery networks
# NOS
2025년 5월 25일 기출

Linux 디렉터리 구성에 대한 설명으로 옳지 않은 것은?
1. /tmp - 임시파일이 저장되는 디렉터리
2. /boot - 시스템이 부팅될 때 부팅 가능한 커널 이미지 파일을 담고 있는 디렉터리
3. /var - 시스템의 로그 파일과 메일이 저장되는 위치
4. /usr - 사용자 계정이 위치하는 파티션 위치 ⇒ /usr가 아닌 /home에 대한 설명


Linux 시스템에 새로운 사용자를 등록하려고 한다. 유저 이름은 'network'로 하고, 'icqa'라는 기본 그룹에 편입시키는 명령은?
1. useradd -g icqa network →
2. useradd -g network icqa
3. adduser -g network icqa
4. adduser -G icqa network


Linux 시스템에서 사용되고 있는 메모리 양과 사용 가능한 메모리 양, 공유 메모리와 가상 메모리에 대한 정보를 볼 수 있는 명령어는?
1. mem ⇒ 존재하지 않는 명령어
2. free
3. du ⇒ 디스크 사용량 확인(Disk Use)
4. cat ⇒ 파일 내용 출력()


서버 담당자 Park 사원은 Windows Server 2016에서 사용할 수 있는 네트워크 스토리지를 구현하고자 한다. 다음 조건에서 설명하는 방식의 네트워크 스토리지로 알맞은 것은?

> 
> <조건>
> - 공통으로 사용되는 저장소를 중앙에서 관리함으로써 각각의 컴퓨터에 저장소를 가지고 있을 때보다 여유 공간의 활용도가 높으며, 대규모 이상의 환경에서 주로 구성되고 있다.
> - 일반적으로 파이버 채널 연결을 이용하여 데이터 접근이 빠르며 대용량 블록 기반의 데이터 전송 기능으로 LAN에 독립적인 데이터 백업, 복구에 탁월한 기능이 있다.
>   

1. NAS(Network Attached Storage)
2. SAN(Storage Area Network) ⇒ 
3. RAID(Redundant Array of Inexpensive Disks)
4. SSD(Solid State Drive)


서버 담당자 Park 사원은 Windows Server 2016에서 가상화 운영을 위한 Hyper-V를 운영하고자 한다. 다음 지문 내용 중 (A)에 공통으로 들어갈 내용으로 올바른 것은?

>
> ( A )은/는 작은 운영체제를 포함하는 가상화 기술을 의미하며, Hyper-V 가상컴퓨터는 완전한 OS를 포함하는 독립된 컴퓨터로 간주된다. Hyper-V 가상머신은 상당히 무거운 반면에, ( A )은/는 가상컴퓨터와 거의 비슷한 기능을 하지만 훨씬 가볍게 생성하고 운영할 수 있다.
> 

1. Virtual Machine
2. Internet Information Services
3. Windows Containers
4. NanoServer


다음 중 Linux의 BIND 설치 및 운영 시 수행해야 할 업무로 적절하지 않은 것은?
1. 방화벽에서 UDP의 53번 포트만 열면 된다. ⇒ 방화벽에서 DNS 서비스를 위해 UDP와 TCP의 53번 포트를 모두 열어야 함
2. 방화벽 설정은 'iptables' 명령어를 통해 설정할 수 있다.
3. BIND 설치여부는 'rpm -qa | grep bind' 로 확인할 수 있다.
4. '/etc/named.conf' 파일의 오류를 체크하는 명령어는 'named-checkconf' 이다.

> [!info] BIND = Berkeley Internet Name Domain
인터넷에서 가장 널리 사용되는 DNS 서버 소프트웨어


서버 관리자 Lee 사원은 Windows Server 2016에서 DNS 서버를 설치 하던 중 다음과 같은 문제를 발견하였다. Lee 사원이 해당 문제를 해결하기 위한 방법으로 가장 적절하지 않은 것은?

> 역할 및 기능 추가 마법사
> 
> ⚠ 유효성 검사 결과
> 유효성 검사 프로세스 중에 기능을 설치할 서버에서 문제가 발견되었습니다. 문제를 무시하고 선택한 기능을 설치하려면 [계속]을 클릭하고, 다른 기능을 선택하려면 [취소]를 클릭하십시오.
> 
>> 유효성 검사 결과 - 서버
>> ⚠ WIN-B4QB4D4CAE4
>> 이 컴퓨터에서 고정 IP 주소를 찾을 수 없습니다. IP 주소가 변경되면 클라이언트가 이 서버에 연결하지 못할 수도 있습니다. DNS 서버를 설치하기 전에 이 컴퓨터에 고정 IP 주소를 구성하십시오.
>					[계속]    [취소]

1. 명령어 프롬프트 창에서 'ipconfig /renew'를 입력하였다. ⇒ /renew는 **동적 IP** 재할당. 정적 IP 주소 설정 필요한 상황에 부적절
2. IP 주소의 할당방식을 고정할당방식으로 변경한다.
3. 이더넷의 IP 속성에서 '다음 IP 주소 사용'을 선택하고 IP 주소를 입력하였다.
4. 이더넷의 IP 속서엥서 '다음 DNS 서버 주소 사용'을 선택하고 DNS 서버 주소를 입력하였다.


Linux Apache 웹서버 httpd.conf 설정값 중 Directory Indexing 공격에 취약할 수 있는 옵션은?
1. Options FollowSymLinks Indexes ⇒ 디렉터리 내에 인덱스 파일(index.html) 없을 경우 파일 목록 노출시켜 Directory **Indexing** 공격에 취약
2. Server Admin : root@localhost
3. DocumentRoot : '/var/www/html'
4. ServerRoot : '/etc/httpd'


찍어서 맞춘 문제들

Windows Server 2016 DHCP 서버의 주요 역할의 설명으로 맞는 것은?
1. 동적 콘텐츠의 HTTP 압축을 구성하는 인프라를 제공한다.
2. TCP/IP 네트워크에 대한 이름을 확인한다.
3. IP 자원의 효율적인 관리 및 IP 자동 할당한다. ⇒ 
4. 사설 IP 주소를 공인 IP 주소로 변환해 준다.
> [!info] DHCP
> Dynamic Host Configuration Protocol
> 네트워크에 연결된 장치에 IP 주소와 기타 네트워크 설정을 자동으로 할당하는 프로토콜


네트워크 담당자 Kim 사원은 Windows Server 2016에서 원격 액세스 서비스를 운용하고자 한다. Windows Server 2016 내에 있는 이 기능은 DirectAccess나 VPN과 달리 원격 컴퓨터를 네트워크에 연결하는 데 사용되지 않는다. 오히려 내부 웹 리소스를 인터넷에 게시하는 데 사용되는 이 기능은?
1. WAP(Web Application Proxy) ⇒ 
2. PPTP(Point-to-Point Tunneling Protocol)
3. L2TP(Layer 2 Tunneling Protocol)
4. SSTP(Secure Socket Tunneling Protocol)


다음 중 Linux 시스템에서 새로운 하드디스크를 추가하고 사용할 수 있도록 설정하는 과정과 관계가 가장 적은 것은?
1. fdisk
2. mkfs
3. mount
4. cal ⇒ 달력 출력하는 명령어


2025년 2월 23일 기출문제

Windows Server 2016에서 지원하는 Hyper-V에 대한 설명으로 옳지 않은 것은?
1. 하드웨어 사용률을 높여준다.
2. 서버 가용성이 줄어든다. ⇒ Hyper-V 사용시 서버 가용성은 늘어남
3. 유지비용을 줄일 수 있다.
4. 개발 및 테스트의 효율성을 향상시킨다.


다음 지문에서 설명하는 Linux 시스템의 구성요소로 옳은 것은?

> 
> 이것은 원격지에 존재하는 호스트 컴퓨터에 접속하기 위해 사용되는 응용프로그램 또는 프로토콜이다. Well-known port는 22번을 사용하며, FTP, Telnet 등에서 사용자의 입력 정보를 평문으로 전송하는 것을 보완하는 보안 프로토콜이다. 하지만 간혹 보안 이슈로 인하여 서버 관리자는 포트번호를 바꾸어 외부로부터의 공격을 차단한다.
> 

1. SSL(Secure Sockets Layer)
2. SSH(Secure Shell) ⇒ 
3. TLS(Transport Layer Security)
4. RDP(Remote Desktop Protocol)


다음 중 Linux 명령어에 대한 설명으로 옳지 않은 것은?
1. mkfs: 파일시스템 생성
2. du: 디스크 사용량 확인
3. mount: 외부장치 등을 디렉터리에 연결
4. fdisk: 파일시스템 점검 ⇒ fdisk는 파티셔닝 명령어. 물리 디스크에 논리 파티션을 생성함


찍어서 맞춘 문제들

Windows Server 2016의 IIS 기본 웹사이트 등록 정보의 필드에 대한 설명으로 옳지 않은 것은?
1. IP 주소: 사이트가 사용할 IP 주소를 기록하며, 한 컴퓨터에 2개 이상의 IP가 할당된 경우는 IP의 접속 순서를 지정
2. TCP 포트: 웹서버 시스템의 물리적인 시리얼 포트 번호를 지정 ⇒ TCP 포트는 논리적 포트 번호.
3. 연결 수 제한: 웹서버에 연결할 수 있는 연결 수 제한을 지정
4. 연결 시간 제한: 웹서버에 접속한 후 일정 시간 동안 움직임이 없으면 세션을 끊도록 지정


Linux에서 'manager'라는 파일을, 파일의 소유자가 아닌 사람도 볼 수는 있지만 수정을 못하도록 하는 명령어는?
1. chmod 777 manager
2. chmod 666 manager
3. chmod 646 manager
4. chmod 644 manager ⇒ 소유자 제외 읽기만 가능하려면 X44 형태여야함

세자리 숫자는 각각 소유자/그룹/사용자의 권한을 의미
각각 읽기(4) + 쓰기(2) + 실행(1) → 부여된 권한의 합으로 확인 가능
- 4: 읽기만 가능
- 6: 읽고 쓰기 가능
- 7: 읽고 쓰고 실행 가능(모든 권한)


다음은 Linux 시스템의 계정정보가 담긴 '/etc/passwd'의 내용이다. 다음의 설명 중 옳지 않은 것은?

`user1:x:500:500::/home/user1:/bin/bash`

1. 사용자 계정의 ID는 'user1' 이다.
2. 패스워드는 'x' 이다. ⇒ 암호필드가 'x'. 패스워드는 '/etc/shadow'에서 확인 가능
3. 사용자의 UID와 GID는 500번이다.
4. 사용자의 기본 Shell은 '/bin/bash' 이다.

> [!info] '/etc/passwd' 구조
> `사용자이름:암호필드:사용자ID(UID):그룹ID(GID):사용자정보필드:홈디렉토리:기본쉘`


네트워크관리사 Kim 사원이 Linux 서버(하드웨어)의 HDD 증설을 위해 서버를 종료하기로 하였다. 이에 Linux 서버를 종료하기 위한 명령어가 아닌 것은?
1. shutdown -h now
2. poweroff
3. init 6 ⇒ 재부팅 명령어
4. halt


네트워크관리사 Park 사원은 Windows Server 2016에서 Active Directory를 구성 중에 있다. 이때 한 도메인 안에서 세부적인 단위로 나누어 관리부, 회계부, 기술부 등의 부서로 구성하고자 한다. 서버 담당자가 설정해야 하는 항목은?
1. DC(Domain Controller)
2. RDC(Read Only Domain Controller)
3. OU(Organization Unit) ⇒
4. Site


Windows Server 2016에서 DHCP 구성에 대한 설명으로 올바른 것은?
1. DHCP에서 새 범위 구성 시 임대 기간은 일, 시간, 분, 초단위로 설정할 수 있다. ⇒ 임대 기간은 기본적으로 일, 시간 단위로 설정
2. DHCP에서 새 범위 구성 시 더 이상 WINS 서버를 구성하지 않는다. ⇒ 여전히 구성 가능. WINS는 과거의 기술로 현재는 많이 사용되지는 않지만 옵션 제거되지는 않았음
3. 새 예약 구성 시 지원되는 유형은 BOOTP 없이 DHCP만 가능하다. ⇒ BOOTP, DHCP 둘 중 하나/둘 다 지정 가능
4. DHCP 서버에서 주소를 분배할 때, 적용할 지연시간은 ms 단위로 지정한다.
# 네트워크 운용기기
2025년 5월 25일 기출

IP Address의 부족과 내부 네트워크 주소의 보안을 위해 사용하는 방법 중 하나로, 내부에서는 사설 IP Address를 사용하고 외부 네트워크로 나가는 주소는 공인 IP Address를 사용하도록 하는 IP Address 변환 방식은?
1. DHCP 방식
2. IPv6 방식
3. NAT 방식 ⇒ 내부 네트워크에서 사설 IP 주소 사용, 외부와 통신할 때는 공인 IP 주소로 변환
4. MAC Address 방식


웹 서버를 보호하는 전용 보안장비로 HTTP, HTTPS 처럼 웹서버에서 동작하는 웹 프로토콜의 공격을 방어하는데 사용되는 보안장비는?
1. IDS
2. IPS
3. Fire Wall
4. WAF ⇒ 


다음 ( )에 해당하는 용어는?

>
> VLAN이 강력한 이유는 스위치 단독으로 닫혀 있는 게 아니라 복수의 스위치에 걸쳐 광범위한 네트워크로 운용할 수 있기 때문이다. 스위치는 다른 스위치와 연결하기 위한 인터페이스로서 (     ) 인터페이스를 갖추고 있다.
> 

1. 포트(Port)
2. 트렁크(Trunk) ⇒ 
3. 소켓(Socket)
4. 플러그(Plug)

---

2025년 2월 23일 기출

무선랜(LAN)은 무선신호 전달방식을 이용하여 두 대 이상의 장치를 연결하는 기술이다. 이를 이용하여 사용자는 근거리 지역에서 이동하면서 지속적으로 네트워크에 접근할 수 있게 된다. 다음의 지문에서 설명하는 와이파이 IEEE 802.11규격은?

>
> - 미국 전기전자학회(IEEE)가 발표한 기술 규격으로 여섯 번째 표준이라는 의미로 '와이파이 6'이라 지칭한다.
> - 다양한 전파 환경에서 전송 효율을 향상시키기 위하여 다중 사용자 미모(MU-MIMO) 기술을 적용하였다.
> - 전송 효율을 높이기 위하여 최대 1024QAM 변조 방식까지 사용할 수 있다.
> - 무선 주파수의 포화 상태로 인한 통신 간섭 문제를 극복하기 위하여 등장한 확장 표준이며 비면허 주파수인 6GHz에서의 통신을 지원한다.
>   

1. IEEE 802.11n ⇒ Wi-Fi 4
2. IEEE 802.11ac ⇒ Wi-Fi 5
3. IEEE 802.11be ⇒ Wi-Fi 7
4. IEEE 802.11ax ⇒ Wi-Fi 6


찍어서 맞춘 문제들

L2 스위치에서 프레임을 전송 시 목적지의 어떤 주소를 확인 후 전송하는가?
1. IP 주소 ⇒ L3 스위치
2. Port 주소
3. MAC 주소 ⇒ L2 스위치
4. URL 주소