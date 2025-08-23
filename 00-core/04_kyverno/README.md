# Kyverno

Kyverno has multiple controllers:

- kyverno-admission-controller → handles admission webhooks (mutate, validate at request time).
- kyverno-background-controller → runs background scans, and also executes generate rules asynchronously (e.g. secret clone).
- kyverno-cleanup-controller → manages cleanup policies.
- kyverno-reports-controller → creates policy reports.