# attack

`attack #<handle>` proves ONE recorded finding with a non-destructive PoC and writes a client-ready report. The handle is on the finding's card and in `list_vulnerabilities`.

## Commands

| Command | What it does |
|---|---|
| `attack #<id>` | Exploit and prove one recorded finding. |
| `validate #<id>` | Settle a finding: exploited / not proven / false positive. |
| `access #<id>` | Use a finding to get real access. |
| `attack:onion <target>` | The same plan over Tor. |

## Steps

cve_match, cve_exploit, php, php_sink, session_cfg, form_scan, sqlmap, param_scan, logic_scan, graphql_scan, authz_scan, content_scan, jwt_tool, git-dumper, webfetch, nuclei, login_brute_all.

## The CVE path

Every CVE goes through one path:

1. `cve_match` reads the products and versions this scan measured (nmap, whatweb, httpx, the target's headers, the PHP step) and matches them against the CVE database.
2. `cve_exploit` hands the model that worklist — CVE, product, version, exploit-db id, our dossier — and the model writes and runs the exploit on the machine.
3. A finding is proven only by a real response that only the vulnerable build produces. A version match is evidence, not access.

## Proof and access

- A working login (weak credentials) is evidence: a session, not a shell.
- An access row (a shell, a key, a session you can use) is created only by the backdoor step, and only with a real proof.
- Access rows are removed only from the Access tab, by its own buttons.
