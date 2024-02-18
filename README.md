# RSSFlow: Go-based RSS Blog Aggregator

RSSFlow is a powerful RSS feed aggregator built using Go! It provides a web server where users can:

- Add RSS feeds to be collected.
- Follow and unfollow RSS feeds added by other users.
- Fetch all the latest posts from the RSS feeds they follow.

This project focuses on leveraging Go for backend development, PostgreSQL for database management, and provides an insightful experience in integrating a Go server with PostgreSQL, database migrations, and long-running service workers.

## Personal Learning Goals

- **Integrate Go with PostgreSQL**: Learn how to connect a Go server with PostgreSQL for data storage and retrieval.
- **Database Migrations**: Gain experience with basic database migrations for setting up and managing database schemas.
- **Long-running Service Workers**: Understand how to implement service workers that continuously collect data from RSS feeds.

## Features

- **RSS Feed Management**: Users can add, follow, and unfollow RSS feeds.
- **RSS Post Collection**: Fetch the latest blog posts from the feeds users are following.
- **Web Interface**: Simple HTTP endpoints to interact with the system.
- **PostgreSQL Integration**: Efficiently stores and manages user data and RSS feed information in PostgreSQL.

## Tech Stack

- **Backend**: Go (Golang)
- **Database**: PostgreSQL
- **Database Migrations**: Goose
- **Environment Configuration**: .env file with `godotenv` for configuration management

## Setup

### 1. Clone the Repository

Start by cloning the repository to your local machine:

```bash
git clone https://github.com/yourusername/rssflow.git
cd rssflow
```

### 2. Configuration

#### a. Define Port

Create a `.env` file in the root of the project and specify the server port:

```bash
PORT="8080"
```

This file will automatically be loaded using `godotenv.Load()` in the main function to set up the environment variables.

#### b. Database Connection String

Add the PostgreSQL connection string to your `.env` file. Make sure to replace the values for username, password, port, and database name:

```bash
CONN=postgres://username:password@localhost:5555/blogator?sslmode=disable
```

- Replace `username`, `password`, and `database` with your own credentials.

### 3. Installing Dependencies

Ensure that you have Go installed and set up the development environment. If you're using Nix, you can utilize the provided `nix` flake to manage dependencies:

```bash
nix develop
```

This will set up the correct environment and install the necessary dependencies for the project.

### 4. Database Setup

#### a. Connect to PostgreSQL Database

Test your PostgreSQL connection string by running the following command with `psql`:

```bash
psql "postgres://username:password@localhost:5555/blogator"
```

This should connect you to the `blogator` database, where you can store and retrieve data related to RSS feeds and user actions.

#### b. Running Database Migrations

The project uses Goose for database migrations. To apply migrations, follow these steps:

1. Navigate to the `sql` directory:

   ```bash
   cd sql
   ```

2. Run the migration to update the database schema:

   ```bash
   goose postgres postgres://username:password@localhost:5555/blogator up
   ```

This will apply any pending migrations to the database and set up the necessary tables for the project.

## Usage

After setting up the environment and database, you can run the server.

1. **Build the project**:

   ```bash
   go build -o out && ./out
   ```

2. **Start the server**:

   The server will start on port `8080` by default, as defined in the `.env` file. You can adjust this if necessary.

3. **Test the server**:

   Once the server is running, you can test it by sending HTTP requests to interact with the various endpoints (e.g., add RSS feeds, follow feeds, fetch posts).

## Endpoints

- **POST /feeds**: Add a new RSS feed.
- **GET /feeds**: Get all the RSS feeds that the user is following.
- **POST /feeds/follow**: Follow a specific RSS feed.
- **POST /feeds/unfollow**: Unfollow a specific RSS feed.
- **GET /posts**: Get the latest posts from all the RSS feeds the user is following.

## Project Structure

- **cmd**: Main entry point for the server.
- **config**: Configuration and environment setup.
- **models**: Database models for users, feeds, and posts.
- **routes**: HTTP route handlers.
- **workers**: Service workers to periodically fetch new posts from RSS feeds.

## Contributing

Feel free to fork the repository and submit pull requests. Please follow the code style guidelines and ensure that your changes are well-tested.

1. Fork the repository.
2. Create a new branch (`git checkout -b feature-name`).
3. Commit your changes (`git commit -m 'Add feature-name'`).
4. Push to the branch (`git push origin feature-name`).
5. Open a Pull Request.

## License

This project is licensed under the MIT License. See the [LICENSE](LICENSE) file for more details.

## Contact

If you have any questions or issues, feel free to open an issue or reach out to me directly at [deshdeepakkant@gmail.com].

---

Made with ❤️ by Desh Deepak Kant