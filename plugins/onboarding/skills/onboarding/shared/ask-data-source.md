# Ask Data Source

Use the AskUserQuestion tool with:

- **Question**: "Which data source should we work with?"
- **Single-select** (not multi-select)
- **Options**:
  | Label | Description |
  |-------|-------------|
  | Test Flight databases | Use tables in the Test Flight account |
  | Bring your own data | Import CSV, JSON, or other files. Please avoid using personal or confidential data. |

## Conditional behavior

- **Test Flight databases**: Default to the `treasurebikes` database unless the user specifies otherwise.
- **Bring your own data**: Remind the user to upload data using the "+" icon in the chat window. Wait for the file attachment before proceeding with any analysis. If the user already has data uploaded, use that instead.
