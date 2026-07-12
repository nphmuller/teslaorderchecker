# TeslaOrderChecker

TeslaOrderChecker is a simple tool designed to periodically check for changes in Tesla vehicle orders. It utilizes the Tesla API to monitor your order status.

![Terminal Screenshot](docs/image-2.png)
![Telegram Screenshot](docs/image-1.png)

## Features
- **Automatic Checking**: Calls the Tesla API at a configurable interval to detect any updates in the order.
- **Local storage of last data**: To notify you of changes while the script was not running.
- **Notifications**: Optional support for Apprise notifications.

## Differences from the original

- **Docker support** — Multi-stage Dockerfile for containerized deployment.
- **GitHub Container Registry publish workflow** — Automated Docker image builds and pushes to GHCR.
- **Updated Tesla API version** — App version bumped to 4.58.0-4392.
- **Configurable polling interval** — Set `interval_seconds` in `config.json` (defaults to 600s).
- **Test notification** — Optionally send a test notification on startup via `test_notification`.
- **API failure notifications** — Sends a notification once when the API fails, with status code and error details, and resets on success.

## Prerequisites
- **Tesla Account Refresh Token**: Obtain your token using [Tesla Auth](https://github.com/adriankumpf/tesla_auth).
- **Reservation Number**: Your Tesla reservation number, starting with RN.

## Setup
1. Clone the repository.
2. Install required dependencies (`pip install -r requirements.txt`).
3. `cp config.json.sample config.json` and fill the JSON file with your variables.

## Usage
Run the script with `python main.py` and wait :)

## Docker
1. Build the image: `docker build -t teslaorderchecker .`
2. Copy `config.sample.json` to `config.json` and fill `config.json` with your variables.
3. Run the container from the repository directory:

   `docker run --rm -it -v "$(pwd)/config.json:/app/config.json:ro" teslaorderchecker`

## Disclaimer
- Not affiliated with Tesla, Inc.
- Use at your own risk.

*This tool is for informational purposes only.*

[!["Buy Me A Coffee"](https://www.buymeacoffee.com/assets/img/custom_images/orange_img.png)](https://www.buymeacoffee.com/wessec)
