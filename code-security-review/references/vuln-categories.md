# Vulnerability Categories Reference

Extended taxonomy for the `code-security-review` skill. Load this file when you need deeper detail on a specific category.

---

## 1. Injection Attacks

The attacker sends hostile data that is interpreted as code or commands.

| Type | Description | Languages / Contexts |
|---|---|---|
| **SQL Injection** | Unsanitized user input in SQL queries | Any DB-backed app |
| **Command Injection** | User input passed to shell commands | Python `os.system`, PHP `exec`, Node `child_process` |
| **SSTI** | Template engine executes attacker-controlled input | Jinja2, Twig, Pebble, Freemarker |
| **XSS (Stored/Reflected/DOM)** | Malicious scripts injected into web pages | HTML, JS, React `dangerouslySetInnerHTML` |
| **XXE** | XML parser processes external entity references | XML parsers in Java, PHP, Python |
| **LDAP Injection** | Unsanitized input in LDAP queries | Directory services |
| **NoSQL Injection** | Operator injection in MongoDB queries | `{$where: ...}`, `{$gt: ""}` patterns |
| **Header Injection** | CRLF injection into HTTP headers | Any HTTP response construction |

**Key CWEs**: CWE-89, CWE-78, CWE-94, CWE-79, CWE-611

---

## 2. Broken Authentication

Flaws that allow attackers to compromise passwords, keys, or session tokens.

- Hardcoded credentials in source code
- Weak or no password hashing (plain text, MD5, SHA1 without salt)
- JWT: `alg: none` accepted, weak secret, no expiry validation
- Session tokens that don't expire or aren't invalidated on logout
- Missing rate limiting / account lockout on login endpoints
- Predictable reset tokens

**Key CWEs**: CWE-798, CWE-916, CWE-307, CWE-384

---

## 3. Sensitive Data Exposure

Sensitive data transmitted or stored insecurely.

- Secrets/API keys/passwords in source code, `.env` committed to git, logs
- PII logged in plaintext
- Weak TLS configuration (SSLv3, TLS 1.0, self-signed in prod)
- Missing `Secure` / `HttpOnly` flags on cookies
- Sensitive data in URL query parameters (visible in logs/history)
- Unencrypted database fields for sensitive data

**Key CWEs**: CWE-312, CWE-319, CWE-532

---

## 4. Broken Access Control

Restrictions on what authenticated users are allowed to do are not properly enforced.

- Missing authorization checks on endpoints
- IDOR: user can access other users' objects by changing an ID
- Path traversal: `../../etc/passwd` via unsanitized file paths
- Privilege escalation: user can modify their own role
- JWT payload tampering accepted without signature verification
- Exposed admin functionality without role check

**Key CWEs**: CWE-22, CWE-284, CWE-639, CWE-285

---

## 5. Security Misconfiguration

Insecure default configurations, unnecessary features enabled, unpatched systems.

- Debug mode / stack traces exposed in production
- Overly permissive CORS (`Access-Control-Allow-Origin: *` on sensitive APIs)
- Default credentials not changed
- Unnecessary HTTP methods enabled (e.g., TRACE, DELETE on public endpoints)
- Verbose error messages leaking internal paths, DB structure, framework versions
- Missing security headers (CSP, HSTS, X-Frame-Options, X-Content-Type-Options)
- World-readable file permissions on sensitive files

**Key CWEs**: CWE-16, CWE-209, CWE-732

---

## 6. Vulnerable and Outdated Components

Using components with known vulnerabilities.

- Dependencies with published CVEs
- Pinned versions that are months/years behind
- Transitive dependency vulnerabilities
- Using deprecated or abandoned libraries

**Detection approach**: Note package names and versions; flag if you recognize known-vulnerable versions (e.g., Log4Shell in log4j < 2.15.0, lodash < 4.17.21 prototype pollution).

**Key CWEs**: CWE-1035, CWE-937

---

## 7. Insecure Deserialization

Deserializing data from untrusted sources without validation.

| Language | Dangerous patterns |
|---|---|
| Python | `pickle.loads()`, `yaml.load()` (without `Loader=SafeLoader`), `marshal` |
| PHP | `unserialize()` on user input |
| Java | `ObjectInputStream.readObject()` on untrusted data |
| Node.js | `node-serialize`, `serialize-javascript` with `eval` |
| Ruby | `Marshal.load` |

**Key CWEs**: CWE-502

---

## 8. Cryptographic Failures

Using broken or weak cryptographic algorithms or implementations.

- MD5 / SHA1 for password hashing (use bcrypt, argon2, scrypt)
- ECB mode for block ciphers (use GCM or CBC with proper IV)
- Hardcoded IVs or nonces
- Insufficient key length (RSA < 2048 bits, AES-128 in sensitive contexts)
- Using `random` instead of `secrets` / `os.urandom` for security-sensitive values
- Custom crypto implementations
- Timing-attack-vulnerable comparison (use `hmac.compare_digest`)

**Key CWEs**: CWE-327, CWE-330, CWE-326, CWE-320

---

## 9. SSRF / CSRF / Open Redirects

### SSRF (Server-Side Request Forgery)
Server makes HTTP request to attacker-controlled URL.
- Fetching user-supplied URLs without allowlist validation
- Cloud metadata endpoint abuse (`169.254.169.254`)

### CSRF (Cross-Site Request Forgery)
Attacker tricks authenticated user's browser into making unwanted requests.
- Missing CSRF tokens on state-changing endpoints
- `SameSite` cookie attribute not set

### Open Redirects
`redirect?url=https://evil.com` — used for phishing
- Unvalidated `next`, `return_to`, `redirect` parameters

**Key CWEs**: CWE-918, CWE-352, CWE-601

---

## 10. Race Conditions & Logic Flaws

### Race Conditions
- TOCTOU (Time-of-Check to Time-of-Use): check then act without atomic operation
- Concurrent writes without locks
- Double-spend vulnerabilities

### Business Logic Flaws
- Negative quantity / price manipulation
- Bypassing multi-step workflows (skipping to final step directly)
- Mass assignment: user can set fields they shouldn't (e.g., `is_admin: true`)
- Replay attacks on one-time tokens

**Key CWEs**: CWE-362, CWE-840, CWE-915

---

## Smart Contracts (Solidity / Rust / Move) {#smart-contracts}

| Vulnerability | Description |
|---|---|
| **Reentrancy** | External call before state update; attacker re-enters function |
| **Integer Overflow/Underflow** | Solidity < 0.8.0: use SafeMath; 0.8+ has built-in checks |
| **Access Control** | Missing `onlyOwner`/role checks on sensitive functions |
| **Front-Running** | Transaction ordering manipulation (MEV) |
| **tx.origin auth** | Use `msg.sender`, never `tx.origin` for auth |
| **Unchecked return values** | `.transfer()` vs `.call()` return value handling |
| **Timestamp dependence** | `block.timestamp` can be manipulated by miners |
| **Delegatecall to untrusted** | Storage layout collision |

**Key CWEs**: CWE-841, CWE-190; also see SWC Registry (https://swcregistry.io/)

---

## Quick Reference — OWASP Links

- [OWASP Top 10](https://owasp.org/www-project-top-ten/)
- [OWASP Cheat Sheet Series](https://cheatsheetseries.owasp.org/)
- [CWE Top 25](https://cwe.mitre.org/top25/)
- [OWASP Testing Guide](https://owasp.org/www-project-web-security-testing-guide/)
