

# Cloudflare Turnstile Page & Captcha Bypass for Scraping

Scraping is an essential tool for gathering data from the web, but it’s often blocked by Cloudflare protection. Here’s a Python-based solution that integrates [CapSolver](https://www.capsolver.com/?utm_source=github&utm_medium=repo&utm_campaign=scraping&utm_term=cloudflare-bypass) for bypassing Cloudflare’s CAPTCHA challenges.



## Setup

To start using the script, clone this repository and install the dependencies:

```bash
git clone https://github.com/your_repo/cloudflare-bypass.git
cd cloudflare-bypass
pip install -r requirements.txt
```



## Quick Start Guide

### Step 1: Initiating Bypass with [CapSolver](https://www.capsolver.com/?utm_source=github&utm_medium=repo&utm_campaign=scraping&utm_term=cloudflare-bypass)

CapSolver makes bypassing Cloudflare’s CAPTCHA challenges effortless. Follow these steps:

```python
from CloudflareBypasser import CloudflareBypasser
from capsolver import CapSolver

# Initialize CapSolver
solver = CapSolver(api_key='your_api_key')

# Use a ChromiumPage as the driver to bypass Cloudflare
driver = ChromiumPage()
driver.get('https://example.com')

# Pass the driver to CloudflareBypasser and solve the CAPTCHA
cf_bypasser = CloudflareBypasser(driver, solver)
cf_bypasser.bypass()
```

---

### How It Works

The CloudflareBypasser utilizes **DrissionPage**, a browser controller that operates directly with the browser, ensuring that it's not detected as a standard WebDriver. This allows the bypass of Cloudflare’s “Checking your browser before accessing” page, a common roadblock in web scraping with tools like Selenium.

---

## Introducing Server Mode

If you're looking for a remote solution, you can bypass Cloudflare protections using **Server Mode**, which allows you to retrieve cookies or HTML content of the protected page.

### Step 1: Server Setup

Install the server-specific dependencies:

```bash
pip install -r server_requirements.txt
```

Start the server:

```bash
python server.py
```

### Step 2: API Endpoints

The server exposes two endpoints:
1. `/cookies?url=<URL>&retries=<>` - Retrieves the cookies, including Cloudflare clearance cookies.
2. `/html?url=<URL>&retries=<>` - Retrieves the full HTML content of the page.

Example:

```bash
curl http://localhost:8000/cookies?url=https://example.com
```

---

## Example Usage of CloudflareBypass

Here’s an example to test the script and see how it bypasses Cloudflare protection:

```bash
python test.py
```

---

## Docker Deployment

For ease of deployment, this script can be containerized using Docker.

First, build the Docker image:

```bash
docker build -t cloudflare-bypass .
```

Then run the container:

```bash
docker run -p 8000:8000 cloudflare-bypass
```

---

## FAQ

### What This Script Cannot Do

This solution is **not** designed to bypass IP blocks enforced by Cloudflare. If your IP is blocked, you will need a clean IP address to regain access. The script focuses solely on bypassing the CAPTCHA and page access verification checks.

### More About DrissionPage

For further details on **DrissionPage**, check out:
- [GitHub Repository](https://github.com/g1879/DrissionPage)
- [Official Documentation](https://drissionpage.cn/)


By integrating [CapSolver](https://www.capsolver.com/?utm_source=github&utm_medium=repo&utm_campaign=scraping&utm_term=cloudflare-bypass) into your scraping workflow, you can easily overcome obstacles like CAPTCHA challenges, enabling smooth and efficient data extraction from websites protected by Cloudflare. Whether you're using the regular mode or server mode, this solution provides flexibility and efficiency in bypassing web protection.

---
