# TourGuard Development Guide

## English

### Development Environment Setup

#### Prerequisites

1. Install Flutter SDK
2. Install Node.js and npm
3. Install PostgreSQL
4. Install Docker and Docker Compose
5. Install Android Studio / Xcode
6. Install VS Code with recommended extensions

#### Required VS Code Extensions

- Flutter
- Dart
- ESLint
- Prettier
- GitLens
- Docker
- Kubernetes

### Project Structure

```
tourguard/
├── mobile/                 # Flutter mobile app
│   ├── lib/
│   │   ├── models/        # Data models
│   │   ├── screens/       # UI screens
│   │   ├── services/      # Business logic
│   │   ├── utils/         # Utilities
│   │   └── widgets/       # Reusable widgets
│   └── test/              # Unit and widget tests
├── backend/               # Node.js backend
│   ├── src/
│   │   ├── controllers/   # Route controllers
│   │   ├── models/        # Database models
│   │   ├── services/      # Business logic
│   │   └── utils/         # Utilities
│   └── test/              # Unit tests
└── docs/                  # Documentation
```

### Development Workflow

#### 1. Setting Up Local Environment

```bash
# Clone repository
git clone https://github.com/your-org/tourguard.git
cd tourguard

# Install dependencies
npm install
flutter pub get

# Start development servers
npm run dev
flutter run
```

#### 2. Code Style Guidelines

- Follow Flutter style guide
- Use ESLint and Prettier for JavaScript/TypeScript
- Write meaningful commit messages
- Document all public APIs
- Write unit tests for critical functionality

#### 3. Testing

```bash
# Run Flutter tests
flutter test

# Run backend tests
npm test

# Run end-to-end tests
npm run test:e2e
```

#### 4. Debugging

- Use Flutter DevTools for mobile app debugging
- Use Chrome DevTools for backend debugging
- Enable debug logging in development
- Use VS Code debugger

### Best Practices

#### Mobile Development

1. Use BLoC pattern for state management
2. Implement proper error handling
3. Optimize for battery usage
4. Handle offline scenarios
5. Follow Material Design guidelines

#### Backend Development

1. Use TypeScript for type safety
2. Implement proper error handling
3. Use dependency injection
4. Write comprehensive tests
5. Follow REST API best practices

#### Database

1. Use migrations for schema changes
2. Implement proper indexing
3. Optimize queries
4. Use transactions where appropriate
5. Implement proper backup strategy

## Tiếng Việt

### Thiết Lập Môi Trường Phát Triển

#### Yêu Cầu

1. Cài đặt Flutter SDK
2. Cài đặt Node.js và npm
3. Cài đặt PostgreSQL
4. Cài đặt Docker và Docker Compose
5. Cài đặt Android Studio / Xcode
6. Cài đặt VS Code với các extension được khuyến nghị

#### Các Extension VS Code Cần Thiết

- Flutter
- Dart
- ESLint
- Prettier
- GitLens
- Docker
- Kubernetes

### Cấu Trúc Dự Án

```
tourguard/
├── mobile/                 # Ứng dụng di động Flutter
│   ├── lib/
│   │   ├── models/        # Các model dữ liệu
│   │   ├── screens/       # Các màn hình UI
│   │   ├── services/      # Logic nghiệp vụ
│   │   ├── utils/         # Tiện ích
│   │   └── widgets/       # Widget tái sử dụng
│   └── test/              # Kiểm thử đơn vị và widget
├── backend/               # Backend Node.js
│   ├── src/
│   │   ├── controllers/   # Bộ điều khiển route
│   │   ├── models/        # Model cơ sở dữ liệu
│   │   ├── services/      # Logic nghiệp vụ
│   │   └── utils/         # Tiện ích
│   └── test/              # Kiểm thử đơn vị
└── docs/                  # Tài liệu
```

### Quy Trình Phát Triển

#### 1. Thiết Lập Môi Trường Cục Bộ

```bash
# Clone repository
git clone https://github.com/your-org/tourguard.git
cd tourguard

# Cài đặt dependencies
npm install
flutter pub get

# Khởi động máy chủ phát triển
npm run dev
flutter run
```

#### 2. Hướng Dẫn Phong Cách Code

- Tuân theo hướng dẫn phong cách Flutter
- Sử dụng ESLint và Prettier cho JavaScript/TypeScript
- Viết commit message có ý nghĩa
- Tài liệu hóa tất cả API công khai
- Viết kiểm thử đơn vị cho chức năng quan trọng

#### 3. Kiểm Thử

```bash
# Chạy kiểm thử Flutter
flutter test

# Chạy kiểm thử backend
npm test

# Chạy kiểm thử end-to-end
npm run test:e2e
```

#### 4. Gỡ Lỗi

- Sử dụng Flutter DevTools để gỡ lỗi ứng dụng di động
- Sử dụng Chrome DevTools để gỡ lỗi backend
- Bật ghi log debug trong môi trường phát triển
- Sử dụng debugger của VS Code

### Thực Hành Tốt Nhất

#### Phát Triển Di Động

1. Sử dụng mẫu BLoC để quản lý trạng thái
2. Triển khai xử lý lỗi phù hợp
3. Tối ưu hóa sử dụng pin
4. Xử lý các tình huống ngoại tuyến
5. Tuân theo hướng dẫn Material Design

#### Phát Triển Backend

1. Sử dụng TypeScript để đảm bảo kiểu dữ liệu
2. Triển khai xử lý lỗi phù hợp
3. Sử dụng dependency injection
4. Viết kiểm thử toàn diện
5. Tuân theo thực hành tốt nhất REST API

#### Cơ Sở Dữ Liệu

1. Sử dụng migrations cho thay đổi schema
2. Triển khai đánh index phù hợp
3. Tối ưu hóa truy vấn
4. Sử dụng transactions khi cần thiết
5. Triển khai chiến lược sao lưu phù hợp
