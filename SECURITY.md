# Security Policy

credswitch routes provider CLIs to per-context credential state. It never
reads, stores, transmits, or proxies credentials itself — but bugs in its
environment handling could still select the wrong identity, which is exactly
the class of failure it exists to prevent. Reports in that category are
treated as security issues, not ordinary bugs.

## Reporting a vulnerability

Please use GitHub's private vulnerability reporting on this repository
(Security → Report a vulnerability) rather than opening a public issue.
You should receive a response within a few days.

## Scope notes

- The fail-closed guarantees (clearing managed variables, denying omitted
  adapters) apply inside contexts: `csw run`, pinned shells, and hooked
  shells. An unhooked, unpinned shell is outside credswitch's control.
- The managed-variable inventory per adapter is documented in the README.
  A credential channel we miss for a supported provider is in scope.
- Provider CLIs' own storage security (e.g. what `az login` writes to disk)
  is out of scope — credswitch inherits it by design.
