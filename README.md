# Chat Server Application

A Flask-based chat server application with OAuth authentication, real-time messaging using SocketIO, and email notifications.

## Features

- User authentication with Google OAuth
- Real-time chat functionality using SocketIO
- Email notifications
- User profile management
- MySQL database integration
- Multilingual support (Vietnamese)

## Prerequisites

- Python 3.x
- MySQL Server
- SMTP server access (Gmail)
- Google OAuth credentials

## Installation

1. Clone the repository:
```bash
git clone <repository-url>
cd chat-server
```

2. Create and activate a virtual environment:
```bash
python -m venv venv
source venv/bin/activate  # On Windows use: venv\Scripts\activate
```

3. Install dependencies:
```bash
pip install -r requirements.txt
```

4. Configure environment variables:
   - Copy `.env.example` to `.env`
   - Update the following variables with your values:
```
SECRET_KEY=<your-secret-key>
NAME_DB=chat_server
PW_DB=<your-database-password>
OAUTH_CLIENT_ID=<your-google-oauth-client-id>
OAUTH_CLIENT_SECRET=<your-google-oauth-client-secret>
MAIL_USERNAME=<your-email>
MAIL_PASSWORD=<your-email-app-password>
```

5. Set up the MySQL database:
   - Create a database named 'chat_server'
   - Configure database credentials in `.env`

6. Configure OAuth:
   - Set up a project in Google Cloud Console
   - Create OAuth 2.0 credentials
   - Add authorized redirect URIs:
     - https://localhost:5001/callback

## Security Configuration

1. Enable HTTPS:
   - SSL certificates are located in `chat_server/ssl/`
   - Ensure valid certificates are in place

2. Environment Security:
   - Never commit `.env` file
   - Use strong, random SECRET_KEY
   - Store sensitive credentials only in environment variables
   - Use app-specific passwords for email services

## Running the Application

1. Start the server:
```bash
python -m flask run --port=5001 --cert=chat_server/ssl/cert.pem --key=chat_server/ssl/key.pem
```

2. Access the application:
   - Open https://localhost:5001 in your browser
   - Login with Google OAuth

## Project Structure

```
chat_server/
├── __init__.py          # Application initialization
├── controllers.py       # Route handlers
├── dao.py              # Data access objects
├── decorators.py       # Custom decorators
├── models.py           # Database models
├── static/             # Static files (CSS, JS, images)
├── templates/          # HTML templates
└── ssl/                # SSL certificates
```

## Development Guidelines

1. Security:
   - Always use HTTPS in production
   - Keep dependencies updated
   - Follow secure coding practices
   - Never commit sensitive credentials

2. Code Style:
   - Follow PEP 8
   - Use meaningful variable names
   - Add comments for complex logic
   - Keep functions focused and modular
