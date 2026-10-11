# Power Automate workflow documentation

The app source references flows for operations including:

- Add requisition
- Edit requisition
- Add interview
- Edit interview
- Add offer
- Edit offer
- Delete row

This file documents the integration pattern only. Production flow definitions are intentionally not copied into this portfolio repository.

## Recommended flow contract

1. Trigger: Power Apps (V2).
2. Inputs: operation type, original unique key, and only the fields required for the operation.
3. Validation: reject missing keys, unsupported table names, and malformed values.
4. Data operation: use an explicit table mapping rather than allowing arbitrary table names from untrusted input.
5. Response: return `Success`, a safe user-facing message, and optionally a non-sensitive error category.
6. App behavior: refresh the corresponding data source and display success only after a confirmed successful response.

## Deletion safeguards

- Require exactly one selected record in the app.
- Ask the user to confirm deletion.
- Verify the key column and target table mapping.
- Test row deletion against a demo workbook before using a production workbook.
- Do not expose raw connector errors or resource identifiers to end users.
