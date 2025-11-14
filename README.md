# Twitter/X Inspection Tools (Python)

Inspect the full data structure that Twitter/X returns for a given user—no official API key required. This tiny CLI tool reads your web-session cookies (`auth_token` and `ct0`) from a local `AUTH.yaml`, uses `twitter-api-client`’s `Scraper`, and prints the user record as nicely formatted YAML.

> ✅ Great for reverse‑engineering fields, exploring what a user object looks like, or debugging third‑party clients.

---

## Features

* 🔐 Simple cookie‑based auth (no OAuth)
* 🧾 Auto‑creates an `AUTH.yaml` template on first run
* 🧰 Dumps complete payload in readable YAML
* 🧵 Works well with shell redirection (save to file, pipe to `grep`, etc.)

---

## Requirements

* **Python**: 3.8+ recommended
* **OS**: macOS, Linux, or Windows
* **Dependencies** (installed via `requirements.txt`):

  * `twitter-api-client>=0.10.22`
  * `PyYAML>=6.0.1`

---

## Installation

```bash
pip install -r requirements.txt
```

---

## Authentication (one‑time setup)

This script uses your **browser session cookies**. You need two values: `auth_token` and `ct0`.

1. Log in to **twitter.com** or **x.com** in your desktop browser.
2. Open **Developer Tools** → **Application/Storage** → **Cookies**.
3. Find the cookie names:

   * `auth_token`
   * `ct0`
4. Copy their values (long strings) and paste them into `AUTH.yaml` like so:

```yaml
auth_token: "PASTE_YOUR_AUTH_TOKEN_HERE"
ct0: "PASTE_YOUR_CT0_TOKEN_HERE"
```

> 💡 First run convenience: if `AUTH.yaml` is missing, the script creates a template with placeholders. Just edit and rerun.

**Security tip:** Treat these values like passwords.

---

## Usage

```bash
# Basic usage
python twitter_info.py <username>

# Examples
python twitter_info.py jack
python twitter_info.py TwitterDev

# Save output to a file
python twitter_info.py jack > jack.yaml
```

On success, you’ll see something like:

```
================================================================================
Full data structure for @jack:
================================================================================
__typename: User
id: "12"
rest_id: "12"
is_blue_verified: true
legacy:
  name: "jack"
  screen_name: "jack"
  created_at: "Tue Mar 21 20:50:14 +0000 2006"
  description: "..."
  followers_count: 6000000
  friends_count: 5000
  ...
```

---

## Ethics & Terms

* This tool uses your authenticated session cookies. **Respect Twitter/X’s Terms of Service** and applicable laws.
* Only access data you’re allowed to access, and avoid excessive or abusive scraping.
* Store credentials securely and rotate them if you suspect exposure.

---------------------------------

Tim Abdiukov
