# Prism AI Feature Requirements

## 1. Context Engine (Swift)
- **Project Indexing:** Fast, reliable indexing of all project files (path, content, language, symbols).
- **Context Extraction:** Generate context snippets for current file, selection, or project summary.
- **Symbol Analysis:** Extract functions, classes, variables, and dependencies for context-rich AI calls.
- **API:** Expose context retrieval via Swift protocols for use in chat, tool calls, and UI actions.

## 2. AI Provider Native Integration
- **Supported Providers:** OpenAI (GPT-5), Anthropic (Claude Sonnet/Opus), Google Vertex AI (Gemini).
- **Swift API:** All AI requests handled via native Swift SDKs or direct HTTP calls.
- **Secure Token Storage:** API keys/tokens stored and managed via iOS Keychain.
- **Provider Settings:** UI for configuring providers (admin/owner only).

## 3. AI Chat Panel
- **SwiftUI UI:** Real-time messaging, markdown/code rendering, streaming responses.
- **Context Attachment:** User can inject code context, selection, or project info into chat.
- **Tool Actions:** Inline buttons for running/refactoring code, formatting, version control, etc.
- **History & Workflow:** Track chat history and attach context/workflow actions.

## 4. Developer Tools (Swift)
- **Native File System:** Read, write, move, delete, search files.
- **Git Integration:** Repository management, commit, diff, branch, push, pull.
- **Editor Manipulation:** Open, replace, insert, format files; diff/merge support.
- **Testing/Build:** Run tests and builds via Swift-native code.

## 5. Authentication & Security
- **Firebase Auth:** Email/password, Google, Apple login via Swift SDK.
- **User Profiles:** View/manage profile info, session state.
- **Secure API Access:** All tool calls and AI requests authenticated.

## 6. Extensibility & Modularity
- **Swift Protocols:** All modules extensible via protocols and dependency injection.
- **Third-Party Extension API:** Documented hooks for future AI extensions.

---

## Excluded

- No Python backend, no FastAPI.
- All system logic and developer tools implemented in Swift/iOS.