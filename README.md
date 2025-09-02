# SMARTCRAM - AI-Powered Interactive Flashcards & Quiz Generator

A complete, scalable web application that generates interactive flashcards and quizzes using AI technology.

## 🚀 Features

- **AI-Powered Content Generation**: Uses OpenAI API to create flashcards and quizzes from text input
- **Interactive Flashcards**: Study with Q&A style flashcards
- **Multiple Choice Quizzes**: Test knowledge with AI-generated quizzes
- **User Authentication**: Secure user registration and login system
- **Export/Import**: Save and share flashcard sets and quizzes
- **Responsive Design**: Works on desktop, tablet, and mobile devices
- **Real-time Generation**: Instant content creation with loading states

## 🛠️ Tech Stack

### Frontend
- **HTML5**: Semantic markup and modern web standards
- **CSS3**: Responsive design with CSS Grid and Flexbox
- **JavaScript (ES6+)**: Vanilla JS with modern async/await patterns

### Backend
- **Python 3.11+**: Core programming language
- **FastAPI**: High-performance web framework
- **MySQL**: Relational database for data persistence
- **SQLAlchemy**: ORM for database operations
- **Alembic**: Database migrations
- **OpenAI API**: AI content generation engine

### DevOps
- **Docker**: Containerization for easy deployment
- **Docker Compose**: Multi-service orchestration
- **JWT**: Secure authentication tokens

## 📁 Project Structure

```
SMARTCRAM/
├── backend/
│   ├── app/
│   │   ├── core/
│   │   │   ├── config.py          # Configuration settings
│   │   │   ├── security.py        # JWT and password utilities
│   │   │   └── openai_client.py   # OpenAI API integration
│   │   ├── db/
│   │   │   ├── database.py        # Database connection
│   │   │   └── models.py          # SQLAlchemy models
│   │   ├── schemas/
│   │   │   ├── auth.py            # Authentication schemas
│   │   │   ├── flashcards.py      # Flashcard schemas
│   │   │   └── quiz.py            # Quiz schemas
│   │   ├── routers/
│   │   │   ├── auth.py            # Authentication endpoints
│   │   │   ├── flashcards.py      # Flashcard endpoints
│   │   │   ├── quiz.py            # Quiz endpoints
│   │   │   └── export_import.py   # Export/import endpoints
│   │   └── main.py                # FastAPI application
│   ├── alembic/                   # Database migrations
│   ├── requirements.txt           # Python dependencies
│   ├── Dockerfile                 # Backend container
│   └── alembic.ini               # Alembic configuration
├── frontend/
│   ├── index.html                # Main HTML file
│   ├── styles.css                # CSS styles
│   ├── script.js                 # JavaScript functionality
│   └── Dockerfile                # Frontend container
├── docs/
│   ├── API.md                    # API documentation
│   ├── DEPLOYMENT.md             # Deployment guide
│   └── DEVELOPMENT.md            # Development guide
├── docker-compose.yml            # Multi-service orchestration
├── .env.example                  # Environment variables template
└── README.md                     # This file
```

## 🚀 Quick Start

### Prerequisites
- Python 3.11+
- MySQL 8.0+
- Docker & Docker Compose (optional)
- OpenAI API key

### Option 1: Docker (Recommended)

1. **Clone and setup**:
   ```bash
   git clone <repository-url>
   cd SMARTCRAM
   cp .env.example .env
   ```

2. **Configure environment**:
   Edit `.env` file:
   ```env
   OPENAI_API_KEY=your_openai_api_key_here
   DATABASE_URL=mysql+mysqlconnector://smartcram:smartpass@db:3306/smartcram
   ```

3. **Start services**:
   ```bash
   docker compose up --build
   ```

4. **Access the application**:
   - Frontend: http://localhost:8080
   - Backend API: http://localhost:8000
   - API Documentation: http://localhost:8000/docs

