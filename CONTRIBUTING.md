# Contributing to Dr. HealBot

Thank you for your interest in contributing to Dr. HealBot! This document provides guidelines for contributing to the project.

## How to Contribute

### Reporting Bugs

If you find a bug, please create an issue with:
- Clear description of the problem
- Steps to reproduce
- Expected vs actual behavior
- Screenshots if applicable
- Your environment (OS, Python version, etc.)

### Suggesting Features

Feature suggestions are welcome! Please:
- Check if the feature has already been requested
- Clearly describe the feature and its benefits
- Provide examples of how it would work

### Code Contributions

1. **Fork the Repository**
   ```bash
   git clone https://github.com/YOUR_USERNAME/finalChatDoc.git
   cd finalChatDoc
   ```

2. **Create a Branch**
   ```bash
   git checkout -b feature/your-feature-name
   ```

3. **Make Your Changes**
   - Follow the existing code style
   - Add comments for complex logic
   - Update documentation if needed

4. **Test Your Changes**
   ```bash
   # Run the application
   uvicorn app:app --reload
   
   # Test all features:
   # - Chat functionality
   # - Voice features
   # - Patient history
   # - Error handling
   ```

5. **Commit Your Changes**
   ```bash
   git add .
   git commit -m "Add: brief description of changes"
   ```

6. **Push and Create Pull Request**
   ```bash
   git push origin feature/your-feature-name
   ```

## Code Style Guidelines

### Python
- Follow PEP 8 style guide
- Use meaningful variable names
- Add docstrings to functions
- Keep functions focused and small

### JavaScript/HTML
- Use consistent indentation (2 spaces)
- Add comments for complex logic
- Keep code modular

## Areas for Contribution

### High Priority
- [ ] Add more AI model providers (OpenAI, Claude, etc.)
- [ ] Improve error handling and user feedback
- [ ] Add unit tests
- [ ] Enhance UI/UX
- [ ] Add multi-language support for UI

### Medium Priority
- [ ] Add patient data export feature
- [ ] Implement appointment scheduling
- [ ] Add medication reminders
- [ ] Improve accessibility features

### Nice to Have
- [ ] Mobile app version
- [ ] Integration with health tracking devices
- [ ] Advanced analytics dashboard
- [ ] Telemedicine video integration

## Development Setup

1. **Install Dependencies**
   ```bash
   pip install -r requirements.txt
   ```

2. **Set Up Environment**
   ```bash
   cp .env.example .env
   # Add your API keys
   ```

3. **Run in Development Mode**
   ```bash
   uvicorn app:app --reload
   ```

## Testing

Before submitting a PR:
- [ ] Test all chat flows
- [ ] Verify voice features work
- [ ] Check error handling
- [ ] Test on different browsers
- [ ] Ensure no API keys are committed

## Questions?

Feel free to:
- Open an issue for discussion
- Reach out to maintainers
- Check existing issues and PRs

---

Thank you for contributing to Dr. HealBot! 🩺
