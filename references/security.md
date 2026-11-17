# Security

## Principles
- Validate input on the server. Client validation improves experience but does not enforce anything.
- Authorize on the server for every protected action and every data read, including by ID (prevent IDOR by checking ownership).
- Least privilege: tokens and roles grant only what is needed.
- Fail closed: when an authorization check errors, deny.

## Input handling
- Validate type, length, format, and range at the boundary, using a schema.
- Encode output for its context (HTML, attribute, URL, JavaScript). Avoid `innerHTML` with unsanitized content; avoid `dangerouslySetInnerHTML` without a sanitizer.
- Use parameterized queries; never build SQL by string concatenation.
- Validate uploads: type by content, size limits, and safe storage names.
- Restrict redirects to an allowlist.

## Secrets
- Never commit secrets, API keys, tokens, or passwords. Use environment variables or a secret manager.
- Keep `.env` out of version control; commit `.env.example` with placeholders only.
- Client bundles contain only public values. Check build output for leaked keys before publishing.
- Rotate any secret that was exposed, even briefly.

## Authentication and sessions
- Use an established auth library or provider rather than custom crypto or password storage.
- Store passwords with a slow adaptive hash (bcrypt, scrypt, or Argon2).
- Cookies: `HttpOnly`, `Secure`, and `SameSite` set appropriately.
- Protect state-changing requests against CSRF when using cookie auth.
- Rate-limit login and sensitive endpoints.

## Transport and headers
- HTTPS only. Set a Content Security Policy where feasible, `X-Content-Type-Options: nosniff`, and frame protections (`frame-ancestors`).
- Avoid sending sensitive data in URL query strings, which are logged.

## Errors and logging
- Show users generic error messages; log details server-side without secrets or personal data.
- Do not expose stack traces in production responses.

## Dependencies
- Keep dependencies minimal and pinned by lock file.
- Run the package manager's audit command when available and record the result.
- Review new packages for maintenance status and install scripts.

## Pre-publish check
- Search the repository for key-like strings and `.env` files before any push.
- Confirm `.gitignore` covers local env files, build output, and credential files.
