# 취약점 분석

## 개요

정보 수집 단계에서 식별된 서비스 및 시스템을 대상으로 취약점 분석을 수행하였습니다.

OpenVAS, Nessus, Nmap 결과를 기반으로 실제 공격 가능성이 높은 취약점을 선별하였으며, 공개 취약점 검증과 수동 분석을 병행하여 위험도를 평가하였습니다.

---

## 분석 대상

### Windows

- FTP
- SMB
- GlassFish
- Jenkins
- Elasticsearch
- Axis2

### Ubuntu

- Apache
- Drupal
- Apache Continuum
- MySQL
- SSH
- CUPS

---

## 주요 발견 취약점

| 서비스 | 취약점 | 위험도 |
|----------|----------|----------|
| SMB | MS17-010 (EternalBlue) | Critical |
| Jenkins | 익명 접근 및 스크립트 실행 | Critical |
| Apache Continuum | Remote Code Execution | Critical |
| GlassFish | Directory Traversal | High |
| FTP | 평문 인증 정보 노출 | Medium |
| MySQL | 민감 정보 저장 | Medium |
| SSH | 취약 계정 사용 | Medium |

---

## 위험도 분류

### Critical

- 원격 코드 실행 가능
- 관리자 권한 획득 가능
- 시스템 전체 장악 가능

### High

- 중요 시스템 정보 노출
- 내부 파일 접근 가능

### Medium

- 인증 정보 노출
- 서비스 정보 노출
- 공격 경로 확보 가능

---

## 분석 결과

취약한 계정 정책, 공개 취약점, 과도한 권한 부여 및 정보 노출 취약점이 복합적으로 존재하는 것을 확인하였습니다.

특히 Apache Continuum RCE, Jenkins 익명 접근, MS17-010(EternalBlue) 취약점은 시스템 장악으로 직접 연결될 수 있는 고위험 취약점으로 확인되었습니다.

---

## MITRE ATT&CK 매핑

| 전술 | ID | 기술 |
|--------|--------|--------|
| Reconnaissance | T1595 | Active Scanning |
| Discovery | T1046 | Network Service Discovery |
| Initial Access | T1190 | Exploit Public-Facing Application |
| Execution | T1059 | Command and Scripting Interpreter |
| Privilege Escalation | T1548 | Abuse Elevation Control Mechanism |
| Credential Access | T1040 | Network Sniffing |
| Collection | T1005 | Data from Local System |

---

## 상세 분석

각 취약점의 상세 분석 내용은 아래 문서를 참고합니다.

- FTP
- SMB
- GlassFish
- Jenkins
- Apache Continuum
- Drupal
- MySQL
