Fix address discovery and the Host check (code, not config):
1. Discovery: list every IPv4 address on this machine's active interfaces (Wi-Fi, Ethernet, VPN),
   not just what the hostname resolves to; skip loopback and link-local; never list an address the
   machine doesn't have. crq ui prints them all, Wi-Fi/Ethernet first.
2. Host check: accept the machine's host names plus any IP the machine has at the time of the
   request (re-read the interfaces at most every 30 s), with the port; plus anything in
   allowed_hosts. Still refuse a foreign Host (DNS rebinding protection stays).
3. Don't add 192.168.0.105 to console.yaml.
4. Tests: an address added after start is accepted; a foreign Host is refused; an address the
   machine no longer has is refused.
Keep UI_RATE_LIMITED as built. Don't change any system or firewall settings. Run python
scripts/check.py --browser; list files changed; stop. No branches, tags or commits.