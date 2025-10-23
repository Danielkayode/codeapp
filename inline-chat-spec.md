# Prism Inline Chat & Tool-Call UI Specification

## 1. Activation & Transient Interface

- **Quick Activation:**  
  - Keyboard Shortcut: Cmd+K .
  - Opens a transient chat bubble at the cursor’s location in the editor.
  - Bubble disappears when action completes or is dismissed.
- **Minimal Distraction:**  
  - Overlay appears only as long as needed.
  - No persistent UI elements unless user pins the chat.

## 2. Focused Context

- **Context Awareness:**  
  - AI sees only the currently selected code block, or the closest surrounding function/class if nothing is selected.
  - The chat bubble displays the active file name and context summary.
- **Prompting:**  
  - User can type requests like:
    - “Refactor this function to async/await”
    - “Fix the bug in this block”
    - “Add comments explaining this code”
    - “Review this code for security” or anything they want/type

## 3. Inline Suggestions & Actions

- **Rapid Execution:**  
  - AI tool-call is triggered immediately.
  - AI response appears inline:
    - Shows suggested code change (diff, refactor, bug fix, comment).
    - User can accept (apply), reject (dismiss), or modify the suggestion.
- **Visual Diff:**  
  - Inline diff/merge view appears in the bubble.
  - Accept/reject buttons for each change.
  - Click for expanded diff details.
- **Status Indicators:**  
  - Show success, error, checkpoint, or pending status for each AI action.

## 4. Multi-Step Workflow

- **Chained Actions:**  
  - AI can perform multi-step workflows in one conversational flow:
    - Find code → Edit → Test → Commit.
  - Each step is shown as a message bubble or card in the conversation.
- **Undo/Restore:**  
  - "Restore checkpoint" or “Undo” button reverts to a previous state.

## 5. Inline Comments & Collaboration

- **Inline Comments:**  
  - AI and human collaborators can add comments/discuss changes directly in the chat bubble.
  - Comments persist as part of the conversational history.
- **Task Assignment:**  
  - Assign a refactor/test/fix/change to another user (for collab).
  - Status of assigned tasks shown inline.

## 6. History & File Cards

- **Step-by-Step History:**  
  - Each conversation step (user prompt, AI action, tool-call result, comment) is visible in order.
- **File Cards:**  
  - Each changed file appears as a clickable card:
    - Shows file name, change summary (`+10 -8`), and status.
    - Click to expand and review the diff.
    - Accept/reject changes from the card.
- **Context & Mapping:**  
  - Each action maps directly to the editor/tool result.
  - AI displays which file/block it’s acting on at each step.

## 7. Advanced Features

- **Multi-user Live Cursors:**  
  - Show other users' cursors and actions in real-time (for collab).
- **Checkpoint/Undo:**  
  - Restore previous state with one click.
- **Notifications:**  
  - Success/error notifications for each accepted/rejected action.
- **Keyboard Navigation:**  
  - All chat and actions accessible via keyboard.

## 8. Example UI Flow

```
[Cmd+K or Ctrl+K] → Inline chat bubble appears at cursor:
-------------------------------------------------------------
| main.swift: func fetchData()                              |
| [Selected code shown here]                                |
|-----------------------------------------------------------|
| User: Refactor to async/await                             |
|-----------------------------------------------------------|
| AI: Suggested refactor (+10 -8) [✔] [✖] [View Diff]       |
|-----------------------------------------------------------|
| [Accept] [Reject] [Undo]                                  |
|-----------------------------------------------------------|
| AI: All tests passed.                                     |
| test_results.xml (+3 -2) [✔]                              |
|-----------------------------------------------------------|
| [Assign as task] [Add comment]                            |
-------------------------------------------------------------
| Conversation history:                                     |
| - User: Refactor...                                       |
| - AI: Suggested change...                                 |
| - AI: Ran tests...                                        |
| - User: Assign to @collaborator                           |
-------------------------------------------------------------
```

## 9. Features Inspired by Windsurf/VSCode Cursor

- **Inline conversational editing**
- **Context-aware suggestions**
- **Multi-step AI workflows**
- **Live collaborative cursors**
- **Inline comments & review**
- **Change summaries and diff cards**
- **Undo/restore checkpoints**
- **Status indicators and notifications**

---

## 10. References

- Inline chat: VSCode Cursor, Windsurf, Copilot Chat.
- Tool-call chaining: Prism toolcall.md, multi-step workflows.
- Diff and merge: GitHub Pull Request UI, VSCode Source Control.
- Collaboration: Live share/cursor, task assignment.