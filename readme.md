### Naver Cloud Platform 의 NCA, NCP 시험준비를 위한 내용 정리

항목에 대한 소개와 시험에 나올법한 내용들(제한 사항이라던지 등등)이라고 생각되는 내용들만 정리

따라서 사용 가이드는 한번 전체적으로 읽을것을 권장함.

사용 가이드 : https://guide.ncloud-docs.com/docs/home

NCA시험은 Overview, Compute, Storage, Database, Network, Media

NCP추가항목 : Management, Analytics, Troubleshooting

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

    - ### 서버 정지 및 반납

  - ### Bare Metal Server

    - ### Bare Metal Server 개요

    - ### 서버 생성

    - ### 서버 정지 및 반납

- ### 접속 환경 설정

  - ### 공인 IP 사용 가이드

  - ### 포트 포워딩 이용 가이드

  - ### ACG 사용 가이드

- ### 서버 접속

  - ### 리눅스 서버 접속 가이드

  - ### 윈도우 서버 접속 가이드

- ### 스토리지 추가

  - ### 스토리지 추가 가이드

- ### 스토리지 크기 변경

  - ### 스토리지 크기 변경 가이드

- ### 내 서버 이미지

  - ### 내 서버 이미지 사용 가이드

- ### 서버 이미지 빌더

  - ### 서버 이미지 빌더 사용 가이드

- ### 스토리지 스냅샷

  - ### 스토리지 스냅샷 사용 가이드

- ### Ncloud Tool Kit(NTK)

  - ### NCloud Tool Kit 사용 가이드

- ### Private Subnet

  - ### Private Subnet 사용 가이드

- ### Network Interface

  - ### Network Interface 사용 가이드

  - ### Secondary IP 사용 가이드 (VPC)

- ### Init Script

  - ### Init Script 사용 가이드

- ### Auto Scaling

  - ### Auto Scaling 개요

  - ### Auto Scaling 사용 가이드

  - ### Auto Scaling 부가 기능

  - ### Auto Scaling 관리

  - ### Auto Scaling 권한 관리

- ### Cloud Functions

  - ### Cloud Functions 사용 가이드

  - ### Action 사용 가이드

    - ### Package, Action 사용 가이드

    - ### Sequence Action

    - ### Node.js

    - ### Python

    - ### Java

    - ### Swift

    - ### PHP

    - ### .Net

    - ### Go

    - ### VPC 리소스 연결 가이드

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