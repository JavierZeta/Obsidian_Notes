# AUTO-LIBRARIAN ROUTING DIRECTIVE

## 1. Zero-Command Processing (CRITICAL)
If I paste a block of text without a specific command, you must follow this "Auto-Process" heuristic:
1. **Detect Context:** Is this a conversation output from a Thinker model (Gemini/Opus)?
2. **Auto-Route:** If yes, immediately load `Z_AI-Workspace/AI-Rules/formatting_rules.md`.
3. **Execute:** Extract the core analysis, apply the academic YAML, identify [[wikilinks]], and save it as a new file in `/Z_AI-Workspace/3-Permanent/`.
4. **Auto-Title:** Generate a precise academic title based on the first two paragraphs.

## 2. Security & Write Quarantine
- **READ (Global):** Open access to vault for context.
- **WRITE (Sandboxed):** You may ONLY save to `/Z_AI-Workspace/`. Never touch my personal folders.

## 3. Passive Rule Routing
- For search/extraction tasks, load: `Z_AI-Workspace/AI-Rules/extraction_rules.md`
- For manual filing tasks, load: `Z_AI-Workspace/AI-Rules/formatting_rules.md`