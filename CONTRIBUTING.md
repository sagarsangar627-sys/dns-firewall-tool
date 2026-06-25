# Contributing to DNS & Firewall Security Tool

Thank you for your interest in contributing! This document provides guidelines and instructions for contributing.

## Code of Conduct

- Be respectful and inclusive
- Report security issues privately
- Follow the existing code style

## Getting Started

1. Fork the repository
2. Clone your fork locally
3. Create a feature branch (`git checkout -b feature/AmazingFeature`)
4. Make your changes
5. Commit your changes (`git commit -m 'Add some AmazingFeature'`)
6. Push to the branch (`git push origin feature/AmazingFeature`)
7. Open a Pull Request

## Development Environment

### Prerequisites
- C++14 compatible compiler
- CMake 3.10+
- libpcap development headers
- libyaml development headers

### Build Instructions

```bash
./scripts/build.sh
```

### Running Tests

```bash
./scripts/run_tests.sh
```

## Code Style

- Use 4-space indentation
- Follow Google C++ style guide
- Use meaningful variable names
- Add comments for complex logic
- Avoid global variables when possible

## Testing

- Write tests for new features
- Ensure all tests pass before submitting PR
- Test both positive and negative cases
- Include edge case testing

## Documentation

- Update README.md if adding features
- Add inline comments for complex code
- Update architecture.md for structural changes
- Document new configuration options

## Commit Messages

- Use clear, descriptive messages
- Start with a verb (Add, Fix, Improve, etc.)
- Keep first line under 50 characters
- Add detailed explanation in body if needed

## Pull Request Process

1. Update documentation as needed
2. Add/update tests
3. Ensure all tests pass
4. Update CHANGELOG.md
5. Request review from maintainers
6. Address feedback promptly

## Reporting Issues

- Use GitHub Issues
- Provide clear description
- Include reproduction steps
- Share relevant log outputs
- Mention your environment

## Security

If you discover a security vulnerability, please email security@example.com instead of using the issue tracker.

## Questions?

Feel free to ask in the GitHub Discussions or create an issue for clarification.

Thank you for contributing!