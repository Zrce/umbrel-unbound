# Zrce's Umbrel App Store

A community app store for [Umbrel](https://umbrel.com).

## Apps

### Pi-hole + Unbound

Network-wide ad blocking with a built-in recursive DNS resolver. Unbound, developed by NLnet Labs, resolves your queries directly against root nameservers with DNSSEC validation — no third-party DNS providers involved.

## Installation

1. Open your Umbrel dashboard
2. Go to **Settings > App Stores**
3. Add this repository URL: `https://github.com/Zrce/umbrel-unbound`
4. The app will appear in the Umbrel App Store under **Networking**

## After Installing

1. Open the Pi-hole dashboard from your Umbrel home screen
2. Log in with your Umbrel password
3. Point your devices' or router's DNS to your Umbrel's IP address
4. Enjoy ad-free, private DNS resolution

## Architecture

```
Devices on your network
        │
        ▼ (port 53)
    ┌────────┐
    │ Pi-hole │  ← blocks ads, caches queries
    └────┬───┘
         │ (port 5335, internal only)
    ┌────▼─────┐
    │ Unbound   │  ← recursive resolver, DNSSEC validation
    └────┬─────┘
         │
         ▼
  Root nameservers → TLD → Authoritative
```

## Development

Test locally with Docker Compose:

```bash
cd wio-unbound-pihole
APP_DATA_DIR=./app-data APP_PASSWORD=test1234 docker compose up
```

Pi-hole web UI: `http://localhost:8054/admin/`

## Still Needed

- [ ] `icon.svg` — 256x256 SVG app icon (no rounded corners)
- [ ] Gallery screenshots — 3 PNG images at 1440x900px in `gallery/`
- [ ] Verify Docker image SHA256 digests on your machine
- [ ] Test on Umbrel (Raspberry Pi or x86)
