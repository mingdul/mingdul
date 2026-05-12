
<div align="center">
<!-- Header Wave -->
<img width="100%" src="https://capsule-render.vercel.app/api?type=waving&color=0:0f2027,50:203a43,100:2c5364&height=120&section=header"/>
<!-- Typing Animation -->
<a href="https://git.io/typing-svg"><img src="https://readme-typing-svg.demolab.com?font=JetBrains+Mono&weight=600&size=22&pause=1000&color=4FC3F7&center=true&vCenter=true&width=600&lines=%22Why%3F%22+%EB%A5%BC+%EC%A7%88%EB%AC%B8%ED%95%98%EB%8A%94+%EB%B0%B1%EC%97%94%EB%93%9C+%EC%97%94%EC%A7%80%EB%8B%88%EC%96%B4;%EB%AC%B8%EC%A0%9C%EB%A5%BC+%EC%88%98%EC%B9%98%EB%A1%9C+%EC%A0%95%EC%9D%98%ED%95%98%EA%B3%A0+%EA%B5%AC%EC%A1%B0%EB%A1%9C+%ED%95%B4%EA%B2%B0%ED%95%A9%EB%8B%88%EB%8B%A4;%EC%96%B8%EC%96%B4%ED%95%99+%E2%86%92+CS+%E2%86%92+%EC%8B%9C%EC%8A%A4%ED%85%9C+%EC%97%94%EC%A7%80%EB%8B%88%EC%96%B4%EB%A7%81" alt="Typing SVG" /></a>
 
<br/>
# 장지민 · Jimin Jang
 
**`"왜?"라는 질문으로 시스템을 파고드는 백엔드 엔지니어`**
 
 
<br/>

