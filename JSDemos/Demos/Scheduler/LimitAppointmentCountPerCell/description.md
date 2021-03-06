This demo shows how to use the [maxAppointmentsPerCell][0] option to limit the number of full-sized appointments displayed per cell.

This option accepts one of the following values. To see how they affect the appointments, switch between **Scheduler** views.

- *"auto"*          
Appointments are narrowed down to a predefined size value that depends on the [view type][1]. Appointments that do not fit into the cell are hidden, and the cell displays an overflow indicator. Users can click the indicator to display the hidden appointments in a tooltip.

- *"unlimited"*             
Appointments are narrowed down without a limit to be fit into a cell.

- **Number**        
The number specifies the maximum number of appointments allowed in a single cell. Appointments that exceed this number are hidden, and the cell displays an overflow indicator. Users can click the indicator to display the hidden appointments in a tooltip.

[0]: /Documentation/ApiReference/UI_Widgets/dxScheduler/Configuration/views/#maxAppointmentsPerCell
[1]: /Documentation/Guide/Widgets/Scheduler/Views/View_Types/