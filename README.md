## UPDATE: 29-02-2024
As I have had my tesla delivered for a while now, I am not maintaining this code anymore. Feel free to pull request any fixes.

# TeslaOrderChecker

TeslaOrderChecker is a simple tool designed to periodically check for changes in Tesla vehicle orders. It utilizes the Tesla API to monitor your order status.

![Terminal Screenshot](docs/image-2.png)
![Telegram Screenshot](docs/image-1.png)

## Features
- **Automatic Checking**: Calls the Tesla API every 10 minutes to detect any updates in the order.
- **Local storage of last data**: To notify you of changes while the script was not running.
- **Notifications**: Optional support for Apprise notifications.

## Prerequisites
- **Tesla Account Refresh Token**: Obtain your token using [Tesla Auth](https://github.com/adriankumpf/tesla_auth).
- **Reservation Number**: Your Tesla reservation number, starting with RN.

## Setup
1. Clone the repository. (`git clone https://github.com/WesSec/teslaorderchecker && cd teslaorderchecker`)
2. Install required dependencies (`pip install -r requirements.txt`).
3. Fill `config.sample.json` with your variables, or copy it to `config.json` and edit that file instead.
4. If you want notifications, set `notifications_enabled` to `true` and put your [Apprise](https://github.com/caronc/apprise) URL in `apprisestr`.

## Usage
Run the script with `python main.py` and wait :) 

## Docker
1. Build the image: `docker build -t teslaorderchecker .`
2. Fill `config.sample.json` with your variables.
3. Run the container from the repository directory:

   `docker run --rm -it -v "$(pwd)/config.sample.json:/app/config.sample.json:ro" teslaorderchecker`

If you prefer, you can mount a populated `config.json` to `/app/config.json` instead.
On Windows, use `%cd%` in Command Prompt or `${PWD}` in PowerShell instead of `$(pwd)`.
To persist the last fetched order data across container restarts, also mount `/app/lastdata.txt`.

## Disclaimer
- Not affiliated with Tesla, Inc.
- Use at your own risk.

*This tool is for informational purposes only.*

[!["Buy Me A Coffee"](https://www.buymeacoffee.com/assets/img/custom_images/orange_img.png)](https://www.buymeacoffee.com/wessec)
