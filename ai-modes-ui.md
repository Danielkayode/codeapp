# Prism AI Modes & Chat Panel UI Specification

## Modes

Prism supports two main modes for AI features:

### 1. Chat Mode (`.chat`)
- **Purpose:** Freeform conversation with the selected AI model (Codex/GPT-5, Gemini, Claude Sonnet/Opus).
- **UI Behavior:** 
  - Input field labeled "Search in context...".
  - User can ask questions, get explanations, code samples, etc.
  - Context-aware: can inject current file/project context into chat.
  - No agent workflow or tool execution; pure Q&A.

### 2. Agent Mode (`.agent`)
- **Purpose:** Task-oriented AI agent mode, enabling tool-calls, refactoring, running tests, etc.
- **UI Behavior:** 
  - Input field labeled "Ask the agent...".
  - Displays a picker for model selection (no mix model, only one active per task).
  - Task history panel shows all previous agent tasks.
  - Agent log panel displays step-by-step execution/results.
  - Enables access to all tool-calls (see toolcall.md).
  - User can choose which model to use for each agent task.
  - Context injection available—attach file/project context to agent prompt.

---

## Model Selection

- **User can choose only one model per task/prompt** (no mixed or ensemble models).
- Model picker uses a dropdown menu UI:
  - Options: Codex GPT-5 (OpenAI), Gemini 2.5 Pro, Claude Sonnet 4, Claude Opus 4.1.
  - Only shows models available/configured by owner.
- Model setting persists per session but can be changed per task.

---

## AI Chat Panel UI Spec

### Layout

```
+------------------------------------------------------+
| Mode: [ Chat ▼ ]   Model: [ GPT-5 ▼ ]               |
+------------------------------------------------------+
| RECENT TASKS   [VIEW ALL TASKS] [⚙️]                |
|------------------------------------------------------|
| [Task history list or 'No recent tasks' placeholder] |
|------------------------------------------------------|
| [Chat or Agent Input Area]                           |
|  - TextField: "Search in context..." or "Ask agent"  |
|  - Model Picker (Agent mode only)                    |
|  - [Paperplane] Send Button                          |
+------------------------------------------------------+
| [Agent Log] (Agent mode only)                        |
|  - Step-by-step results, errors, cost, model used    |
+------------------------------------------------------+
```

### Details

- **Mode Switcher:** Menu button lets user choose between Chat and Agent mode.
- **Model Picker:** Appears in Agent mode, lets user pick the AI model for the current task.
- **Input Field:** 
  - Chat mode: quick questions, explanations, code, etc.
  - Agent mode: task prompts, refactoring, code generation, test runs, etc.
- **Send Button:** Disabled if field is empty; triggers submitAction.
- **Context Attach:** Button or option to attach file/project context to prompt.
- **Task History:** Scrollable panel of past tasks (PrismTask), showing type, model, cost, tokens.
- **Agent Log:** In Agent mode, displays logs/steps/output/errors for each agent task.
- **Accent Colors:** Follows Prism’s design (purple accent, dark background).

### Example SwiftUI bindings (from prismtestversion):

```swift
@State private var currentMode: PMode = .chat
@Published var selectedModel: AIConfig.AIModel = .gemini

Menu {
    Button("Chat", action: { withAnimation { currentMode = .chat } })
    Button("Agent", action: { withAnimation { currentMode = .agent } })
} label: { ... }

Picker("Model", selection: $contextService.selectedModel) {
    ForEach(AIConfig.shared.availableModels(), id: \.self) { model in
        Text(model.displayName).tag(model)
    }
}
.pickerStyle(MenuPickerStyle())
.frame(width: 120)
```

---

## Context Engine & Injection

- Utilizes PrismContextEngine for code/project context extraction.
- Context can be injected into both Chat and Agent mode prompts.
- Context preview before sending.

---

## Security & API Key Handling

- **API keys for AI models are managed by the app owner only.**
- End-users cannot input, view, or change API keys.
- Only available models (with valid keys) are shown in the picker.

---

## References

- `CodeApp/Views/PrismView.swift`: UI logic and bindings for mode/model selection.
- `CodeApp/AI/AIConfig.swift`: Model listing, secure config, key management.
- `CodeApp/Prism/PrismTask.swift`: Task struct for history/logs.
- `CodeApp/Services/PrismContentService.swift`: Context engine integration.

---

*This spec is designed for direct implementation in Swift/SwiftUI and ensures users can freely switch between chat and agent modes, selecting their preferred AI model for each task, with all security and context features handled as required.*