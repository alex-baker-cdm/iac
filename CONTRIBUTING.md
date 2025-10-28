# Contributing to IAC Examples

Thank you for your interest in contributing to the Infrastructure as Code Examples repository! This document provides guidelines and instructions for contributing.

## Code of Conduct

We are committed to providing a welcoming and inclusive environment for all contributors. Please:

- Be respectful and professional in all interactions
- Welcome diverse perspectives and experiences
- Focus on constructive feedback
- Report any misconduct to the maintainers

## How to Contribute

### Reporting Issues

1. **Check existing issues** to avoid duplicates
2. **Provide detailed information**:
   - Clear description of the problem
   - Steps to reproduce (if applicable)
   - Expected vs actual behavior
   - Environment details (OS, tool versions)
3. **Include relevant code/templates** if applicable

### Submitting Examples

1. **Fork the repository**
2. **Create a feature branch**:
   ```bash
   git checkout -b add/new-example
   ```
3. **Add your example**:
   - Place in appropriate directory (AWS, Azure, Basic, or Examples)
   - Follow naming conventions (descriptive names)
   - Include comments explaining key sections
4. **Document your contribution**:
   - Update relevant README.md files
   - Add prerequisites if needed
   - Include deployment instructions
5. **Test thoroughly** before submitting
6. **Commit with descriptive messages**:
   ```bash
   git commit -m "feat: add [description] example"
   ```
7. **Push and create a Pull Request**

### Improving Documentation

1. Fix typos and grammatical errors
2. Clarify confusing sections
3. Add missing prerequisites or instructions
4. Improve code comments

### Pull Request Process

1. **Fork and branch** from `main`
2. **Make focused changes** - one feature or fix per PR
3. **Write clear commit messages**:
   - Use present tense ("add feature" not "added feature")
   - Reference related issues
   - Keep messages concise but descriptive
4. **Update documentation** as needed
5. **Test your changes** thoroughly
6. **Keep commits clean** - squash if necessary
7. **Submit the PR** with:
   - Clear title
   - Description of changes
   - Link to related issues (if any)
   - Instructions for testing

## Coding Standards

### Infrastructure Templates

- **AWS CloudFormation**:
  - Use YAML format for readability
  - Include descriptive comments
  - Provide parameter descriptions
  - Use consistent indentation (2 spaces)
  - Include Tags for resource management

- **Azure ARM Templates**:
  - Valid JSON structure
  - Include metadata and descriptions
  - Use meaningful variable names
  - Document all parameters
  - Include outputs for important values

- **Terraform**:
  - Follow HCL conventions
  - Use descriptive variable names
  - Include `description` for variables
  - Document outputs
  - Use consistent formatting

### JavaScript/Node.js

- Use ES6+ syntax
- Include error handling
- Add comments for complex logic
- Use meaningful variable names
- Format with 2-space indentation

### Documentation

- Use Markdown for all documentation
- Include code blocks with syntax highlighting
- Use clear headers and sections
- Provide examples and use cases
- Keep language simple and clear

## Directory Structure Conventions

When adding new examples:

- **Basic/** - Simple, introductory examples
- **Examples/** - More complex, advanced examples
- **AWS/** - AWS-specific infrastructure
- **[Other providers]/** - Create as needed

Each category should have:
- A descriptive README.md
- Well-commented templates/code
- Clear deployment instructions

## Testing Guidelines

Before submitting:

1. **Validate syntax**:
   - AWS: Use AWS CloudFormation validate
   - Azure: Use Azure CLI validation
   - Terraform: Run `terraform validate`

2. **Test deployment** in your own environment
3. **Verify documentation** accuracy
4. **Check for security issues**:
   - No hardcoded credentials
   - No sensitive data in templates
   - Follow least-privilege principle

## Review Process

1. **Initial Review**: Maintainer checks for completeness and standards compliance
2. **Feedback**: Comments and suggestions will be provided
3. **Revisions**: You may be asked to make changes
4. **Approval**: Once approved, the PR will be merged
5. **Release**: Changes will be included in next release

## Recognition

Contributors are recognized in:
- Pull Request comments
- Release notes
- Contributors section (when established)

## License

By contributing, you agree that your contributions will be licensed under the MIT License.

## Questions?

If you have questions or need clarification:

1. Check existing documentation and issues
2. Ask in a new issue with the `question` label
3. Contact the maintainer: [@nolecram](https://github.com/nolecram)

---

**Thank you for contributing!**
