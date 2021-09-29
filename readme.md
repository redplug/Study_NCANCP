### Naver Cloud Platform 의 NCA, NCP 시험준비를 위한 내용 정리

- 항목에 대한 소개와 시험에 나올법한 내용들(제한 사항이라던지 등등)이라고 생각되는 내용들만 정리
- 따라서 별도로 사용 가이드는 한번 전체적으로 읽을 것을 권장함
- Classic이라고 명시된 부분은 적지 않음
- 사용 가이드 : https://guide.ncloud-docs.com/docs/home
- NCA시험은 Overview, Compute, Storage, Database, Network, Media
- NCP추가항목 : Management, Analytics, Troubleshooting

## Overview

- 이건 뭘 넣어야되나..
- 블로그에서 참고한 카테고리 :
  - VMWare ON Cloud
  - WORKPLACE
  - Cloud hadoop
  - Ncloud cli
  - Backup
  - Cloud log Analytics
  - NAT 의 작동방식
  - Data Teleporter / AI

## Compute

- ### 서버 생성

  - ### Virtual Machine Server

    - ### Virtual Machine Server 개요

      - 물리적인 서버 자원 없이 사용만큼 지불하는 서비스

      - 비용은 월요금제외 시간요금제가 있음

      - 편리한 서버 생성, 모니터링 기능제공, 강화된보안, 효율적인 비용관리

      - 제공 서버 타입

        | 서버타입                 | 특징                                                         |
        | ------------------------ | ------------------------------------------------------------ |
        | Micro                    | - 체험용 서버 - 계정당 1대만 이용 가능 <br />- 가용성 및 성능 보장 불가 <br />- 거주지 국가가 한국인 경우만 제공 <br />- 신규 가입 후 최초 결제 수단 등록 월부터 1년간 무료 제공 <br /> |
        | Compact                  | - 저사양 서버 <br />- 성능 이슈가 적은 서비스에 운영에 사용 <br />- 서버 운영 비용 부담을 더는 목적으로 사용 |
        | Standard                 | - 다양한 IT 비즈니스에 활용할 수 있는 표준 서버 <br />- 균형 잡힌 서버 사양 제공 <br />- 높은 가용성과 안정성 |
        | High Memory              | - 64GB 이상의 고메모리 서버 <br />- 메모리 성능에 영향을 많이 받는 애플리케이션 운영에 적합 <br />- 최대 10대까지 생성 가능 - 대수 제한 조정은 고객지원에 요청 |
        | High CPU                 | - Memory 대비 vCPU 비율을 높인 서버 <br />- Computing 집약적 워크로드에 적합한 서비스 제공 |
        | GPU                      | - 최신 TESLA 아키텍처 GPU(P40, V100, T4)가 장착된 서버 <br />- 빠른 데이터를 처리하는 환경에 적합 - 최대 5대까지 생성 가능 <br />- 대수 제한 조정은 고객지원에 요청 |
        | Virtual Dedicated Server | - 고성능 물리 서버를 단독으로 제공하는 서비스 <br />- 많은 양의 데이터 처리와 고성능의 I/O를 요구하는 서비스에 적합 <br />- 일부 기능을 제외하고 일반 서버처럼 서버 기능을 사용하거나 다른 서비스에 연동해 사용 가능 |

      - 주요 기능 가능 여부 비교표

        | 기능                   | Micro | Compact | Standard | High Memory     | CPU Intensive | VDS        | GPU  | 2세대 서버(High CPU, Standard, High Memory, CPU Intensive) |
        | ---------------------- | ----- | ------- | -------- | --------------- | ------------- | ---------- | ---- | ---------------------------------------------------------- |
        | 스토리지 추가          | 불가  | 가능    | 가능     | 가능            | 가능          | 가능       | 가능 | 가능                                                       |
        | SSD 스토리지 이용      | 불가  | 가능    | 가능     | 가능            | 가능          | SSD만 제공 | 가능 | 가능                                                       |
        | 오토스케일링 이용      | 불가  | 가능    | 가능     | 불가(개선 예정) | 가능          | 불가       | 불가 | 가능(High CPU, Standard)                                   |
        | IOPS 성능              | 낮음  | 높음    | 높음     | 높음            | 높음          | 높음       | 높음 | 높음                                                       |
        | Network Interface 이용 | 불가  | 가능    | 가능     | 가능            | 가능          | 가능       | 불가 | 가능                                                       |
        | 글로벌 회선 이용       | 불가  | 가능    | 가능     | 불가            | 불가          | 불가       | 불가 | 가능                                                       |

      - 서버생성시 운영체제 디스크는 기본 50GB 디스크 제공, 윈도우는 기본 100GB

      - 서버 스팩 변경은 타입이 동일한 서버 내에서만 가능

        * 서버의 이미지를 생성한 후에 변경은 가능하긴 함.(IP 바뀜)

      - 로컬 디스크 서버

        - Local Disk 는 Network Disk 보다 I/O가 높음
        - 로컬 디스크 추가 및 서버 스펙 변경 불가
        - H/W 장애시 데이터 복구 불가, Network Disk와 이중화 권고

      - SSD 서버 참고

        - 서버 부팅 스토리지 SSD를 이용하는 서버, 고성능 I/O가 필요한 서비스
        - 기본 4,000 IOPS보장(1GB당 40 IOPS 제공)

    - ### 서버 생성

      - NCP는 HA구조를 제공, Live Migration 지원(불가할경우 VM서버 리붓)

      - VM 1대 운영이렴 다중화 하는 것을 권장

      - 서버생성

        - 생성 방법 설명 -> 보지말고 그냥 실습해보는게 좋음
        - 콘솔 접속 > 이미지 생성 . 서버 설정 > 인증키 설정 > 네트워크 접근 설정 > 최종 확인
        - OS와 상관없이 인증키는 *.pem 확장자로 저장

        

    - ### 서버 정지 및 반납

      - 이것도 실습 권장
      - 서버 정지 > 스토리지 반납 > 서버 반납
      - 스토리지 반납은 
        - 추가한 경우에만 없을 경우 바로 서버 반납
        - 서버에서 연겨을 해제 한 후에 반납처리

  - ### Bare Metal Server

    - ### Bare Metal Server 개요

      - 물리서버를 가상화 환경 없이 단독 제공, 대규모 입출력이 발생하거나 빠른 입출력이 필요한 경우
      - 시간 요금제로만 청구
      - 이점 : 고성능, 다양한 스펙, 손쉬운 생성과 구성 변경
      - 타입별 주요 기능 비교표
        ![image-20210926185452800](https://raw.githubusercontent.com/redplug/shareimages/master/img/image-20210926185452800.png)

    - ### 서버 생성

      - 가상서버와 동일함

    - ### 서버 정지 및 반납

      - 가상 서버와 크게 다르지 않음

- ### 접속 환경 설정

  - ### 공인 IP 사용 가이드

    - 고객이 지정한 서버에 공인 IP 할당해주는 서버
    - VPC환경에서는 Internet Gateway가 설정된 Subnet의 서버만 연결 가능
    - 공인 아이피는 리전별로 리전 내 생성된 서버 수와 동일하게 제공
    - 생성이 불가할 경우 다른 Zone에 사용하지 않는 공인 IP삭제 후 생성
    - 공인IP 할당 서버 변경가능, 변경 시 공인IP가 위치한 Zone과 서버가 위치한 Zone이 동일 해야 함
    - 할당 방법은 실습 해볼 것

  - ### 포트 포워딩 이용 가이드

    - 포트포워딩 : 비공인 아이피를 가진 서버에 공인 IP의 포트를 통해 접속 하는것
    - 포트 포워딩은 서버 접속 용도로만 사용 가능하며, 서비스 목적의 포트 연결은 공인 IP를 사용해주세요.
    - Server, Bare Metal Server에서 공인 IP와 포트 포워딩을 동시에 사용하면 22(Linux), 3389(Windows) 포트가 포트 포워딩에 먼저 할당됨에 따라 공인 IP에서 해당 포트 사용이 불가해집니다. 공인 IP에서 22, 3389 포트를 사용하려면 해당 서버의 포트 포워딩 설정을 삭제해주세요.
    - 이것도 실습 해보면 쉽게 알듯

  - ### ACG 사용 가이드

    - Access Control Group, 서버간 네트워크 접근 제어 및 관리를 할수 있는 IP/Port 기반 필터링 방화벽 서비스

    - VPC 환경 기준 제한사항

      - VPC당 최대 500개까지의 ACG를 생성할 수 있습니다.
      - NIC당 3개의 ACG를 허용합니다.
      - Inbound / Outbound 각각 50개의 ACG 규칙을 생성할 수 있습니다.

    - Default ACG, Custom ACG
      ![image-20210926190305072](https://raw.githubusercontent.com/redplug/shareimages/master/img/image-20210926190305072.png)

    - ACG 규칙 설정

      - 네이버 클라우드 플랫폼 2.0은 기본적으로 서버에 모든 들어오는 연결(inbound traffic)을 차단, 모든 나가는 연결(outbound traffic)을 허용합니다.
        ACG에 적용한 모든 규칙들은 ACG 내 속하는 서버에 대해 들어오는 연결(inbound traffic)을 허용합니다.
        규칙에는 네트워크 프로토콜, 접근소스, 포트 설정이 가능합니다. 자세한 내용은 아래 표를 참고하세요.
        ![image-20210926190343701](https://raw.githubusercontent.com/redplug/shareimages/master/img/image-20210926190343701.png)

      

- ### 서버 접속

  - ### 리눅스 서버 접속 가이드

    - ssh key 인증서 접속을 위해서는 서버에 ~/.ssh/authorized_keys 위치에 공개키 내용 추가 필요
    - 실습해보는게 빠름

  - ### 윈도우 서버 접속 가이드

    - 실습이 빠름

- ### 스토리지 추가

  - ### 스토리지 추가 가이드

    - HDD, SSD 스토리지 제공
    - Micro 타입의 서버, Bare Metal 서버는 스토리지를 추가할 수 없습니다.
    - 개당 최대 2000GB지원, 서버 한대당 최대 16개 스토리지(부팅포함)
    - 삭제 시 마운트 해제 하고 해야 함.
      - linux의 경우 스토리지를 삭제(또는 연결 해제)한 후 반드시 스토리지의 마운트 정보를 /etc/fstab에서 삭제해야 합니다. 마운트 정보가 남아있으면 서버가 재부팅될 때 디스크 인식 실패로 정상적으로 부팅되지 않을 수 있습니다.
    - Q. 이용 중인 스토리지를 다른 서버로 옮길 수 있나요?
      - 최신 서버에 연결된 스토리지에 한해, 가능합니다.
      - Compact, Standard, High Memory, VDS, GPU 서버 타입에 대해 지원합니다.(Micro, Bare Metal Server 지원 안 함) 

- ### 스토리지 크기 변경

  - ### 스토리지 크기 변경 가이드

    - 연결된 디스크일 경우 서버 정지상태에서 가능
    - 디스크 한개당 2TB, 변경전보다 크게만 가능
    - SSD의 경우 1GB당 40 IOPS씩 증가 (4000이 최소, 최대 24000인가(?)까지임)

- ### 내 서버 이미지

  - ### 내 서버 이미지 사용 가이드

    - 현재 사용중인 서버의 이미지를 생성하는 기능, 서버의 현재상태 저장
    - 서버가 정지 혹은 운영중인 상태에서만 생성 가능 (클래식은 정지상태에서만 가능)
    - 50GB당 약 30분 소요, 추가 디스크가 있고 불필요한 경우 분리 후 작업 하면 좋음
    - 다른 리전으로 복제 기능 있음.
    - 내 서버이미지 생성 시 다른 타입의 서버로 스펙 변경 가능

- ### 서버 이미지 빌더

  - ### 서버 이미지 빌더 사용 가이드

    - 클래식만 사용 가능
    - 스크립트 기반으로 내가 원하는 이미지 만드는 빌더, 오픈소스 Packer를 활용
    - 2008을 제외한 모든 이미지 이용 가능
    - 빌드 시 서버가 만들어지고 반납되어 비용 발생, 스토리지 사용에 대한 요금 별도
    - 인증키가 있어야 함.
    - 생성시간은 50GB당 30분 소요
    - 실습은 별도로

- ### 스토리지 스냅샷

  - ### 스토리지 스냅샷 사용 가이드

    - 스냅샷 사진 찍듯이 특정 시점의 스토리지 데이터를 저장하고, 저장된 데이터가 필요할 때 새로운 디스크의 형태로 복구할 수 있는 기능
    - 다른 리젼 복제 가능
    - VPC환경에서 증분 스냅샷 생성 가능 최대 7개
    - 증분 스냅샷 제한 사항
      - 2021년 1월 21 이전에 전체 스토리지 스냅샷으로 증분 스냅샷을 생성하는 경우
      - 스토리지를 서버로부터 Attach.Detach 하는 경우
      - 스토리지 용량을 변경 하는 경우
      - 증분 스냅샷이 삭제되는 경우 -> 전체 스토리지 스냅샷 새로 생성 필요
    - 가장 최근에 생성한 전체 스토리지 스냅샷을 기준으로만 증분 스냅샷 가능
    - 스냅샷 스토리지 부팅오류 방지 가이드(리눅스만 해당)
      - 부팅용 사용하던거 걸 붙일 경우에 발생할 수 있음
      - 추가 스토리지의 식별자를 변경 하면됨
      - **CentOS 5.x는 스토리지를 라벨(LABEL)로 식별하고, CentOS 6.x 이상과 Ubuntu 12,x 이상은 스토리지를 UUID로 식별합니다.**
      - CentOS 5.x tune2fs 로 '/'이 아닌 다른 라벨을 붙인다
      - CentOS 6.x, Ubuntu 12.x, 14.x 는 tune2fs로 UUID 수정
      - UUID는 uuidgen으로 새로 생성 할 수 있음.

- ### Ncloud Tool Kit(NTK)

  - ### NCloud Tool Kit 사용 가이드

    - Ncloud에서 제공하는 Linux 서버 상태 진단 툴
    - 쉘 접근하여 설치 필요
    - 이건 안나올것 같음.

- ### Private Subnet

  - ### Private Subnet 사용 가이드

    - 서버들간 내부 통신을 할 수 있는 독립된 가상 네트워크 환경
    - 존당 1개 생성 가능
    - 192.168.0.0/16내에서 /24단위로 생성 가능
    - NIC와 함께 사용 필요

- ### Network Interface

  - ### Network Interface 사용 가이드

    - NIC 추가 생성 서비스
    - Private Subnet를 먼저 신청해야 사용 가능
    - eth1번 사용 (Bare Metal은 eth3)
    - Flow log : 네트워크 모니터링에서 로그 수집목적으로 사용하는 log

  - ### Secondary IP 사용 가이드 (VPC)

    - VPC 환경
    - HA솔루션 등에 활용하기 위한 보조 IP
    - NIC는 최대 5개 가능
    - ACG는 최대 3개

- ### Init Script

  - ### Init Script 사용 가이드

    - 서버 생성 시 자동 실행 스크립트, 최초1회만 실행
    - 리눅스 : Python, Perl, Shell 스크립트
    - 윈도우 : Visual Basic 스크립트
    - 언제 사용? 
      - 같은 용도 서버를 여러 대 일괄로 생성하는 경우 : 사용자 스크립트 생성 후 여러 서버 생성 시 해당 스크립트 일괄 적용합니다.
      - 동일한 환경의 서버를 주기적으로 생성하는 경우 : 사용자 스크립트를 생성하고 저장한 후, 서버 생성 시 해당 스크립트 선택 적용합니다.
      - 용도별로 서버 초기 환경 관리가 필요한 경우 : 용도별로 다양한 스크립트를 생성하고 저장한 후, 서버 생성 시 필요에 따라 선택하여 사용합니다.
    - 설치 완료 여부 로깅 파일 위치
      - Linux는 /var/log/ncloud-init.log
      - Windows는 C:\Program Files(X86)\NBP\ncloud-init\logs를 참고하면 됩니다.
        

- ### Auto Scaling

  - ### Auto Scaling 개요

    - 미리 정한 조건에 따라 가상 서버수를 증가 또는 감소 시켜주는 서비스(Scale in/out)
    - 유형
      - 서버 그룹 모니터링
      - 스케쥴링
      - 매뉴얼
    - 서비스 제한 사항
      - 총 디스크 사이즈 150GB 이하 서버만 가능
      - Windows OS는 Windows 2012. 2016만 지원
      - Micro 서버는 불가
      - High Memory 서버는 불가(추후 개선 예정)
      - Local disk 기반 서버는 불가
    - 설정 제한 사항
      - 고객별 생성 가능한 Auto Scaling Group 최대 수: 100
      - 고객별 생성 가능한 Launch Configuration 최대 수: 100
      - Auto Scaling Group당 생성 가능한 스케줄(Scheduled Action) 최대 수: 100
      - Auto Scaling Group당 생성 가능한 Scaling Policy 최대 수: 10
      - Auto Scaling Group당 생성 가능한 최대 서버 수: 30대
      - Auto Scaling Group당 연결 가능한 Load Balancer 최대 수 : 10
    - Launch Configuration : 오토스케일 대상 서버 그룹에 대한 설정 (템플릿)
    - Auto Scaling Group : 증가/감소량, 쿨다운, 스케일링에 대한 설정
    - 

  - ### Auto Scaling 사용 가이드

    - 이벤트 룰 : 증가/감소 시킬 조건 정의 할 수 있는거

  - ### Auto Scaling 부가 기능

    - 별거 없음

  - ### Auto Scaling 관리

    - 내서버 이미지 + Init Sciprt 생성 지원
    - 쿨다운 기본 값 : 서비스 수행 하기 까지 기다려주는 시간
      헬스체크 보류 기간도 비슷한 목적이라고 보면됨

  - ### Sub Account 권한 관리

    - 이건 외워야 될꺼 같은데 불가해보임.

- ### Cloud Functions

  - ### Cloud Functions 사용 가이드

    - 사용자의 인프라 관리 부담없이 원하는 로직을 분산된 클라우드 환경에서 동작하고 결과를 반환합니다.
    - 서버리스 컴퓨팅, 서버 컴퓨팅 파워 없이, 코드만 짜고 실행 조건만 가지고 사용하는거라고 보면됨.

  - ### Action 사용 가이드

    - ### Package, Action 사용 가이드

      - 액션 : 사용자가 정의하는 상태 비저장(Stateless) 코드의 코드 조각(Snippets)으로, 다양한 언어로 작성될 수 있습니다.
      - 액션의 Input과 Output은 모두 키-값(key-value) 형태의 JSON 값
      - Sequence 액션 : 여러개 액션을 모음
      - 지원 언어
        - Node.js 6, 8, 12
        - Python 3.6, 3.7
        - Java 8
        - Swift 3.1.1
        - PHP 7.1, 7.3
        - Go 1.1
        - .Net Core 2.2
        - Ruby (추후 지원)
      - 액션 컨테이너 : 액션 실행을 위해 생성되는 공간이라고 생각하면됨
        - pre-warming를 통해 미리 액션 컨테이너 구동 가능
      - 액션 실행 결과
        - **`namespace`**: 액션이 속한 namespace. 사용자와의 계약에 의해 할당된 고유 공간입니다. 계약 종료 후 재계약 시에는 다른 namespace를 할당받습니다.
        - **`name`**: 액션의 이름
        - **`activationId`**: 액션 실행 결과의 고유 ID
        - **`start`**: 액션이 시작된 시간
        - **`end`**: 액션이 종료된 시간
        - **`duration`**: 액션이 실행된 기간(ms)
        - **`response`**: 액션의 실행 결과. 액션이 최종 반환한 결과는 `result` 필드로 전달됩니다.
        - **`logs`**: 사용자가 액션 내에서 출력한 로그
        - **`annotations`**: 액션과 관련된 정보
        - **`publish`**: 액션이 공유되었는지 여부
      - result옵션 : result에 해당 하는 정보만 반환
      - 액션 로그 남기기 : stout, sterr

    - ### Sequence Action

      - 선행 액션의 리턴한 결과 JSON 값을 후행 액션 파라미터값으로 전달받음
      - 사용자 액션 파라미터는 첫번째 액션에서만 전달
      - 

    - ### Node.js, Python, Java, Swift, PHP, .Net, Go

      - 코드설명이라 안나올듯

    - ### VPC 리소스 연결 가이드

      - KR-2 제한
      - Private Subnet 제한, 인터넷 통신을 하기 위해서는 NAT Gateway 설정 필요

  - ### Trigger 사용하기

    - ### Cron Type Trigger 사용 가이드

    - ### Github 이벤트 Trigger 사용 가이드

    - ### Cloud Insight Trigger 사용 가이드

    - ### Cloud IoT Core Trigger 사용 가이드

    - ### Object Storage Trigger 사용 가이드

  - ### Activation 사용 가이드

  - ### 시스템 제한

  - ### 실행하기

  - ### 웹 액션 실행하기

  - ### Sub Account 권한 관리

- ### Container Registry

  - ### 사용하기 전에

  - ### Quick Start

  - ### Container Registry 사용 가이드

  - ### 컨테이너 이미지 보안 취약점 스캔 기능

- ### Kubernetes Service

  - ### Kubernetes Service 사용 가이드

  - ### 클러스터 이용 가이드

  - ### 로드밸런서 연동 가이드

  - ### 블록 스토리지 CSI 이용 가이드

  - ### 노드 유지보수 가이드

  - ### 클러스터 권한 제어 가이드

  - ### Helm 이용 가이드

  - ### CLuster Autoscaler 이용 가이드

  - ### WordPress 튜토리얼

  - ### Ingress 튜토리얼

- ### Kubernetes Service (VPC)

  - ### Kubernetes Service 사용 가이드

  - ### 클러스터 이용 가이드

  - ### 로드밸런서 연동 가이드

    - ### 네트워크 프록시 로드밸런서 연동 가이드

    - ### 네트워크 로드밸런서 연동 가이드

    - ### ALB Ingress Controller 가이드

  - ### 블록 스토리지 CSI 이용 가이드

  - ### NFS Client Provisioner 이용 가이드

  - ### 노드 유지보수 가이드

  - ### WordPress 튜토리얼

  - ### Ingress 튜토리얼

  - ### Kubeflow 튜토리얼

    - ### Kubeflow 설치 가이드

    - ### Kubeflow Notebook 활용 개발

    - ### 로컬 개발환경에서 Kubeflow 활용

  - ### 클러스터 권한 제어 가이드

  - ### Node pool 가이드

  - ### Cluster Autoscaler 이용 가이드

  - ### Sub Account 권한 관리

  - ### Metrics Exporter 이용 가이드

  - ### GPU 노드 사용 가이드

  - ### Velero 이용가이드

  - ### 업그레이드 가이드

- ### Application Server Launcher

  - ### Application Server Launcher 사용 가이드

- ### LAMP

  - ### Lamp 사용 가이드

- ### WordPress

  - ### WordPress 사용 가이드

- ### Magento

  - ### Magneto 사용 가이드

- ### META Commerce

  - ### META Commerce 사용 가이드

  - ### META Commerce 퍼블리싱 가이드

- ### Drupal

  - ### Drupal 사용 가이드

- ### Joomla!

  - ### Joomla! 사용 가이드

- ### Shadowsocks

  - ### Shadowsocks 사용 가이드

- ### HCP

  - ### HPC 사용 가이드

- ### LEMP

  - ### LEMP 사용 가이드

- ### Node.js

  - ### Node.js 사용 가이드

- ### Gitlab CE

  - ### Gitlab CE 사용 가이드

- ### Hugo

  - ### Hugo 사용 가이드

- ### Superset

  - ### Superset 설치하기

  - ### Superset 시작하기

- ### Tomcat

  - ### Tomcat 사용 가이드

- ### Gradle

  - ### Gradle 사용 가이드

- ### Sub Account 권한 관리

  - ### Sub Account 사용 가이드

- ### Server Status 점검

  - ### Server Status 점검 가이드

  - ### 윈도우서버 Xentools 사용 가이드

  - ### Server 복구

## Storage

- ### Object Stroage

  - ### Object Storage 사용 가이드

    - ### Object Storage 개요

    - ### Java SDK

    - ### Python SDK

    - ### Javascript SDK

    - ### CLI

    - ### Sub Account 권한 관리

- ### Archive Storage

  - ### Archive Storage 사용 가이드

    - ### Archive Storage 개요

    - ### 대용량 파일 관리 (DLO)

    - ### 대용량 파일 관리 (SLO)

    - ### 오브젝트 생명주기 관리

    - ### Python SDK

    - ### Java SDK

    - ### Javascript SDK

    - ### CLI

    - ### S3 APII

- ### NAS

  - ### NAS 사용 가이드

  - ### Sub Account 권한 관리

- ### Backup

  - ### Backup 사용 가이드

## Database

- ### MySQL

  - ### MySQL 서버 이미지 사용 가이드

- ### MSSQL

  - ### MSSQL 서버 이미지 사용 가이드

  - ### MSSQL 한글 환경으로 변경

  - ### MSSQL Log Collector (Lazylog) 사용 가이드

  - ### MSSQL Log Collector (Lazylog) 다운로드

- ### CUBRID

  - ### CUBRID 서버 이미지 사용 가이드

- ### REDIS

  - ### REDIS 서버 이미지 사용 가이드

- ### Tibero

  - ### Tibero 사용 가이드

- ### Cloud DB for MySQL

  - ### 퀵스타트 가이드

  - ### DB 서버 생성 및 접근 가이드

  - ### DB 서버 상세 보기 및 설정 가이드

  - ### Monitoring 사용 가이드

  - ### Backup 사용 가이드

  - ### Event 사용 가이드

  - ### phpMyAdmin 설치 및 사용 가이드

  - ### DB 서버 로드밸런서 설정 가이드

  - ### DB 서버 외부 접근 가이드

  - ### Sub Account 권한 관리 (VPC)

- ### Cloud DB for Redis

  - ### 퀵스타트 가이드

  - ### Redis 서버 생성 및 접근 가이드

  - ### Monitoring 사용 가이드

  - ### Backup 사용 가이드

  - ### Event 사용 가이드

  - ### SSL VPN을 이용한 DB 서버 외부 접근 가이드

  - ### Redis Cluster 사용 가이드

  - ### Sub Account 권한 관리 (VPC)

  - ### Config Group 사용 가이드 (VPC)

- ### Cloud DB for MSSQL

  - ### 퀵스타트 가이드

  - ### DB 서버 생성 및 접근 가이드

  - ### DB 서버 상세 보기 및 설정 가이드

  - ### COnfig Group 설정 및 사용 가이드

  - ### Monitoring 사용 가이드

  - ### Backup 사용 가이드

  - ### Event 사용 가이드

  - ### SSMS 설치 및 사용 가이드

  - ### SSL VPN을 이용한 DB 서버 외부 접근 가이드

  - ### DB 서버 외부 접근 가이드

  - ### Sub Account 권한 관리 (VPC)

- ### Cloud DB for MongoDB

  - ### 퀵스타트 가이드

  - ### DB 서버 생성 및 접근 가이드

  - ### DB 서버 설정 가이드

  - ### Monitoring 사용 가이드

  - ### Backup 사용 가이드

  - ### Event 사용 가이드

  - ### DB 서버 외부 접근 가이드

  - ### Sub Account 권한 관리 (VPC)

- ### PostgreSQL

  - ### PostgreSQl 서버 이미지 사용 가이드

- ### MariaDB

  - ### MariaDB 사용 가이드

- ### MongoDB

  - ### MongoDB 서버 이미지 사용 가이드

  - ### MongoDB 사용하기 전에 Linux OS 설정하기

  - ### MongoDB Cluster 구성하기

  - ### Public IP 기능 사용하여 외부와 연동하기

  - ### Compass로 MongoDB 관리하기

  - ### CLI로 MongoDB 모니터링하기

## Network

- ### VPC

  - ### VPC 개요

  - ### 사용자 시나리오

    - ### 시나리오 1. 단일 Public Subnet

    - ### 시나리오 2. Public과 Private Subnet

    - ### 시나리오 3. Public과 IPsec VPN 연결 Subnet

    - ### 시나리오 4. VPC간 사설 통신 (Peering 구성)

  - ### 보안

    - ### 보안 개요

    - ### Deny-Allow Group 사용 가이드

  - ### VPC 세부 구성 요소

    - ### VPC/Subnet

    - ### NAT Gateway

    - ### VGW

    - ### Peering

    - ### Route Table

    - ### Sub Account 권한 관리

- ### Load Balancer

  - ### Load Balancer 개요

  - ### 사용 가이드

    - ### Target Group

    - ### Application Load Balancer

    - ### Network Load Balancer

    - ### Network Proxy Load Balancer

    - ### Classic Load Balancer

  - ### Load Balancer 부가 기능

  - ### Sub Account 권한 관리

- ### Global DNS

  - ### DNS 리소스 레코드 안내서

  - ### Global DNS 사용 가이드

  - ### Sub Account 권한 관리

- ### CDN+

  - ### CDN+ 사용 가이드

- ### Global CDN

  - ### Global CDN 사용 가이드

- ### IPsec VPN

  - ### IPsec VPN 사용 가이드

    - ### IPsec VPN 개요

    - ### Cisco

    - ### Fortinet

    - ### Juniper

    - ### Paloalto

- ### NAT Gateway

  - ### NAT Gateway 사용 가이드

- ### Global Route Manager

  - ### Global Route Manater 사용 가이드

- ### DNS

  - ### DNS 리소스 레코드 안내서

  - ### DNS 사용 가이드

## Media

- ### VOD Transcoder (Deprecated) : 없어질꺼라 따로 정리 안함

- ### Image Optimizer

  - ### Image Optimizer 사용 가이드

  - ### Query String 작성 가이드

- ### Live Station

  - ### Live Station 사용 가이드

  - ### Channel Management

    - ### Channel 관리

    - ### 녹화 기능 사용 가이드

  - ### Quality Management

    - ### Quality 설정

    - ### Quality Profile 설정

  - ### Re-Stream Management

  - ### Notification 설정

  - ### 라이브 인코더 송출 가이드

  - ### Sub Account 권한 관리

- ### VOD Station (Deprecated) : 없어질꺼라 따로 정리 안함

- ### VOD Station (New)

  - ### VOD Station 개요

  - ### VOD Station 사용 준비

  - ### VOD Station 시작

  - ### VOD Station 사용

    - ### 미디어 인코딩

    - ### 스트리밍 채널 설정

    - ### VOD 스티리밍

  - ### VOD Station 문제 해결

  - ### VOD Station 권한 관리

  - ### VOD Station 릴리즈 노트

- ### Video Player

  - ### Video Player 콘솔 사용 가이드

  - ### Video Player 사용 가이드

  - ### Video Player Demo 가이드

  - ### Sub Account 권한 관리

------

### 하기는 NCP 추가내용(NCA 따고 업데이트)

## Analytics

- Cloud Log Analytics (CLA)
- Real User Analytics
- Effective Log Search & Analytics
- Cloud Hadoop
- Cloud Hadoop (VPC)
- Data Forest (VPC)
- Cloud Search
- Search Engine Service
- Cloud Data Streaming Service
- Data Analytics Service
- Cloud Data Box
- HEaan Homomorphic Analytics

## Management

- Monitoring
- Sub Account
- Web service Monitoring System
- Network Traffic Monitoring
- Cloud Activity Tracer
- Resource Manager
- Cloud Insight
- Pinpoint Cloud
- Cloud Advisor
- Organization

## Troubleshooting

- https://www.edwith.org/ncloudprofessional/lecture/173863?isDesc=false
- 요거 다시좀 봐야 할듯
