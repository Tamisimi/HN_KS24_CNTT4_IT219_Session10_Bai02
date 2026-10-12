# Bài 2 — Đóng gói ứng dụng Web Backend bằng Single-stage Dockerfile

## Cấu trúc

```text
homework/session_10/ex2/
├── Dockerfile
├── package.json
├── server.js
└── README.md
```

## Dockerfile (Single-stage)

- `FROM node:18-alpine`
- `WORKDIR /app`
- `COPY` + `RUN npm install`
- `ENV PORT=3000` / `EXPOSE 3000`
- `CMD ["node", "server.js"]` (exec form)

## Cách chạy

```bash
cd homework/session_10/ex2

docker build -t hw-backend:v1 .
docker run -d --name app-single-stage -p 8080:3000 hw-backend:v1

docker ps
docker logs app-single-stage
curl -i http://localhost:8080/
```

## Kết quả mong đợi

- Build không lỗi, container trạng thái **Up**
- `curl` trả **HTTP 200** và JSON:

```json
{"status":"success","message":"Hello from Docker Single-stage!"}
```

## Dọn dẹp

```bash
docker stop app-single-stage && docker rm app-single-stage
```
