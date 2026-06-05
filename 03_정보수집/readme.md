# 정보 수집 (Reconnaissance)

## 개요

침투 테스트 수행 전 대상 시스템의 운영체제, 서비스, 포트 및 취약점을 식별하기 위해 정보 수집을 수행하였습니다.

정보 수집은 Nmap, OpenVAS, Nessus를 활용하여 진행하였으며, 자동화 도구 결과와 실제 서비스 상태를 비교 검증하였습니다.

---

## Nmap 포트 스캔

### Windows Server 2008 R2

#### 주요 서비스

- FTP (21)
- HTTP (80)
- SMB (139, 445)
- GlassFish (4848)
- Jenkins (8484)
- Elasticsearch
- Axis2

---

### Ubuntu 14.04

#### 주요 서비스

- SSH (22)
- HTTP (80)
- MySQL (3306)
- Apache Continuum
- CUPS

---

## OpenVAS 취약점 진단

![OpenVAS Result](../images/openvas_result.png)

### 주요 결과

- Apache Continuum RCE
- 취약한 서비스 구성
- 정보 노출 취약점
- 인증 관련 취약점

---

## Nessus 취약점 진단

### 주요 결과

- 서비스 버전 노출
- 공개 취약점 식별
- 운영체제 정보 식별
- 취약한 구성 설정 발견

---

## 정보 수집 결과

정보 수집 결과 Windows와 Ubuntu 환경 모두 다수의 서비스가 외부에 노출되어 있었으며, 공개 취약점 및 정보 노출 취약점을 식별할 수 있었습니다.

수집된 정보를 기반으로 공격 가능성이 높은 서비스와 취약점을 선별하여 상세 분석을 진행하였습니다.
