# 간단한 counter api를 docker-compose를 이용해 ec2에 자동 배포
# 🐳 Docker Compose 구성

Services
1. Redis
- Image: redis:7-alpine
- Port: 6379
- 역할: 카운터 데이터를 저장하는 인메모리 데이터 저장소
2. App (Spring Boot Application)
- Image: kkang5430/counter-app:latest
- 역할: Counter API 서버
- 의존성: Redis 서비스에 의존
3. Nginx
- Image: nginx:alpine
- Port: 80
- 역할: 리버스 프록시 / 로드 밸런서
- 설정: ./nginx.conf 파일을 통해 구성
- 의존성: App 서비스에 의존
# 서비스 시작
docker-compose up -d

# 로그 확인
docker-compose logs -f

# 서비스 중지
docker-compose down

