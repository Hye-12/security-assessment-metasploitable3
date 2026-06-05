# 권한 상승 (Privilege Escalation)

## 개요

초기 침투를 통해 획득한 일반 사용자 권한을 기반으로 시스템 내부 권한 구조를 분석하고 관리자 권한 획득 가능 여부를 검증하였습니다.

Windows 및 Ubuntu 환경 모두 권한 관리 설정의 취약점을 이용하여 최종적으로 최고 권한(SYSTEM, Root)을 획득할 수 있었습니다.

---

## 권한 상승 절차

초기 침투
↓
사용자 권한 확인
↓
권한 구조 분석
↓
취약 설정 확인
↓
관리자 권한 획득

---

## Windows 환경

### 수행 내용

- 사용자 및 서비스 권한 확인
- 실행 중인 서비스 분석
- 권한 상승 가능 경로 조사
- SYSTEM 권한 획득

### 결과

- NT AUTHORITY\SYSTEM 권한 확보
- 시스템 전체 제어 가능

---

## Ubuntu 환경

### 수행 내용

- 사용자 권한 확인
- sudo 설정 분석
- 권한 관리 정책 점검
- Root 권한 획득

### 결과

- Root 권한 확보
- 시스템 전체 제어 가능

---

## 주요 발견 사항

| 구분 | 내용 |
|--------|--------|
| Windows | 서비스 권한 설정 취약점 |
| Ubuntu | sudo NOPASSWD 설정 |
| 공통 | 최소 권한 원칙 미적용 |

---

## MITRE ATT&CK

| 전술 | ID | 기술 |
|--------|--------|--------|
| Privilege Escalation | T1548 | Abuse Elevation Control Mechanism |
| Discovery | T1082 | System Information Discovery |

---

## 분석 결과

권한 상승 단계에서는 운영체제 자체 취약점보다도 잘못된 권한 설정과 과도한 관리자 권한 부여가 더 큰 위험 요소로 작용하였습니다.

특히 Ubuntu 환경의 sudo 설정은 별도의 인증 없이 Root 권한 획득이 가능한 상태였으며, Windows 환경 역시 서비스 권한 설정을 통해 SYSTEM 권한 획득이 가능하였습니다.

---

## 상세 문서

- Windows 권한 상승
- Linux 권한 상승
