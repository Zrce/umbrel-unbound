# Unbound for Umbrel

This installs Unbound on your Umbrel without using the command line.

A validating, recursive, and caching DNS resolver by NLnet Labs. Resolves queries directly against root nameservers with DNSSEC validation — no third-party DNS providers involved.

## Installation

1. Open the **App Store** on your Umbrel
2. In the top right corner, click the **three dots** and open **Community App Stores**
3. Add `https://github.com/Zrce/umbrel-unbound`
4. Open it and click **Unbound**
5. Click **Install**

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
