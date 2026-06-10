# Zrce's Umbrel App Store

A community app store for [Umbrel](https://umbrel.com).

## Apps

### Unbound

A validating, recursive, and caching DNS resolver by NLnet Labs. Resolves queries directly against root nameservers with DNSSEC validation — no third-party DNS providers involved.

## Installation

1. Open your Umbrel dashboard
2. Go to **Settings > App Stores**
3. Add this repository URL: `https://github.com/Zrce/umbrel-unbound`
4. Install **Unbound** from the Networking category

## Connecting Pi-hole to Unbound

After installing both Pi-hole and Unbound on your Umbrel:

1. Open the Pi-hole dashboard
2. Go to **Settings > DNS**
3. Remove all upstream DNS servers
4. Add a custom upstream: `127.0.0.1#5335`
5. **Disable** Pi-hole's DNSSEC setting (Unbound handles DNSSEC validation)
6. Save

Your DNS flow becomes:

```
Your devices → Pi-hole (port 53, ad blocking) → Unbound (port 5335, recursive resolver) → Root nameservers
```

## Development

Test locally:

```bash
cd zrce-unbound
docker compose up
dig @127.0.0.1 -p 5335 example.com
```
