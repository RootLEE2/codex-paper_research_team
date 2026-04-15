# Note Validation Report Schema

Use this shape for `note-validation.md` in a session or cycle folder.

```markdown
# Note Validation

- Date:
- Session:
- Agent:
- Scope:
- Source policy: PDF, preprint, or confirmed full text required.

## Summary

- Total notes checked:
- Passed:
- Repair required:
- Blocked missing full text:
- Synthesis gate:

## Checks

### [Paper ID or Citation Key]

- Note:
- Source full text:
- Status: pass | repair_required | blocked_missing_full_text
- Bibliographic identity:
- Source coverage:
- Extraction depth:
- Methods and apparatus:
- Experimental design:
- Participants or dataset:
- Measures:
- Analysis/statistics:
- Results:
- Limitations and future work:
- Language policy:
- Required repairs:

## Synthesis Gate Decision

State whether synthesis may proceed. If not, list the exact papers and required next action.
```
