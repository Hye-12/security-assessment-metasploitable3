# Ubuntu 취약점 분석

## 개요

Metasploitable3 Ubuntu 14.04 환경을 대상으로 서비스 식별, 취약점 분석 및 공격 가능성 검증을 수행하였다.

진단 결과 ProFTPD, Samba, Apache Continuum, CUPS, MySQL, SSH 등 다양한 서비스에서 공개 취약점, 정보 노출 및 취약한 인증 정책이 확인되었다.

특히 Apache Continuum 원격 코드 실행 취약점을 이용하여 시스템 접근이 가능하였으며, 이후 데이터베이스 분석 및 계정 확보를 통해 추가적인 시스템 접근 가능성을 확인하였다.

---

## 진단 대상 서비스

| 서비스              | 포트   | 주요 내용            | 위험도      |
| ---------------- | ---- | ---------------- | -------- |
| ProFTPD          | 21   | FTP 서비스 분석       | Medium   |
| Samba            | 445  | 공유 자원 및 정보 노출 확인 | Medium   |
| CUPS             | 631  | 서비스 정보 노출        | Medium   |
| Apache Continuum | 8080 | 원격 코드 실행(RCE)    | Critical |
| MySQL            | 3306 | 계정 정보 저장 및 접근 가능 | High     |
| IRC              | 6667 | 서비스 정보 확인        | Low      |
| OpenSSH          | 22   | 계정 기반 원격 접속      | High     |

---

## 주요 발견 사항

### 원격 코드 실행 가능

* Apache Continuum

공개 취약점을 이용하여 원격 코드 실행 및 시스템 접근 가능성을 확인하였다.

### 계정 및 인증 정보 노출

* MySQL Payroll 데이터베이스
* SSH 계정 정보 확보

데이터베이스 분석 과정에서 계정 정보를 확보할 수 있었으며, 이를 이용한 추가 접근 가능성을 확인하였다.

### 정보 노출

* CUPS
* Samba
* FTP

서비스 설정 및 시스템 정보를 통해 공격자가 추가 공격에 활용할 수 있는 정보가 확인되었다.

### 권한 상승 가능

* sudo 설정 분석
* 권한 관리 취약점 확인

시스템 내부 접근 이후 Root 권한 획득 가능성을 확인하였다.

---

## 취약점 상세 분석

### Critical

* [Apache Continuum](./01_Apache_Continuum.md)

### High

* [MySQL](./05_MySQL.md)
* [OpenSSH](./07_OpenSSH.md)

### Medium

* [ProFTPD](./01_ProFTPD.md)
* [Samba](./02_Samba.md)
* [CUPS](./03_CUPS.md)

### Low

* [IRC](./06_IRC.md)

---

## 요약

Ubuntu 환경에서는 Apache Continuum의 원격 코드 실행 취약점이 가장 위험도가 높은 취약점으로 확인되었다.

또한 데이터베이스 및 서비스 분석 과정에서 계정 정보 확보가 가능하였으며, 확보된 계정을 기반으로 시스템 내부 접근 및 권한 상승이 가능하였다.

이는 공개 취약점 관리뿐 아니라 계정 관리, 접근 통제, 최소 권한 원칙 적용이 중요함을 보여준다.
