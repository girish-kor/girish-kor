# Full Stack Node.js Essentials 

## 1. Core Node.js Concepts
- **Event Loop**: Non-blocking I/O model for handling async operations.
- **Modules**: Use `require()` and `module.exports` for code organization.
  ```javascript
  // Export
  module.exports = myFunction;
  // Import
  const myModule = require('./myModule');
  ```
- **npm**: Package manager (`npm init`, `npm install <package>`).

## 2. Express.js Basics
- **Setup**:
  ```javascript
  const express = require('express');
  const app = express();
  app.listen(3000, () => console.log('Server running'));
  ```
- **Routes**:
  ```javascript
  app.get('/', (req, res) => res.send('Hello World'));
  app.post('/submit', (req, res) => { /* Handle data */ });
  ```
- **Middleware**:
  ```javascript
  app.use(express.json()); // Parse JSON
  app.use(cors()); // Enable CORS
  ```

## 3. Database Integration (MongoDB/Mongoose)
- **Connect**:
  ```javascript
  const mongoose = require('mongoose');
  mongoose.connect('mongodb://localhost:27017/mydb');
  ```
- **Schema/Model**:
  ```javascript
  const userSchema = new mongoose.Schema({
    name: String,
    email: { type: String, unique: true }
  });
  const User = mongoose.model('User', userSchema);
  ```
- **CRUD Operations**:
  ```javascript
  User.create({ name: 'John' }); // Create
  User.find(); // Read
  User.updateOne({ name: 'John' }, { email: 'john@mail.com' }); // Update
  User.deleteOne({ name: 'John' }); // Delete
  ```

## 4. Authentication (JWT)
- **Setup**:
  ```javascript
  const jwt = require('jsonwebtoken');
  const token = jwt.sign({ userId: user._id }, 'SECRET_KEY');
  ```
- **Middleware Protection**:
  ```javascript
  function auth(req, res, next) {
    const token = req.header('x-auth-token');
    if (!token) return res.status(401).send('Access denied');
    try {
      const decoded = jwt.verify(token, 'SECRET_KEY');
      req.user = decoded;
      next();
    } catch (err) { res.status(400).send('Invalid token'); }
  }
  ```

## 5. Frontend Integration
- **Serve Static Files**:
  ```javascript
  app.use(express.static('public'));
  ```
- **Template Engines (EJS)**:
  ```javascript
  app.set('view engine', 'ejs');
  app.get('/', (req, res) => res.render('index', { data }));
  ```

## 6. RESTful API Design
- **HTTP Methods**:
  - `GET` (Read), `POST` (Create), `PUT/PATCH` (Update), `DELETE`
- **Status Codes**:
  - `200 OK`, `201 Created`, `400 Bad Request`, `401 Unauthorized`, `404 Not Found`, `500 Server Error`

## 7. Deployment
- **Environment Variables**:
  ```javascript
  require('dotenv').config();
  const PORT = process.env.PORT || 3000;
  ```
- **Dockerize**:
  ```dockerfile
  FROM node:18
  WORKDIR /app
  COPY package*.json ./
  RUN npm install
  COPY . .
  CMD ["node", "server.js"]
  ```
- **Platforms**: Heroku, AWS EC2, or Render.com.

## 8. Security Essentials
- **Helmet**: Secure headers (`app.use(helmet())`).
- **Sanitize Inputs**: Use `express-validator`.
- **Rate Limiting**: `express-rate-limit`.

## 9. Testing (Jest/Mocha)
- **Basic Test**:
  ```javascript
  test('adds 1 + 2 to equal 3', () => {
    expect(sum(1, 2)).toBe(3);
  });
  ```

## 10. Real-Time (WebSockets)
- **Socket.io**:
  ```javascript
  const io = require('socket.io')(server);
  io.on('connection', (socket) => {
    socket.emit('message', 'Welcome!');
  });
  ```

## 11. Git Basics
- **Key Commands**:
  ```bash
  git init
  git add .
  git commit -m "Initial commit"
  git push origin main
  ```

## 12. Project Structure Best Practices
```
my-app/
├── server.js          # Entry point
├── package.json
├── config/            # DB/config files
├── models/            # Mongoose models
├── routes/            # Express routes
├── controllers/       # Business logic
├── middleware/        # Auth/validation
└── public/            # Frontend assets
```

## 13. 20% Practice Projects
1. **Todo App**: CRUD API + EJS frontend.
2. **Auth System**: JWT registration/login.
3. **Blog API**: REST endpoints + MongoDB.
4. **Real-Time Chat**: Socket.io basics.

---
