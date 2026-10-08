# Swag Labs Automation with Cypress

End-to-end test automation for the [Swag Labs](https://www.saucedemo.com/) web application using **Cypress and JavaScript**.

The project focuses on automating core authentication and navigation workflows while maintaining reusable test data, centralized selectors, Cypress support configuration, and a clean E2E test structure.

## Tech Stack

| Technology | Purpose |
|---|---|
| Cypress | End-to-end test automation |
| JavaScript | Test implementation |
| Node.js | Runtime and package management |
| npm | Dependency management |

## Project Structure

```text
swaglabs-automation-cypress/
│
├── cypress/
│   ├── e2e/
│   │   └── test.cy.js
│   │
│   ├── fixtures/
│   │   └── example.json
│   │
│   └── support/
│       ├── commands.js
│       ├── data.js
│       └── e2e.js
│
├── cypress.config.js
├── package.json
├── package-lock.json
└── README.md
```

## Framework Structure

### E2E Tests

The `cypress/e2e` directory contains the automated test specifications.

The current suite covers:

- Login using supported Swag Labs users
- Navigation to the inventory page after authentication
- Opening the application menu
- Logout validation
- Verification of the application URL after logout

### Test Data and Selectors

The `cypress/support/data.js` file centralizes:

- Valid user credentials
- Invalid test credentials
- Application URLs
- Login page selectors
- Navigation menu selectors
- Shopping cart selectors
- Checkout selectors
- Product removal selectors
- Expected validation messages

Keeping selectors and test data outside the test specification makes the test code easier to maintain when the application changes.

### Cypress Support

The `cypress/support` directory contains shared Cypress configuration and reusable support files.

`commands.js` provides the standard location for custom Cypress commands that can be introduced as the suite grows.

`e2e.js` contains the global E2E support configuration.

## Automated Scenarios

### Authentication

The current automation validates login using the supported Swag Labs user accounts:

- `standard_user`
- `locked_out_user`
- `problem_user`
- `performance_glitch_user`
- `error_user`
- `visual_user`

The test iterates through the configured users, performs authentication, validates successful navigation to the inventory page, and then verifies logout.

### Navigation

The test suite also validates:

- Opening the application menu
- Logging out
- Returning to the login page after logout

The repository also contains centralized selectors and test data for additional application areas, including:

- Application menu
- Shopping cart
- Checkout
- Product removal
- Filtering

These provide the foundation for extending the E2E coverage.

## Cypress Configuration

The Cypress configuration is defined in `cypress.config.js`.

Current configuration includes:

- Base URL: `https://www.saucedemo.com/`
- Viewport: `1920 × 1080`
- E2E test configuration

Using a configured `baseUrl` allows tests to use relative navigation such as:

```javascript
cy.visit('/')
```

instead of hard-coding the application URL in every test.

## Prerequisites

Make sure the following are installed:

- Node.js
- npm

Check the installed versions:

```bash
node --version
npm --version
```

## Installation

Clone the repository:

```bash
git clone https://github.com/hasanazeerkhan/swaglabs-automation-cypress.git
```

Navigate to the project:

```bash
cd swaglabs-automation-cypress
```

Install dependencies:

```bash
npm install
```

## Running Tests

### Cypress Interactive Mode

Open the Cypress Test Runner:

```bash
npx cypress open
```

Select **E2E Testing**, choose a browser, and execute the available test specification.

### Headless Execution

Run the E2E suite from the command line:

```bash
npx cypress run
```

### Run a Specific Test File

```bash
npx cypress run --spec "cypress/e2e/test.cy.js"
```

## Test Design Approach

The project follows a simple separation of responsibilities:

```text
Test Specification
        │
        ▼
   Cypress Commands
        │
        ▼
Test Data & Selectors
        │
        ▼
   Swag Labs Application
```

The test specification focuses on the user workflow, while selectors, URLs, credentials, and other reusable values are maintained separately.

## Key Automation Practices

- End-to-end browser automation using Cypress
- Centralized selectors
- Centralized test data
- Data-driven login validation
- Reusable Cypress support structure
- Configurable application base URL
- Assertions for navigation and authentication state
- Headless and interactive test execution

## Application Under Test

**Swag Labs**

https://www.saucedemo.com/

## Future Improvements

Potential extensions to the current suite include:

- Product filtering validation
- Shopping cart workflows
- Checkout flow validation
- Negative login scenarios
- Custom Cypress commands for authentication
- Screenshot and video artifacts for failures
- CI execution using GitHub Actions
- Improved test reporting
- Expanded fixture-based test data

## Author

**Hasan**

GitHub:  
https://github.com/hasanazeerkhan
