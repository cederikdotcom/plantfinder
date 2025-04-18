# Plantfinder

Plantfinder is a powerful plant identification application that lets users take pictures of plants and discover similar species. The application is designed to serve hobby gardeners looking to expand their knowledge and collection.

![Plantfinder Logo](assets/logo.png)

## Features

- **Plant Identification**: Take a photo of any plant to identify it and find similar species
- **Comprehensive Plant Repository**: Access to an up-to-date database of plants, including care instructions and growing tips
- **Friend Feature**: Connect with other gardeners, share discoveries, and exchange tips
- **Multi-tier Access**: Free, Pro, and Enterprise subscription options

## Table of Contents

- [Getting Started](#getting-started)
  - [Prerequisites](#prerequisites)
  - [Installation](#installation)
- [Development](#development)
  - [Tech Stack](#tech-stack)
  - [Project Structure](#project-structure)
  - [Environment Variables](#environment-variables)
- [Deployment](#deployment)
- [Testing](#testing)
- [Contributing](#contributing)
- [License](#license)
- [Contact](#contact)

## Getting Started

### Prerequisites

- Node.js (v16.x or later)
- Python (v3.8 or later)
- PostgreSQL (v13 or later)
- TensorFlow (v2.8 or later)
- Docker and Docker Compose (optional, for containerized development)

### Installation

1. Clone the repository:
   ```bash
   git clone https://github.com/yourusername/plantfinder.git
   cd plantfinder
   ```

2. Set up the backend:
   ```bash
   cd backend
   python -m venv venv
   source venv/bin/activate  # On Windows: venv\Scripts\activate
   pip install -r requirements.txt
   python manage.py migrate
   ```

3. Set up the frontend:
   ```bash
   cd ../frontend
   npm install
   ```

4. Start the development servers:
   ```bash
   # In one terminal (backend)
   cd backend
   source venv/bin/activate  # On Windows: venv\Scripts\activate
   python manage.py runserver
   
   # In another terminal (frontend)
   cd frontend
   npm start
   ```

5. Visit `http://localhost:3000` to see the application running.

## Development

### Tech Stack

- **Frontend**: React Native (mobile), React (web)
- **Backend**: Django REST Framework
- **Database**: PostgreSQL
- **ML Model**: TensorFlow/PyTorch
- **Image Processing**: OpenCV
- **Authentication**: JWT
- **Infrastructure**: AWS (ECS, S3, RDS)

### Project Structure

```
plantfinder/
├── backend/               # Django REST Framework backend
│   ├── api/               # API endpoints
│   ├── ml/                # Machine learning models
│   ├── plants/            # Plant database logic
│   └── users/             # User management
├── frontend/              # React Native mobile app & React web app
│   ├── mobile/            # Mobile application
│   └── web/               # Web application
├── ml-training/           # Scripts for ML model training
├── docs/                  # Documentation
└── infrastructure/        # IaC and deployment scripts
```

### Environment Variables

Create a `.env` file in both the `backend` and `frontend` directories. Examples are provided in `.env.example`.

Required environment variables:

```
# Backend
DATABASE_URL=postgresql://user:password@localhost:5432/plantfinder
SECRET_KEY=your-secret-key
AWS_ACCESS_KEY_ID=your-access-key
AWS_SECRET_ACCESS_KEY=your-secret-key
ML_MODEL_PATH=path/to/model

# Frontend
REACT_APP_API_URL=http://localhost:8000/api
```

## Deployment

### Production Deployment

1. Build the Docker images:
   ```bash
   docker-compose -f docker-compose.prod.yml build
   ```

2. Deploy to AWS ECS:
   ```bash
   cd infrastructure
   terraform init
   terraform apply
   ```

### Staging Deployment

For staging deployments, use:

```bash
cd infrastructure
terraform workspace select staging
terraform apply -var-file=staging.tfvars
```

## Testing

### Running Tests

```bash
# Backend tests
cd backend
pytest

# Frontend tests
cd frontend
npm test
```

### CI/CD Pipeline

This project uses GitHub Actions for CI/CD. The configuration is in `.github/workflows/`.

## Contributing

We welcome contributions to Plantfinder! Please follow these steps:

1. Fork the repository
2. Create a feature branch: `git checkout -b feature/amazing-feature`
3. Commit your changes: `git commit -m 'Add amazing feature'`
4. Push to the branch: `git push origin feature/amazing-feature`
5. Open a Pull Request

Please read [CONTRIBUTING.md](CONTRIBUTING.md) for details on our code of conduct and the process for submitting pull requests.

### Development Guidelines

- Follow the coding style defined in the `.editorconfig` file
- Write tests for new features
- Update documentation when changing functionality
- Use descriptive commit messages

## License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

## Contact

Project Link: [https://github.com/yourusername/plantfinder](https://github.com/yourusername/plantfinder)

Website: [https://plantfinder.app](https://plantfinder.app)
