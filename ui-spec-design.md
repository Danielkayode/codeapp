# Prism AI UI / Spec Design

## 1. Chat Panel UI (SwiftUI)

- **Main Panel**
  - Conversation thread with user and AI messages.
  - Supports markdown/code blocks, syntax highlighting.
  - Streaming responses (live typing from AI).
  - File/line references, clickable to open in editor.

- **Provider Selector**
  - Dropdown/menu for switching between AI providers (GPT-5, Gemini, Claude Sonnet/Opus).
  - Shows connection/auth status (API keys managed by owner only).

- **Context Injection**
  - Button to attach current editor context, selected code, or entire project summary.
  - Preview context snippet before sending to AI.

- **Tool Actions**
  - Inline buttons for actions: Run Code, Refactor, Generate Tests, Format Document, Commit, Push.
  - Confirmation dialogs for destructive actions (e.g., file replace).

- **History & Workflow**
  - List of chat sessions and tool actions.
  - Save/restore chat sessions with context.

## 2. Context Engine Integration

- **Swift Protocols**
  - Context engine exposes `getContext(for: selection/project/file)`.
  - API available to chat panel and tool actions.

- **Context Preview**
  - User can preview/edit context before sending to AI.

## 3. Tool Call UI

- **Action Buttons**
  - Each tool call surfaced inline in chat/editor.
  - Status feedback (pending, success, error) shown in chat or status bar.

- **Result Display**
  - Tool call results (test output, diff, commit log) shown inline in chat.
  - Option to open result in dedicated view (diff/merge, test runner, etc.).

## 4. Provider & Auth Settings

- **Settings Screen**
  - Admin-only: configure AI providers, manage API keys.
  - View authentication state, switch user/profile.

## 5. Collaboration & Debugging UI (Future)

- **Presence Bar**
  - Show active collaborators, cursor positions, sync status.
- **Debugger Panel**
  - Breakpoints, call stack, variable inspector, step controls.

---

## Wireframe Sketch (Textual)
```
+--------------------------------------------------------------+
| Mode: [Chat ▼]   Model: [GPT-5 ▼]   Context: [Attach File]   |
+--------------------------------------------------------------+
| > User: Refactor this function to async                      |
| < AI: Sure! Here is your refactored code:                   |
| ------------------------------------------------------------|
| ```swift                                                    |
| func foo() async -> ...                                     |
| ...                                                         |
| ```                                                         |
| [Run] [Commit] [Format]                                     |
| ------------------------------------------------------------|
| > User: Generate unit tests                                 |
| < AI: Here are some tests:                                  |
| ...                                                         |
+--------------------------------------------------------------+
| [History] [Settings]                                        |
+--------------------------------------------------------------+
```

---

## Accessibility and Responsiveness

- VoiceOver, dynamic type, keyboard support.
- Split view and slide-over modes.

---

## References

- All logic and UI implemented in Swift/SwiftUI.
- No Python backend.