# HOLO: Home Organization & Lifestyle Optimization
## 서비스 소개
![image](https://github.com/user-attachments/assets/76718aa2-1441-45d5-b10a-09777b6bcbba)

HOLO는 1인 가구를 대상으로 한 인테리어 쇼핑몰입니다. 1인 가구의 라이프 스타일과 딱 맞는 인테리어 제품을 쉽고 빠르게 구매할 수 있습니다!  
> **"혼자만의 공간을 나만의 감성으로"** HOLO는 1인 가구를 위한 맞춤형 인테리어 경험을 제공합니다.

# Links
프론트엔드 배포 상태: [![Netlify Status](https://api.netlify.com/api/v1/badges/c94a2a65-b5d9-4f7a-b9ba-bfcd8080ee16/deploy-status)](https://app.netlify.com/sites/elice-holo/deploys)  
  
  
백엔드 배포 상태: ![Github Actions](https://github.com/team-HOLO/HOLO-BE/actions/workflows/deploy.yml/badge.svg?branch=dev)
- https://elice-holo.netlify.app 

# 팀원 소개
- 팀원 모두 프론트엔드와 백엔드에 참여하여, 도메인 별로 담당을 나눠 프로젝트를 진행했습니다.
  | 이름 (Name)  | 역할 (Role)  | 담당 도메인 (Domain)      | 주요 기여 (Key Contributions) |
  |-------------|------------|-------------------------|-------------------------------|
  | 심우민       | 팀장 (Leader) | 상품 (Product)          | 상품 등록/수정/삭제 API, 상품 정렬 및 검색 기능, S3를 이용한 이미지 업로드 기능 구현 |
  | 백승주       | 팀원 (Member) | 회원 (Member)           |  회원 가입/로그인/수정/ 삭제 API, Spring Security- jwt 토큰 쿠키 사용 인증 방식, oauth 로그인 기능 구현 |
  | 손병훈       | 팀원 (Member) | 주문 (Order)            |  주문 등록/수정/삭제 API, 주문 조회 및 상태 변경기능 |
  | 윤지현       | 팀원 (Member) | 카테고리 (Category)      | 카테고리 등록/수정/삭제 API, 카테고리 조회 기능 구현, Netlify와 Github Actions를 사용한 CI/CD, EC2 서버 세팅, Discord 주문 알림 |
  | 임서현       | 팀원 (Member) | 장바구니 (Cart)          | localstorge를 통해 장바구니 등록 /수량 수정/ 선택 삭제/ 전체 삭제/조회/ 총 가격 계산 |

# 핵심 기능
## 일반 유저

### 회원 가입
![image](https://github.com/user-attachments/assets/7c254ae9-1f90-4e73-9402-8902613af935)

### 장바구니
![image](https://github.com/user-attachments/assets/b10da188-e946-4e5a-baca-4e3fbb3f5b5e)

### 상품 구매
![image](https://github.com/user-attachments/assets/c709969e-8961-4be4-8836-7888e1628f21)

### Oauth 이용 로그인
![image](https://github.com/user-attachments/assets/c11de9c6-f9b8-405b-8b51-88e302badfd9)

### 마이페이지
![image](https://github.com/user-attachments/assets/89d894b0-8215-4044-8343-1b0f843b359b)

## 관리자
### 상품 관리
![image](https://github.com/user-attachments/assets/79f1d990-f9a9-4200-9ffe-f6a100caf456)

### 카테고리 관리
![image](https://github.com/user-attachments/assets/8c1bd814-a736-408b-b19a-eced853ec766)

### 주문 관리
![image](https://github.com/user-attachments/assets/9febcc65-94b3-43c4-88fc-dcd9da5cb941)

### 접근 제한
![image](https://github.com/user-attachments/assets/f793a30b-001b-4d8e-94fb-87ab452ee07f)

- 관리자 권한 없이 Admin 페이지에 접근한 경우: 권한 안내 페이지로 이동
- 유저 권한 없이 MyPage에 접근한 경우: 로그인 페이지로 이동
## 디스코드 봇
- 주문 생성, 수정, 취소 시 관리자에게 실시간 Discord 알림 전송
- CS 대응을 위한 실시간 모니터링 기능
![image](https://github.com/user-attachments/assets/70281f12-4ba1-457a-8cf9-9d3af0cf9f2d)
![image](https://github.com/user-attachments/assets/0772f970-36ee-4bd8-b7ee-9be994abb51b)



# 기술 스택
- **Frontend** : React(v18.3.1), Material UI(v6.1.3)
- **Backend** : Spring Boot(v3.3.4), Java(v21)
- **Storage** : AWS S3(이미지 파일 저장), AWS RDS (MySQL Community v8.0.39)
- **Test** : Junit(v5.10.3)
- **Security & Authentication** : Spring Security (v6), JWT, Google OAuth2, Let's Encrypt(TLSv1.2, v1.3)
- **Deployment**: Netlify(Frontend), AWS EC2(Backend, Ubuntu 22.04.5 LTS), Github Actions(CI/CD), Nginx(Reverse Proxy, 1.18.0)
- **DNS**: AWS Route 53

# 아키텍처
![image](https://github.com/user-attachments/assets/86eaa41b-b9c1-4253-8d43-c391ab209191)

- Netlify를 이용한 React 프론트 배포
- Nginx는 SSL을 처리하고, 리버스 프록시로서 클라이언트 요청을 Spring 애플리케이션으로 전달
- AWS S3, RDS를 사용해 데이터 저장 및 이미지 업로드 기능 제공
- Github Actions를 이용한 CI/CD
- Google Oauth를 사용한 사용자 인증 및 인가 기능 제공
- 주문 생성, 수정, 삭제와 같은 주요 이벤트는 Discord Webhook을 통해 관리자에게 실시간으로 알림 전달


# ERD
![image](https://github.com/user-attachments/assets/fd4e1686-af14-4eb8-9fea-78cc3eaf957f)


# 배포 환경
```
 - 서버 : AWS EC2
   - 운영 체제: Ubuntu 22.04.5 LTS (GNU/Linux 6.8.0-1017-aws x86_64)
   - JRE: openjdk version "21.0.4"
   - 애플리케이션 서버: Spring Boot (내장 Tomcat 사용)
   - 리버스 프록시: Nginx(v1.18.0)
     - HTTPS 및 SSL/TLS 처리
     - TLSv1.2, TLSv1.3
 - 데이터 베이스: AWS RDS
   - MySQL Community(8.0.39)
 - 이미지 파일 저장: AWS S3
 - 도메인 및 DNS
    - 가비아에서 구매한 도메인 `elice-holo.shop`을 AWS Route 53에서 관리
    - EC2 인스턴스의 퍼블릭 IP에 도메인 연결
    - SSL/TLS 인증서를 사용한 HTTPS 제공 (Let's Encrypt)
```

# API 문서
- [Swagger-UI](https://elice-holo.shop/swagger-ui/index.html)

# 트러블 슈팅
1. 배포 환경에서의 CORS 문제
![스크린샷 2024-10-26 오후 12 06 13](https://github.com/user-attachments/assets/d2d57f27-8344-4677-b437-f392797cb987)
![스크린샷 2024-10-26 오후 12 06 18](https://github.com/user-attachments/assets/2a19d74b-6ffc-4bd5-b8d3-94173323610a)

  
2. 역직렬화 오류
![스크린샷 2024-10-26 오후 12 06 23](https://github.com/user-attachments/assets/dcb97278-ccf4-4e0a-bd05-6453cb6266b4)
![스크린샷 2024-10-26 오후 12 06 30](https://github.com/user-attachments/assets/52854f98-5bdd-4eaf-a449-a82f7ea2ae44)
