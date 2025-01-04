## 👋인사잘해팀 : HR(human resources)
### 프로젝트 소개
<img width="100%" alt="인사잘해" src="https://github.com/user-attachments/assets/5970ff18-2172-468f-9858-77458d432e61" />

> 인사 및 근태 관리를 통합한 사내 HR 프로그램!

본 프로젝트는 사내 인사 및 근태 관리를 효율화하기 위해 개발된 HR 시스템입니다.
직원들은 사내 채팅, 휴가 신청, 출퇴근 기록, 게시판 활용, 급여 확인 등을 하나의 플랫폼에서 손쉽게 처리할 수 있습니다.
관리자들은 직원 정보 및 근태를 체계적으로 관리할 수 있어 업무 생산성이 향상됩니다.

[인사잘해](http://34.47.90.224:3000/)

**접속 가능한 계정**
- 이상해 사원
  - **ID** : 20241216
  - **PW** : 123123123

---

### API 문서
**Swagger-UI** : http://34.47.90.224:8080/swagger-ui/index.html

---

### 개발 기간
- 2024.11.18 ~ 2024.12.13

---

### 팀원 소개
| 이름 (Name) | 역할 (Role)  | 담당 도메인 (Domain) | 
  |-----------|------------|-----------------|
| 정현        | 팀장 (Leader) | 사원              | 
| 한현        | 팀원 (Member) | 메신저             | 
| 이서율       | 팀원 (Member) | 게시판             |  
| 송진욱       | 팀원 (Member) | 근태/휴가/일정        | 
| 김준수       | 팀원 (Member) | 급여              | 

---

### 기술 스택
- **Frontend** : React, Bootstrap, HTML, CSS, Javascript
- **Backend** : Java, JPA, Spring Boot, Spring Security, JWT, Websocket, STOMP, MyBatis, QueryDSL
- **Storage** : AWS S3, MariaDB
- **Deployment**: GCP, Nginx

---

### 와이어프레임
![와이어프레임](https://github.com/user-attachments/assets/794f6b45-ce24-4aec-a9ec-80a0aacc2d6e)

---

### ERD
![인사잘해 ERD ](https://github.com/user-attachments/assets/ffe86490-a2ab-4339-89d9-995463ac02dc)

---

### 📌주요 기능
##### 홈
![hr-handlers_11](https://github.com/user-attachments/assets/c27959d1-6a7b-40f6-927e-c7a8b0252f20)

##### 사원
![hr-handlers_12](https://github.com/user-attachments/assets/de07380d-93b3-4679-b473-f4236d9bfb68)
![hr-handlers_13](https://github.com/user-attachments/assets/ada46b6d-25a0-4608-b33f-699d3c0a5577)

##### 근태
![hr-handlers_15](https://github.com/user-attachments/assets/2f86c0fe-7849-4276-bc70-975e0a8eed1e)

##### 일정
![hr-handlers_17](https://github.com/user-attachments/assets/d7108759-89f5-4019-8e2f-7950ee5ca6a6)

##### 휴가
![hr-handlers_16](https://github.com/user-attachments/assets/8afcd93f-1bdf-4f5f-9d2f-2482fc80fe29)

##### 게시판
![hr-handlers_18](https://github.com/user-attachments/assets/97f8c227-9061-4f32-9682-63895be55c2c)
![hr-handlers_19](https://github.com/user-attachments/assets/e369648c-15fa-4fec-bae3-af42a2a86e54)
![hr-handlers_20](https://github.com/user-attachments/assets/b487f2be-1746-43fc-9e95-76a96b23857a)

##### 메신저
![hr-handlers_14](https://github.com/user-attachments/assets/b8d1f5c7-8fc1-4778-8da5-4d89875e5c89)

##### 급여
![hr-handlers_21](https://github.com/user-attachments/assets/b81eadb0-f85f-4af6-aeff-226b8566e16d)
![hr-handlers_22](https://github.com/user-attachments/assets/38bb9640-a098-4190-829c-9afd9d80856b)

---

### 🚨트러블슈팅
#### 출근/퇴근 시간이 서버시간과 다르게 9시간전으로 저장되는 이슈 
**시도해본 것**
1. Nginx 서버 시간 UTC -> KST 타임존 변경 
  
   - 서버 시간은 변경 되었지만, 동일한 문제 발생

2. 데이터 베이스 시간 변경 
   - 변경 시 오류가 없던 다른 도메인 시간대가 9시간 전으로 변경 되는 다른 문제 발생

**해결 방법**

시간대를 저장하는 Service 부분에 명시적으로 한국시간을 설정해주는 코드로 변경
`LocalDateTime.now(ZoneId.of("Asia/Seoul"))`
