# TourGuard API Documentation

## English

### Authentication

#### Login

```http
POST /api/auth/login
Content-Type: application/json

{
  "email": "string",
  "password": "string"
}
```

Response:

```json
{
  "token": "string",
  "user": {
    "id": "string",
    "email": "string",
    "name": "string",
    "role": "string"
  }
}
```

### Groups

#### Create Group

```http
POST /api/groups
Authorization: Bearer <token>
Content-Type: application/json

{
  "name": "string",
  "description": "string",
  "maxDistance": number,
  "settings": {
    "notifyOnDistanceExceeded": boolean,
    "notifyOnMemberLeft": boolean
  }
}
```

#### Get Group Members

```http
GET /api/groups/{groupId}/members
Authorization: Bearer <token>
```

#### Add Member to Group

```http
POST /api/groups/{groupId}/members
Authorization: Bearer <token>
Content-Type: application/json

{
  "userId": "string",
  "role": "string"
}
```

### Location Tracking

#### Update Location

```http
POST /api/location/update
Authorization: Bearer <token>
Content-Type: application/json

{
  "latitude": number,
  "longitude": number,
  "accuracy": number,
  "timestamp": "string"
}
```

#### Get Group Members Location

```http
GET /api/groups/{groupId}/locations
Authorization: Bearer <token>
```

### Notifications

#### Get Notifications

```http
GET /api/notifications
Authorization: Bearer <token>
```

#### Mark Notification as Read

```http
PATCH /api/notifications/{notificationId}
Authorization: Bearer <token>
Content-Type: application/json

{
  "read": true
}
```

### WebSocket Events

#### Connection

```javascript
ws://api.tourguard.com/ws?token=<jwt_token>
```

#### Events

- `location_update`: Real-time location updates
- `member_joined`: When a member joins the group
- `member_left`: When a member leaves the group
- `distance_alert`: When a member exceeds the maximum distance
- `group_update`: Group settings or member changes

## Tiếng Việt

### Xác Thực

#### Đăng Nhập

```http
POST /api/auth/login
Content-Type: application/json

{
  "email": "string",
  "password": "string"
}
```

Phản Hồi:

```json
{
  "token": "string",
  "user": {
    "id": "string",
    "email": "string",
    "name": "string",
    "role": "string"
  }
}
```

### Nhóm

#### Tạo Nhóm

```http
POST /api/groups
Authorization: Bearer <token>
Content-Type: application/json

{
  "name": "string",
  "description": "string",
  "maxDistance": number,
  "settings": {
    "notifyOnDistanceExceeded": boolean,
    "notifyOnMemberLeft": boolean
  }
}
```

#### Lấy Danh Sách Thành Viên

```http
GET /api/groups/{groupId}/members
Authorization: Bearer <token>
```

#### Thêm Thành Viên Vào Nhóm

```http
POST /api/groups/{groupId}/members
Authorization: Bearer <token>
Content-Type: application/json

{
  "userId": "string",
  "role": "string"
}
```

### Theo Dõi Vị Trí

#### Cập Nhật Vị Trí

```http
POST /api/location/update
Authorization: Bearer <token>
Content-Type: application/json

{
  "latitude": number,
  "longitude": number,
  "accuracy": number,
  "timestamp": "string"
}
```

#### Lấy Vị Trí Thành Viên

```http
GET /api/groups/{groupId}/locations
Authorization: Bearer <token>
```

### Thông Báo

#### Lấy Thông Báo

```http
GET /api/notifications
Authorization: Bearer <token>
```

#### Đánh Dấu Đã Đọc

```http
PATCH /api/notifications/{notificationId}
Authorization: Bearer <token>
Content-Type: application/json

{
  "read": true
}
```

### Sự Kiện WebSocket

#### Kết Nối

```javascript
ws://api.tourguard.com/ws?token=<jwt_token>
```

#### Các Sự Kiện

- `location_update`: Cập nhật vị trí thời gian thực
- `member_joined`: Khi thành viên tham gia nhóm
- `member_left`: Khi thành viên rời nhóm
- `distance_alert`: Khi thành viên vượt quá khoảng cách tối đa
- `group_update`: Cập nhật cài đặt nhóm hoặc thay đổi thành viên
