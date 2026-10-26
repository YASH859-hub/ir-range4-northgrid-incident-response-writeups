# Evidence Index

Terminal screenshots are embedded in the associated write-up below the command block they document. The table maps each evidence image to its intended report use.

## M1

- [`01-clean-baseline.png`](evidence/M1/01-clean-baseline.png) — Clean reset/setup and listener check. Clean reset and setup validation; Range 4 historian gateway is shown listening on TCP/15432.
- [`02-live-attack-validation.png`](evidence/M1/02-live-attack-validation.png) — Successful controlled incident validation. Controlled Nuclei trigger and successful M1 attack validation.
- [`03-package-baseline-comparison.png`](evidence/M1/03-package-baseline-comparison.png) — Observed-versus-approved package manifest comparison. Observed package manifest compared with the approved 7.4.11 baseline.
- [`04-audit-correlation-and-handoff.png`](evidence/M1/04-audit-correlation-and-handoff.png) — Release audit, runtime and M1-to-M2 handoff. Runtime state, release audit events, historian probe and signed M1-to-M2 handoff.
- [`05-initial-attempt-diagnostic.png`](evidence/M1/05-initial-attempt-diagnostic.png) — Earlier failed attempt diagnostics (clearly marked non-final). Earlier non-passing attempt showing a stale logger-path permission issue; retained as troubleshooting evidence, not as proof of the final pass.

## M2

- [`01-clean-baseline.png`](evidence/M2/01-clean-baseline.png) — Setup validation and kernel headers. M2 setup validator passed; kernel version and matching header path recorded.
- [`02-live-attack-validation.png`](evidence/M2/02-live-attack-validation.png) — Kernel-thread/memory/OT validation. Controlled incident trigger and successful validation of kernel, memory, audit, debugfs, OT UDP and PCAP evidence.
- [`03-handoff-build-and-signature.png`](evidence/M2/03-handoff-build-and-signature.png) — M2-to-M3 signed handoff generation and verification. M2-to-M3 handoff build and successful absolute-path signature verification.
- [`04-evidence-and-saved-handoff.png`](evidence/M2/04-evidence-and-saved-handoff.png) — Saved handoff and signature verification. M2 package documentation, saved handoff files and signature verification result.

## M3

- [`01-portal-and-attack-instructions.png`](evidence/M3/01-portal-and-attack-instructions.png) — Portal health and attack instructions. M3 local portal health and supplied attack instructions, with the local target on TCP/32773.
- [`02-live-attack-validation.png`](evidence/M3/02-live-attack-validation.png) — Successful media/firmware incident validation. M3 incident dispatch and passing validation for media mount, firmware execution, callback, PCAP and audit sources.
- [`03-evidence-hashes-and-handoff.png`](evidence/M3/03-evidence-hashes-and-handoff.png) — Evidence hash checks and M3-to-M4 handoff. M3 evidence hashes, preserved incident artefacts and M3-to-M4 handoff verification.

## M4

- [`01-clean-baseline.png`](evidence/M4/01-clean-baseline.png) — Clean PostgreSQL baseline and service status. M4 native PostgreSQL setup and clean baseline validation; the legacy Range 3 service is separately identified.
- [`02-actual-incoming-handoff.png`](evidence/M4/02-actual-incoming-handoff.png) — Actual M3 handoff matching/signature and baseline verification. Correct group `nghistorian`, matching hashes for the actual M3 handoff files, valid signature and M4 setup pass.
- [`03-live-attack-validation.png`](evidence/M4/03-live-attack-validation.png) — Historian persistence incident validation. M4 incident record and passing validation for PostgreSQL persistence, CLR assembly, alarm suppression, invoice falsification, callback, PCAP and audit data.
- [`04-evidence-and-signed-handoff.png`](evidence/M4/04-evidence-and-signed-handoff.png) — Evidence integrity and signed M4-to-M5 handoff. Evidence-manifest results, M4-to-M5 handoff build, signature verification and preserved hashes.

## M5

- [`01-setup-and-m4-handoff.png`](evidence/M5/01-setup-and-m4-handoff.png) — M4 handoff and clean PLC baseline. M4-to-M5 handoff signature verified; native Modbus PLC M5 setup and clean-state validator passed.
- [`02-live-attack-validation.png`](evidence/M5/02-live-attack-validation.png) — Controlled Modbus state incident validation. M5 incident record and successful validation of Modbus state change, controlled outage, binary side channel, callback, PCAP and audit evidence.
- [`03-evidence-hash-verification.png`](evidence/M5/03-evidence-hash-verification.png) — M5 evidence manifest verified. Correct-directory verification of the M5 SHA256SUMS manifest; evidence files report OK.
- [`04-final-handoff-signature.png`](evidence/M5/04-final-handoff-signature.png) — Final handoff signature and state fields. Final Range 5 handoff signature verified and final PLC state fields preserved.
