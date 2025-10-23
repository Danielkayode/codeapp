# Prism AI Tool-Call Layer Specification (Expanded)


 DESKTOP-UBKUGIL

## Overview

All AI tool-calls are Swift-native, exposed via the `ToolCallable` protocol. API keys for AI models are managed exclusively by the app owner (Danielkayode); users cannot provide their own keys. Only owner-selected models are available.

---

## 1. ToolCallable Protocol

```swift
public protocol ToolCallable {
    var name: String { get }
    var description: String { get }
    func call(_ params: [String: Any]) async throws -> [String: Any]
}
```

- All tool-calls registered in `CodeApp/CodeUI/AIKit/ToolRegistry.swift`.

---

## 2. Supported AI Providers

- **OpenAI Codex/GPT-5 (Direct API)**
- **Google Gemini 2.5 Pro (Vertex AI)**
- **Anthropic Claude Sonnet 4 & Opus 4.1 (Vertex AI Partnership)**

---

## 3. Tool Groups (Expanded & Inspired by Windsurf/VSCode Cursor)

### Core Tools
- **GitTools:** git_status, git_diff, git_commit, git_branch, git_push, git_log, git_rebase, git_stash, git_tag
- **ShellTools:** shell_exec, shell_spawn, shell_kill, shell_attach, shell_prompt
- **LspTools:** lsp_symbols, lsp_rename, lsp_hover, lsp_diagnostic, lsp_format, lsp_code_actions, lsp_references, lsp_organize_imports
- **FileTools:** fs_read, fs_write, fs_move, fs_delete, fs_list, fs_search, fs_watch, fs_zip, fs_unzip
- **BuildTools:** pkg_install, pkg_remove, build_run, build_clean, build_configure
- **TestTools:** test_discover, test_run, test_debug, test_watch, test_coverage
- **DebugTools:** debug_start, debug_breakpoint, debug_eval, debug_continue, debug_step_into, debug_step_over, debug_step_out, debug_attach
- **LintTools:** lint_run, lint_fix, security_scan, lint_configure
- **DocTools:** doc_generate, readme_toc, doc_search, doc_update, doc_publish
- **CloudTools:** docker_build, docker_run, deploy_aws, deploy_gcp, deploy_azure, cloud_login, cloud_logs
- **SnapshotTools:** snapshot_create, snapshot_restore, snapshot_compare, snapshot_schedule
- **ContextEngine:** extract_context, index_symbols, summarize_project, context_history

### Advanced/Bonus Tools (Maximum AI Autonomy & Modern Editor Features)
- **AIHelperTools:** ai_complete, ai_chat, ai_refactor, ai_review_pr, ai_generate_tests, ai_explain_code, ai_optimize_code, ai_generate_docs, ai_rewrite, ai_summarize, ai_detect_bugs
- **CodeQualityTools:** coverage_report, static_analysis, cyclomatic_complexity, code_duplication, code_metrics, code_review_auto, code_smells
- **PerformanceTools:** benchmark_run, profile_run, memory_profile, cpu_profile
- **SecurityTools:** vuln_scan, secrets_detect, dependency_audit, security_report, threat_model, access_audit
- **CollaborationTools:** active_users, share_project, resolve_conflict, session_invite, live_cursors, remote_pairing, comment_thread, task_assign, change_request
- **PackageManagerTools:** package_search, package_update, package_lock, package_audit, package_info
- **VisualizationTools:** generate_flowchart, generate_sequence_diagram, generate_class_diagram, generate_dependency_graph, generate_heatmap
- **MigrationTools:** migrate_python3, migrate_swift6, upgrade_dependencies, migrate_node, migrate_java, migrate_ui_framework
- **UIAutomationTools:** ui_run_test, ui_record_macro, ui_play_macro, ui_screenshot, ui_video_record
- **AccessibilityTools:** accessibility_scan, alt_text_suggest, contrast_check, voiceover_check
- **NotificationTools:** notify_success, notify_error, notify_alert, notify_task_done
- **WorkspaceTools:** workspace_sync, workspace_clone, workspace_fork, workspace_merge, workspace_clean, workspace_status
- **VersionTools:** version_check, version_bump, version_tag, version_publish
- **TerminalTools:** terminal_focus, terminal_resize, terminal_clear, terminal_set_env
- **SettingsTools:** settings_export, settings_import, settings_reset, settings_apply_profile
- **ExtensionTools:** extension_list, extension_install, extension_remove, extension_update
- **ThemeTools:** theme_switch, theme_customize, theme_preview
- **KeyboardShortcutTools:** shortcut_list, shortcut_customize, shortcut_reset

---

## 4. API Key Management

- **API keys/tokens for AI providers are stored and managed only by the app owner (Danielkayode).**
- End-users do not see or input API keys.
- Provider settings screen is admin-only.

---

## 5. UI Security & Controls

- Settings: “Allow AI to run shell commands” toggle, default OFF.
- All AI tool-calls surfaced in a dedicated “AI Tools” panel.
- Destructive actions require user confirmation.

---

## 6. Example Tool Definition

```swift
final class LiveCursorTool: ToolCallable {
    let name = "live_cursors"
    let description = "Show and synchronize cursor positions for all active collaborators."
    func call(_ params: [String: Any]) async throws -> [String: Any] {
        // Implementation...
    }
}
```

---

## 7. Commit Message Pattern

Use `[AI-pN] <what>` for each phase (N = phase number).

---

## 8. References

- See `roadmap.md` and `prompts-jules.md` for implementation steps and prompt examples.
- Features adapted from Windsurf, VSCode Cursor, and other modern AI-powered code editors.

---