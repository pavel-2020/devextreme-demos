Our **DataGrid** widget manages its edit state automatically. If your use case requires full control over the editing process, you can use the API members below to manage state manually. In this demo, we manage state with a help of the <a href="https://reactjs.org/docs/hooks-reference.html#usereducer" target="_blank">useReducer</a> React hook.

**Widget Options**

- **editing**.[editRowKey](/Documentation/ApiReference/UI_Widgets/dxDataGrid/Configuration/editing/#editRowKey)        
The key for the row being edited.

- **editing**.[editColumnName](/Documentation/ApiReference/UI_Widgets/dxDataGrid/Configuration/editing/#editColumnName)        
The name or data field of the column being edited.

- **editing**.[changes](/Documentation/ApiReference/UI_Widgets/dxDataGrid/Configuration/editing/#changes)       
Pending row changes.

Bind these options to state props and set the props to change edit state at runtime. In this demo, we bind the **editRowKey** and **changes** options and use the corresponding **on_OptionName_Change** event handlers to set the bound props.

**Utility Method**

- [DevExpress.data.applyChanges(data, changes, options)](/Documentation/ApiReference/Data_Layer/Utils/#applyChangesdata_changes_options)      
Applies an array of changes to a source data array.

**Event Handlers**

- [onSaving](/Documentation/ApiReference/UI_Widgets/dxDataGrid/Configuration/#onSaving) / [onSaved](/Documentation/ApiReference/UI_Widgets/dxDataGrid/Configuration/#onSaved)        
Functions that are called before / after pending row changes are saved via the UI or programmatically.

- [onEditCanceling](/Documentation/ApiReference/UI_Widgets/dxDataGrid/Configuration/#onEditCanceling) / [onEditCanceled](/Documentation/ApiReference/UI_Widgets/dxDataGrid/Configuration/#onEditCanceled)      
Functions that are called before / after editing is canceled and pending row changes are discarded.

Use these functions to perform custom actions. In this demo, the **onSaving** function sends pending changes to a server. The function's parameter `e` contains fields for this capability. To implement the same in your application, follow these steps:

1. **Disable built-in edit state management**       
Set the `e.cancel` field to **true**.

1. **Send a request to the server**      
Pending changes are stored in the `e.changes` array. This array has only a single element in all [edit modes](/Documentation/ApiReference/UI_Widgets/dxDataGrid/Configuration/editing/#mode), except for batch. Check if this element is not empty and send it to the server (see the `saveChange` action in `actions.js`).

1. **Apply the same changes to the widget's data source and reset edit state**       
If the server successfully saves changes, call the **applyChanges** method to save the same changes in the widget's data source. Assign **null** to the **editRowKey** and an empty array to the **changes** option. This resets edit state (see the `SAVING_SUCCESS` handler in `reducer.js`).

[note] This functionality is available as a <a href="https://www.devexpress.com/aboutus/pre-release.xml" target="_blank">community technology preview (CTP)</a>. Should you have any questions or suggestions prior to its official release, please email your comments to <a href="mailto:support@devexpress.com">support@devexpress.com</a>.