### Option 2: Local Development

1. **Setup database**:
   ```bash
   # Create MySQL database
   mysql -u root -p
   CREATE DATABASE smartcram;
   CREATE USER 'smartcram'@'localhost' IDENTIFIED BY 'smartpass';
   GRANT ALL PRIVILEGES ON smartcram.* TO 'smartcram'@'localhost';
   FLUSH PRIVILEGES;
   ```

2. **Setup Python environment**:
   ```bash
   cd backend
   python -m venv venv
   source venv/bin/activate  # On Windows: venv\Scripts\activate
   pip install -r requirements.txt
   ```

3. **Configure environment**:
   ```bash
   cp .env.example .env
   # Edit .env with your database and OpenAI credentials
   ```

4. **Run database migrations**:
   ```bash
   cd backend
   alembic upgrade head
   ```

5. **Start backend**:
   ```bash
   uvicorn app.main:app --reload --host 0.0.0.0 --port 8000
   ```

6. **Open frontend**:
   Open `frontend/index.html` in your browser or serve it with a local server.

## 📚 API Documentation

### Authentication Endpoints
- `POST /auth/register` - Register new user
- `POST /auth/login` - Login user
- `GET /auth/me` - Get current user info

### Flashcard Endpoints
- `POST /flashcards/generate` - Generate flashcards from text
- `GET /flashcards/{set_id}` - Get flashcard set
- `GET /flashcards/` - List all flashcard sets

### Quiz Endpoints
- `POST /quiz/generate` - Generate quiz from text
- `GET /quiz/{quiz_id}` - Get quiz
- `GET /quiz/` - List all quizzes

### Export/Import Endpoints
- `GET /transfer/export/flashcards/{set_id}` - Export flashcard set
- `POST /transfer/import/flashcards` - Import flashcard set
- `GET /transfer/export/quiz/{quiz_id}` - Export quiz
- `POST /transfer/import/quiz` - Import quiz

## 🎯 Usage Examples

### Generate Flashcards
1. Navigate to the flashcards section
2. Enter a topic (e.g., "Photosynthesis")
3. Paste source text or notes
4. Set number of cards (1-30)
5. Click "Generate Flashcards"
6. Study the generated Q&A cards

### Generate Quiz
1. Navigate to the quiz section
2. Enter a topic (e.g., "Cell Biology")
3. Paste source text or notes
4. Set number of questions (1-20)
5. Click "Generate Quiz"
6. Take the multiple-choice quiz

### Export/Import
- Export: Download flashcard sets or quizzes as JSON
- Import: Upload previously exported files to restore content

## 🔧 Development

### Running Tests
```bash
cd backend
pytest
```

### Database Migrations
```bash
cd backend
# Create new migration
alembic revision --autogenerate -m "description"

# Apply migrations
alembic upgrade head

# Rollback migration
alembic downgrade -1
```

### Code Style
- Python: Follow PEP 8
- JavaScript: Use ES6+ features
- CSS: Use BEM methodology

## 🚀 Deployment

### Production Deployment
1. Set up production MySQL database
2. Configure environment variables
3. Build and run Docker containers
4. Set up reverse proxy (nginx)
5. Configure SSL certificates

See `docs/DEPLOYMENT.md` for detailed deployment instructions.

## 🤝 Contributing

1. Fork the repository
2. Create a feature branch
3. Make your changes
4. Add tests if applicable
5. Submit a pull request

## 📄 License

This project is licensed under the MIT License - see the LICENSE file for details.

## 🆘 Support

- Check the documentation in the `docs/` folder
- Review API documentation at `/docs` when running the backend
- Open an issue for bugs or feature requests

## 🔮 Roadmap

- [ ] Spaced repetition algorithm
- [ ] Study progress tracking
- [ ] Collaborative flashcard sets
- [ ] Mobile app
- [ ] Advanced quiz types
- [ ] Integration with learning management systems
