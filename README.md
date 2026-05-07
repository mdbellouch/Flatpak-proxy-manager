[README.md](https://github.com/user-attachments/files/27496534/README.md)
# fproxy — Flatpak Proxy Configurator

> A simple interactive CLI tool to manage proxy settings for your Flatpak applications.

**Created by:** Md BELLOUCH  
**GitHub:** [mdbellouch](https://github.com/mdbellouch)  
**License:** MIT

---

## What is fproxy?

`fproxy` is a Python script that lets you easily set, view, and clear proxy environment variables (`http_proxy`, `https_proxy`, `ftp_proxy`, `all_proxy`) for Flatpak apps — either globally for all apps, or per individual app — all from a clean terminal menu.

---

## Requirements

- **Python 3** (any recent version)
- **Flatpak** installed and available in your `PATH`
- A Linux system with a terminal

---

## Installation

1. Download or clone the script:

```bash
git clone https://github.com/mdbellouch/fproxy.git
cd fproxy
```

2. Make it executable:

```bash
chmod +x fproxy
```

3. #Move it to your PATH so you can run it from anywhere:

```bash
sudo mv fproxy /usr/local/bin/fproxy
```

---

## Usage

Run the script:

```bash

fproxy
```

You'll be greeted by an interactive menu:

```
[1] Proxy ALL Apps (Global Override)
[2] Proxy SPECIFIC App
[3] SHOW Status (Proxied Apps)
[4] Clear ALL Proxy Settings
[9] Exit
```

---

## Menu Options

### `[1]` Proxy ALL Apps (Global Override)
Sets a proxy for **all Flatpak apps at once** using a global user override.  
You'll be prompted to enter a proxy URL. If you press Enter without typing one, it defaults to:
```
http://10.187.197.92:7071
```

### `[2]` Proxy SPECIFIC App
Lists all your installed Flatpak apps and lets you choose one to proxy individually.  
Sets `http_proxy`, `https_proxy`, `ftp_proxy`, and `all_proxy` for that app only.

### `[3]` Show Status
Displays the current proxy configuration — both the global setting and any per-app overrides that are active.

### `[4]` Clear ALL Proxy Settings
Removes all proxy environment variables, both globally and for every individual app. You'll be asked to confirm before anything is deleted.

### `[9]` Exit
Closes the tool.

---

## Changing the Default Proxy

The default proxy URL is defined at the top of the script:

```python
DEFAULT_PROXY = "http://10.187.197.92:7071"
```

Edit this line to set your own default before running the script.

---

## How It Works

`fproxy` uses the `flatpak override` command under the hood:

```bash
# Set proxy for a specific app
flatpak override --user --env=http_proxy=http://... com.example.App

# Set global proxy
flatpak override --user --env=http_proxy=http://...

# Clear proxy for a specific app
flatpak override --user --unset-env=http_proxy com.example.App
```

All overrides are applied at the **user level** (not system-wide).

---

## License

MIT License — see the top of the script for full text.

---

## Author

Made with ❤️ by **Md BELLOUCH**  
GitHub: [mdbellouch](https://github.com/mdbellouch) | IG: `s3j_.4`
