# TourGuard Security Guidelines

## English

### Authentication & Authorization

1. **Password Requirements**

   - Minimum 8 characters
   - Must contain at least one uppercase letter
   - Must contain at least one lowercase letter
   - Must contain at least one number
   - Must contain at least one special character
   - Passwords are hashed using bcrypt with salt

2. **JWT Implementation**

   - Use RS256 algorithm for token signing
   - Token expiration: 1 hour for access tokens
   - Refresh token expiration: 7 days
   - Store refresh tokens in secure HTTP-only cookies
   - Implement token rotation on refresh

3. **Role-Based Access Control**
   - Admin: Full system access
   - Group Leader: Can manage their groups
   - Member: Basic access to their groups
   - Implement least privilege principle

### Data Protection

1. **Data Encryption**

   - All API communications use TLS 1.3
   - Sensitive data encrypted at rest
   - Use environment variables for secrets
   - Implement proper key rotation

2. **Location Data**

   - Encrypt location data in transit
   - Implement data retention policies
   - Allow users to delete their location history
   - Anonymize data for analytics

3. **Personal Information**
   - Minimize data collection
   - Implement data masking
   - Regular data cleanup
   - GDPR compliance measures

### API Security

1. **Rate Limiting**

   - Implement per-IP rate limiting
   - Different limits for authenticated/unauthenticated requests
   - Use Redis for rate limiting storage
   - Implement exponential backoff

2. **Input Validation**

   - Validate all input data
   - Use parameterized queries
   - Implement request size limits
   - Sanitize user inputs

3. **CORS Policy**
   - Strict CORS configuration
   - Whitelist allowed origins
   - Limit allowed methods
   - Implement preflight caching

### Mobile App Security

1. **App Security**

   - Implement certificate pinning
   - Secure local storage
   - Implement app integrity checks
   - Regular security updates

2. **Location Services**

   - Request minimum required permissions
   - Implement location accuracy controls
   - Secure location data transmission
   - Background location handling

3. **Offline Security**
   - Encrypt local database
   - Implement secure data sync
   - Handle offline authentication
   - Secure offline data storage

### Monitoring & Incident Response

1. **Logging**

   - Implement comprehensive logging
   - Log security events
   - Monitor failed login attempts
   - Track API usage patterns

2. **Alerting**

   - Set up security alerts
   - Monitor unusual activities
   - Implement automated responses
   - Regular security audits

3. **Incident Response**
   - Document incident response plan
   - Regular security drills
   - Maintain incident response team
   - Post-incident analysis

## Tiếng Việt

### Xác thực & Phân quyền

1. **Yêu cầu Mật khẩu**

   - Tối thiểu 8 ký tự
   - Phải có ít nhất một chữ hoa
   - Phải có ít nhất một chữ thường
   - Phải có ít nhất một số
   - Phải có ít nhất một ký tự đặc biệt
   - Mật khẩu được mã hóa bằng bcrypt với salt

2. **Triển khai JWT**

   - Sử dụng thuật toán RS256 để ký token
   - Thời hạn token: 1 giờ cho access token
   - Thời hạn refresh token: 7 ngày
   - Lưu refresh token trong cookie HTTP-only
   - Thực hiện luân chuyển token khi refresh

3. **Kiểm soát Truy cập dựa trên Vai trò**
   - Admin: Toàn quyền hệ thống
   - Trưởng nhóm: Quản lý nhóm của họ
   - Thành viên: Quyền cơ bản trong nhóm
   - Áp dụng nguyên tắc đặc quyền tối thiểu

### Bảo vệ Dữ liệu

1. **Mã hóa Dữ liệu**

   - Tất cả giao tiếp API sử dụng TLS 1.3
   - Mã hóa dữ liệu nhạy cảm khi lưu trữ
   - Sử dụng biến môi trường cho các bí mật
   - Thực hiện luân chuyển khóa đúng cách

2. **Dữ liệu Vị trí**

   - Mã hóa dữ liệu vị trí khi truyền tải
   - Thực hiện chính sách lưu trữ dữ liệu
   - Cho phép người dùng xóa lịch sử vị trí
   - Ẩn danh dữ liệu cho phân tích

3. **Thông tin Cá nhân**
   - Giảm thiểu thu thập dữ liệu
   - Thực hiện che giấu dữ liệu
   - Dọn dẹp dữ liệu định kỳ
   - Tuân thủ GDPR

### Bảo mật API

1. **Giới hạn Tốc độ**

   - Thực hiện giới hạn theo IP
   - Giới hạn khác nhau cho yêu cầu đã xác thực/chưa xác thực
   - Sử dụng Redis để lưu trữ giới hạn
   - Thực hiện exponential backoff

2. **Kiểm tra Đầu vào**

   - Kiểm tra tất cả dữ liệu đầu vào
   - Sử dụng truy vấn tham số hóa
   - Thực hiện giới hạn kích thước yêu cầu
   - Làm sạch đầu vào người dùng

3. **Chính sách CORS**
   - Cấu hình CORS nghiêm ngặt
   - Danh sách trắng nguồn gốc được phép
   - Giới hạn phương thức được phép
   - Thực hiện bộ nhớ đệm preflight

### Bảo mật Ứng dụng Di động

1. **Bảo mật Ứng dụng**

   - Thực hiện certificate pinning
   - Bảo mật lưu trữ cục bộ
   - Thực hiện kiểm tra tính toàn vẹn ứng dụng
   - Cập nhật bảo mật định kỳ

2. **Dịch vụ Vị trí**

   - Yêu cầu quyền tối thiểu cần thiết
   - Thực hiện kiểm soát độ chính xác vị trí
   - Bảo mật truyền tải dữ liệu vị trí
   - Xử lý vị trí nền

3. **Bảo mật Ngoại tuyến**
   - Mã hóa cơ sở dữ liệu cục bộ
   - Thực hiện đồng bộ dữ liệu an toàn
   - Xử lý xác thực ngoại tuyến
   - Lưu trữ dữ liệu ngoại tuyến an toàn

### Giám sát & Phản ứng Sự cố

1. **Ghi nhật ký**

   - Thực hiện ghi nhật ký toàn diện
   - Ghi lại sự kiện bảo mật
   - Giám sát đăng nhập thất bại
   - Theo dõi mẫu sử dụng API

2. **Cảnh báo**

   - Thiết lập cảnh báo bảo mật
   - Giám sát hoạt động bất thường
   - Thực hiện phản ứng tự động
   - Kiểm tra bảo mật định kỳ

3. **Phản ứng Sự cố**
   - Tài liệu hóa kế hoạch phản ứng sự cố
   - Diễn tập bảo mật định kỳ
   - Duy trì nhóm phản ứng sự cố
   - Phân tích sau sự cố
