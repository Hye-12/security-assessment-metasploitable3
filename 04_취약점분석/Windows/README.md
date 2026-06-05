# Windows 취약점 분석

## 개요

Metasploitable3 Windows Server 2008 R2 환경을 대상으로 서비스 식별, 취약점 분석 및 공격 가능성 검증을 수행하였다.

진단 결과 SMB, Apache Axis2, Elasticsearch, GlassFish, IIS, MySQL, OpenSSH 등 다양한 서비스에서 공개 취약점, 취약한 인증 정책 및 정보 노출 문제가 확인되었다.

특히 일부 서비스는 원격 코드 실행(Remote Code Execution) 및 시스템 장악으로 이어질 수 있는 고위험 취약점이 존재하였으며, 실제 침투 가능성을 검증하였다.

---

## 진단 대상 서비스

| 서비스            | 포트   | 주요 내용                 | 위험도      |
| -------------- | ---- | --------------------- | -------- |
| SMB            | 445  | MS17-010(EternalBlue) | Critical |
| Apache Axis2   | 8282 | 기본 계정 및 관리자 페이지 노출    | High     |
| Elasticsearch  | 9200 | 원격 코드 실행 가능성          | Critical |
| GlassFish      | 4848 | Directory Traversal   | High     |
| IIS (HTTP.sys) | 80   | 서비스 거부 공격(DoS)        | Medium   |
| MySQL          | 3306 | 기본 계정 및 비밀번호 미설정      | High     |
| OpenSSH        | 22   | 기본 계정 사용              | High     |
| Ruby on Rails  | 3000 | 서비스 정보 확인             | Low      |
| Microsoft FTP  | 21   | 서비스 접근 확인             | Low      |

---

## 주요 발견 사항

### 원격 코드 실행 가능

* SMB (MS17-010)
* Apache Axis2
* Elasticsearch

공격자가 원격에서 시스템 명령을 실행하거나 시스템 권한을 획득할 수 있는 위험성이 확인되었다.

### 취약한 인증 정책

* MySQL 기본 계정 사용
* OpenSSH 기본 계정 사용
* Apache Axis2 기본 관리자 계정 사용

기본 계정 및 취약한 인증 정책으로 인해 무단 접근 가능성이 존재하였다.

### 정보 노출

* GlassFish Directory Traversal
* 서비스 버전 정보 노출

공격자가 내부 구조를 파악하고 추가 공격을 수행할 수 있는 정보가 확인되었다.

### 서비스 가용성 저하

* IIS HTTP.sys 취약점

서비스 중단 및 시스템 장애를 유발할 수 있는 가능성이 확인되었다.

---

## 취약점 상세 분석

### Critical

* [SMB (MS17-010)](./01_SMB_MS17-010.md)
* [Elasticsearch](./04_Elasticsearch.md)

### High

* [Apache Axis2](./02_Apache_Axis2.md)
* [GlassFish](./03_GlassFish.md)
* [MySQL](./06_MySQL_Default_Password.md)
* [OpenSSH](./07_OpenSSH_Default_Account.md)

### Medium

* [IIS (HTTP.sys)](./05_IIS_HTTPsys.md)

### Low

* [Ruby on Rails](./08_Ruby_on_Rails.md)
* [Microsoft FTP](./09_Microsoft_FTP.md)

---

## 요약

Windows 환경에서는 공개 취약점, 기본 계정 사용, 인증 정책 미흡, 정보 노출 등 다양한 보안 문제가 확인되었다.

특히 MS17-010, Apache Axis2, Elasticsearch와 같이 시스템 장악으로 이어질 수 있는 취약점이 존재하였으며, 기본 계정 관리 미흡 또한 주요 위험 요소로 확인되었다.

이는 취약점 패치뿐만 아니라 계정 관리, 접근 통제 및 정기적인 보안 점검이 함께 수행되어야 함을 보여준다.
