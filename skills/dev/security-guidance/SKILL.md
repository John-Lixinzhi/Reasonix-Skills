---
name: security-guidance
description: [dev] Security review - USE when auditing code security. DO 3-layer: patterns, LLM diff, agentic commit review. NOT for regular code review. Triggers: security/vulnerability/audit
---

# Security Guidance

Three-layer security review for AI-generated code.

## Layers

1. Pattern warnings - 25+ dangerous patterns
2. LLM diff review - per-turn security check
3. Agentic commit review - cross-file vulnerability tracing

## Coverage

SQL injection, XSS, SSRF, hardcoded secrets, IDOR, unsafe deserialization, path traversal
