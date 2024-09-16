
# URL Shortener with NestJS

A simple URL shortener service built using [NestJS](https://nestjs.com/) and SQLite, which allows users to shorten long URLs and redirect them using the generated short URL.

## Features

- Shorten long URLs into short, manageable links.
- Redirect users from the short URL to the original long URL.
- Simple, easy-to-use API.
- Built-in SQLite support.
  
## Tech Stack

- **Backend**: [NestJS](https://nestjs.com/)
- **Database**: SQLite (can be easily swapped for any other database like MySQL or PostgreSQL).
- **URL Shortening**: Using [shortid](https://www.npmjs.com/package/shortid) for generating unique short URLs.

## Getting Started

### Prerequisites

- [Node.js](https://nodejs.org/) (v14 or later)
- [NestJS CLI](https://docs.nestjs.com/cli/overview) (`npm install -g @nestjs/cli`)

### Installation

1. Clone the repository:

```bash
git clone https://github.com/yourusername/url-shortener-nestjs.git
cd url-shortener-nestjs
```

2. Install the dependencies:

```bash
npm install
```

3. Run the development server:

```bash
npm run start
```

4. The server will be running at `http://localhost:3000`.

### API Endpoints

- **POST /url/shorten**

  Shorten a long URL.

  **Request Body** (JSON):
  ```json
  {
    "originalUrl": "https://example.com"
  }
  ```

  **Response**:
  ```json
  {
    "originalUrl": "https://example.com",
    "shortUrl": "http://localhost:3000/url/abc123"
  }
  ```

- **GET /url/:shortUrl**

  Redirects to the original URL.

  Example:
  ```bash
  GET http://localhost:3000/url/abc123
  ```

### Configuration

By default, the project uses SQLite for storing URLs. The database is stored as `urlshortener.sqlite` in the root folder. If you want to switch to another database (like PostgreSQL or MySQL), modify the `TypeOrmModule` configuration in `app.module.ts`.

### Project Structure

```bash
src/
│
├── url/
│   ├── url.controller.ts   # API routes for URL shortening and redirection
│   ├── url.service.ts      # Business logic for URL management
│   ├── url.entity.ts       # URL database entity
│   └── url.module.ts       # URL module that bundles the controller and service
│
├── app.module.ts           # Main application module
└── main.ts                 # Entry point of the application
```

### Running the Application

1. Run the application:

   ```bash
   npm run start
   ```

2. The API will be available at `http://localhost:3000`.

### Testing

The project includes a basic API, and you can test it using [Postman](https://www.postman.com/) or `curl`.

- To shorten a URL, make a `POST` request to `/url/shorten` with the `originalUrl` in the body.
- Access the short URL using a `GET` request to `/url/:shortUrl`.

### License

This project is licensed under the MIT License. See the [LICENSE](LICENSE) file for details.

### Contributions

Feel free to submit issues or pull requests if you want to contribute. All contributions are welcome!

---

Happy coding! 🎉
