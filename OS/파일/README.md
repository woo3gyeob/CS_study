## 파일시스템

![img](https://s3.us-west-2.amazonaws.com/secure.notion-static.com/239aee23-9a24-4cb7-aa9d-3bf74efcc853/Untitled.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Credential=AKIAT73L2G45O3KS52Y5%2F20210704%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20210704T141018Z&X-Amz-Expires=86400&X-Amz-Signature=c6b5a81a2efd376d63e9dcef5d53fa8e5a0ca885118c08f09d5f854732763a67&X-Amz-SignedHeaders=host&response-content-disposition=filename%20%3D%22Untitled.png%22)

<br>

**파일 시스템**

- 컴퓨터에서 파일이나 자료를 쉽게 발견 할 수 있도록, 유지, 관리하는 방법이다.

즉, 저장매체에는 많은 파일이 있으므로, 이러한 **파일을 관리하는 방법**을 말한다.

- 사용자 영역이 아닌 커널 영역에서 동작
- 파일을 빠르게 읽기, 쓰기, 삭제 등 기본적인 기능을 원활히 수행하기 위한 목적

<br>

**파일 시스템 특징**

- 계층적 디렉터리 구조를 가진다.
- 디스크 파티션 별로 하나씩 둘 수 있다.

<br>

**파일 시스템의 역할**

- 파일관리 : 파일 저장, 참조, 공유
- 보조 저장소 관리 : 저장 공간 할당
- 파일 무결성 메커니즘 : 파일이 의도한 정보만 포함하고 있음을 의미
- 접근 방법 : 저장된 데이터에 접근할 수 있는 방법 제공

<br>

**파일 시스템 개발 목적**

- HDD와 메인 메모리 속도차 줄이기
- 파일 관리 용이
- HDD의 막대한 용량을 효율적으로 이용

<br>

**주요 파일 시스템**

Windows : **FAT(FAT12/16/32,exFAT), NTFS**

Linux : **ext(ext2/3/4)**

Mac OS : HFS, HFS+

Google : GFS

- GFS : Google File System으로 구글에서 사용하는 분산 파일 시스템

<br>

**파일 시스템 구조**

- **메타 영역**과 **데이터 영역** 두가지 영역으로 구분이 된다.
- 메타 영역 : 데이터 영역에 기록된 파일의 이름, 위치, 크기, 시간정보, 삭제유무 등 **파일의 정보**
- 데이터 영역 : 파일의 데이터
- 윈도우 탐색기를 이용하여 검색할때 메타 영역을 탐색하면서 파일을 찾는다.

<br>

**FAT**은 File Allocation Table의 약자로 파일에 디스크에 존재한 파일의 정보가 저장되어

섹터들을 찾아볼 수 있도록 정보를 저장하고 있는 특수영역,

**NTFS** 는 NT에서 사용되는 File sytem으로, FAT과는 달리 MFT ( Master File Table ) 사용.

또한 이에 대한 미러( mirror )와 파일 로그가 유지되어 파일 복구 가능.

한 클러스터는 FAT32와 같이 최소 1KB 에서 최대 4KB로 디스크 손실이 적음.

**EXT2** 는 리눅스를 위한 확장성 있고 강력한 파일 시스템으로 가장 성공적인 파일 시스템.

현재 배포되고 있는 모든 리눅스 배포판의 기본을 이룸.

파일 복구에 매우 강하다.

**EXT3** 는 저널링 파일 시스템으로 대부분의 유명한 리눅스 배포판에 채택