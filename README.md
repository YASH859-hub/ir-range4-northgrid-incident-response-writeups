# IR Range 4 — NorthGrid Incident Response Write-ups

Five evidence-led Markdown reports documenting the controlled **Silent Meridian / NorthGrid Operational Resilience** training range. Every report places the relevant terminal command and its matching screenshot together in the same workflow section. Screenshots are stored in `evidence/` and embedded with relative Markdown paths, so they render on GitHub.

> **Scope:** This is a controlled training-lab report. Observed service names, incident IDs, PLC values, invoice references and the `ORCHID-17`/`7F3A` side-channel are lab data. The scenarios targeted local loopback portals and a local simulated Modbus server. They do not demonstrate an attack on a real power system, actual invoice, or physical PLC.

## Reports

| Report | Scenario | Key evidence / outcome |
|---|---|---|
| [M1 — Maintenance Script Compromise](writeups/01-M1-Maintenance-Script-Compromise.md) | `IR-Range4-M1` | Run `NG04-20261026T032927Z-bb80d5`; observed 7.4.12 package deviated from approved 7.4.11 baseline; M1-to-M2 handoff created. |
| [M2 — Kernel-Hidden Control Thread](writeups/02-M2-Kernel-Hidden-Control-Thread.md) | `IR-Range4-M2` | Incident `NG04-KMEM-20261026T035539Z-bc00fa`; kernel/memory/audit/debugfs/OT UDP/PCAP validation passed; M2-to-M3 signature verified. |
| [M3 — Decoy Firmware Media](writeups/03-M3-Decoy-Firmware-Media.md) | `IR-Range4-M3` | Incident `NG04-FW-20261026T042201Z-7757be`; media mount, firmware execution, callback, audit and PCAP validation passed; M3-to-M4 handoff created. |
| [M4 — Historian Persistence](writeups/04-M4-Historian-Persistence.md) | `IR-Range4-M4` | Incident `NG04-HIST-20261026T045623Z-b6287b`; PostgreSQL persistence, CLR assembly, alarm suppression and invoice evidence validated; M4-to-M5 handoff verified. |
| [M5 — PLC State Manipulation](writeups/05-M5-PLC-State-Manipulation.md) | `IR-Range4-M5` | Incident `NG04-PLC-20261026T051114Z-519164`; Modbus state, side channel, callback, PCAP and audit validated; final Range 5 handoff signature verified. |

## Evidence and chain of custody

The handoff sequence recorded during the work was:

1. M1 → M2 (`HDO-R4M1-R4M2-0001`)
2. M2 → M3 (`HDO-R4M2-R4M3-0001`)
3. M3 → M4 (`HDO-R4M3-R4M4-0001`)
4. M4 → M5 (`HDO-R4M4-R4M5-0001`)
5. M5 → Range 5 M1 (`HDO-R4M5-R5M1-0001`)

The signed handoffs were verified in the lab using the supplied public keys. Raw evidence collections and the handoff JSON/signature files are deliberately not included in this public-ready bundle.

### Screenshot index

- [M1 terminal evidence](evidence/M1/)
- [M2 terminal evidence](evidence/M2/)
- [M3 terminal evidence](evidence/M3/)
- [M4 terminal evidence](evidence/M4/)
- [M5 terminal evidence](evidence/M5/)

`EVIDENCE-INDEX.md` maps screenshots to the report sections. Images are included as terminal screenshots, not separate cropped results; they therefore preserve the command and output together as requested.

## What is and is not included

Included: five Markdown reports, command snippets, scenario findings supported by the supplied screenshots, relevant screenshots, repository README, and evidence index.

Excluded on purpose: raw PCAPs, live memory dumps, database dumps, environment files, actual handoff JSON/signatures, private keys, credentials, and complete lab packages. Keep those in your private case folders. Review screenshots once more before public posting if your lab policy treats internal host paths or simulated indicators as sensitive.

## Platform and limitations

The M2 package documentation states an Ubuntu Server 22.04 x86-64 validated profile, while the screenshots show a newer Ubuntu 26.04 environment and kernel `7.0.0-38-generic`. The M2 module built and its validator passed in the observed run, but the platform difference is a reproducibility caveat. The M5 final incident state reports `trip_inhibit: true`; the final handoff displayed `trip_inhibited: null`. M5 report documents this handoff data-quality discrepancy rather than silently resolving it.

The initial M1 attempt with a stale logger-path permission error is called out explicitly and is not used as the successful-run evidence. The later clean-baseline run and live validator passed.

## Suggested GitHub repository name

**`ir-range4-northgrid-incident-response-writeups`**

## Push to GitHub

Unzip this bundle, open a terminal in the extracted `ir-range4-northgrid-writeups` folder, then run:

```bash
git init
git add README.md EVIDENCE-INDEX.md FILE-SHA256SUMS.txt writeups evidence
git commit -m "Add IR Range 4 incident response write-ups and inline evidence"
git branch -M main
git remote add origin https://github.com/<YOUR-USERNAME>/ir-range4-northgrid-incident-response-writeups.git
git push -u origin main
```

Replace `<YOUR-USERNAME>` with your GitHub username. If `origin` already exists, inspect it with `git remote -v` and update it deliberately instead of adding a second remote. If the remote repository already has a commit, run `git pull --rebase origin main` before pushing, and resolve any conflicts before proceeding.

## Reproducibility

The commands in these reports reflect the session workflow and the documented lab package. Commands are presented for understanding and case documentation, not as a reason to rerun an incident. Avoid replaying triggers or resetting the environment solely to regenerate screenshots after a successful run.
