# Hospital Management System – Playwright Automation

End-to-end UI test automation for a Hospital Management System (HMS), built with **JavaScript**, **Playwright Test**, and the **Page Object Model (POM)**. The suite automates patient-facing and doctor-facing workflows, uses reusable fixtures and generated test data, and is configured to produce Playwright HTML and Allure reports.

> **Project branch:** `UPDATED_PROJECT`  
> **Repository:** [Project1-Hospital_Doctor-Patient_Management_System-](https://github.com/nandagopalm01-byte/Project1-Hospital_Doctor-Patient_Management_System-/tree/UPDATED_PROJECT)

## Project overview

The project tests key workflows in a Hospital Management System with separate patient and doctor areas. Patient workflows include registration, login, dashboard navigation, profile updates, appointment booking and appointment history, email/password changes, and logout. Doctor workflows include login, viewing appointment history, adding and searching for patients, and accessing patient medical-history functionality.

The framework uses page-object classes to keep page locators and page actions separate from test assertions. Custom Playwright fixtures provide a logged-in patient session, while a setup test creates a doctor authentication state for tests that use the saved session.

## Technology stack

| Technology | Purpose |
|---|---|
| JavaScript | Test implementation |
| Node.js and npm | Runtime and dependency management |
| Playwright Test | Browser automation, assertions, fixtures and test runner |
| Chromium | Configured browser project |
| Page Object Model | Page-level locator and action organization |
| dotenv | Load environment-specific configuration |
| Faker | Generate dynamic patient names, addresses, cities and passwords |
| Allure Playwright | Allure test-result generation |
| Jenkins | CI pipeline for test execution and report publishing |
| GitHub Actions | Workflow configuration for automated test execution |

## Framework structure

```text
.
├── .github/
│   └── workflows/
│       └── playwright.yml
├── POM/
│   ├── 01_hms.js
│   ├── 02_home.page.js
│   ├── 03_patient_login.page.js
│   ├── 04_patient_Appointment.page.js
│   ├── 05_patient_registration.page.js
│   ├── 06_patient_details_updation.js
│   ├── 07_doctor_login.page.js
│   └── 08_doctor_patient.page.js
├── fixtures/
│   └── hms_login.fixture.js
├── test-data/
│   ├── login-data.json
│   ├── patient-data.json
│   ├── patient-medical-history.json
│   └── registration-data.json
├── test-scenarios/
│   ├── HMS_Playwright_Test_Scenarios.xlsx
│   └── test-sceanrios-01.xlsx
├── tests/
│   ├── HMS_04.3.spec.js
│   └── doctor_auth.setup.js
├── utils/
│   └── FakerData.js
├── JenkinsFile
├── package.json
├── package-lock.json
├── playwright.config.js
└── .gitignore
```

Generated folders such as `.auth/`, `allure-results/`, `allure-report/`, `test-results/` and `playwright-report/` may appear locally after test execution. They are generated state or report output, not source folders that need to be committed.

## Automated test coverage

The main specification file is `tests/HMS_04.3.spec.js`. It contains the following 15 test cases:

| Test ID | Scenario | Area |
|---|---|---|
| HMS_TC_01 | Register a new patient successfully | Patient registration |
| HMS_TC_02 | Register a patient and log in with the new credentials | Registration and login |
| HMS_TC_03 | Log in as a patient and verify the dashboard | Patient login |
| HMS_TC_04 | Open Edit Profile and verify the page heading | Patient profile |
| HMS_TC_05 | Book an appointment successfully | Appointment booking |
| HMS_TC_06 | Verify a booked appointment in appointment history | Appointment history |
| HMS_TC_07 | Update patient profile details | Profile management |
| HMS_TC_08 | Update patient email address | Account management |
| HMS_TC_09 | Update patient password | Account management |
| HMS_TC_10 | Log out and verify protected-page access | Session management |
| HMS_TC_11 | Log in as a doctor and verify the dashboard | Doctor login |
| HMS_TC_12 | Verify a patient's appointment in the doctor's appointment history | Patient–doctor workflow |
| HMS_TC_13 | Add a patient and verify the patient in Manage Patients | Doctor patient management |
| HMS_TC_14 | Add medical history for a patient | Patient medical records |
| HMS_TC_15 | Search for a patient and verify the search result | Patient search |

The test suite also uses reusable helper functions for patient and doctor login navigation, patient registration, and JavaScript dialog acceptance. The patient fixture logs in with configured patient credentials, and the doctor setup saves browser storage state for authenticated doctor tests.

**Coverage note:** These are the scenarios represented by the current test file, not a claim that every scenario has been independently validated or that the full suite currently passes. Review each test's assertions and the target application's current availability before using a run result as a quality metric.

## Framework capabilities

### Page Object Model

The `POM/` directory contains page classes for the application home page, patient login, appointment booking, registration, patient profile management, doctor login and doctor patient management. Each page class groups relevant locators and user actions.

### Custom fixture

`fixtures/hms_login.fixture.js` defines a `loggedInPatient` fixture. It creates a browser context, navigates through the application to the patient login page, logs in using environment credentials, provides the page to the test, and closes the context during teardown.

### Doctor authentication setup

`tests/doctor_auth.setup.js` signs in as a doctor and saves the browser storage state to `.auth/user.json`. The authenticated doctor tests use that state through Playwright's `storageState` option. Authentication state is session-specific and should be generated locally or in CI; never commit a real session cookie or storage-state file.

### Dynamic test data

`utils/FakerData.js` wraps Faker methods for generating names, addresses, cities and passwords. The tests also generate unique patient email addresses to reduce duplicate-registration conflicts. JSON files in `test-data/` hold supporting patient and medical-history data.

### Dialog handling

The main test file contains a reusable helper that waits for a JavaScript dialog, captures its message, accepts it, and runs the triggering action. This is used for flows such as registration and adding medical history.

## Prerequisites

Install the following before running the tests:

- Node.js version compatible with the dependencies in `package-lock.json`
- npm
- Git
- Access to a running and reachable HMS application and valid patient/doctor test accounts

Install the project dependencies and Playwright browser binaries:

```bash
npm ci
npx playwright install
```

On Linux CI runners, install the required operating-system browser dependencies with:

```bash
npx playwright install --with-deps
```

## Environment configuration

Create a local `.env` file in the project root. Do not commit this file. Add the application URL and the test-account credentials expected by the project:

```env
BASE_URL=http://<your-hms-host-and-base-path>/

PATIENT_1_EMAIL=<patient-login-email>
PATIENT_1_PASSWORD=<patient-login-password>

UPD_PATIENT_EMAIL=<patient-email-for-update-tests>
UPD_PATIENT_PASSWORD=<patient-password-for-update-tests>

DOCTOR_1_EMAIL=<doctor-login-email>
DOCTOR_1_PWD=<doctor-login-password>

DOCTOR_2_EMAIL=<second-doctor-login-email>
DOCTOR_2_PWD=<second-doctor-login-password>
```

Use valid accounts from your own test environment. The exact variables above are read by the fixture, test specification, and doctor authentication setup. Confirm that the configured `BASE_URL` is the application entry point expected by the project before running tests.

> **Security:** Do not commit `.env`, real credentials, session cookies, or `.auth/user.json`. Use Jenkins credentials or GitHub Actions secrets for CI. Use fictional/sample data in committed JSON files.

## Running the tests

Run the complete Playwright suite:

```bash
npx playwright test
```

Run the main HMS specification:

```bash
npx playwright test tests/HMS_04.3.spec.js
```

Run the main specification in headed mode:

```bash
npx playwright test tests/HMS_04.3.spec.js --headed
```

Run a test by its title:

```bash
npx playwright test -g "HMS_TC_03"
```

Run the doctor authentication setup project explicitly when regenerating doctor storage state:

```bash
npx playwright test --project=setup
```

The configured Chromium project currently depends on the `setup` project, so the doctor authentication setup is part of the normal project dependency graph. Tests in the doctor-authenticated describe block expect the storage-state file to exist. Do not manually create or publish a real authentication state file.

## Reports

The Playwright configuration includes the list reporter, HTML reporter and Allure Playwright reporter. Screenshots, videos and traces are configured to be retained on failure.

After a run, open the Playwright HTML report with:

```bash
npx playwright show-report
```

Generate an Allure HTML report from the collected Allure results with:

```bash
npx allure generate allure-results --clean -o allure-report
npx allure open allure-report
```

The Allure CLI must be available in your environment for the report-generation commands. The project includes the `allure-playwright` adapter; the CLI is a separate reporting tool.

Do not commit generated test results or report folders. Share reports as CI artifacts when needed, after ensuring they do not expose credentials or sensitive test data.

## CI integration

### Jenkins

The root `JenkinsFile` defines a Windows-oriented pipeline using `bat` commands. It installs npm dependencies and Playwright browsers, loads application credentials through Jenkins `withCredentials`, runs `tests/HMS_04.3.spec.js`, and publishes the Playwright HTML and Allure reports.

Configure the Jenkins credential IDs referenced in the Jenkinsfile and ensure the required Jenkins plugins are installed and configured for HTML and Allure report publishing. The pipeline currently continues to the post-build report stage after test failures; review the pipeline's final build status handling before treating a successful Jenkins build as proof that all tests passed.

### GitHub Actions

The repository includes `.github/workflows/playwright.yml`. It checks out the code, sets up Node.js, runs `npm ci`, installs Playwright browsers with system dependencies, runs Playwright tests, and uploads the Playwright HTML report as an artifact.

The workflow's current branch filters target `main` and `master`. The project is being maintained on `UPDATED_PROJECT`; add that branch to the workflow trigger if CI should run for pushes and pull requests on this branch. Configure all required environment variables as GitHub Actions secrets and pass them into the test step. The workflow does not currently define those secrets in its job environment, so it is not ready to execute the credential-dependent suite unchanged.

## Important maintenance notes

- The project has a configured Chromium project; Firefox and WebKit are present only as commented configuration examples.
- The suite uses a fixed appointment date in some test cases. Update appointment dates to valid future dates in the target environment before execution.
- Keep test data isolated and use synthetic patient details. Avoid committing personally identifying or real patient data.
- Verify that each test asserts the business outcome, not only a success dialog or page navigation.
- Keep authentication storage and generated reports out of Git.
- Keep CI branch triggers and required credentials aligned with the branch and tests being executed.

## Repository branch

This README is intended for the `UPDATED_PROJECT` branch:

[View source on GitHub](https://github.com/nandagopalm01-byte/Project1-Hospital_Doctor-Patient_Management_System-/tree/UPDATED_PROJECT)

---

**Note:** This repository documents a learning/portfolio automation project. Test execution depends on access to the HMS application and valid environment-specific credentials. No live test execution or passing-build guarantee is implied by this README.
