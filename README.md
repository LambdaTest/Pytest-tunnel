# Run Local Tests in Pytest with TestMu AI (Formerly LambdaTest) Tunnel 

<p align="center">
  <a href="https://www.testmuai.com/"><img src="https://img.shields.io/badge/MADE%20BY%20TestMu%20AI-000000.svg?style=for-the-badge&labelColor=000" alt="Made by TestMu AI"></a>
  <a href="https://pypi.org/project/pytest/"><img src="https://img.shields.io/pypi/v/pytest.svg?style=for-the-badge&labelColor=000000" alt="pytest version"></a>
  <a href="https://community.testmuai.com/"><img src="https://img.shields.io/badge/Join%20the%20community-blueviolet.svg?style=for-the-badge&labelColor=000000" alt="Community"></a>
</p>

## Getting Started

[TestMu AI](https://www.testmuai.com/) (Formerly LambdaTest) is the world's first full-stack AI Agentic Quality Engineering platform that empowers teams to test intelligently, smarter, and ship faster. Built for scale, it offers a full-stack testing cloud with 10K+ real devices and 3,000+ browsers. With AI-native test management, MCP servers, and agent-based automation, TestMu AI supports Selenium, Appium, Playwright, and all major frameworks.

With TestMu AI (Formerly LambdaTest), you can run automation tests against locally hosted or privately hosted applications using the TestMu AI Tunnel. This sample shows how to configure tunnel in Pytest on the TestMu AI cloud.

- [Sign up on TestMu AI](https://www.testmuai.com/register/) (Formerly LambdaTest).
- Follow the [TestMu AI documentation](https://www.testmuai.com/support/docs/) (Formerly LambdaTest) for the full setup walkthrough.

### Prerequisites

- Python 3.x and pip
- pytest: `pip install pytest`
- A TestMu AI (Formerly LambdaTest) account with your username and access key

### Setup

Clone the sample repository and install dependencies:

```bash
git clone https://github.com/LambdaTest/pytest-selenium-sample.git
cd pytest-selenium-sample
pip install -r requirements.txt
```

Set your credentials as environment variables.

**macOS / Linux:**

```bash
export LT_USERNAME="YOUR_USERNAME"
export LT_ACCESS_KEY="YOUR_ACCESS_KEY"
```

**Windows:**

```bash
set LT_USERNAME="YOUR_USERNAME"
set LT_ACCESS_KEY="YOUR_ACCESS_KEY"
```

### Local testing with TestMu AI Tunnel

If you want to run your automation test in Pytest on TestMu AI (Formerly LambdaTest) using the tunnel and want to start the tunnel automatically in the script, you can use the following steps. You can refer to sample test repo [here](https://github.com/LambdaTest/pytest-selenium-sample).

#### Step 1: Download the LT tunnel binary from the TestMu AI (Formerly LambdaTest) Dashboard

Go to your TestMu AI (Formerly LambdaTest) dashboard and click the configure tunnel button on the top right corner and use the download link to download the binary file.

#### Step 2: Code to run LT tunnel before test

In your `conftest.py` file, ensure that you have specified the username and accesskey and paste the following code (refer to `conftest.py` for full code):

```python
import subprocess

# start tunnel process
tunnel_process = subprocess.Popen(["./LT","--user",username,"--key",access_key],stdout=subprocess.DEVNULL,stderr=subprocess.STDOUT)

# leave rest of the configuration untouched

# In the fin function, end the process
def fin():
        if request.node.rep_call.failed:
            browser.execute_script("lambda-status=failed")
        else:
            browser.execute_script("lambda-status=passed")
            browser.quit()
        # end tunnel process
        tunnel_process.terminate()
```

#### Step 3: Set tunnel capability to True

Add the following line in `conftest.py`:

```python
desired_caps['tunnel'] = True
```

### Run tests

```bash
cd tests
python sample_todo.py
```

View results on your TestMu AI dashboard.

## Contributions

Contributions are welcome. Open an issue to discuss your idea before submitting a pull request. When reporting bugs, include your Python version, OS, and pytest version.

## TestMu AI (Formerly LambdaTest) Community

Connect with testers and developers in the [TestMu AI Community](https://community.testmuai.com/). Ask questions, share what you are building, and discuss best practices in test automation and DevOps.

## TestMu AI (Formerly LambdaTest) Certifications

Earn free [TestMu AI Certifications](https://www.testmuai.com/certifications/) for testers, developers, and QA engineers. Validate your skills in Selenium, Cypress, Playwright, Appium, Espresso and more. Industry-recognized, shareable on LinkedIn, and built by practitioners, not marketers.

## Learning Resources by TestMu AI (Formerly LambdaTest)

Learn modern testing through tutorials, guides, videos, and weekly updates:

* [TestMu AI Blog](https://www.testmuai.com/blog/)
* [TestMu AI Learning Hub](https://www.testmuai.com/learning-hub/)
* [TestMu AI on YouTube](https://www.youtube.com/@TestMuAI)
* [TestMu AI Newsletter](https://www.testmuai.com/newsletter/)

## LambdaTest is Now TestMu AI

On **January 12, 2026**, [LambdaTest evolved to TestMu AI](https://www.testmuai.com/lambdatest-is-now-testmuai/), the world's first fully autonomous **Agentic AI Quality Engineering Platform**.

Same team. Same infrastructure. Same customer accounts. All existing LambdaTest logins, scripts, capabilities, and integrations continue to work without change.

👉 Find the new home for [LambdaTest](https://www.testmuai.com).

### How LambdaTest Evolved into TestMu AI

In 2017, we launched LambdaTest with a simple mission: make testing fast, reliable, and accessible. As LambdaTest grew, we expanded into Test Intelligence, Visual Regression Testing, Accessibility Testing, API Testing, and Performance Testing, covering the full depth of the testing lifecycle.

As software development entered the AI era, testing had to evolve, too. We rebuilt the architecture to be AI-native from the ground up, with autonomous agents that **plan, author, execute, analyze, and optimize tests** while keeping humans in the loop. The platform integrates with your repos, CI, IDEs, and terminals, continuously learning from every code change and development signal.

That evolution earned a new name: **TestMu AI**, built for an AI-first future of quality engineering. TestMu is not a new name for us. It is the name of our annual community conference, which has brought together 100,000+ quality engineers to discuss how AI would reshape testing, long before that became an industry norm.

What started as a high-performance cloud testing platform has transformed into an AI-native, multi-agent system powering a connected, end-to-end quality layer. That evolution defined a new identity: LambdaTest evolved into TestMu AI, built for an AI-first future of quality engineering.

## Support

Got a question? Email [support@testmuai.com](mailto:support@testmuai.com) or chat with us 24x7 from our chat portal.
