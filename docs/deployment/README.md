# TourGuard Deployment Guide

## English

### Prerequisites

- Docker and Docker Compose
- Kubernetes cluster
- PostgreSQL 13+
- Node.js 16+
- Flutter SDK
- Firebase project setup

### Deployment Architecture

#### Development Environment

```
┌─────────────┐     ┌─────────────┐     ┌─────────────┐
│   Flutter   │     │   Node.js   │     │ PostgreSQL  │
│   Mobile    │◄────┤   Backend   │◄────┤   Database  │
└─────────────┘     └─────────────┘     └─────────────┘
```

#### Production Environment

```
┌─────────────┐     ┌─────────────┐     ┌─────────────┐
│   Flutter   │     │  Kubernetes │     │ PostgreSQL  │
│   Mobile    │◄────┤   Cluster   │◄────┤   Database  │
└─────────────┘     └─────────────┘     └─────────────┘
```

### Deployment Steps

#### 1. Backend Deployment

1. Build Docker image:
   ```bash
   docker build -t tourguard-backend:latest ./backend
   ```
2. Push to container registry:
   ```bash
   docker push your-registry/tourguard-backend:latest
   ```
3. Deploy to Kubernetes:
   ```bash
   kubectl apply -f k8s/backend-deployment.yaml
   ```

#### 2. Database Setup

1. Initialize PostgreSQL:
   ```bash
   kubectl apply -f k8s/postgres-deployment.yaml
   ```
2. Run migrations:
   ```bash
   kubectl exec -it tourguard-backend -- npm run migrate
   ```

#### 3. Mobile App Deployment

1. Build Flutter app:
   ```bash
   flutter build appbundle
   flutter build ios
   ```
2. Deploy to stores:
   - Google Play Console
   - Apple App Store

### CI/CD Pipeline

#### GitHub Actions Workflow

```yaml
name: TourGuard CI/CD

on:
  push:
    branches: [main]
  pull_request:
    branches: [main]

jobs:
  test:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v2
      - name: Run tests
        run: |
          npm install
          npm test

  build:
    needs: test
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v2
      - name: Build and push
        run: |
          docker build -t tourguard-backend:latest .
          docker push your-registry/tourguard-backend:latest

  deploy:
    needs: build
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v2
      - name: Deploy to Kubernetes
        run: |
          kubectl apply -f k8s/
```

### Monitoring and Logging

#### Prometheus Metrics

- API response times
- WebSocket connections
- Database performance
- System resources

#### ELK Stack

- Application logs
- Error tracking
- User activity
- Performance metrics

## Tiếng Việt

### Yêu Cầu

- Docker và Docker Compose
- Cụm Kubernetes
- PostgreSQL 13+
- Node.js 16+
- Flutter SDK
- Thiết lập dự án Firebase

### Kiến Trúc Triển Khai

#### Môi Trường Phát Triển

```
┌─────────────┐     ┌─────────────┐     ┌─────────────┐
│   Flutter   │     │   Node.js   │     │ PostgreSQL  │
│   Mobile    │◄────┤   Backend   │◄────┤   Database  │
└─────────────┘     └─────────────┘     └─────────────┘
```

#### Môi Trường Sản Xuất

```
┌─────────────┐     ┌─────────────┐     ┌─────────────┐
│   Flutter   │     │  Kubernetes │     │ PostgreSQL  │
│   Mobile    │◄────┤   Cluster   │◄────┤   Database  │
└─────────────┘     └─────────────┘     └─────────────┘
```

### Các Bước Triển Khai

#### 1. Triển Khai Backend

1. Build Docker image:
   ```bash
   docker build -t tourguard-backend:latest ./backend
   ```
2. Push lên container registry:
   ```bash
   docker push your-registry/tourguard-backend:latest
   ```
3. Triển khai lên Kubernetes:
   ```bash
   kubectl apply -f k8s/backend-deployment.yaml
   ```

#### 2. Thiết Lập Cơ Sở Dữ Liệu

1. Khởi tạo PostgreSQL:
   ```bash
   kubectl apply -f k8s/postgres-deployment.yaml
   ```
2. Chạy migrations:
   ```bash
   kubectl exec -it tourguard-backend -- npm run migrate
   ```

#### 3. Triển Khai Ứng Dụng Di Động

1. Build ứng dụng Flutter:
   ```bash
   flutter build appbundle
   flutter build ios
   ```
2. Triển khai lên cửa hàng:
   - Google Play Console
   - Apple App Store

### Pipeline CI/CD

#### Quy Trình GitHub Actions

```yaml
name: TourGuard CI/CD

on:
  push:
    branches: [main]
  pull_request:
    branches: [main]

jobs:
  test:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v2
      - name: Run tests
        run: |
          npm install
          npm test

  build:
    needs: test
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v2
      - name: Build and push
        run: |
          docker build -t tourguard-backend:latest .
          docker push your-registry/tourguard-backend:latest

  deploy:
    needs: build
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v2
      - name: Deploy to Kubernetes
        run: |
          kubectl apply -f k8s/
```

### Giám Sát và Ghi Log

#### Metrics Prometheus

- Thời gian phản hồi API
- Kết nối WebSocket
- Hiệu suất cơ sở dữ liệu
- Tài nguyên hệ thống

#### ELK Stack

- Log ứng dụng
- Theo dõi lỗi
- Hoạt động người dùng
- Metrics hiệu suất
