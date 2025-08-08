# AI-Powered-Test-Automation-Framework
A scalable, AI-powered test automation framework combining Python, Behave BDD, and Playwright — enhanced with Generative AI tools like ChatGPT and OpenAI API to create, refine, and optimize test scenarios. Includes UI &amp; API test automation, CI/CD integration with Jenkins, Allure reporting, and secure QA practices.


Sure! Here’s a technical yet clear README.md draft for your **AI Powered Test Automation Framework** repo based on all the info you provided:

---

# AI Powered Test Automation Framework

## Overview

This repository contains an AI-powered Behavior-Driven Development (BDD) test automation framework built with **Python**, **Behave**, and **Playwright**. The framework leverages OpenAI’s language models to **automatically generate Gherkin scenarios** and test code, enabling faster and smarter test creation. It supports both **UI automation** and **API testing**, with integrated reporting via **Allure**.

---

## Key Features

* **AI-generated Gherkin scenarios** using OpenAI prompts for faster test specification.
* **Modular folder structure**:

  * `config` for environment and API keys.
  * `features` containing Gherkin `.feature` files.
  * `steps` for step definitions implementing BDD steps.
  * `utils` for OpenAI integration and helper utilities.
* **Playwright-based UI automation** with easy configuration of browser and headless mode.
* **API testing support** using Python requests integrated with BDD steps.
* **Environment management** using `environment.py` to setup and teardown Playwright instances.
* **Comprehensive logging** and screenshot capture on failures.
* **Allure integration** for detailed, user-friendly test reports.
* **Custom test runner** supporting tag-based test execution and automated report directory cleanup.

---

## Getting Started

### Prerequisites

* Python 3.8+
* Playwright (`pip install playwright` and `playwright install`)
* Behave (`pip install behave`)
* Requests (`pip install requests`)
* Allure commandline tool (optional for report generation)
* OpenAI API key (stored in `config/openai_key.json`)

---

### Installation

1. Clone the repo:

```bash
git clone https://github.com/yourusername/AI-Powered-Test-Automation-Framework.git
cd AI-Powered-Test-Automation-Framework
```

2. Create and activate a virtual environment:

```bash
python -m venv .venv
source .venv/bin/activate  # Linux/macOS
.venv\Scripts\activate     # Windows
```

3. Install dependencies:

```bash
pip install -r requirements.txt
playwright install
```

4. Add your OpenAI API key in `config/openai_key.json`:

```json
{
  "api_key": "your_api_key_here"
}
```

5. Configure `config/env.json` to adjust base URL, browser type, and headless mode:

```json
{
  "base_url": "https://webdriveruniversity.com/",
  "browser": "chromium",
  "headless": false
}
```

---

## Usage

### Generate Gherkin Scenarios with AI

Run the `run_test.py` script to generate Gherkin `.feature` files automatically:

```bash
python run_test.py
```

### Run Tests

Use the custom runner to execute tests with specific tags (e.g., `@regression`):

```bash
python custom_runner.py --tags @regression
```

This will:

* Clean and recreate the `reports` and `screenshots` folders.
* Run Behave tests filtered by the given tags.
* Generate Allure-compatible result files in `reports/allure-results`.

---

### Generate Allure Reports

After running tests, generate and open Allure reports with:

```bash
allure generate reports/allure-results -o reports/allure-report --clean
allure open reports/allure-report
```

---

## Framework Structure

```
AI-Powered-Test-Automation-Framework/
├── config/
│   ├── env.json               # Environment configs (base URL, browser, etc.)
│   ├── openai_key.json        # OpenAI API key
│   ├── prompt.py              # JSON-like dictionary of AI prompts
│   └── __init__.py            # Package marker
├── features/
│   ├── contact_us_form.feature
│   └── goal_tracker_api.feature
├── features/steps/
│   ├── contact_us_form_steps.py
│   └── goal_tracker_api_steps.py
├── reports/                   # Allure reports output (auto-generated)
├── screenshots/               # Screenshots on test failures
├── utils/
│   ├── api_test_generator.py # AI-driven API test generation utility
│   ├── analyze_steps.py      # AI-assisted step implementation analyzer
│   ├── openai_utils.py       # OpenAI API client and helpers
│   └── types.py              # Custom context typing for Playwright & Behave
├── environment.py             # Behave environment setup and teardown
├── custom_runner.py           # Test runner with tag filtering & report cleanup
├── run_test.py                # AI-generated feature file creation
├── requirements.txt
└── README.md
```

---

## How It Works

* The **environment.py** initializes Playwright and handles browser setup/teardown.
* Step definitions under **features/steps/** implement BDD steps using Playwright and requests.
* **run\_test.py** generates Gherkin feature files based on AI prompts stored in `config/prompt.py`.
* **custom\_runner.py** orchestrates test execution with tag filters and prepares Allure reports.
* Failures trigger screenshots and logs, attached automatically to Allure reports.
* API tests are supported via dedicated step definitions that make HTTP calls and validate responses.

---

## Contributing

Feel free to open issues or submit pull requests to improve the framework. Contributions are welcome for:

* Adding new AI prompts.
* Expanding step implementations.
* Integrating additional browsers or test runners.
* Enhancing reporting and logging.

---

## License

This project is licensed under the MIT License.

---

If you want me to help with adding badges, setup instructions for CI/CD, or any other section, just say!
