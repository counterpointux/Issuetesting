---
title: Built-in code editor with native file explorer
status: Open
priority: Medium
type: Feature
area: Code Editor
assigned: Unassigned
created: 2026-04-06
---

Add an integrated code editor to Orchestrator using CodeMirror or Monaco Editor, paired with a native file explorer panel. This gives users the ability to view and edit project files directly inside the app without switching to an external editor.

## Code Editor

- Embed CodeMirror or Monaco as the editing surface (Monaco offers VS Code parity; CodeMirror is lighter weight — evaluate both)
- Syntax highlighting for common languages (TypeScript, JavaScript, Rust, JSON, Markdown, CSS, HTML, etc.)
- Tab-based multi-file editing
- Basic editor features: find/replace, line numbers, minimap (Monaco), bracket matching
- Read file contents via Tauri FS plugin; write back on save (Cmd+S)

## File Explorer

- Native file explorer panel (tree view) showing the current project's working directory
- Expand/collapse directories, click to open files in editor tabs
- Respect common ignore patterns (.gitignore, node_modules, target/, .git/)
- Context menu or icons for basic file operations (new file, new folder, rename, delete)
- File explorer can live in the sidebar or as a toggleable panel

## Integration Points

- Clicking file paths in terminal output (see #038) could open files in the editor
- Artifacts extracted from Claude sessions (#020) could open in editor tabs
- Editor tabs should be per-project, persisted across sessions
