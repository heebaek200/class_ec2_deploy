# class_ec2_deploy

## Docker Compose로 실행

로컬에서 실행 중인 Spring Boot가 있다면 먼저 종료해 8080 포트를 비운다.

```powershell
docker compose up --build -d
```

<http://localhost:8080>에서 접속한다. Spring Boot 컨테이너는 Compose 서비스 이름인 `redis`로 Redis에 연결한다.

## Spring Boot만 로컬에서 실행

루트 경로의 방문 횟수는 Redis에 저장되므로 애플리케이션보다 먼저 Redis를 실행한다.

```powershell
docker compose up -d --wait redis
.\gradlew.bat bootRun
```

- 애플리케이션: <http://localhost:8080>
- Redis 기본 접속 주소: `localhost:6379`
- 다른 Redis를 사용할 때: `REDIS_HOST`, `REDIS_PORT` 환경 변수 지정

## 컨테이너 종료

```powershell
docker compose stop
```
