# Final Project Checklist (Total: 50 points)

## Library (genailib_rd) (13 points)

1. [ ] Implement OpenAI API integration
2. [ ] Add support for different OpenAI models
3. [ ] Implement environment variable and .env file support for API key
4. [ ] Use Pydantic for validating API responses
5. [ ] Write comprehensive unit tests
6. [ ] Implement a useful command-line application (4 points)
7. [ ] Add type hints throughout the codebase
8. [ ] Run and pass mypy static type checking
9. [ ] Lint the code using ruff
10. [ ] Format the code using ruff
11. [ ] Write thorough documentation (docstrings, README, etc.)
12. [ ] Build and upload the package to TestPyPI

## Flask Server (AIConverse) (13 points + 15 points for UI)

13. [ ] Implement user authentication (login/registration)
14. [ ] Create user management functionality
15. [ ] Implement conversation management
16. [ ] Implement chat functionality within conversations
17. [ ] Integrate with genailib_rd for OpenAI API calls
18. [ ] Implement automatic saving of chats and conversations
19. [ ] Send last 3 exchanges to the model for context (or use API's memory feature if available)
20. [ ] Lint the code using ruff
21. [ ] Format the code using ruff
22. [ ] Write thorough documentation (docstrings, README, etc.)
23. [ ] Create a Dockerfile for containerization
24. [ ] Ensure database file and configurations are external to the Docker container
25. [ ] Follow 12-factor app principles
26. [ ] Implement responsive design (test on different screen sizes and devices)
27. [ ] Create an appealing and functional user interface (15 points)

## Deployment (Dokku)

28. [ ] Add Dokku remote to your Git repository
29. [ ] Set up GitHub Action for automatic deployment to Dokku on commit
30. [ ] Configure secrets on Dokku:
    - [ ] Use comments in Dockerfile for secret injection (refer to github.com/rahuldave/todoapprd)
    - [ ] Or use `dokku config:set` mechanism for environment variables
31. [ ] Deploy the application to Dokku
32. [ ] Verify the application is running at appname.rahuldave.us

## General Project

33. [ ] Ensure both repositories (library and server) are properly structured
34. [ ] Create comprehensive README files for both projects
35. [ ] Set up continuous integration (CI) for both projects
36. [ ] Implement proper error handling and logging
37. [ ] Conduct security review (e.g., check for exposed API keys, SQL injection vulnerabilities)
38. [ ] Perform cross-browser testing
39. [ ] Write user documentation or help guide

## Final Deliverables

40. [ ] GitHub repository for genailib_rd (library)
41. [ ] GitHub repository for AIConverse (Flask server)
42. [ ] Deployed application URL (appname.rahuldave.us)

## Point Distribution
- Library development practices: 13 points
- Flask server development practices: 13 points
- Command-line application in library: 4 points
- User interface: 15 points
- Additional features or improvements: 5 points

## Additional Features (Extra Credit) - Choose from these or propose your own (5 points)

43. [ ] Implement model selection feature in AIConverse UI
44. [ ] Add unit tests for Flask routes and functions
45. [ ] Implement end-to-end tests for AIConverse
46. [ ] Use mocks for testing external dependencies in AIConverse
47. [ ] Add type hints throughout the AIConverse codebase
48. [ ] Run and pass mypy static type checking for AIConverse
49. [ ] Implement a feature to export conversation history
50. [ ] Implement a feature to share conversations with other users
