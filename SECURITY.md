# Security Policy

This is the default policy for repositories in the **meta-agentic** organisation. A repository
that ships something security-sensitive overrides it with its own `SECURITY.md` — if you are
reading this on a repository, no override exists and the terms below apply.

## Reporting a vulnerability

**Please do not open a public issue, discussion, or pull request for a security problem.**

Use GitHub's **private vulnerability reporting**: the *Security* tab on the affected repository
→ **Report a vulnerability**. That opens a private advisory visible only to the maintainers, and
it gives us a private fork in which to develop and review the fix before anything is public.

If that button is missing on a repository, that is our bug and not yours — report it against
[meta-os](https://github.com/meta-agentic/meta-os/security/advisories/new) instead and say which
repository you meant.

Please include:

- what you found, and the security impact if it were exploited;
- a `file:line` reference or reproduction steps — the exact command you ran is ideal;
- the version, tag, or commit SHA you tested;
- a suggested fix or mitigation, if you have one.

Reports where you ran the command or read the line are far more actionable than ones inferred
from reading alone. If you are unsure whether something counts, send it anyway.

## What to expect

These are solo-maintained projects, so triage is best-effort rather than contractual:

- **Acknowledgement within 5 business days.** If you have not heard back within 10, assume the
  message went astray and ping again — silence here is never a decision.
- We verify every report against the real code before acting. We will not dismiss a finding
  without saying why, and we will not call something fixed without a command that demonstrates
  it.
- We will agree a disclosure timeline with you rather than impose one. If we cannot fix an
  issue, we will say so and document the limitation rather than leave it unstated.
- We credit reporters in the advisory and release notes unless you would rather stay anonymous.
  Tell us which you prefer.

## Supported versions

**The default branch is the supported version.** Fixes land there; if a repository maintains
release lines, its own `SECURITY.md` will say so. Please report against the latest default
branch or the newest published artifact.

We deliberately publish no version-support table. A hardcoded table rots the moment it is not
updated, and a stale one is worse than none — it makes "is my version supported?" unanswerable
while still looking authoritative.

## Scope

Most repositories here ship **prompt-based skills, agent definitions, conventions, and hooks
executed by AI coding assistants** rather than a runtime service. For those, these are in scope
and genuinely welcome:

- **prompt-injection vectors** — skill or reference content that could steer an assistant into
  exfiltrating data, running destructive commands, or bypassing a confirmation gate;
- **dangerous instructions** — steps that would have an assistant weaken a host's safety
  configuration, disable a gate, or execute unsafe shell commands;
- **hooks that do more than they document** — anything reading, writing, or transmitting beyond
  its stated behaviour, especially where prompt text, file contents, or credentials could reach
  disk or the network;
- **supply-chain issues** — vendored content diverging from its documented upstream, or
  instructions pinning known-vulnerable tool versions.

Also in scope wherever it applies: secrets committed or logged, injection and path traversal in
code we ship, dependency vulnerabilities we can act on, and CI or release workflows that could
be abused to ship altered artifacts.

Out of scope: findings that require an already-compromised machine or a deliberately
misconfigured deployment; missing hardening with no demonstrated exploit path; raw scanner
output pasted without a verified impact; and the security of the **host assistant itself**
(Claude Code and compatible hosts) — please report those to the host's vendor. Hardening of the
host through permission modes, sandboxes, and hooks is strongly recommended but is out of scope
for these repositories.

Volume-submitted or AI-generated reports with no verified reproduction will be closed unread.

## What we do not claim

This document asserts no list of security guarantees. Any such claim would be one a reporter
could falsify in ten minutes, and a policy that overstates its own rigour loses credibility
exactly when it is most needed. What we commit to is the process above: private intake, real
verification against the code, honest disclosure, and credit.
