# Twitter/X Inspection Tools

[![GitHub](https://img.shields.io/badge/GitHub-TAbdiukov/PyTwitterTools-black?logo=github)](https://github.com/TAbdiukov/PyTwitterTools)
![License](https://img.shields.io/github/license/TAbdiukov/PyTwitterTools)

[![buymeacoffee](https://www.buymeacoffee.com/assets/img/custom_images/orange_img.png)](https://www.buymeacoffee.com/tabdiukov)

Inspect the raw Twitter/X user payload for a username without an official API key.

The script reads browser session cookies from `AUTH.yaml`, calls `twitter-api-client`'s `Scraper`, and prints the user result as YAML.

## Requirements

- Python 3.8+
- Dependencies from `requirements.txt`

```bash
pip install -r requirements.txt
```

## Authentication

Create `AUTH.yaml` in the project directory:

```yaml
auth_token: "PASTE_YOUR_AUTH_TOKEN_HERE"
ct0: "PASTE_YOUR_CT0_TOKEN_HERE"
```

Get both values from a logged-in browser session:

1. Open `twitter.com` or `x.com`.
2. Open Developer Tools.
3. Go to Application/Storage → Cookies.
4. Copy the `auth_token` and `ct0` cookie values.

If `AUTH.yaml` is missing, the script creates a template on first run. Edit it, then run the command again.

Treat these cookies like passwords. Do not commit `AUTH.yaml`.

## Usage

```bash
python twitter_info.py <username>
python twitter_info.py jack
python twitter_info.py jack > jack.yaml
```

Example output:

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

## Notes

Use only accounts and data you are allowed to access. Respect Twitter/X's Terms of Service, applicable law, and rate limits.

Tim Abdiukov
