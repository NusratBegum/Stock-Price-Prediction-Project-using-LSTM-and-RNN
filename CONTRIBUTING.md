# Contributing to Stock Price Prediction Project

First off, thank you for considering contributing to this project! It's people like you that make this project such a great learning resource.

## Table of Contents

- [Code of Conduct](#code-of-conduct)
- [How Can I Contribute?](#how-can-i-contribute)
- [Development Setup](#development-setup)
- [Contribution Guidelines](#contribution-guidelines)
- [Style Guide](#style-guide)
- [Commit Messages](#commit-messages)

## Code of Conduct

This project and everyone participating in it is governed by our commitment to fostering an open and welcoming environment. By participating, you are expected to uphold this code:

- Use welcoming and inclusive language
- Be respectful of differing viewpoints and experiences
- Gracefully accept constructive criticism
- Focus on what is best for the community
- Show empathy towards other community members

## How Can I Contribute?

### Reporting Bugs

Before creating bug reports, please check existing issues to avoid duplicates. When you create a bug report, include as many details as possible:

- **Use a clear and descriptive title**
- **Describe the exact steps to reproduce the problem**
- **Provide specific examples** (code snippets, screenshots)
- **Describe the behavior you observed** and what you expected
- **Include details about your environment** (Python version, OS, library versions)

### Suggesting Enhancements

Enhancement suggestions are tracked as GitHub issues. When creating an enhancement suggestion:

- **Use a clear and descriptive title**
- **Provide a detailed description** of the suggested enhancement
- **Explain why this enhancement would be useful**
- **List some examples** of how it would be used

### Pull Requests

- Fill in the required template
- Follow the [style guide](#style-guide)
- Include appropriate test cases if applicable
- Update documentation as needed
- End all files with a newline

## Development Setup

1. **Fork the repository**
   ```bash
   # Click the 'Fork' button on GitHub
   ```

2. **Clone your fork**
   ```bash
   git clone https://github.com/YOUR_USERNAME/Stock-Price-Prediction-Project-using-LSTM-and-RNN.git
   cd Stock-Price-Prediction-Project-using-LSTM-and-RNN
   ```

3. **Create a virtual environment**
   ```bash
   python -m venv venv
   source venv/bin/activate  # On Windows: venv\Scripts\activate
   ```

4. **Install dependencies**
   ```bash
   pip install -r requirements.txt
   ```

5. **Create a branch**
   ```bash
   git checkout -b feature/your-feature-name
   ```

6. **Make your changes**
   - Follow the style guide
   - Write clear commit messages
   - Test your changes

7. **Push to your fork**
   ```bash
   git push origin feature/your-feature-name
   ```

8. **Create a Pull Request**
   - Go to the original repository
   - Click "New Pull Request"
   - Select your branch
   - Fill in the PR template

## Contribution Guidelines

### Types of Contributions

We welcome contributions in the following areas:

1. **Code Improvements**
   - Bug fixes
   - Performance optimizations
   - New model architectures
   - Additional technical indicators

2. **Documentation**
   - Improving existing documentation
   - Adding examples
   - Fixing typos
   - Translating documentation

3. **Testing**
   - Adding test cases
   - Improving test coverage
   - Fixing test failures

4. **Features**
   - New visualization techniques
   - Additional evaluation metrics
   - Data preprocessing improvements
   - Model interpretability features

### What We're Looking For

- **Clean, readable code** following Python best practices
- **Well-documented code** with clear comments and docstrings
- **Comprehensive testing** for new features
- **Updated documentation** reflecting changes
- **Performance considerations** for computational efficiency

### What to Avoid

- Large, monolithic pull requests (break them into smaller ones)
- Changes that break backward compatibility without discussion
- Undocumented code changes
- Code that doesn't follow the existing style
- Features that drastically change the project scope without prior discussion

## Style Guide

### Python Style

Follow [PEP 8](https://www.python.org/dev/peps/pep-0008/) guidelines:

```python
# Good
def calculate_rsi(prices, period=14):
    """
    Calculate Relative Strength Index.
    
    Parameters:
    -----------
    prices : array-like
        Price data
    period : int, default=14
        RSI period
    
    Returns:
    --------
    rsi : array
        RSI values
    """
    # Implementation
    pass

# Avoid
def calc_rsi(p,per=14):
    # No docstring, unclear variable names
    pass
```

### Jupyter Notebook Style

- Use markdown cells liberally for documentation
- Keep code cells focused and not too long
- Clear all outputs before committing (unless they're essential)
- Use meaningful cell headings
- Add comments explaining complex operations

### Documentation Style

- Use clear, concise language
- Include code examples where appropriate
- Use proper markdown formatting
- Check spelling and grammar
- Update table of contents if adding sections

## Commit Messages

Write clear, descriptive commit messages:

### Format

```
type: Short description (50 chars or less)

Longer description if necessary. Explain what changed and why.
Include any relevant issue numbers.

Fixes #123
```

### Types

- `feat`: New feature
- `fix`: Bug fix
- `docs`: Documentation changes
- `style`: Code style changes (formatting, etc.)
- `refactor`: Code refactoring
- `test`: Adding or updating tests
- `chore`: Maintenance tasks

### Examples

```
feat: Add attention mechanism to LSTM model

Implemented multi-head attention layer to improve long-range 
dependencies in price prediction. Includes visualization of 
attention weights.

Relates to #45
```

```
fix: Correct RSI calculation for edge cases

Fixed division by zero error when price changes are constant.
Added handling for NaN values in the first period rows.

Fixes #67
```

```
docs: Update README with installation instructions

Added detailed setup steps for Windows users and clarified
Kaggle API configuration process.
```

## Testing

If you're adding new features, please include appropriate tests:

```python
# Example test structure
def test_calculate_rsi():
    """Test RSI calculation with known values."""
    prices = np.array([44, 44.5, 45, 45.5, 45, 44.5])
    rsi = calculate_rsi(prices, period=14)
    # Assert expected behavior
    assert rsi is not None
```

## Questions?

Feel free to:
- Open an issue for questions
- Start a discussion in the Discussions tab
- Reach out through the contact information in the README

## Recognition

Contributors will be recognized in the project README. Thank you for helping make this project better!

---

**Happy Contributing!**
