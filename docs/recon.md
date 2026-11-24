# recon

Send `recon` for the menu. `recon <target>` fingerprints first, then runs the whole applicable chain: `host:port` names the service on that port, an IP or host runs ports → services → web, a URL runs the web plan.

## Commands

| Command | What it does |
|---|---|
| `recon <target>` | Umbrella: the whole applicable chain for that target. |
| `recon:domain` | Host-wide scan: subdomains → live hosts → the web app on each. |
| `recon:host` | Network only: ports and services, then hand off to web. |
| `recon:web` | The web app: crawl, forms, parameters, stack, CVEs. |
| `recon:ports` | Port sweep only. |

A `.onion` runs web-only over Tor.

## Steps (31)

fingerprint, subfinder, crtsh, dig, naabu, nmap, httpx, whatweb, wafw00f, katana, link_crawl, gau, cve_match, php, php_sink, session_cfg, form_scan, js_deobf, content_scan, sqlmap, param_scan, logic_scan, graphql_scan, nuclei, authz_scan, arjun, jwt_tool, secretfinder, supply_scan, infra_scan, report.

## Re-run a subset

`--steps sqlmap,param_scan` runs only those steps, in command order. Take the codes from `command_status`; do not invent them.

## Notes

- A step that cannot run is not in the plan: no recorded login form means no brute-force step.
- A host whose page cannot be read is marked `walled` only after the captcha solver and the browser both fail.
- A discovered subdomain is queued for its own recon run, bounded per scan.
