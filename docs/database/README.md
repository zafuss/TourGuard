# TourGuard Database Schema

## English

### Users Collection

```javascript
{
  _id: ObjectId,
  email: String,  // unique
  passwordHash: String,
  name: String,
  role: String,
  createdAt: Date,
  updatedAt: Date
}

// Indexes
db.users.createIndex({ "email": 1 }, { unique: true })
db.users.createIndex({ "role": 1 })
```

### Groups Collection

```javascript
{
  _id: ObjectId,
  name: String,
  description: String,
  maxDistance: Number,
  createdBy: ObjectId,  // reference to users._id
  members: [{
    userId: ObjectId,   // reference to users._id
    role: String,
    status: String,
    joinedAt: Date,
    leftAt: Date
  }],
  createdAt: Date,
  updatedAt: Date
}

// Indexes
db.groups.createIndex({ "createdBy": 1 })
db.groups.createIndex({ "members.userId": 1 })
db.groups.createIndex({ "members.status": 1 })
```

### Locations Collection

```javascript
{
  _id: ObjectId,
  userId: ObjectId,     // reference to users._id
  groupId: ObjectId,    // reference to groups._id
  location: {
    type: "Point",
    coordinates: [longitude, latitude]  // GeoJSON format
  },
  accuracy: Number,
  timestamp: Date
}

// Indexes
db.locations.createIndex({ "userId": 1 })
db.locations.createIndex({ "groupId": 1 })
db.locations.createIndex({ "timestamp": 1 })
db.locations.createIndex({ "location": "2dsphere" })  // Geospatial index
```

### Notifications Collection

```javascript
{
  _id: ObjectId,
  userId: ObjectId,     // reference to users._id
  groupId: ObjectId,    // reference to groups._id
  type: String,
  message: String,
  read: Boolean,
  createdAt: Date
}

// Indexes
db.notifications.createIndex({ "userId": 1 })
db.notifications.createIndex({ "groupId": 1 })
db.notifications.createIndex({ "read": 1 })
```

## Tiếng Việt

### Collection Users

```javascript
{
  _id: ObjectId,
  email: String,  // unique
  passwordHash: String,
  name: String,
  role: String,
  createdAt: Date,
  updatedAt: Date
}

// Chỉ mục
db.users.createIndex({ "email": 1 }, { unique: true })
db.users.createIndex({ "role": 1 })
```

### Collection Groups

```javascript
{
  _id: ObjectId,
  name: String,
  description: String,
  maxDistance: Number,
  createdBy: ObjectId,  // tham chiếu đến users._id
  members: [{
    userId: ObjectId,   // tham chiếu đến users._id
    role: String,
    status: String,
    joinedAt: Date,
    leftAt: Date
  }],
  createdAt: Date,
  updatedAt: Date
}

// Chỉ mục
db.groups.createIndex({ "createdBy": 1 })
db.groups.createIndex({ "members.userId": 1 })
db.groups.createIndex({ "members.status": 1 })
```

### Collection Locations

```javascript
{
  _id: ObjectId,
  userId: ObjectId,     // tham chiếu đến users._id
  groupId: ObjectId,    // tham chiếu đến groups._id
  location: {
    type: "Point",
    coordinates: [longitude, latitude]  // định dạng GeoJSON
  },
  accuracy: Number,
  timestamp: Date
}

// Chỉ mục
db.locations.createIndex({ "userId": 1 })
db.locations.createIndex({ "groupId": 1 })
db.locations.createIndex({ "timestamp": 1 })
db.locations.createIndex({ "location": "2dsphere" })  // chỉ mục không gian địa lý
```

### Collection Notifications

```javascript
{
  _id: ObjectId,
  userId: ObjectId,     // tham chiếu đến users._id
  groupId: ObjectId,    // tham chiếu đến groups._id
  type: String,
  message: String,
  read: Boolean,
  createdAt: Date
}

// Chỉ mục
db.notifications.createIndex({ "userId": 1 })
db.notifications.createIndex({ "groupId": 1 })
db.notifications.createIndex({ "read": 1 })
```
