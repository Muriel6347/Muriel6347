# GitHub Settings Documentation

This repository uses GitHub Actions for continuous integration and code quality checks.

## Workflows

### 1. Tests (`tests.yml`)
- **Trigger:** Push to main/develop, Pull Requests
- **Purpose:** Run automated tests on Node.js versions 18.x and 20.x
- **Actions:** Install dependencies, run tests, and lint code

### 2. CodeQL (`codeql.yml`)
- **Trigger:** Push to main/develop, Pull Requests, Weekly schedule
- **Purpose:** Security analysis and vulnerability scanning
- **Actions:** Analyzes code for potential security issues

### 3. Code Quality (`quality.yml`)
- **Trigger:** Push to main/develop, Pull Requests
- **Purpose:** Enforce code quality standards
- **Actions:** Format checks, linting, and test coverage reports

## Branch Protection Rules

To enable branch protection:

1. Go to **Settings → Branches → Add rule**
2. Set branch name pattern to `main`
3. Enable:
   - ✓ Require a pull request before merging
   - ✓ Require status checks to pass before merging
   - ✓ Require branches to be up to date before merging
   - ✓ Require code reviews before merging (optional)
   - ✓ Dismiss stale pull request approvals

## Recommended Configuration

### Repository Settings
- **Visibility:** Public/Private (choose as needed)
- **Discussions:** Enable for community engagement
- **Issues:** Enable for bug tracking
- **Projects:** Enable for task management
- **Wiki:** Optional, for documentation

### Required Status Checks
- `test` job
- `analyze` job (CodeQL)
- `quality` job

## Next Steps

1. Configure `package.json` scripts:
   ```json
   {
     "scripts": {
       "test": "jest",
       "test:coverage": "jest --coverage",
       "lint": "eslint .",
       "format:check": "prettier --check .",
       "format": "prettier --write ."
     }
   }
   ```

2. Set up branch protection rules
3. Configure required status checks
4. Enable automated security updates (Dependabot)
