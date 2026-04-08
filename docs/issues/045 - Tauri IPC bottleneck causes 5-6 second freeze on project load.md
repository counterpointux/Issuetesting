---
title: Tauri IPC bottleneck causes 5-6 second freeze on project load
status: Open
priority: High
type: Bug
area: Performance
assigned: Unassigned
created: 2026-04-07
---

## Problem

When opening or switching projects, the UI freezes for 5-6 seconds before any content appears. The screen appears completely unresponsive during this time, then everything loads at once.

## Root Cause (investigated)

The Tauri IPC bridge between JavaScript and Rust is blocked for 5-6 seconds. Rust commands execute in 2-4ms but JS callbacks don't resolve for ~6 seconds.

### Evidence

- `invoke('create_session')` takes 2-4ms on Rust side, 5,400-6,000ms on JS side
- `@tauri-apps/plugin-store` `s.get()` takes 5,700ms on first call
- React renders in 163ms (`requestAnimationFrame` confirms first paint), but the screen appears frozen because all IPC-dependent content is stuck
- Orphaned Tauri callback IDs flood the console (dozens of "Couldn't find callback id" warnings)
- Issue persists on fresh boot with no prior sessions — not caused by old PTY cleanup
- Issue persists with lazy PTY creation (1 shell instead of 8) — not caused by concurrent shells
- Issue persists with store plugin completely bypassed (direct file I/O) — not caused by store plugin alone
- Issue persists in both dev and production builds

### What was ruled out

1. **Store plugin reads** — bypassed entirely with direct `readTextFile`, no improvement
2. **Store plugin writes** — replaced with direct `writeTextFile`, no improvement
3. **Multiple simultaneous shell spawns** — reduced to 1 via lazy PTY, no improvement
4. **Old PTY sessions flooding IPC** — tested on fresh boot with no prior sessions, no improvement
5. **React rendering** — confirmed React renders in 163ms, the delay is purely IPC

### What remains unknown

- Why does the Tauri IPC bridge block for 5-6 seconds even for simple invoke calls?
- Is there a Tauri plugin or configuration causing the bottleneck?
- Does the `store:default` plugin registration in capabilities cause IPC overhead even when unused from JS?
- Are there Tauri-level thread pool or event loop constraints?
- Is the macOS WKWebView IPC mechanism itself the bottleneck?

## Completed work (preserved)

Tasks 1-8 from the loading performance plan are committed and working correctly. They will deliver their intended benefit once the IPC bottleneck is resolved:

- Rust ZDOTDIR shell pre-config (eliminates 600ms frontend pauses)
- Eager PTY creation (no waiting for container dimensions)
- Skeleton shimmer components for issues, files, terminal
- Legacy migration code removed
- Builtin issues startup parallelized
- In-memory store cache (getData reads are 3-12ms)

## Next steps

Needs a focused investigation into the Tauri IPC bridge itself — profiling the Rust event loop, checking plugin initialization overhead, and potentially restructuring how the app communicates with the backend.
