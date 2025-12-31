# Contributing to UniFi Network MCP

Thank you for your interest in contributing! We welcome contributions from the community.

## Getting Started

1. **Fork the repository** on GitHub
2. **Clone your fork** locally:
   ```bash
   git clone https://github.com/your-username/unifi-network-mcp.git
   cd unifi-network-mcp
   ```

3. **Create a branch** for your changes:
   ```bash
   git checkout -b feature/your-feature-name
   ```

## Development Setup

```bash
# Install dependencies
go mod download

# Build the project
make build

# Run tests
make test

# Run with Docker
make docker-build
make docker-run
```

## Making Changes

- **Code Style**: Follow Go conventions
- **Testing**: Add tests for new features
- **Documentation**: Update docs for API changes
- **Commits**: Use clear, descriptive commit messages

## Submitting Changes

1. **Push to your fork**:
   ```bash
   git push origin feature/your-feature-name
   ```

2. **Open a Pull Request** with:
   - Clear description of changes
   - Reference to any related issues (#123)
   - Explanation of why the change is needed

3. **Wait for review** - maintainers will review and provide feedback

## Reporting Issues

- **Bugs**: Use the bug report template, include reproduction steps
- **Features**: Use feature request template, explain use case
- **Security**: See SECURITY.md for reporting sensitive issues

## Code of Conduct

Please review our [CODE_OF_CONDUCT.md](CODE_OF_CONDUCT.md) before contributing.

## Questions?

Open an issue or discussion on GitHub - we're here to help!

---

**Thank you for contributing to UniFi Network MCP!** 🙏
