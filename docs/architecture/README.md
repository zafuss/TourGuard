# TourGuard Architecture

## English

### System Overview

TourGuard is a distributed system consisting of three main components:

1. Mobile Application (Flutter)
2. Backend Services (Node.js)
3. Database (PostgreSQL)

### Component Architecture

#### Mobile Application

- Built with Flutter for cross-platform support
- Implements real-time location tracking
- Handles push notifications
- Manages offline data synchronization
- Implements user authentication
- Provides tour guide management interface

#### Backend Services

- RESTful API for CRUD operations
- WebSocket server for real-time updates
- Authentication and authorization services
- Location tracking and distance calculation
- Notification management
- Data synchronization

#### Database

- PostgreSQL for persistent storage
- TimescaleDB extension for time-series data
- PostGIS extension for geospatial queries

### Key Features Implementation

#### Real-time Location Tracking

1. Mobile app sends location updates via WebSocket
2. Backend calculates distances between group members
3. Alerts are triggered when distance thresholds are exceeded
4. Notifications are sent via Firebase Cloud Messaging

#### Group Management

1. Tour guides can create and manage groups
2. Members can be added/removed with different permission levels
3. Group settings include distance thresholds and notification preferences
4. Real-time group status monitoring

#### Offline Support

1. Local SQLite database for offline data storage
2. Background sync when connection is restored
3. Conflict resolution for concurrent updates

### Security Considerations

1. End-to-end encryption for sensitive data
2. JWT-based authentication
3. Role-based access control
4. Secure WebSocket connections
5. Data encryption at rest

## Tiếng Việt

### Tổng Quan Hệ Thống

TourGuard là một hệ thống phân tán bao gồm ba thành phần chính:

1. Ứng dụng Di động (Flutter)
2. Dịch vụ Backend (Node.js)
3. Cơ sở dữ liệu (PostgreSQL)

### Kiến Trúc Thành Phần

#### Ứng dụng Di động

- Xây dựng bằng Flutter để hỗ trợ đa nền tảng
- Triển khai theo dõi vị trí thời gian thực
- Xử lý thông báo đẩy
- Quản lý đồng bộ hóa dữ liệu ngoại tuyến
- Triển khai xác thực người dùng
- Cung cấp giao diện quản lý cho hướng dẫn viên

#### Dịch vụ Backend

- API RESTful cho các thao tác CRUD
- Máy chủ WebSocket cho cập nhật thời gian thực
- Dịch vụ xác thực và phân quyền
- Theo dõi vị trí và tính toán khoảng cách
- Quản lý thông báo
- Đồng bộ hóa dữ liệu

#### Cơ sở dữ liệu

- PostgreSQL cho lưu trữ dữ liệu
- Tiện ích mở rộng TimescaleDB cho dữ liệu chuỗi thời gian
- Tiện ích mở rộng PostGIS cho truy vấn không gian địa lý

### Triển Khai Tính Năng Chính

#### Theo Dõi Vị Trí Thời Gian Thực

1. Ứng dụng di động gửi cập nhật vị trí qua WebSocket
2. Backend tính toán khoảng cách giữa các thành viên
3. Cảnh báo được kích hoạt khi vượt quá ngưỡng khoảng cách
4. Thông báo được gửi qua Firebase Cloud Messaging

#### Quản Lý Nhóm

1. Hướng dẫn viên có thể tạo và quản lý nhóm
2. Thành viên có thể được thêm/xóa với các cấp độ quyền khác nhau
3. Cài đặt nhóm bao gồm ngưỡng khoảng cách và tùy chọn thông báo
4. Giám sát trạng thái nhóm thời gian thực

#### Hỗ Trợ Ngoại Tuyến

1. Cơ sở dữ liệu SQLite cục bộ cho lưu trữ dữ liệu ngoại tuyến
2. Đồng bộ hóa nền khi kết nối được khôi phục
3. Giải quyết xung đột cho các cập nhật đồng thời

### Cân Nhắc Bảo Mật

1. Mã hóa đầu cuối cho dữ liệu nhạy cảm
2. Xác thực dựa trên JWT
3. Kiểm soát truy cập dựa trên vai trò
4. Kết nối WebSocket an toàn
5. Mã hóa dữ liệu khi lưu trữ
