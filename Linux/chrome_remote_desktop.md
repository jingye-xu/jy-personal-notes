# chrome_remote_desktop on Ubuntu

## 1. Ensure you install the "Chrome Remote Desktop" extension in your browser

## 2. Install packages to enable share your device

```bash
wget https://dl.google.com/linux/direct/chrome-remote-desktop_current_amd64.deb -P /tmp
sudo apt install /tmp/chrome-remote-desktop_current_amd64.deb
```

## 3. Enable remote desktop connections by opening the Chrome remote desktop extension and clicking Turn on

## 4. If the button is not visible, create the Chrome remote desktop configuration directory:

```bash
mkdir ~/.config/chrome-remote-desktop
```

