- ### Naver Cloud Platform 의 NCA, NCP 시험준비를 위한 내용 정리

  - 항목에 대한 소개와 시험에 나올법한 내용들(제한 사항이라던지 등등)이라고 생각되는 내용들만 정리
  - 따라서 별도로 사용 가이드는 한번 전체적으로 읽을 것을 권장함(본 문서는 시험보기 전에 작성하였음.)
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

      - ### Trigger 사용 가이드

        - 이벤트 기반 기능 제공
        - KV(키/벨류) 딕셔너리르 사용하여 동작
        - 시행 시마다 Activiation ID 부여

      - ### Cron Type Trigger 사용 가이드

        - 특정 시간 기준으로 주기적 실행

      - ### Github 이벤트 Trigger 사용 가이드

        - Github에 사용자가 등록한 이벤트 리스트를 등록하여 해당 이벤트가 일어날 떄 트리거 호출

      - ### Cloud Insight Trigger 사용 가이드

        - Cloud Insight는 네이버 클라우드 플랫폼이 제공하는 상품들의 성능 지표를 통합 관리하고, 장애 발생 시 담당자에게 장애 정보를 신속히 전달할 수 있는 모니터링 서비스

      - ### Cloud IoT Core Trigger 사용 가이드

        - 딱히 추가할 내용 없어보임

      - ### Object Storage Trigger 사용 가이드

        - 딱히 추가할 내용 없어보임

    - ### Activation 사용 가이드

      - 액션이나 트리거를 실행한 결과
      - 필드값
        - **namespace**: 액션이 속한 namespace
        - **name**: 액션의 이름
        - **activationId**: 액션 실행결과의 고유 ID
        - **start**: 액션이 시작된 시간
        - **end**: 액션이 종료된 시간
        - **duration**: 액션이 실행된 기간 (ms)
        - **response**: 액션의 실행 결과, 액션이 최종 반환한 결과는 `result` 필드로 전달됨
        - **logs**: 사용자가 액션 내에서 출력한 로그
        - **annotations**: 액션과 관련된 정보
        - **publish**: 액션이 공유되었는지 여부 (beta에서 지원하지 않습니다.)

    - ### 시스템 제한

      - 응답결과로 `Too many concurrent requests in flight()`와 같은 형태의 응답을 받으면, 관리자에게 문의 요청을 주시면 사용 가능한 concurrent 수치를 상향 할 수 있습니다.

      - 제한사항

        | Limit      | Unit         | Default | Description                                                  |
        | ---------- | ------------ | ------- | ------------------------------------------------------------ |
        | timeout    | milliseconds | 60000   | 액션이 실행될 수 있는 최대 시간, 이 시간을 초과하면 강제 종료됨 |
        | memory     | MB           | 256     | 액션 컨테이너에 할당되는 메모리 크기                         |
        | logs       | MB           | 1       | 액션이 출력할 수 있는 최대 `stdout` 크기                     |
        | concurrent | number       | 100     | namespace별로 동시에 실행 가능한 액션 수                     |
        | codeSize   | MB           | 38      | 압축파일이나 code 사이즈는 약 38 MB                          |
        | parameters | MB           | 1       | 최대 파라미터 크기                                           |
        | result     | MB           | 1       | 액션이 반환할 수 있는 최대 결과 크기                         |

        

    - ### 실행하기

    - ### 웹 액션 실행하기

      - 웹 액션은 인증키 없이 실행이 가능하여, 누구나 접근 가능한 웹 애플리케이션을 구축할 수 있습니다.
      - 에러 처리
        - . 첫 번째는 *application error* 로 알려져 있으며 catch 예외와 유사합니다. 액션은 error 속성을 가지는 최상위 JSON 객체를 반환합니다. 
        - 두 번째는 *developer error* 로, 액션이 실패하고 응답을 만들지 않을 때 발생합니다. uncaught 예외와 유사합니다.

    - ### Sub Account 권한 관리

  - ### Container Registry

    - ### 사용하기 전에

      - CR은 프라이빗 도커 허브(이미지 저장소)
      - 매니져(NCP_CONTAINER_REGISTRY_MANAGER)와 뷰어(NCP_CONTAINER_REGISTRY_VIEWER)권한이 있으며, 매니져는 Docker 컨테이너 이미지에 대한 Push, Pull 권한을 가지며, 뷰어는 Pull권한 만을 가집니다.
      - short 메모는 100자 이내
      - full 은 마크다운 지원
      - 연동한 Object Storage는 수정하면 안됨

    - ### Quick Start

    - ### Container Registry 사용 가이드

      - 제공 리전 : 한국(KR), 싱가포르(SG(SGN))
      - 엔드포인트
        - 퍼블릭 엔드포인트: `<registry-name>`.`<region-code>`.ncr.ntruss.com
        - 프라이빗 엔드포인트: `<random-id>`.kr.private-ncr.ntruss.com
      - Docker Engine 1.10버젼 이상 필요
      - 기능 활성화시 이용 불가
        - WORM(Write Once Read Many)
        - Lifecycle Management
        - ACL(Access Control List)

    - ### 컨테이너 이미지 보안 취약점 스캔 기능

      - Clair 기반으로 제공
      - CVE 목록 제공
      - 

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

      - K8s v1.18, 1.19 제공
      - Private Subnet은 최대 3개 선택
      - Private 대역(10.0.0.0/8,172.16.0.0/12,192.168.0.0/16) 내에서 /17~/26 범위의 Private Subnet, 로드 밸런서 전용 Subnet이 필요합니다.
      - Docker Bridge 대역의 충돌을 방지하기 위해 172.17.0.0/16 범위 내의 Private Subnet, 로드 밸런서 전용 Subnet는 선택할 수 없습니다.
      - 노드풀은 최대 10개

    - ### 클러스터 이용 가이드

    - ### 로드밸런서 연동 가이드

      - ### 네트워크 프록시 로드밸런서 연동 가이드

      - ### 네트워크 로드밸런서 연동 가이드

      - ### ALB Ingress Controller 가이드

    - ### 블록 스토리지 CSI 이용 가이드

      - 할당 가능한 용량 : 10GB ~ 2000GB (10GB단위로 할당, 기본값 20GB)

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

      -  전 세계에서 많이 사용하는 오픈 소스 소프트웨어를 쉽게 설치할 수 있게 하는 상품
      - 제공 솔루션
        - Drupal (CMS)
        - Joomla! (CMS)
        - Magento (E-Commerce)
        - Shadowsocks (VPN)
        - LAMP (Web Stack)
        - WordPress (CMS)
        - Jenkins (Dev Tools)

  - ### LAMP

    - ### Lamp 사용 가이드

      - LAMP 상품은 "Linux + Apache + MySQL + PHP" 설치 및 프로세스를 원클릭으로 시작할 수 있는 설치형 서비스 상품
      - AMP 상품은 리눅스를 운영체제로 사용하면서, Apache Web Server/MySQL(MariaDB/PHP)를 활용한 Web Application Stack 서비스
      - LAMP 웹 서비스를 사용하기 위해서는 공인 IP 주소를 신청하여 서버에 할당해야 하며, ACG에 `80` 포트가 추가
      - `/root/lamp` 디렉터리에 다운로드됩니다.
      - LAMP 상품의 Web Service Root Directory는 `/ncp/data/www`입니다.

  - ### WordPress

    - ### WordPress 사용 가이드

      - WordPress 상품은 "Linux + Apache + MySQL + PHP + WordPress" 설치 프로세스를 원클릭으로 시작할 수 있는 설치형 서비스 상품
      - WordPress 상품의 Web Service Root Directory는 `/ncp/data/www/wordpress`

  - ### Magento

    - ### Magneto 사용 가이드

      - Magento 상품은 "Linux + Apache + MySQL + PHP + Magento" 설치 프로세스를 원클릭으로 시작할 수 있는 설치형 서비스 상품
      - Magento 상품은 리눅스를 운영체제로 사용하면서, Apache Web Server/MySQL(MariaDB/PHP)를 활용한 쇼핑몰 구축 서비스 플랫폼
      - Magento 상품의 Web Service Root Directory는 `/ncp/data/www/magento`

  - ### META Commerce

    - ### META Commerce 사용 가이드

      - META Commerce 상품은 리눅스를 운영체제로 사용하면서, Apache Web Server/MySQL을 활용한 쇼핑몰 구축 서비스 플랫폼
      - META Commerce 상품의 Web Service Root Directory는 `/home/admin`, `/home/front`, `/home/httproot`
      - https가 기본 프로톨(http 리디렉션됨)

    - ### META Commerce 퍼블리싱 가이드

  - ### Drupal

    - ### Drupal 사용 가이드

      - Drupal 상품은 리눅스를 운영체제로 사용하면서, Apache Web Server/MySQL(MariaDB/PHP)를 활용한 CMS 구축 서비스 플랫폼
      - Drupal 상품의 Web Service Root Directory는 `/ncp/data/www/drupal`

  - ### Joomla!

    - ### Joomla! 사용 가이드

      - Joomla! 상품은 리눅스를 운영체제로 사용하면서, Apache Web Server/MySQL(MariaDB/PHP)를 활용한 CMS 구축 서비스 플랫폼
      - Joomla! 상품의 Web Service Root Directory는 `/ncp/data/www/joomla`

  - ### Shadowsocks

    - ### Shadowsocks 사용 가이드

      - Shadowsocks 상품은 리눅스를 운영체제로 사용하면서, Shadowsocks Server를 활용한 VPN(Virtual Private Network) 구축 서비스 플랫폼
      - Shadowsocks 상품의 설정 파일 위치는 `/etc/shadowsocks/shadowsocks.json`

  - ### HCP

    - ### HPC 사용 가이드

      - 복잡한 연산을 풀기 위한 컴퓨터로, 슈퍼컴퓨터 또는 컴퓨터 클러스터를 의미
      - 주의사항
        - HPC, Active Directory의 모든 노드 간에 통신이 원활해야 합니다.
        - ACG 설정 시 아래의 HPC 서비스에서 사용하는 포트를 참고해 설정해야 합니다.
        - 모든 설치가 완료된 후 init Script에서 Active Directory 계정 관련 정보를 반드시 삭제해야 합니다.
      - ![image-20211003135629204](https://raw.githubusercontent.com/redplug/shareimages/master/img/image-20211003135629204.png)

    - Windows HPC Pack 2012 R2는 Active Directory를 기반으로 구성

    - init script 변수 값

      - domain: 사용자가 생성하고자 하는 Active Directory Domain Name
      - domain_password: Domain Admin 계정의 Password
      - hpc_user: HPC 서비스에서 사용할 Domain user명
      - hpc_password: HPC 계정의 Password

    - Head 노드는 Windows HPC에서 job scheduling, deployment, cluster 관리를 담당

  - ### LEMP

    - ### LEMP 사용 가이드

      - LEMP 상품은 리눅스를 운영체제로 사용하면서, Nginx Web Server, MySQL(MariaDB), PHP를 활용한 Web Application Service Stack 서비스
      - LEMP 상품의 Web Service Root Directory는 `/ncp/data/www`

  - ### Node.js

    - ### Node.js 사용 가이드

      - Node.js 상품은 리눅스를 운영체제로 사용하면서, Node.js를 활용한 Javascript Development Stack 서비스 플랫폼
      - Node.js 상품의 파일 위치는 `/root/nodejs` , `/root/.nvm`

  - ### Gitlab CE

    - ### Gitlab CE 사용 가이드

      - Gitlab CE 상품은 리눅스를 운영체제로 사용하면서, Gitlab CE를 활용한 Collaboration Code 서비스 플랫폼
      - Gitlab CE 상품의 파일 위치는 `/root/gitlab`

  - ### Hugo

    - ### Hugo 사용 가이드

      - Hugo는 GO 언어로 만들어진 가장 인기있는 오픈 소스 정적 사이트 생성기 중 하나입니다. 정적 웹 페이지를 빠르게 만들고 쉽게 관리

  - ### Superset

    - ### Superset 설치하기

      - Superset은 Apache 오픈 소스 웹 기반의 데이터 시각화 BI 툴입니다.
      - 업로드한 엑셀 파일이나 함께 설치된 PostgreSQL DB에 저장한 데이터를 이용하여 손쉽게 시각화 대시보드를 작성할 수 있습니다.

    - ### Superset 시작하기

  - ### Tomcat

    - ### Tomcat 사용 가이드

      - Tomcat 상품은 리눅스를 운영체제로 사용하면서, Tomcat를 활용한 Web Application Server 및 Servelt Container 서비스 플랫폼
      - Tomcat 상품의 설치 위치는 `/opt/tomcat`

  - ### Gradle

    - ### Gradle 사용 가이드

      - Gradle 상품은 리눅스를 운영체제로 사용하면서, Gradle를 활용한 빌드 서비스 플랫폼
      - Gradle 상품의 파일 위치는 `/opt/gradle/{$GRADLE_VERSION}`

  - ### Sub Account 권한 관리

    - ### Sub Account 사용 가이드

  - ### Server Status 점검

    - ### Server Status 점검 가이드

      - Server Status Check 활성화 조건
        - 서버에서는 Xen Guest Monitoring 역할을 수행하는 Xen Tools Agent가 동작합니다.
          이러한 Xen Tools Agent 자체가 비정상적으로 동작하거나, 또는 다른 요인에 의해 서버가 비정상적으로 동작하게 되면 “Server Status Check” 기능이 활성화됩니다.

    - ### 윈도우서버 Xentools 사용 가이드

      - Windows VM의 I/O 드라이버 및 관리 에이전트로 고성능의 I/O 서비스 제공하기 위해 사용되는 Tool

    - ### Server 복구

      - 네이버 클라우드 플랫폼에서는 메모리, CPU, 전원 공급 등 물리 서버의 장애에 대비하기 위해 High Availability(HA) 구조를 제공합니다.

        HA는 하드웨어에서 발생한 장애가 Virtual Machine(VM) 서버로 확대되는 것을 방지하기 위한 정책으로 호스트 서버에 장애가 발생하면 자동으로 호스트 서버 안에 있는 VM 서버를 안정된 다른 호스트 서버로 옮기는 Live Migration을 지원합니다.

        단, Live Migration을 진행할 수 없는 오류가 발생하면 VM 서버가 재시작(reboot) 됩니다.
        VM 서버 1대로 서비스를 운영하고 있다면 VM 서버 재시작으로 발생할 수 있는 장애 발생 빈도를 줄이기 위해 VM 서버 또한 다중화하는 것을 권장

  ## Storage

  - ### Object Stroage

    - ### Object Storage 사용 가이드

      - ### Object Storage 개요

        - Object Storage는 사용자가 언제 어디서나 원하는 데이터를 저장하고 탐색할 수 있도록 파일 저장 공간을 제공하는 서비스

        - 제한사항 및 한도

          - 버킷 수량 : 최대 1,000개 (※ 버킷 수량은 고객문의를 통해 요청하실 경우 한도 증가 가능합니다.)
          - 오브젝트 이름 문자열 길이(폴더path 포함) : 최대 1024 Byte
          - 업로드시 단일 오브젝트 최대 용량 : 콘솔에서 업로드시 파일당 최대 2GB, API 사용시 파일당 최대 10TB까지 업로드 가능합니다. (※ 버킷에 저장용량 제한은 없습니다.)
          - 객체 잠금 설정(WORM) 기능 적용 시, 보존 기간 만료 전까지 삭제 및 수정이 불가합니다.

        - AWS S3 compatible API를 제공하여 S3 Browser를 사용하여 사용 가능

        - Object Storage 요금 = 데이터 저장량 요금 + API 요청 수 요금 + 네트워크 전송 요금

          - 데이터 저장량 요금: 고객의 파일이 실제로 Object Storage에 저장된 데이터 저장량과 저장 시간에 따른 요금
          - API 요청 수 요금: Object Storage를 사용하기 위한 목록 조회, 업로드, 다운로드 요청 등의 API 요청에 따른 요금
          - 네트워크 전송 요금: 파일 다운로드에 따른 요금
            (VPC에서 사설 도메인을 이용할 경우 별도 요금이 발생합니다.)
          - Object Storage와 CDN+, Global CDN 상품 간에 발생하는 네트워크 전송 요금은 무과금 처리됩니다.

        - 크기

          - 콘솔은 업/다운 2GB 이하, 보다 큰건 API로

        - Lifecycle Management : 비용 절감을 위하여 장기보관 데이터는 Archive Storage에 저장하는데 이걸 스케쥴 기반으로 넘길 자동으로 넘길 수 있게 해주는 기능

          - overwright 기능 없음

        - VPC에서 Object Storage로 접속 시 아래와 같은 방법이 있습니다.

          \1. Public Subnet 내 서버

          - 공인 도메인 kr.object.ncloudstorage.com를 이용해 인터넷 기반의 통신이 가능합니다.
          - 사설 도메인 kr.object.private.ncloudstorage.com을 이용해서 사설 통신이 가능합니다.

          \2. Private Subnet 내 서버

          - 기본적으로 사설 도메인인 kr.object.private.ncloudstorage.com을 이용해서 통신이 가능합니다.
          - NAT Gateway를 이용하시면 공인 도메인인 kr.object.ncloudstorage.com을 이용해 통신하실 수 있습니다.

      - ### Java SDK

      - ### Python SDK

      - ### Javascript SDK

      - ### CLI

      - ### Sub Account 권한 관리

  - ### Archive Storage

    - ### Archive Storage 사용 가이드

      - ### Archive Storage 개요

        - Archive Storage는 자주 사용하지 않지만 장기간 저장이 필요한 데이터를 위해 저렴하게 저장공간을 제공하는 서비스
        - 의료 정보, 제조 정보 관리, 금융 거래 내역 등 컴플라이언스 준수를 위해 장기간 데이터 저장이 필요한 경우, 테이프 형태의 소산 백업에 대한 관리 부담이 상승하는 경우, 향후 분석을 위해 방대한 양의 데이터를 저장해야 하는 경우에 사용하시기를 권합니다.
        - 또한 Object Storage와 연계하여, 사용 빈도가 높은 데이터는 Object Storage에 저장을 하고, 빈도가 낮고 장기 저장이 필요한 데이터는 Archive Storage에 저장하신다면 TCO를 절약하실 수 있습니다.

      - ### 대용량 파일 관리 (DLO)

        - 대용량 파일을 여러 개의 segment object로 분할하여 동시에 업로드가 가능하며, 저장 가능한 최대 segment의 크기는 5GB입니다.
        - 따라서, 5GB 이상의 object은 반드시 분할하여 업로드 해야합니다.
        - segment object들은 매니페스트 파일을 생성하여 하나의 오브젝트로 접근가능하게 됩니다.
        - 매니페스트 파일에 segment object를 관리방식에 따라, Dynamic Large Object(DLO), Static Large Object(SLO) 2가지 방식이 있으며, 해당 가이드에서는 DLO 방식을 설명
        - 분할 크기는 분할 갯수 10000개를 넘지 않은 크기로 정해야합니다.
        - manifest object는 해당 object의 metadata를 갖고있으며 실제 데이터는 segment object에 링크되어 있습니다. 따라서, segment object 또는 manifest object 둘중 하나라도 삭제할 경우, object는 복구가 불가능합니다.

      - ### 대용량 파일 관리 (SLO)

      - ### 오브젝트 생명주기 관리

        - 오브젝트 단위로 원하는 시간에 자동으로 삭제되도록 설정하는 Expiring Objects 기능을 설명
        - X-Delete-At 혹은 X-Delete-After 헤더를 사용하여 설정할 수 있으며, 오브젝트 PUT(업로드) 요청에 헤더를 입력하여 설정할 수 있고 업로드 이후 POST 요청에 헤더를 입력하여 설정 및 변경
        - 생명주기 설정은 단일 object별로 적용 가능하므로, 생명주기 설정할 Object가 DLO/SLO로 업로드된 경우, segment object와 manifest object 개별로 생명주기 설정을 추가해야합니다.

      - ### Python SDK

      - ### Java SDK

      - ### Javascript SDK

      - ### CLI

      - ### S3 APII

  - ### NAS

    - ### NAS 사용 가이드

      - Linux Server와 Windows Server 모두 NAS를 마운트
      - Linux Server는 NFS 프로토콜, Windows Server는 CIFS 프로토콜 기반으로 NAS 볼륨을 마운트
      - NAS 볼륨은 네이버 클라우드 플랫폼 인프라 내에 있는 서버에서만 마운트
      - 여러 개 계정을 가지고 있는 회원인 경우, 다른 계정에 있는 서버의 사설 IP만 있으면 마운트 가능
      - 볼륨 최초 생성시 "볼륨 암호화 적용" 선택시 암호화된 볼륨으로 데이터 저장이 가능합니다. 생성된 볼륨은 "암호화볼륨 <-> 일반볼륨"으로 전환이 불가능 합니다.

    - ### Sub Account 권한 관리

  - ### Backup

    - ### Backup 사용 가이드

      - 백업 서비스는 클라우드 서버(VM)의 중요 데이터를 정기적으로 백업/보관하여 유사 시 데이터 복구를 통해 고객사의 비지니스 연속성을 보장하기 위해 제공되는 서비스
      - 백업 서비스 신청을 하면, 먼저 백업 Agent 설치
      - 모든 OS 플랫폼 파일 시스템 백업 및 DBMS(mssql, mysql)의 온라인 백업을 제공합니다. 이를 통해 안전하게 데이터를 보호할 수 있으며 복구 시 파일 시스템은 파일 단위부터 폴더 단위까지, DBMS는 table 단위부터 DB 단위까지 복구가 가능합니다.
      - 백업방식
        - 전체 백업과 증분 백업을 제공하고 두 가지 방식을 조합하여 아래와 같이 효과적인 백업 정책을 제공합니다. 단 DBMS의 경우 중요성을 고려하여 최대 1주 단위 백업까지 제공
          ![image-20211003141255918](https://raw.githubusercontent.com/redplug/shareimages/master/img/image-20211003141255918.png)
      -  백업된 데이터는 최소 1주부터 최대 52주까지 보관이 가능

  ## Database

  - ### MySQL

    - ### MySQL 서버 이미지 사용 가이드

      - "MySQL"은 세계에서 가장 많이 쓰이는 오픈 소스 관계형 데이터베이스(RDBMS)인 MySQL을 이용
      - 외부 접속 허용
        - 계정 권한 부여 : GRANT ALL PRIVILEGES ON *.* to '계정명'@'%' IDENTIFIED BY '비밀번호';
        - sudo vi /etc/mysql/mysql.conf.d/mysqld.cnf
          - bind-address 주석 처리
          - mysql 재시작
      - SQLSTATUS
        - 네이버클라우드에서 제공하는 MySQL 서비스에는 CLI(Command Line Interface) 형태의 모니터링 프로그램
        - MySQL의 내부 Status를 1초 단위로 볼 수 있도록 Binary 형태로 제공
        - 1초간의 MySQL Status를 Display를 하여 Real-Time으로 DB의 상태 변화를 볼 수 있습니다.

  - ### MSSQL

    - ### MSSQL 서버 이미지 사용 가이드

    - ### MSSQL 한글 환경으로 변경

    - ### MSSQL Log Collector (Lazylog) 사용 가이드

      - MSSQL 로그 수집기(LazyLog) 
        - SQL 서버 운영 시 모니터링 대상 서버의 설정이나, 프로그램의 쿼리 성능, 서버의 이벤트 로그, 성능 카운터의 베이스라인을 수집해 두는 것은 매우 중요합니다.
          이러한 베이스라인 데이터가 없다면 현재 서비스가 정상인지 (어제와 다른지) 판단에 오랜 시간이 걸릴 수 있습니다. 이에 네이버클라우드에서는 SQL 서버 로그 수집 프로그램을 배포하고 있으며, 수집된 데이터는 장애 분석이나 성능 분석용 필수 데이터(**윈도우 성능카운터, 윈도우 이벤트로그, SQL 에러로그 Agent 로그, 쿼리 구문, 쿼리 실행계획, 대기, 잠금 등 필수 DMV 스냅샷**)입니다.
        - **그 수집 콘솔 응용 프로그램(LazyLog)은 SQL Server 2008, 2012, 2014, 2016을 지원**

    - ### MSSQL Log Collector (Lazylog) 다운로드

  - ### CUBRID

    - ### CUBRID 서버 이미지 사용 가이드

      - 국내 유일 Open Source DBMS(Database Management System:이하 DBMS)로서, 데이터베이스 서버, 브로커, CUBRID 매니저로 구성됩니다.
        데이터베이스 서버는 다른 DMBS와 마찬가지로 Table, Column단위의 구조를 사용하여 Record단위의 데이터를 조회/변경/추가/삭제를 합니다.
        브로커는 서버와 외부 응용 프로그램 간의 통신을 중계하는 CUBRID 전용 미들웨어로서, 커넥션 풀링, 모니터링, 로그 추적 및 분석 기능을 제공합니다.
        CUBRID Manager(이하 CM)는 데이터베이스와 브로커를 원격에서 관리할 수 있는 GUI 툴입니다. 또한, CUBRID 매니저는 사용자가 데이터베이스 서버에 SQL 질의를 수행할 수 있는 편리한 기능의 질의 편집기를 제공합니다.

        CUBRID는 2008년 11월 CUBRID 2008 R1.0 버전 출시를 시작으로, 2014년 9.3 버전을 출시했으며 계속해서 발전되고 있습니다. 네이버클라우드에서 제공하는 CUBRID 설치형 서비스에는 안정성이 검증된 CUBRID 9.2 버전을 지원합니다.

  - ### REDIS

    - ### REDIS 서버 이미지 사용 가이드

      - Redis(Remote Dictionary Server)는 Open Source 기반의 in memory data structure store
      - String, hashes, lists, sets, sorted sets과 같은 data structure를 제공하며 관계형 데이터베이스 시스템(Relational Database Management System:이하 RDBMS)이 아닌 key/value의 형태로 Data
      - 네이버클라우드에서는 Redis 4.0 버전을 제공하며 Basic Install수준의 기 설치된 이미지를 지원

  - ### Tibero

    - ### Tibero 사용 가이드

      - 차별화된 아키텍쳐와 다양한 기능이 반영된 DBMS인 Tibero를 Server 설치형

  - ### Cloud DB for MySQL

    - ### 퀵스타트 가이드

    - ### DB 서버 생성 및 접근 가이드

      - CloudDB for MySQL은 MySQL 데이터베이스를 몇 가지 설정과 클릭만으로 간편하게 구축하고, 네이버의 최적화 설정을 통해 안정적으로 운영하며, 장애가 발생하면 자동 복구하는 완전 관리형 클라우드 데이터베이스 서비스
      - 어떤 서비스에서 DB를 사용하고 사용량이 얼마나 될지를 미리 예측하여, 어떤 서버 타입으로 생성할지 미리 결정하셔야 합니다.
      - 또한 고가용성 여부에 따라 장애 자동 복구와 백업 여부가 변경되므로 역시 신중한 고려가 필요합니다.
      - 몇대가 생성되는가?
        - 기본2대(Active + Standby), 스탠드 얼론 1대
      - 제약사항
        - 동일 타입내 스펙 변경 가능
        - 하나의 DB서비스내 동일 스펙만 가능
        - 스펙 변경은 DB재시작 필요
      - 기본 디스크 50GB, 용량 변경 불가, CentOS 7.8 설치
      - 데이터 스토리지
        - 10GB부터 10GB단위로 6000GB까지 자동 증가
        - HDD or SSD 선택 가능
      - 스토리지 엔진 : InnoDB 스토리지 엔진과 Memory 엔진만 지원

    - ### DB 서버 상세 보기 및 설정 가이드

      - Slave는 10개까지 생성 가능

    - ### Monitoring 사용 가이드

      - 최근 60일 이내 모니터링 지표 확인가능
      -  Query Timeline은 72시간 이내 지표 확인 가능
      - 

    - ### Backup 사용 가이드

      - 하루에 한번 매일 실행, 최대 30일 보관
      - 자동으로 설정할 경우 임의의 시간이 선택되며, 이후 매일 해당시간에 백업이 시작됩니다.
      - 사용자 정의로 시간을 설정한 경우 사용자가 설정한 시간에 시작됩니다.

    - ### Event 사용 가이드

      - Cloud DB for MySQL 서버에서 발생한 이벤트 이력을 확인

    - ### phpMyAdmin 설치 및 사용 가이드

    - ### DB 서버 로드밸런서 설정 가이드

      - Cloud DB for MySQL에서 로드밸런서는 한대 이상의 Slave DB 서버를 로드밸런서로 묶어 읽기 부하 분산을 하기 위해 사용합니다.

    - ### DB 서버 외부 접근 가이드

      - SL VPN 상품을 사용하면, 개인 PC에 SSL VPN Client를 설치하여 DB Server로 접근
      - Public 도메인을 사용하면 네이버 클라우드 플랫폼 외부에서도 DB Server로 접근

    - ### Sub Account 권한 관리 (VPC)

  - ### Cloud DB for Redis

    - ### 퀵스타트 가이드

    - ### Redis 서버 생성 및 접근 가이드

      - 원활한 Cloud DB for Redis 서비스 운영을 위해 아래 명령어들은 사용할 수 없습니다.

        일부 명령어들에 대해서는 API를 지원할 예정입니다.

        - BGREWIRTEAOF
        - BGSAVE
        - SAVE
        - SLAVEOF
        - FLUSHALL
        - FLUSHDB
        - CONFIG
        - KEYS
        - MIGRATE
        - SHUTDOWN

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

      - **Q. DB Config Group이 무엇인가요?**

        - Cloud DB 상품의 서비스 특성에 맞게 sp_configure와 trace flag를 변경해 Config Group을 생성할 수 있습니다. 생성된 Config Group은 여러 Cloud DB 서비스에 적용이 가능합니다.
        - MSSQL 설치 기본값이 포함된 Config Group이 기본 제공됩니다.

        **Q. Config Group 화면에서 수행 가능한 작업에는 어떤 것이 있나요?**

        - Cloud DB 서비스에 적용 가능한 Config Group을 생성, 변경, 삭제할 수 있습니다.
          - Config Group 변경 : Config Group을 이미 적용한 Cloud DB 서비스가 있다면 해당 DB 서버들도 변경 적용되며, 재시작이 필요한 변경은 Cloud DB 서버 재시작 후에 적용됩니다.
          - Config Group 삭제 : 삭제하려는 Config Group이 적용된 서버가 있을 경우, 삭제되지 않습니다.
          - 기본 제공되는 Config Group은 변경 및 삭제할 수 없습니다.

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

      - 원하는 CentOS 버전에 PostgreSQL을 몇 가지 설정과 클릭만으로 간편하게 구축할 수 있는 Basic Install 기능만을 지원하는 상품
      - "PostgreSQL"은 확장 가능성 및 표준준수를 강조하는 오픈소스 객체-관계형 데이터베이스(ORDBMS)인 PostgreSQL을 이용
      - 제공 타입
        ![image-20211004102958818](https://raw.githubusercontent.com/redplug/shareimages/master/img/image-20211004102958818.png)
      - 리눅스, 50GB 제공

  - ### MariaDB

    - ### MariaDB 사용 가이드

      - "MariaDB"는 MySQL과 동일한 소스코드를 기반으로 한 오픈소스 관계형 데이터베이스(RDBMS)인 MariaDB를 이용
      -  **DB 설치 이외 부분에 대해서는 기술 지원하지 않고 있습니다**.

  - ### MongoDB

    - ### MongoDB 서버 이미지 사용 가이드

      - MongoDB는 전세계에서 가장 인기 있고 많이 사용하고 있는 OpenSource 기반의 Document Store Database
      - MongoDB는 MySQL과 같은 RDBMS의 특성과, 일반적인 NoSQL 특성을 다 가지고 있는 DBMS
    
    - ### MongoDB 사용하기 전에 Linux OS 설정하기
    
    - ### MongoDB Cluster 구성하기
    
      - 3대 이상의 Member로 구성
    
      - Member Role(Primary, Secondary, Arbiter)
    
      - 각각의 role에 따라 Replica Set 구성에 차이가 있을 수 있는데 주로 3개의 Member에 대하여 P-S-A(Primary-Secondary-Arbiter) 혹은 P-S-S(Primary-Secondary-Secondary) 구성이 일반적입니다.
        ![image-20211004103221133](https://raw.githubusercontent.com/redplug/shareimages/master/img/image-20211004103221133.png)
    
      - 만일 사용하고자 할 mongodb에서 처리해야 할 데이터량이 많아 분산 처리가 필요할 경우 등 하나의 replica Set만으로는 운영에 어려움이 있을 경우 mongodb에서 제공하는 ‘Sharding’ 기능을 사용할 수 있습니다.
    
        Sharding 기능을 이용하여 다수의 replica set을 분산 구성한 형태를 “Sharded Cluster”라고 부르며 이는 MongoDB의 핵심 기능 중 하나입니다.
    
    - ### Public IP 기능 사용하여 외부와 연동하기
    
    - ### Compass로 MongoDB 관리하기
    
    - ### CLI로 MongoDB 모니터링하기

  ## Network

  - ### VPC

    - ### VPC 개요

      - VPC(Virtual Private Cloud)는 퍼블릭 클라우드 상에서 제공되는 고객 전용 사설 네트워크를 의미합니다.
      - 계정마다 VPC 최대 3개
      - 각 VPC 최대 넷마스크 
      - `0.0.255.255/16` (IP 65,536개) 크기의 네트워크 주소 공간을 제공
      - Subnet(Subnet)은 VPC 네트워크 공간을 세분화하여 사용할 수 있는 기능입니다. 필요에 따라 Internet Gateway와 연결하여 인터넷 통신을 지원
      - ACG vs Network ACL / 나올법해서 기억해두면 좋을듯
        ![image-20211004103457826](https://raw.githubusercontent.com/redplug/shareimages/master/img/image-20211004103457826.png)
      - VPC 간 내부통신은 VPC Peering를 통해 구성
      - 사용 한도
        ![image-20211004103559231](https://raw.githubusercontent.com/redplug/shareimages/master/img/image-20211004103559231.png)

    - ### 사용자 시나리오

      - ### 시나리오 1. 단일 Public Subnet

      - ### 시나리오 2. Public과 Private Subnet

      - ### 시나리오 3. Public과 IPsec VPN 연결 Subnet

      - ### 시나리오 4. VPC간 사설 통신 (Peering 구성)

    - ### 보안

      - ### 보안 개요

      - ### Deny-Allow Group 사용 가이드

        - 현재 제공가능한 Deny-Allow Group의 수량은 최대 **4개/vpc** 입니다.
        - Deny-Allow Group에 등록할 수 있는 IP의 수량은 최대 **100개/Group** 입니다.
        - Deny-Allow Group내 IP는 중복등록 될 수 없습니다.

    - ### VPC 세부 구성 요소

      - ### VPC/Subnet

        - VPC에 새로운 Subnet을 추가하려면 **VPC 주소 범위 내에서** Subnet의 주소 범위를 지정
        -  Subnet은 인터넷과 연결되는 **Public Subnet**과 폐쇄적인 **Private Subnet**으로 구분
      
      - ### NAT Gateway
      
        - NAT Gateway는 VPC 내부 네트워크 사용만 가능한 Private Subnet내의 자원에 인터넷 연결을 제공
        - NAT Gateway는 각 Zone당 1개씩 생성 가능

      - ### VGW
      
        - Site to Site VPN
        - Virtual Private Gateway(VGW)는 VPC와 IPsec VPN 또는 Cloud Connect를 연결하기 위한 접점
      
      - ### Peering
      
        - VPC Peering은 단방향 통신만 가능하므로, TCP 등 양방향 통신이 요구되는 경우에는 요청 VPC와 수락 VPC를 맞바꾸어 2개를 생성 하셔야 합니다.
      
      - ### Route Table
      
        - Route Table은 VPC내 자원의 네트워크 경로를 정의하여 트래픽 흐름을 제어
      
      - ### Sub Account 권한 관리

  - ### Load Balancer

    - ### Load Balancer 개요

      - Classic 플랫폼에서는 Classic Load Balancer를 제공하며, VPC 플랫폼에서는 Network Load Balancer / Application Load Balancer / Network Proxy Load Balancer 를 각각 제공함으로써 고객 서비스에 적합한 로드밸런서를 선택
      - Network Load Balancer : TCP분산, DSR(Direct Server Return) 구조 가능
      - Application Load Balancer : SSL 인증 암호화, HTTP, HTTPS
      - Network Proxy Load Balancer : TCP 세션유지, SSL인증, DSR불가

    - ### 사용 가이드

      - ### Target Group

        - Target Group은 하나 이상의 등록된 대상에 요청을 분배하는데 사용됩니다. 즉, 요청을 처리할 대상(서버)에 대한 집합이며, 이는 Load Balancer 서비스에서만 사용됩니다. Load Balancer의 리스너를 생성할 때 동작에 대한 Target Group을 지정하고, 조건에 따라 트래픽을 분배하게 됩니다.

      - ### Application Load Balancer

      - ### Network Load Balancer

      - ### Network Proxy Load Balancer

      - ### Classic Load Balancer

    - ### Load Balancer 부가 기능

    - ### Sub Account 권한 관리

  - ### Global DNS

    - ### DNS 리소스 레코드 안내서

      - 레코드 종류
        - SOA : SOA 레코드는 해당 도메인(zone) 마다 반드시 기술되어야 하며 authority, 수정불가
        - A : ipv4 맵핑
        - AAAA : ipv6 맵핑
        - NS : 네임서버
        - PTR ; 역방향(IP) 맵핑
        - CNAME : Alias
        - MX : 메일서버
        - SPF : 메일 보안관련(발송자) 확인용
        - TXT : SPF, DKIM, 인증서 등록등에 활용
        - SRV :  서비스의 위치(호스트네임 과 포트번호)를 저장하기 위해서 사용하는 레코드
        - CAA :  도메인에 대한 인증서를 발급할 수 있는 CA (인증 기관)를 지정할 수 있도록 하는 DNS 레코드

    - ### Global DNS 사용 가이드

      - 인터넷에서 사용하는 도메인 이름을 실제로 접속 가능한 주소로 식별해서 찾을 수 있게 하는 서비스
      - 도메인 구매/등록은 타 등록기관에서 가능
      - 타 기관에서 네임서버 등록하면 가능함

    - ### Sub Account 권한 관리

  - ### CDN+

    - ### CDN+ 사용 가이드

      - 국내 CDN 상품에 보다 안정적으로 다양한 기능을 제공하도록 개선된 CDN 플랫폼
      - 대용량 콘텐츠 전송
      - 다양한 원본 서버 지원
      - 강력한 콘텐츠 전송 보안
      - 네이버 클라우드 플랫폼의 타 상품과 연계 가능
      - 용어 설명
        ![image-20211004104908405](https://raw.githubusercontent.com/redplug/shareimages/master/img/image-20211004104908405.png)

  - ### Global CDN

    - ### Global CDN 사용 가이드

      - Global CDN은 전 세계 거점에 위치한 캐시 서버를 통해 사용자에게 빠르고 안전하게 콘텐츠를 전송하는 서비스
      - Global 콘텐츠 전송
      - 다양한 원본 서버 지원
      - 강력한 콘텐츠 전송 보안
      - 고속 Purge 기능
      - 국내 및 중국내 서비스에 대한 품질 보장하지 않음
        - 국내는 CDN+ 사용
        - 중국은 ICP(Internet Content Provider) License가 필요

  - ### IPsec VPN

    - ### IPsec VPN 사용 가이드

      - ### IPsec VPN 개요

        - VPN은 가상 사설망(Virtual Private Network)의 약자로, 외부에서 접근할 수 없는 사설망에 내 PC나 네트워크를 연결시키는 방법을 말합니다.
        - 사설망과의 연결은 가상 터널을 통해 이루어지며, 이 가상 터널을 IPsec(Internet Protocol Security)으로 암호화하여 보호하는 것이 IPsec VPN입니다.
      
      - ### Cisco
      
      - ### Fortinet
      
      - ### Juniper
      
      - ### Paloalto

  - ### NAT Gateway

    - ### NAT Gateway 사용 가이드

      - NAT는 네트워크 주소 변환(Network Address Translation)의 약자로, 비공인 네트워크에 속한 여러 개의 호스트가 하나의 공인 IP 주소를 사용하여 인터넷에 접속하는 방법
      - 클라우드 플랫폼 내부에 있는 고객의 서버가 인터넷상의 고객의 호스트 혹은 고객과 연관이 있는 공인 IP 주소를 가진 호스트와 연결할 수 있도록 NAT 서비스를 제공하는 Gateway입

  - ### Global Route Manager

    - ### Global Route Manater 사용 가이드

      - Global Route Manager는 DNS 기반의 다양한 방법을 통해 네트워크 트래픽을 안정적으로 로드밸런싱하는 GSLB(global server load balancing) 상품
      - Global Route Manager는 DNS 기반에서 동작
      - 로드밸런싱타입과 추가 가능한 리소스 정보
        ![image-20211004105246961](https://raw.githubusercontent.com/redplug/shareimages/master/img/image-20211004105246961.png)

  - ### DNS

    - ### DNS 리소스 레코드 안내서

      - 이버 클라우드 플랫폼 DNS의 리소스 레코드를 설명하고, 레코드 추가 절차와 주의 사항 등을 안내
    
    - ### DNS 사용 가이드

  ## Media

  - ### VOD Transcoder (Deprecated) : 없어질꺼라 따로 정리 안함

  - ### Image Optimizer

    - ### Image Optimizer 사용 가이드

      - mage Optimizer는 원본 이미지를 모바일, 태블릿, PC 등 다양한 기기의 해상도에 맞게 손쉽게 리사이징 할 수 있는 클라우드 기반의 실시간 이미지 변환 서비스

    - ### Query String 작성 가이드

      - 섬네일 호출 URL은 상품 등록 당시의 [CDN 도메인] + [오브젝트 스토리지 내의 파일 경로] + [섬네일 생성 옵션]과 같이 3가지 영역으로 생성
      - 형식: `https://{CDN-DOMAIN}/{FILE-PATH-IN-OBJSTORAGE}?{QUERYSTRINGS}`

  - ### Live Station

    - ### Live Station 사용 가이드

      - Live Station은 실시간 라이브 방송 서비스 구축에 필요한 모든 기능을 제공하는 영상 인코딩 플랫폼
      - Live Station을 통해 단일 RTMP(Real Time Messaging Protocol) 원본 스트림을 웹 인터페이스를 통하여 쉽고 빠르게 여러 개의 Multi-bitrate 출력 스트림을 만들어낼 수 있으며, 영상을 HLS(Http Live Streaming)로 패킷화(Packetizing)하여 전송
      -  라이브 미디어 영상을 손쉽게 타 플랫폼으로 동시 송출 가능한 Re-Stream 기능도 제공

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

      - VOD Station은 저장된 영상을 다양한 디바이스에서 시청할 수 있도록 변환하는 인코딩 기능과 동영상 파일을 패킷타이징하여 네트워크를 효율적으로 사용할 수 있는 스트리밍 기능을 제공하는 VOD 전용 서비스
      - 특징
        - **하나의 상품으로 인코딩과 송출 가능**: 여러 가지 VOD 서비스 상품을 고민할 필요 없이 VOD Station 하나로 인코딩과 스트리밍이 가능합니다.
        - **영상의 길이와 해상도에 따른 합리적 과금**: 영상의 길이와 코딩 후 변환된 해상도에 따라 요금이 책정되므로 합리적인 비용으로 서비스를 이용할 수 있습니다.
        - **고품질의 안정적인 스트리밍**: Progressive Download 방식이 아닌 영상을 패킷타이징하여 송출하는 방식이므로 안정적인 품질로 스트리밍을 제공할 수 있습니다.
        - **간편한 CDN 생성**: CDN(Content Delivery Network) 선택 옵션을 통해 VOD 스트리밍 서비스에 최적화된 CDN을 쉽게 생성할 수 있습니다.
        - **상품 간의 유연한 연동**: 인코딩, 보안, 비디오 플레이어와의 연동 등 VOD 서비스에 필요한 상품 간의 유연한 연동성을 제공합니다.
      - 기능
        - **인코딩**: 고비용의 미디어 인코딩 인프라를 직접 구축하거나 운영할 필요 없이 클라우드 환경에서 손쉽게 파일의 포맷을 변경하거나 멀티스크린에 맞는 다양한 사이즈로 영상 변환 작업을 수행할 수 있습니다.
        - **On-the-fly 패킷타이징**: 사용자가 VOD 스트리밍을 요청하면 Object Storage의 MP4 파일을 설정된 Segment Duration 단위로 패킷타이징을 진행합니다. 네트워크를 효율적으로 사용할 수 있으며, 서비스 부하에 대한 리스크를 차단합니다.
        - **템플릿 인코딩 설정**: 자주 사용되는 옵션들을 모아 기본 인코딩 설정 목록으로 제공하여 복잡한 인코딩 옵션들을 설정할 필요 없이 목록에서 선택해 사용할 수 있습니다.
        - **DRM**: VOD 스트리밍 패킷에 DRM을 적용하여 콘텐츠 보안을 강화할 수 있습니다. 파일 자체에 DRM을 적용하여 별도 관리하고 서비스하던 기존의 방법보다 빠르고 쉬우면서도 견고한 보안성을 제공합니다. 유료 콘텐츠 서비스에서의 불법 다운로드 리스크를 해소할 수 있습니다.
        - **썸네일 추출**: 비디오 인코딩 작업을 수행하면서 원본 영상 파일로부터 고품질 썸네일 이미지를 추출할 수 있습니다. 추출한 썸네일을 인코딩한 출력 영상 파일과 별도로 다른 파일 스토리지 경로에 저장할 수 있으며, CDN과 연동하여 손쉽게 서비스에 활용할 수 있습니다.
        - **최적의 CDN 생성(선택 옵션)**: 미디어 서비스의 품질을 위해 필요한 CDN을 설정하는 것은 매우 복잡하지만, VOD Station은 채널 설정 완료와 동시에 이에 맞는 최적의 CDN을 자동으로 설정하여 제공합니다.

    - ### VOD Station 사용 준비

    - ### VOD Station 시작

    - ### VOD Station 사용

      - ### 미디어 인코딩

      - ### 스트리밍 채널 설정

      - ### VOD 스티리밍

    - ### VOD Station 문제 해결

      - 미디어 변환 관련
        - **UPLOAD_ERROR**:
          **원인**: 출력 Object Storage 버킷에 인코딩이 완료된 출력 비디오 파일 업로드 중 오류 발생
          **해결 방법**: Object Storage의 버킷 목록에서 카테고리에 지정된 파일 경로에 출력 파일 폴더가 있는지 확인하거나 새로고침을 실행한 후 다시 시도해 주십시오.
        - **DOWNLOAD_ERROR**:
          **원인**: 인코딩 진행 중 Object Storage에서 원본 비디오 파일이 변경되거나 삭제됨
          **해결 방법**: Object Storage의 해당 경로에서 원본 파일이 있는지 확인하고, 필요한 경우 다시 업로드한 후 진행해 주십시오.
        - **FILE_NOT_FOUND**:
          **원인**: 선택한 원본 비디오 파일이 Object Storage 내에 존재하지 않음
          **해결 방법**: Object Storage의 해당 경로에 원본 파일이 있는지 확인해 주십시오. 원본 파일을 다시 업로드하거나 다른 파일을 선택한 후 진행해 주십시오.
        - **FILE_ALREADY_EXISTS**:
          **원인**: 같은 이름의 출력 비디오 파일이 출력 Object Storage 내에 존재함
          **해결 방법**: 출력 Object Storage 버킷에서 같은 이름을 가진 파일의 이름을 변경해 주십시오.
        - **WRONG_INPUT_FILE**:
          **원인**: 지원하지 않는 형식의 원본 비디오 파일 사용
          **해결 방법**: VOD Station이 지원하는 형식의 비디오 파일을 사용해 주십시오. 지원되는 파일 사양은 [서비스 사양](https://guide.ncloud-docs.com/docs/vodstation-vodstationprep#서비스사양)을 참고해 주십시오.
        - **TRANSCODING_ERROR**:
          **원인**: 원본 비디오 파일 속성이 일반적이지 않아 변환할 수 없음
          **해결 방법**:
          - 원본 비디오 파일 헤더를 추출할 수 없거나 재생 시간(Duration)이 정상적이지 않은 경우일 수 있습니다. mediainfo와 같은 비디오 파일 속성을 확인할 수 있는 프로그램을 이용하여 VOD Station이 지원하는 비디오 또는 오디오 형식인지, 헤더의 재생 시간과 비디오/오디오 재생 시간이 동일한지 확인해 주십시오. 지원되는 파일 사양은 [서비스 사양](https://guide.ncloud-docs.com/docs/vodstation-vodstationprep#서비스사양)을 참고해 주십시오.
          - 원인 확인이 어렵다면 네이버 클라우드 플랫폼 포털의 고객 문의 기능을 이용해 문의해 주십시오.
      - VOD 스트리밍 관련
        - 다음은 VOD 스트리밍과 관련해 발생할 수 있는 오류 메시지입니다.
          - **URL 생성 호출이 실패하였습니다.**
            **원인**: Object Storage의 버킷에서 파일이 유실되거나 오류 발생
            **해결 방법**: Object Storage의 버킷 목록에서 해당 위치에 파일이 있는지 확인하거나 새로고침을 실행한 후 다시 시도해 주십시오

    - ### VOD Station 권한 관리

    - ### VOD Station 릴리즈 노트

  - ### Video Player

    - ### Video Player 콘솔 사용 가이드

      - 이버 클라우드 플랫폼의 비디오 플레이어는 최신의 네이버 미디어 플레이어를 기반으로 개발된 클라우드 전용 상품

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
