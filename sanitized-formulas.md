# Sanitized Power Fx examples

These examples are generalized portfolio examples based on patterns in the app. They are not a complete export of the production source and intentionally omit production IDs, connector references, and environment-specific configuration.

## Filter tasks by status

```powerfx
Switch(
    FilterTabs.Selected.Value,
    "All",
    MasterTrackerTasks,
    "Active",
    Filter(MasterTrackerTasks, Status = "Active"),
    "Completed",
    Filter(MasterTrackerTasks, Status = "Completed"),
    MasterTrackerTasks
)
```

## Validate a single selected row

```powerfx
If(
    CountRows(MainGrid.SelectedItems) <> 1,
    Notify(
        "Select exactly one record.",
        NotificationType.Warning
    ),
    /* Continue with the selected-record operation */
)
```

## Navigate to a form with selected-record context

```powerfx
Set(varSelectedRow, RequisitionGrid.Selected);
Set(varSourceType, "Requisitions");
Navigate(EditRecordScreen, ScreenTransition.None)
```

## Design note

When a form saves data through Power Automate, pass a stable original key separately from editable fields. The flow should return an explicit success/failure result, and the app should refresh data and show a success message only after success is confirmed.
