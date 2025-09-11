<div align="center">
  <picture>
    <source media="(prefers-color-scheme: dark)" srcset="./resources/logo-dark.svg">
    <source media="(prefers-color-scheme: light)" srcset="./resources/logo-light.svg">
    <img src="./resources/logo-light.svg" alt="Jumble Logo" width="400" />
  </picture>
  <p>logo designed by <a href="http://wolfertdan.com/">Daniel David</a></p>
</div>

# Jumble

A user-friendly Nostr client focused on relay feed browsing and relay discovery

## Features

- **Relay Feeds:** Explore content directly through relays without following specific users
- **Relay-Friendly Design:** Minimized and simplified requests ensure efficient communication with relays
- **Relay Sets:** Easily manage and switch between relay sets
- **Clean Interface:** Enjoy a minimalist design and intuitive interactions

## Screenshots

<img src="./screenshots/01.png" alt="Jumble Screenshot 01" width="650" />
<div> 
  <img src="./screenshots/02.png" alt="Jumble Screenshot 02" width="200" />
  <img src="./screenshots/03.png" alt="Jumble Screenshot 03" width="200" />
  <img src="./screenshots/04.png" alt="Jumble Screenshot 04" width="200" />
</div>

## Run Locally

```bash
# Clone this repository
git clone https://github.com/CodyTseng/jumble.git

# Go into the repository
cd jumble

# Install dependencies
npm install

# Run the app
npm run dev
```

### Run on system boot (MacOS)
- Requires NPM Homebrew (https://formulae.brew.sh/formula/node)
- Update USERNAME
- Update path to Jumble

```bash
sudo nano ~/Library/LaunchAgents/com.USERNAME.jumble.plist
```

```bash
<?xml version="1.0" encoding="UTF-8"?>
<!DOCTYPE plist PUBLIC "-//Apple Computer//DTD PLIST 1.0//EN"
 "http://www.apple.com/DTDs/PropertyList-1.0.dtd">
<plist version="1.0">
<dict>
  <key>Label</key>
  <string>com.jumble.dev</string>

  <!-- run a short shell command (non-login) that sets PATH and execs node/npm -->
  <key>ProgramArguments</key>
  <array>
    <string>/bin/sh</string>
    <string>-c</string>
    <string>cd "$HOME/jumble" \
      && export PATH="/opt/homebrew/bin:/usr/local/bin:/usr/bin:/bin:/usr/sbin:/sbin" \
      && if [ -f /opt/homebrew/lib/node_modules/npm/bin/npm-cli.js ]; then \
           exec /opt/homebrew/bin/node /opt/homebrew/lib/node_modules/npm/bin/npm-cli.js run dev; \
         else \
           exec /opt/homebrew/bin/npm run dev; \
         fi
    </string>
  </array>

  <!-- keep it alive and log output -->
  <key>RunAtLoad</key>
  <true/>
  <key>KeepAlive</key>
  <true/>
  <key>StandardOutPath</key>
  <string>/tmp/jumbledev.log</string>
  <key>StandardErrorPath</key>
  <string>/tmp/jumbledev.err</string>
</dict>
</plist>

```
```bash
launchctl load ~/Library/LaunchAgents/com.USERNAME.jumble.plist

```



## Run Docker

```bash
# Clone this repository
git clone https://github.com/CodyTseng/jumble.git

# Go into the repository
cd jumble

# Run the docker compose
docker compose up --build -d
```

After finishing, access: http://localhost:8089

## Sponsors

<a target="_blank" href="https://opensats.org/">
  <img alt="open-sats-logo" src="./resources/open-sats-logo.svg" height="44"> 
</a>

## Donate

If you like this project, you can buy me a coffee :)

lightning: ⚡️ codytseng@getalby.com ⚡️

bitcoin: bc1qx8kvutghdhejx7vuvatmvw2ghypdungu0qm7ds

geyser: https://geyser.fund/project/jumble

## License

MIT
