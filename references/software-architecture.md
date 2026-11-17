# Software Architecture

## Goals
Changes should be easy to understand, easy to test, and cheap to extend. Architecture exists to reduce the cost of future change, not to look sophisticated.

## Layers
Common separation, adapted to the project's size:
1. **Presentation:** pages, components, view models.
2. **Application/use cases:** orchestrates actions such as "book a session" or "create an order".
3. **Domain:** business rules, validation, calculations. No framework imports.
4. **Infrastructure:** database, APIs, storage, messaging, third-party SDKs.

Dependencies point inward: presentation may call use cases; domain never imports infrastructure.

## Module boundaries
- Each module exposes a small public interface (an index file or explicit exports).
- Other modules do not reach into internal files.
- Shared code is genuinely shared (used by 2+ modules with the same meaning). Do not create a "shared" folder for convenience.

## Data flow
- Define data shapes in one place (types or schemas) and derive validators from them where possible.
- Validate at boundaries: HTTP inputs, form inputs, external API responses, stored data read back.
- Use explicit mapping between external and internal shapes.

## Scalability
- Stateless request handlers; state lives in stores.
- Paginate lists. Avoid unbounded queries.
- Background or slow work goes to a queue or job, not the request path, when the platform supports it.

## Configuration
- Environment-specific values come from configuration, validated at startup.
- No hard-coded URLs, IDs, or credentials.

## Change discipline
- Before a refactor, list the callers and the tests that protect current behavior.
- Refactor in steps that keep the system working: add the new path, migrate callers, remove the old path.
- Do not rewrite a working architecture to match a preferred pattern without a concrete problem it solves.

## Red flags
- A single file that imports most of the codebase.
- Business rules inside UI event handlers.
- Duplicate sources of truth for the same value.
- Circular dependencies between modules.
- "Manager", "Helper", or "Utils" files that collect unrelated functions.
