<div>

### 병목이 생기는 이유를 이해하고 더 나은 구조를 고민하는 개발자 장지민입니다.

개발을 할 때 문제가 생긴 이유를 정확히 이해하는 데 시간을 쏟는 편입니다. <br/>
문제를 수치로 확인하고 여러 선택지의 트레이드오프를 비교하며, 팀이 납득할 수 있는 근거를 남기는 개발자로 성장하고 있습니다.
 

 > 관심 분야: MSA / Kafka / MultiCore-Processing


</div>

---
 
## Projects
 
**Courm — 이커머스 플랫폼 | `2025.12 – 2026.02` | BE 개발**

- PG사 장애가 전체 서비스로 전파되지 않도록 Monolithic 구조를 MSA로 전환했습니다.
- 분산 트랜잭션 정합성을 보장하기 위해 Choreography Saga 패턴을 적용했습니다.
- 개발 전 Application 설계 문서를 작성해 API 흐름, 이벤트 구조, 책임 범위를 팀원들과 공유했습니다.
- Kafka를 전담해 이벤트 발행·구독 구조를 설계하고 구현했으며, EKS 환경에 배포했습니다.

`Kafka` `Kubernetes` `AWS EKS` `MSA` `Redis` `PostgreSQL` 
 
---
 
**AIOps 클라우드 장애 대응 시스템 | `2025.09 – 2025.12` | 인프라 및 자동화 워크플로우 설계**
 
- Prometheus 임계치 기반으로 장애 징후를 선제 탐지했습니다.
- 탐지 이벤트를 LLM 분석으로 연결하고, Slack에서 운영자가 승인하도록 구성했습니다.
- 자동 대응의 할루시네이션 리스크를 줄이기 위해 Human-in-the-loop 구조를 적용했습니다.
- Airflow, Jenkins와 비교한 뒤 경량 실시간 파이프라인에 적합한 N8N을 채택했습니다.
  
`Kubernetes` `Prometheus` `Grafana` `N8N` `Llama3` `Gemini` `Slack`
 
---
 
**WaveFlow — 음악 협업 플랫폼 | `2025.06 – 2025.07` | FE 개발**
 
> 오디오 파형 렌더링 2,584ms → 379ms (85% 단축)
 
- 프론트엔드에서 오디오를 실시간 디코딩하며 발생하는 렌더링 병목을 확인했습니다.
- Python 서버가 Librosa와 Celery로 업로드 시점에 peaks 배열을 미리 추출하도록 변경했습니다.
- 추출된 peaks 데이터를 S3에 저장하고, 프론트엔드는 이를 받아 즉시 렌더링하도록 구성했습니다.

`React` `TypeScript` `Python` `Celery` `Amazon SQS` `S3` `WaveSurfer.js`
 
---
 
## Tech Stack
 
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

**Observability**
 
![Prometheus](https://img.shields.io/badge/Prometheus-E6522C?style=flat-square&logo=prometheus&logoColor=white)
![Grafana](https://img.shields.io/badge/Grafana-F46800?style=flat-square&logo=grafana&logoColor=white)
 
</div>
---
 
## Education
 
| 기간 | 내용 |
|------|------|
| 2025.03 – 2025.07 | **크래프톤 정글 8기** — CS 기초·시스템 프로그래밍·알고리즘 스터디 4개월 주도 |
| 2022.03 – 2027.02 (예정) | **한국외국어대학교** 언어인지과학과 / 컴퓨터공학과 복수전공 |
 
---

## More Info

[![Velog](https://img.shields.io/badge/Velog-20C997?style=for-the-badge&logo=velog&logoColor=white)](https://velog.io/@mingdul)
[![Gmail](https://img.shields.io/badge/Gmail-dd4e41?style=for-the-badge&logo=gmail&logoColor=white)](mailto:jmjang2122@gmail.com)
 

</div>
 
