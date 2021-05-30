# 2021.05.30  CS

##### `CS 스터디 - 3차`

> 1) Encoding vs Decoding
>
> 2) HTTP vs HTTPS
>
> 3) `IP`

<br>

<br>

## IP

**인터넷 프로토콜(Internet Protocol) **

<br>

다른 컴퓨터와 통신할 때 사용

`nslookup`으로 자신의 IP주소 알 수 있음

![img](https://s3.us-west-2.amazonaws.com/secure.notion-static.com/55a64ccb-c724-437a-a76c-4b11ff4c1c17/Untitled.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Credential=AKIAT73L2G45O3KS52Y5%2F20210530%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20210530T161719Z&X-Amz-Expires=86400&X-Amz-Signature=e81348cfb73961130746e64e6127b453e5ad0afcf5ad08b4b425eac613661b4b&X-Amz-SignedHeaders=host&response-content-disposition=filename%20%3D%22Untitled.png%22)

흔히 사용하는 IP주소 체계 : **`IPv4`**

단점 : 오직 32비트만을 사용해 약 40억개의 IP주소를 가짐.  그래서 등장한 것이 **IPv6(대중화 되진 않음)**

<br>

## 공인 IP, 사설 IP, 고정 IP, 유동 IP

공인 IP: 세계에서 단 하나

사설 IP: 공유기를 이용해 만들 수 있는 가상의 IP주소

고정 IP: 해당 컴퓨터의 IP 주소를 고정적으로 사용

유동 IP: 수시로 변하는 IP 주소

서버역할을 하는 것은 보통은 공인 IP사용

유동 IP인 경우에도 서버 구축가능 → DDNS(Dynamic DNS): 사용자가 도메인 주소로 해당 서버에 접속할 때 DDNS를 통해 DNS 서버에게 자신의 바뀐 IP주소를 알려줌.

사설 IP 주소를 이용해 서버를 구축할 수 있음 → 포트포워딩 이용

<br>

## ISP(Internet Service Provider)

ex. KT

보통 ISP(KT)에서 유동 IP를 받아서 사용

<br>

##### `라우터 vs 스위치`

> 라우터를 통해서 IP를 전달하게 됨(예, 모뎀)
>
> 스위치에 있는 MAC 주소 테이블을 사용하여 프레임을 전달

<br>

## NAT

공유기가 하나의 공인 IP를 내부 사설 IP로 나누는 기술

사설 IP의 사용으로 내부망을 보호

**사설 IP 끼리 통신 어떻게???**

<br>



## 별첨

IPv4 대중화 (IPv6까지 필요없어서)

공인 ip : 세계에서 단 하나 (서버 역할을 하는 건 보통 공인 IP로 사용)

사설 ip : 공유기를 이용해 만들 수 있는 가상의 IP 주소



고정 ip : 해당 컴퓨터의 IP 주소를 고정적으로 사용

유동 ip : 수시로 변하는 IP 주소 (DDNS를 사용해서 )



인코딩, 디코딩

컴퓨터 언어를 사람이 볼 수 있게 하는 게 디코딩

사람의 언어를 컴퓨터 언어로 변환하는게 인코딩



쿠키 세션 -> Jwt -> 웹소켓


