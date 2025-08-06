# PythonTest

A Python test repository demonstrating **Git Flow** branching strategy.

## Git Flow Branching Strategy

This repository follows the **Git Flow** branching model, which provides a robust framework for managing releases and development.

### Branch Structure

#### Main Branches
- **`main`** - Production-ready code. Only accepts merges from `release` and `hotfix` branches
- **`develop`** - Integration branch for features. The main development branch

#### Supporting Branches
- **`feature/*`** - Feature development branches (e.g., `feature/user-authentication`)
- **`release/*`** - Release preparation branches (e.g., `release/1.0.0`)
- **`hotfix/*`** - Critical bug fixes for production (e.g., `hotfix/1.0.1`)

### Workflow

#### Feature Development
```bash
# Create and switch to feature branch from develop
git checkout develop
git pull origin develop
git checkout -b feature/new-feature

# Work on your feature...
git add .
git commit -m "Add new feature"

# Push feature branch
git push origin feature/new-feature

# Create PR: feature/new-feature → develop
```

#### Release Process
```bash
# Create release branch from develop
git checkout develop
git pull origin develop
git checkout -b release/1.0.0

# Final testing, bug fixes, version bumps...
git add .
git commit -m "Prepare release 1.0.0"

# Merge to main
git checkout main
git merge release/1.0.0
git tag -a v1.0.0 -m "Release version 1.0.0"

# Merge back to develop
git checkout develop
git merge release/1.0.0

# Delete release branch
git branch -d release/1.0.0
```

#### Hotfix Process
```bash
# Create hotfix branch from main
git checkout main
git pull origin main
git checkout -b hotfix/1.0.1

# Fix critical issue...
git add .
git commit -m "Fix critical bug"

# Merge to main
git checkout main
git merge hotfix/1.0.1
git tag -a v1.0.1 -m "Hotfix version 1.0.1"

# Merge to develop
git checkout develop
git merge hotfix/1.0.1

# Delete hotfix branch
git branch -d hotfix/1.0.1
```

## Project Structure

```
PythonTest/
├── src/                    # Source code
│   └── main.py            # Main application
├── tests/                 # Test files (to be added)
├── docs/                  # Documentation (to be added)
├── .gitignore            # Git ignore rules
├── requirements.txt       # Python dependencies
└── README.md             # This file
```

## Setup and Installation

1. **Clone the repository**
   ```bash
   git clone https://github.com/bdsdesilva/PythonTest.git
   cd PythonTest
   ```

2. **Create virtual environment**
   ```bash
   python -m venv venv
   source venv/bin/activate  # On Windows: venv\Scripts\activate
   ```

3. **Install dependencies**
   ```bash
   pip install -r requirements.txt
   ```

4. **Run the application**
   ```bash
   python src/main.py
   ```

## Contributing

1. **Start from develop branch**
   ```bash
   git checkout develop
   git pull origin develop
   ```

2. **Create feature branch**
   ```bash
   git checkout -b feature/your-feature-name
   ```

3. **Make changes and commit**
   ```bash
   git add .
   git commit -m "Descriptive commit message"
   ```

4. **Push and create PR**
   ```bash
   git push origin feature/your-feature-name
   # Create PR: feature/your-feature-name → develop
   ```

## Version History

- **v0.1.0-dev** - Initial development setup with git flow structure

## License

This project is for testing and demonstration purposes.
