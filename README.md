# JWKS Server Project 2

This project implements a secure JSON Web Key Set (JWKS) server using SQLite to store private keys. It provides endpoints for issuing JWTs and serving valid public keys via JWKS. This server also implements protection against SQL injection attacks.

## Prerequisites

Before running this project, ensure that you have Python 3.x installed. If you don't have Python installed, you can download it from [python.org](https://www.python.org/downloads/).

Additionally, you will need `pip` (Python's package manager) to install required dependencies.

## Setup Instructions

Follow these steps to set up the environment and run the project:

### 1. Create a Virtual Environment
```bash
python -m venv venv
venv\Scripts\activate
```

### 2. Install Dependencies
```bash
pip install -r requirements.txt
```

### 3. Run the Server
- Ensure gradebot.exe is within the project directory
```bash
python app.py
```

### 4. Testing Endpoints
- Get JWKS (Returns public keys in JSON Web Key Set format)
```bash
curl http://localhost:8080/.well-known/jwks.json
```
- Post Auth (Issues a JWT using a valid private key)
```bash
curl -X POST http://localhost:8080/auth
```

- Post Auth with Expired Key (Issues a JWT using an expired private key)
```bash
curl -X POST "http://localhost:8080/auth?expired=true"
```

### 5. Run Tests
```bash
pytest test_app.py --cov=app --cov-report=term-missing
```
