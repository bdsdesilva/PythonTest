# Git Flow Commands Cheat Sheet

## Initial Setup (One-time)
```bash
# Clone the repository
git clone https://github.com/bdsdesilva/PythonTest.git
cd PythonTest

# Initialize git flow (optional - for local git flow tool)
git flow init
```

## Feature Development Workflow

### Start New Feature
```bash
# Method 1: Manual
git checkout develop
git pull origin develop
git checkout -b feature/feature-name

# Method 2: Using git-flow tool
git flow feature start feature-name
```

### Work on Feature
```bash
# Make changes to your code
git add .
git commit -m "Implement feature XYZ"
git push origin feature/feature-name
```

### Finish Feature
```bash
# Method 1: Manual
git checkout develop
git pull origin develop
git merge feature/feature-name
git push origin develop
git branch -d feature/feature-name
git push origin --delete feature/feature-name

# Method 2: Using git-flow tool
git flow feature finish feature-name
```

## Release Workflow

### Start Release
```bash
# Method 1: Manual
git checkout develop
git pull origin develop
git checkout -b release/1.0.0

# Method 2: Using git-flow tool
git flow release start 1.0.0
```

### Prepare Release
```bash
# Update version numbers, changelog, etc.
git add .
git commit -m "Bump version to 1.0.0"
git push origin release/1.0.0
```

### Finish Release
```bash
# Method 1: Manual
git checkout main
git pull origin main
git merge release/1.0.0
git tag -a v1.0.0 -m "Release 1.0.0"
git push origin main
git push origin v1.0.0

git checkout develop
git merge release/1.0.0
git push origin develop
git branch -d release/1.0.0
git push origin --delete release/1.0.0

# Method 2: Using git-flow tool
git flow release finish 1.0.0
```

## Hotfix Workflow

### Start Hotfix
```bash
# Method 1: Manual
git checkout main
git pull origin main
git checkout -b hotfix/1.0.1

# Method 2: Using git-flow tool
git flow hotfix start 1.0.1
```

### Fix and Test
```bash
# Make critical fixes
git add .
git commit -m "Fix critical bug in authentication"
git push origin hotfix/1.0.1
```

### Finish Hotfix
```bash
# Method 1: Manual
git checkout main
git pull origin main
git merge hotfix/1.0.1
git tag -a v1.0.1 -m "Hotfix 1.0.1"
git push origin main
git push origin v1.0.1

git checkout develop
git merge hotfix/1.0.1
git push origin develop
git branch -d hotfix/1.0.1
git push origin --delete hotfix/1.0.1

# Method 2: Using git-flow tool
git flow hotfix finish 1.0.1
```

## Branch Overview

- **main**: Production-ready code
- **develop**: Integration branch for new features
- **feature/\***: Feature development branches
- **release/\***: Release preparation branches
- **hotfix/\***: Critical bug fix branches

## Best Practices

1. **Always start feature branches from develop**
2. **Never commit directly to main**
3. **Use descriptive branch names**: `feature/user-authentication`, `hotfix/memory-leak`
4. **Test thoroughly before finishing releases**
5. **Keep feature branches small and focused**
6. **Write clear commit messages**
7. **Use pull requests for code review**
