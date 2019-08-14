# 광복절 해커톤

**Link :  https://bit.ly/inlinesk***

[인라인스케이트팀 신청서](https://www.notion.so/a0a4d75318724fddad69056555f09ed2)

------

**팀명 : 인라인 스케이트**

**참가팀원 : 권대명, 임지훈, 박건호**

**주제 : Openwet 및 Suricata 오픈소스를 활용한 침입탐지/차단 시스템(NIDS/IPS)**

**프로젝트 목표 :**

- **나는 IDS/IPS의 사용법을 알고, In-line 방식의 네트워크 침입탐지/차단 시스템을 구축할 수 있다.**

- **나는 Suricata 오픈소스의 사용법을 알고 시스템, 네트워크 및 룰셋 설정방법 등을 자유롭게 구축할 수 있다.**

- **나는 Suricata의 로그를 이해하고 보안관제를 위한 모니터링 시스템을 만들 수 있다.**

  

### **Architecture**

![Untitled](https://user-images.githubusercontent.com/41619898/63038888-22b80780-befd-11e9-8d93-c1e4c36b9e7f.png)

------

### Ubuntu Firewall Down

```
sudo ufw disable
```

### Install Build Dependencies

```
sudo apt install subversion g++ zlib1g-dev build-essential git python
sudo apt install libncurses5-dev gawk gettext unzip file libssl-dev wget
```

### **OpenWrt Install**

```
mkdir openwrt
cd openwrt
git clone <https://git.openwrt.org/openwrt/openwrt.git>
git checkout openwrt-18.06
```

- error handling

  apt install gnutls-bin git config --global http.postBuffer 1048576000

  

# Suricata Install

- Install  Dependencies / MD5, GeoIP, Unix Socket ...

  - Suricata에서 필요한 라이브러리 패키지를 가진 repostory를 내려받아 설치.
  - 패킷 캡처를 위한 libpcap, libnet, pcre 등을 설치
  - MD5, GeoIP, Unix Socket 등 추가 기능의 라이브러리 설치
  - 패킷 캡처를 위한 Libcap-ng를 설치
  - JSON 포맷을 지원하기 위해 Jansson을 설치
  - HTML을 처리하기 위해 HTP 라이브러리를 설치
  - IPS 기능을 위해 NetFilter 라이브러리를 설치

- Install Suricata

  ```shell
  cd /tmp wget http://www.openinfosecfoundation.org/download/suricata-2.0.6.tar.gz tar -xvzf suricata-2.0.6.tar.gz cd suricata-2.0.6 ./configure --prefix=/usr/ --sysconfdir=/etc/ --localstatedir=/var/ \ --enable-unix-socket --enable-profiling --enable-geoip \ --with-libnss-libraries=/usr/lib64 --with-libnss-includes=/usr/include/nss3 \ --with-libnspr-libraries=/usr/lib64 --with-libnspr-includes=/usr/include/nspr4 make && make install && ldconfig make install-full
  ```

### Nginx Setting (In Server Computer)

```
sudo apt-get install nginx
ps -ef | grep nginx
# check master & worker node
systemctl status nginx
# check
systemctl start nginx
# restart
service nginx restart
```

# **Snorby** Install

```
sudo apt-get install gcc g++ build-essential libssl-dev libreadline6-dev zlib1g-dev linux-headers-generic libsqlite3-dev \\
libxslt-dev libxml2-dev imagemagick git-core libmysqlclient-dev mysql-server libmagickwand-dev default-jre ruby1.9.3
```

------

# Reference Sources

**Apache Install**

```
sudo su -
apt-get update
apt-get install apache2
systemctl status apache2

# 아파치 시작
apachectl start
httpd start

# 아파치 중지
apachectl stop
httpd stop

# 아파치 리스타트
apachectl restart
httpd restart
```

------

**OpenWrt 패키지 빌드 환경 세팅**

[**Ubuntu(우분투) PC에 OpenWRT 개발 환경(크로스 컴파일) 설치**](https://skylit.tistory.com/76)

[**OpenWrt 기본 방화벽 세팅](https://openwrt.org/ko/docs/guide-user/firewall_configuration) (Official Site)**

> **Suricata**

**Suricata Installation (Officail Site)**

[**Suricata 소개 및 설치 및 구성 활용 & 오픈스택 환경**](https://sola99.tistory.com/401?category=529639)

[**Suricata를 이용한 포트 미러링으로 오픈스택 IDS 테스트**](https://ryusstory.tistory.com/entry/suricata를-이용한-포트-미러링으로-오픈스택-IDS-테스트)

> **Snorby**

네트워크 보안 관제를 웹을 통해 쉽게 확인할수 있는 오픈소스

**Suricata, Snorby & Barnyard2 Set Up Guide**