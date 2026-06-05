# 초기 침투 (Initial Access)

## 개요

취약점 분석 단계에서 식별된 공개 취약점 및 노출된 서비스를 대상으로 초기 침투를 수행하였습니다.

Windows 및 Ubuntu 환경에 대해 각각 공격 경로를 분석하였으며, 실제 시스템 접근 가능 여부를 검증하였습니다.

---

## 공격 흐름

정보 수집
↓
취약점 분석
↓
공격 대상 선정
↓
초기 침투 성공
↓
권한 상승

---

## Windows 환경

### 공격 대상

- SMB
- Elasticsearch
- Axis2

### 수행 내용

- 공개 취약점 조사
- 서비스 접근 가능 여부 확인
- Metasploit 기반 공격 수행
- Meterpreter 세션 획득

### 결과

- 대상 시스템 접근 성공
- Meterpreter 세션 확보

---

## Ubuntu 환경

### 공격 대상

- Apache Continuum
- Drupal
- MySQL

### 수행 내용

- 서비스 버전 분석
- 공개 취약점 확인
- Apache Continuum RCE 취약점 악용
- Reverse Shell 획득

### 결과

- Ubuntu 시스템 접근 성공
- 일반 사용자 권한 획득

---

## 주요 활용 기술

| 구분 | 내용 |
|--------|--------|
| 서비스 분석 | Nmap, Nessus, OpenVAS |
| 취약점 검증 | CVE 분석 |
| 공격 수행 | Metasploit Framework |
| 원격 접근 | Reverse Shell, Meterpreter |

---

## 공격 결과

Windows와 Ubuntu 환경 모두 공개 취약점 및 서비스 설정 미흡으로 인해 원격 접근이 가능하였으며, 이후 권한 상승 단계로 진행할 수 있는 기반을 확보하였습니다.

---

## 상세 문서

- Windows 초기 침투
- Ubuntu 초기 침투
