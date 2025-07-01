# Events Booking Backend

A Node.js/TypeScript backend for an events booking system using Express and MongoDB.

## Features

- User registration and authentication (JWT)
- Event creation, update, deletion, and booking
- Event types: free and pro
- RESTful API endpoints
- Input validation
- Password hashing
- MongoDB with Mongoose

## Technologies Used

- Node.js
- TypeScript
- Express.js
- MongoDB (Mongoose)
- JWT (jsonwebtoken)
- bcryptjs
- express-validator
- cors
- dotenv

## Project Structure

```
├── middlewares/
│   ├── authUser.ts
│   └── createEventM.ts
├── models/
│   ├── IEvent.ts
│   ├── IUser.ts
│   ├── event.ts
│   └── user.ts
├── routers/
│   ├── eventsRouter.ts
│   └── usersRouter.ts
├── server.ts
├── package.json
└── tsconfig.json
```

## Getting Started

1. **Clone the repository**
2. **Install dependencies**
   ```bash
   npm install
   ```
3. Create a `.env` file with the following variables:

```
MONGO_DB_LOCAL=mongodb://localhost:27017/your-db-name
HOST_NAME=localhost
PORT=3000
JWT_SECRET_KEY=your-secret-key
```

4. **Start the server**
   ```bash
   npm run start
   ```

## API Endpoints

### Users

- POST /users/registe : Register a new user
- POST /users/login : Login and receive JWT token

### Events

- POST /events/ : Create a new event (fields: title, body, price, type ['free'|'pro'], image)
- GET /events/ : Get all events or a single event by eventId query parameter
- GET /events/free : Get all free events
- GET /events/pro : Get all pro events
- PUT /events/ : Update an event by eventId query parameter
- DELETE /events/:eventId : Delete an event by ID
- POST /events/book : Book an event (requires JWT in Authorization header and eventId query parameter)

## Models

### User

- firstName (required)
- lastName
- username (required, unique)
- email (required, unique)
- password (hashed)
- avatar
- eventsBooked (array of events)
- isAdmin (default: false)

### Event

- title (required)
- body (required)
- price (required)
- type (required: 'free' or 'pro')
- image (required)

## Middlewares

- authUser : Authenticates user credentials
- createEventMiddle : Sets price to 0 for free events

## Environment Variables

- MONGO_DB_LOCAL : MongoDB connection string
- HOST_NAME : Server hostname
- PORT : Server port
- JWT_SECRET_KEY : JWT secret key

## License

ISC