[![Velog](https://img.shields.io/badge/Velog-20C997?style=for-the-badge&logo=velog&logoColor=white)](https://velog.io/@mingdul)
[![Gmail](https://img.shields.io/badge/Gmail-dd4e41?style=for-the-badge&logo=gmail&logoColor=white)](mailto:jmjang2122@gmail.com)
 
</div>
---
 
## 🧭 About Me
 
```
📚 한국외국어대학교 언어인지과학과 / 컴퓨터공학과 복수전공
🌱 크래프톤 정글 5기 수료 (2025.03 – 2025.07)
🔍 언어의 구조를 분석하듯, 시스템의 구조를 분석합니다
⚡ 수치로 문제를 정의하고, 기술 선택 근거를 먼저 따집니다
🎯 관심 분야: 고트래픽 백엔드 / MSA / 인프라 / 시스템 프로그래밍
```
 
---
 
## 🚀 Projects
 
### 🛒 Courm — 이커머스 플랫폼 `2025.12 – 2026.02` `4인 팀`
 
> **Kafka + MSA + EKS 기반 고트래픽 주문 처리 시스템**  
> `100VU 기준 43,344건 처리 · 성공률 99.12% · 평균 응답 69ms · TPS 35`
 
**핵심 설계 결정**
 
| 문제 | 선택 | 근거 |
|------|------|------|
| Monolithic → PG사 장애 시 서비스 전체 정지 | MSA + Choreography Saga | Orchestration의 단일 장애점 제거 |
| 동시 주문 처리 시 DB Lock 경합 | Redis Lua Script 원자 연산 | 커넥션 고갈 없이 재고 조회·차감 단일 처리 |
| MSA 분산 트랜잭션 불일치 | Transactional Outbox + Polling | CDC/Debezium 대비 운영 리소스 절감 |
| Kafka 메시지 순서 보장 + Hot Partition 방지 | orderId(UUID) Message Key | 동일 파티션 라우팅 + UUID 특성상 자연 분산 |
 
<details>
<summary><b>📐 인프라 상세 설계</b></summary>
- **Kafka**: Brokers 3, Partition 3, Replication Factor 3, min.insync.replicas 2
  - 파티션 산정: 목표 TPS(900) ÷ 파티션당 처리 TPS(300) = 3
  - ack-mode=RECORD + Retry 3회 + DLQ(DeadLetterPublishingRecoverer)
- **Kubernetes**: AWS EKS (ap-northeast-2, 멀티 AZ), Istio Gateway 트래픽 제어
- **GitOps**: ArgoCD 배포 자동화, Jenkins Agent CI 파이프라인
- **IaC**: Terraform (EKS, RDS, ElastiCache, ECR)
- **관측성**: Prometheus + Grafana + Tempo + Loki + Fluent Bit
- **동시성**: Redis TTL 15분 선점 → PaymentCompletedEvent 수신 후 DB 확정 차감
  - Redis 장애 시 Fail-Fast → DB 무결성 보호
</details>
`Kafka` `Kubernetes` `AWS EKS` `MSA` `Redis` `PostgreSQL` `Terraform` `ArgoCD` `Istio`
 
---
 
### 🤖 AIOps 클라우드 장애 대응 시스템 `2025.09 – 2025.12` `3인 팀 · 팀장`
 
> **LLM 기반 자동 장애 탐지 · 대응 파이프라인**
 
- Prometheus 임계치 기반 **선제 탐지** → LLM 분석 → Slack **Human-in-the-loop 승인**
- N8N 채택: Airflow · Jenkins 비교 후 경량 실시간 파이프라인 요건에 최적 판단
- 할루시네이션 리스크를 **운영자 승인 구조**로 제어
`Kubernetes` `Prometheus` `Grafana` `N8N` `Llama3` `Gemini` `Slack`
 
---
 
### 🎵 WaveFlow — 음악 협업 플랫폼 `2025.06 – 2025.07` `5인 팀`
 
> **오디오 파형 렌더링 2,584ms → 379ms (85% 단축)**
 
프론트엔드 실시간 디코딩이 병목임을 파악 →  
Python 서버(Librosa + Celery)가 업로드 시점에 peaks 배열 미리 추출 → S3 저장 → 즉시 렌더링
 
`React` `TypeScript` `Python` `Celery` `Amazon SQS` `S3` `WaveSurfer.js`
 
---
 
### 🖥️ PintOS OS 구현 `2025.05 – 2025.06` `KAIST`
 
> **C언어로 OS 핵심 서브시스템 직접 구현**
 
가상 메모리 · 시스템 콜 · 스레드 · 동기화 구현  
시스템 레벨 동작 원리를 코드로 검증
 
`C` `GDB` `Docker`
 
---
 
## 🛠 Tech Stack
 
<div align="center">
**Backend**
 
![Java](https://img.shields.io/badge/Java-ED8B00?style=flat-square&logo=openjdk&logoColor=white)
![Spring Boot](https://img.shields.io/badge/Spring_Boot-6DB33F?style=flat-square&logo=spring-boot&logoColor=white)
![Python](https://img.shields.io/badge/Python-3776AB?style=flat-square&logo=python&logoColor=white)
![C](https://img.shields.io/badge/C-00599C?style=flat-square&logo=c&logoColor=white)
 
**Message / Cache / DB**
 
![Kafka](https://img.shields.io/badge/Apache_Kafka-231F20?style=flat-square&logo=apache-kafka&logoColor=white)
![Redis](https://img.shields.io/badge/Redis-DC382D?style=flat-square&logo=redis&logoColor=white)
![PostgreSQL](https://img.shields.io/badge/PostgreSQL-4169E1?style=flat-square&logo=postgresql&logoColor=white)
![DynamoDB](https://img.shields.io/badge/DynamoDB-4053D6?style=flat-square&logo=amazon-dynamodb&logoColor=white)
 
**Infra / Cloud**
 
![AWS](https://img.shields.io/badge/AWS-232F3E?style=flat-square&logo=amazon-aws&logoColor=white)
![Kubernetes](https://img.shields.io/badge/Kubernetes-326CE5?style=flat-square&logo=kubernetes&logoColor=white)
![Terraform](https://img.shields.io/badge/Terraform-7B42BC?style=flat-square&logo=terraform&logoColor=white)
![Docker](https://img.shields.io/badge/Docker-2496ED?style=flat-square&logo=docker&logoColor=white)
![ArgoCD](https://img.shields.io/badge/ArgoCD-EF7B4D?style=flat-square&logo=argo&logoColor=white)
![Istio](https://img.shields.io/badge/Istio-466BB0?style=flat-square&logo=istio&logoColor=white)
 
**Observability**
 
![Prometheus](https://img.shields.io/badge/Prometheus-E6522C?style=flat-square&logo=prometheus&logoColor=white)
![Grafana](https://img.shields.io/badge/Grafana-F46800?style=flat-square&logo=grafana&logoColor=white)
 
</div>
---
 
## 📊 GitHub Stats
 
<div align="center">
<img height="160" src="https://github-readme-stats.vercel.app/api?username=mingdul&show_icons=true&theme=tokyonight&hide_border=true&count_private=true"/>
<img height="160" src="https://github-readme-stats.vercel.app/api/top-langs/?username=your-mingdul&layout=compact&theme=tokyonight&hide_border=true"/>
</div>
<div align="center">
[![GitHub Streak](https://streak-stats.demolab.com?user=mingdul&theme=tokyonight&hide_border=true)](https://git.io/streak-stats)
 
</div>
---
 
## 📚 Education
 
| 기간 | 내용 |
|------|------|
| 2025.03 – 2025.07 | **크래프톤 정글 5기** — CS 기초·시스템 프로그래밍·알고리즘 스터디 4개월 주도 |
| 2022.03 – 2027.02 (예정) | **한국외국어대학교** 언어인지과학과 / 컴퓨터공학과 복수전공 |
 
---

## Contact

[![Velog](https://img.shields.io/badge/Velog-20C997?style=for-the-badge&logo=velog&logoColor=white)](https://velog.io/@mingdul)
<br>
[![Gmail](https://img.shields.io/badge/Gmail-dd4e41?style=for-the-badge&logo=gmail&logoColor=white)](mailto:jmjang2122@gmail.com)
 
<div align="center">
*"언어의 구조를 분석하듯, 시스템의 병목을 분석하고 구조로 해결합니다."*
 
<img width="100%" src="https://capsule-render.vercel.app/api?type=waving&color=0:2c5364,50:203a43,100:0f2027&height=80&section=footer"/>
</div>
 
