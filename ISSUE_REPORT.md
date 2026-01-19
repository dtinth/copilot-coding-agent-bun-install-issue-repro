# Bun install investigation (Bun v1.3.6)

## Environment
- Bun v1.3.6 (d530ed99) on Linux x64 (kernel 6.11.0, glibc 2.39)
- Repository: [`copilot-coding-agent-bun-install-issue-repro`](https://github.com/dtinth/copilot-coding-agent-bun-install-issue-repro) (provides a minimal Bun init reproduction for this issue)

## Steps and outcomes
1. Installed Bun with `BUN_INSTALL_VERSION=1.3.6` using the official install script.
2. `bun install` (from repo root): **succeeded**, installed `@tsconfig/strictest@2.0.8`, `citty@0.1.6`, `confbox@0.2.2`.
3. `bun add typescript`: **failed with crash**  
   - Output excerpt:  
     ```
     panic: Assertion failure: Expected metadata to be set
     oh no: Bun has crashed. This indicates a bug in Bun, not your code.
     ...
     Illegal instruction (core dumped)
     ```
   - Full crash link emitted by Bun output: [Crash Report](https://bun.report/1.3.6/lI1d530ed9AgggggCwml71Cuy277Ck3v6hDmqlnB2muqCA0eNpzLC5OLSrJzM9TSEvMzCktSrVScK0oSE0uSU1RyE0tSUxJLElUKMlXSEpVKE4tAQCXxBEE)
   - Note: Crash observed on Jan 19 (UTC); link availability may change and no local crash archive was produced, so the panic excerpt above is retained as the durable record.

## Additional observations
- No crash files were generated under `~/.bun/crash`.
- Working tree remains clean; no dependency changes were recorded.
