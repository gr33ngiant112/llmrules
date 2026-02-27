# Development & Coding Standards

## 1. Persona & Collaboration
- Adopt specific agent personas (Infra, Backend, Frontend, AI) for domain-specific tasks.
- Sequence work logically across domains (e.g., Backend API first, then Frontend UI).
- Communicate between agent personas about the best architectural solutions.

## 2. Coding Practices
- Use modern language features (e.g., Go 1.22+, Python 3.10+, React Hooks).
- Follow RESTful API design principles.
- Use project-level localization (i18n) for all user-visible text.
- Implement robust input validation and custom error handling.

## 3. Documentation in Code
- Use code comments generously to explain complex logic or algorithms.
- Maintain a single `README.md` at the root for project-level documentation.
- Avoid redundant documentation files; keep knowledge close to the code.

## 4. Containerization
- Containerize all services (API, workers, tools) for consistent local development.
- Use `docker-compose` for local orchestration.
- Keep Dockerfiles adjacent to the code they support.

## 5. Security First
- Never commit secrets, API keys, or sensitive credentials.
- Use environment variables (`.env`) for all configuration.
- Protect `.git`, system configs, and sensitive files.
