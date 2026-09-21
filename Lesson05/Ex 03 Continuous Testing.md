### Continuous Testing
Create the following continuous integration jobs or pipelines in the CI tools of your choice (e.g., GitHub Actions):
- One for a repo with unit tests
  - The CI job must run the unit tests and stop if encountering an error
  - The CI job must also run a static code analysis tool (e.g., SonarQube) and stop if it finds an error
- One for a repo with API tests
  - The CI job must run the API tests (e.g., using Newman for Postman) and stop if it finds an error
