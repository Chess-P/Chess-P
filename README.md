## ![](./img/background/api.svg)

## 👨‍💻 Skills

<div align="center"> 
    <img src="./img/skills/html5.png" width="70" alt="HTML5" title="HTML5"/> 
    <img src="./img/skills/css.png" width="70" alt="CSS3" title="CSS3"/> 
    <img src="./img/skills/javascript.png" width="70" alt="JavaScript" title="JavaScript"/> 
    <img src="./img/skills/linux.png" width="70" alt="Linux" title="Linux"/> 
    <img src="./img/skills/php.png" width="70" alt="PHP" title="PHP"/> 
    <img src="./img/skills/java.png" width="70" alt="Java" title="Java"/> 
    <img src="./img/skills/spring-boot.png" width="70" alt="Spring Boot" title="Spring Boot"/>
    <img src="./img/skills/python.png" width="70" alt="Python" title="Python"/> 
    <img src="./img/skills/mysql.png" width="70" alt="MySQL" title="MySQL"/> 
    <img src="./img/skills/mariadb.png" width="70" alt="MariaDB" title="MariaDB"/>
    <img src="./img/skills/docker.png" width="70" alt="docker" title="docker"/>
</div>

## 💡 IDEs

<div align="center"> 
    <img src="./img/skills/intellij.png" width="70" alt="intellij" title="intellij"/>
    <img src="./img/skills/vscode48.png" width="70" alt="vscode48" title="vscode48"/>
    <img src="./img/skills/eclipse.png" width="70" alt="eclipse" title="eclipse"/>
</div>

## 🔭 Project

- #### PHP
  
  > 시스템 성능 개선
  
  ### 📌 개요
  
  과거 PHP로 구현된 실시간 인원 계수 시스템에서 **DB 처리 성능 이슈**를 겪으며, 속도 향상을 위한 성능 개선 작업을 수행했습니다.
  
  ---
  
  ### 🚩 문제 상황
  
  - 초당 수십 건 이상의 인원 수 데이터가 입력되며 DB에 병목 발생
  
  - 조건 기반 조회(시간, 장치, 유형)에 대해 응답 지연 발생
  
  - 데이터 중복 삽입으로 인한 용량 증가 및 불필요 연산 발생
  
  ---
  
  ### 🛠 개선 작업
  
  #### ✅ 1. Insert 성능 개선
  
  - **Batch Insert 적용**
    
    - 단건 반복 대신 다건 `INSERT INTO ... VALUES (...), (...), ...)` 형태로 처리
  
  - **트랜잭션 적용**
    
    - `autocommit`을 비활성화하고 일괄 커밋하여 I/O 비용 절감
  
  - **중복 방지 로직**
    
    - `ON DUPLICATE KEY UPDATE`, `INSERT IGNORE` 도입
  
  - **Connection 재사용**
    
    - `PDO` 기반 connection pool-like 구조 구성
  
  ---
  
  #### ✅ 2. Select 성능 개선
  
  - **인덱스 설계**
    
    - `(device_cd, count_type, count_time)` 복합 인덱스 생성
  
  - **불필요 컬럼 제거**
    
    - `SELECT *` 제거, 필요한 필드만 조회
  
  - **EXPLAIN 분석**
    
    - 인덱스 타는지 확인, 정렬/필터 순서 조정
  
  - **LIMIT 기반 페이지네이션 도입**
    
    - 전체 결과 반환 대신 일부만 응답
  
  ---
  
  ### 📈 개선 효과
  
  | 항목              | 개선 전   | 개선 후       | 비고                 |
  | --------------- | ------ | ---------- | ------------------ |
  | Insert 처리량      | 초당 30건 | 초당 500건 이상 | 트랜잭션 + 일괄 삽입 적용    |
  | 조건 기반 Select 응답 | 1.5초   | 0.2초       | 인덱스 최적화 + LIMIT 적용 |
  
  ---
  
  ### 💡 느낀 점
  
  > 간단한 로직이라도 **DB 구조와 트랜잭션 설계에 따라 수십 배의 성능 차이**가 발생할 수 있다는 점을 체감했습니다. 실시간 데이터를 다루는 시스템에서는 **DB 접근 방식에 대한 고민**이 무엇보다 중요하다는 것을 배웠습니다.





