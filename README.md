# RBAC MERN Boilerplate

## Welcome to the RBAC MERN Boilerplate Project
A complete  MERN boilerplate repository with RBAC (Role-Based Access Control) features, following all production best practices.
![image](https://github.com/user-attachments/assets/b98c62ff-45ca-42ba-b166-b6c514b53945)
![image](https://github.com/user-attachments/assets/7acc1fc6-c600-43bc-b338-9bfe1939a9f3)


This repository is continuously updated with the best practices for a MERN (MongoDB, Express.js, React.js, and Node.js) project. The UI is built with Ant Design Pro for a better user experience, with potential future support for MUI.

## Technology Stack
### Client Side
- **React** - A JavaScript library for building user interfaces
- **Ant Design Pro** - A design system for enterprise-level products
- **Testing Library** - React Testing Library
- **Umi Request** - HTTP client for executing requests from the browser to the server

### Server Side
- **Node.js** - Event-driven I/O for the backend
- **Express.js** - Fast, minimalist web framework for Node.js
- **MongoDB** - NoSQL database
- **Mongoose** - Object Data Modeling (ODM) library for MongoDB
- **Swagger** - API documentation (Not implemented yet)
- **Jest** - JavaScript testing framework
- **Supertest** - API testing framework

For more details, check the `package.json` files in the `server` and `client` directories.

## Running the Application
The project can be run in two ways:
1. **Using Docker**
2. **Manually via Visual Studio Code**

![image](https://github.com/user-attachments/assets/6f9f012f-040c-4d7d-b38b-eb5da3fe613d)

### Docker
Select the appropriate `docker-compose` file based on the MongoDB hosting option:
- `docker-compose.mongocloud.yml` - For MongoDB.com hosted cluster
- `docker-compose.yml` - For local MongoDB container

#### Configuration
- Update `MONGODB_CLOUD_URL` in `docker-compose.mongocloud.yml` with the correct MongoDB connection string.
- Update `REACT_APP_API_URL` in `docker-compose.yml` with the appropriate API URL (default: `http://localhost:8002`).

#### Run Docker Commands
Ensure `docker` and `docker-compose` are installed on your machine. Navigate to the root of the repository and execute the following commands:

##### With Cloud-Hosted MongoDB
```sh
cd project-root
docker-compose -f docker-compose.mongocloud.yml build
docker-compose -f docker-compose.mongocloud.yml up
```

##### With Local MongoDB
```sh
cd project-root
docker-compose build
docker-compose up
```

Once running, the client and server should be accessible via the client URL.

### Data Seeding
Run the following commands inside the Docker container to seed the database with roles, users, and products:
```sh
docker exec -it appserver bash
npm run db:seed
npm run db:migrate
```
![image](https://github.com/user-attachments/assets/d7916dec-20a5-4f82-a773-2718c3506ce7)
![image](https://github.com/user-attachments/assets/7b8392bb-23ef-42ff-86dc-d8de2adc0c70)


## Running the Application Manually (VS Code)
### Prerequisites
- **Node.js** - To run npm packages
- **MongoDB** - To store application data

### Steps
1. Ensure MongoDB is running.
2. Create a `.env` file inside the `server` directory with the following values (modify as needed):
```
DB_HOST=localhost
DB_PORT=27017
DB_NAME=appdb
JWT_SECRET=secret
JWT_EXPIRES_IN=3600
PORT=5000
IS_MONGODB_CLOUD_URL=false
MONGODB_CLOUD_URL=mongodb+srv://<USER>:<PASSWORD>@cluster0.abcd.mongodb.net/myFirstDatabase?retryWrites=true
```

### Start the Server
```sh
cd server
npm i
npm run db:up
npm start
```

### Start the Client
```sh
cd client-pro
nvm use --lts
yarn
yarn start
```

## Permission Management UI
The application includes a permission management UI. Below is a sample:

![Uploading image.png…]()

*(Placeholder for permission management UI image)*

## Logging with Sentry.io
Centralized logging is enabled via [Sentry.io](https://sentry.io/). To configure, update `client/src/env.config.js` with your DSN.

```js
Sentry.init({
  dsn: Config.dsn,
  integrations: [new Integrations.BrowserTracing()],
  tracesSampleRate: 1.0,
});
```

## API Testing (Not Implemented Yet)
Visit `http://localhost:5000/api-docs` to view API documentation (Swagger setup pending). Use the provided Postman collection in `docs/rbac-mern-boilerplate.postman_collection.json` for testing API endpoints.

## Scripts
| Project | Command | Task |
|---------|---------|------|
| Root | `npm run build` | Build the containers |
| Root | `npm run start` | Start projects & DB in Docker |
| Root | `docker exec -it appserver /bin/sh && npm run db:seed` | Seed database |
| Server | `npm i` | Install dependencies |
| Server | `npm run db:up` | Start database in Docker |
| Server | `npm run test` | Run Jest tests |
| Client | `npm i` | Install dependencies |
| Client | `npm run start` | Start React app |
| Client | `npm run build` | Build React app for production |
| Client | `npm run test` | Run tests using Testing Library |

## Testing
This repository includes both unit and integration tests. The current code coverage is low but will be improved to 90%+ in future updates.

### Client-Side Testing
Unit tests mock external dependencies (e.g., `localStorage`, `axios`).
```sh
npm run test
```

### Server-Side Testing
- **Integration Testing** - Uses Jest, Supertest, and MongoDB memory server.
- **Unit Testing** - Uses Jest, mocking external dependencies like MongoDB.
```sh
npm run test
```

## License
This project is licensed under the MIT License.

## Contribution
Currently, external code contributions are not accepted. However, if you find bugs or have suggestions, feel free to open an issue or pull request.

For discussions, visit our **GitHub Discussion Board**.

## Tutorials & Support
This project is documented in a YouTube playlist (in Bangla). For paid English sessions, contact `foyzulkarim@gmail.com`.

Thanks! 🚀