- #### JAVA
  
  > 통행량 계수 장치 `관제 및 관리 시스템`
  
  #### 📌 프로젝트 개요
  
  - **프로젝트명**: 계수관제 시스템
  
  - **개발 기간**: 202X.XX ~ 202X.XX
  
  - **담당 역할**: 백엔드 개발, 데이터베이스 설계 및 최적화, 배포 자동화
  
  - **기술 스택**:  
    `Spring Boot` · `PostgreSQL` · `TimescaleDB` · `JPA` · `Docker` · `GitHub Actions`
  
  ---
  
  ## 🎯 주요 기능
  
  - 출입 장비에서 수집된 인원 데이터를 실시간 저장 및 분석
  
  - 출입구·장치·시간 기준 유동인구 모니터링 API 제공
  
  - 고속 쿼리를 위한 DB 파티셔닝 및 하이퍼테이블 구조 실험
  
  - 관리자용 웹 페이지 연동을 위한 REST API 제공
  
  ---
  
  ## 🛠 기술적 특징
  
  ### ✅ 백엔드
  
  - Spring Boot 기반 REST API 서버 설계
  
  - JPA + QueryDSL로 유연한 동적 쿼리 처리
  
  - 계수 유형, 장치, 시간 기준 정렬·필터링 기능 지원
  
  ### ✅ 데이터베이스
  
  - PostgreSQL 기반, TimescaleDB 하이퍼테이블로 시계열 데이터 처리
  
  - 10억 건 이상의 대규모 데이터 처리 실험 수행
  
  - `device_cd`, `count_type`, `count_time` 기준 복합 인덱스 구성
  
  - `work_mem`, 병렬처리 등 성능 설정 실험 및 최적화
  
  ---
  
  ## ⚙️ 성능 최적화 실험
  
  | 실험 구조         | 평균 쿼리 시간 | 특이사항                          |
  | ------------- | -------- | ----------------------------- |
  | 일반 테이블        | 약 4.8초   | 인덱스 없이 전체 스캔                  |
  | 파티셔닝 테이블      | 약 1.2초   | `device_cd` 기준 100개 파티션       |
  | 하이퍼테이블 (64MB) | 약 0.5초   | TimescaleDB, `work_mem` 튜닝 적용 |
  
  ---
  
  ## 💡 문제 해결 경험
  
  - **문제**: 대량 데이터 정렬 시 응답 지연  
    → `work_mem` 조정 및 하이퍼테이블로 해결
  
  - **문제**: 장치 ID 기준 조회 성능 저하  
    → `device_cd` 기준 파티셔닝 및 인덱싱으로 개선
  
  - **문제**: 장기 운영 시 인덱스 성능 저하  
    → 자동 `vacuum` 및 `analyze` 설정으로 관리 효율화
  
  ---
  
  ## 📌 프로젝트 회고
  
  - 대규모 실시간 데이터를 안정적으로 처리하기 위해 **DB 설계 단계부터 성능을 고려**한 구조가 중요함을 경험했습니다.
  
  - 실험을 통해 파티셔닝, 하이퍼테이블, 인덱싱 등 다양한 전략의 차이를 체감하며, **데이터 처리에 대한 깊은 이해를 쌓을 수 있었습니다.**
  
  <div style="display: flex;
    flex-wrap: wrap;
    flex-direction: row;
    justify-content: center;
    align-items: center;
    gap:10px;"> 
    <img src="./img/projects/java/1.로그인.png" width="500"/>
    <img src="./img/projects/java/2.대시보드.png" width="500"/>
    <img src="./img/projects/java/3.이력.png" width="500"/>
    <img src="./img/projects/java/4.통계.png" width="500"/>
    <img src="./img/projects/java/5.유지보수.png" width="500"/>
  </div>

## 📈 History

- 2025.07 ~ : SSAFY
- 2022.11 ~ 2025.04 : (주)KIOT

## 📞 Contect

- 010-0000-8712
- qh613@naver.com

<div align="center">
  <img src="https://capsule-render.vercel.app/api?type=waving&color=auto&height=200&section=footer" width="100%"/>
</div>
