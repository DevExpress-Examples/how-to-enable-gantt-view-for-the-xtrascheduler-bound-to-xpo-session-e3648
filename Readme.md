# How to enable Gantt view for the XtraScheduler bound to XPO Session


<p>This is a simple example of XtraScheduler bound to <a href="http://documentation.devexpress.com/#XPO/CustomDocument2022"><u>XPO Session</u></a>  displaying <a href="http://documentation.devexpress.com/#WindowsForms/CustomDocument10698"><u>Gantt view</u></a>. This project also utilizes the <a href="http://documentation.devexpress.com/#WindowsForms/CustomDocument10685"><u>ResourcesTree control</u></a> to display an hierarchy of resources and the <a href="http://documentation.devexpress.com/#WindowsForms/clsDevExpressXtraEditorsSplitContainerControltopic"><u>SplitContainer control</u></a> to allow resizing of Scheduler and ResourceTree controls. <br />
By default, XPO uses <strong>MS Access</strong> OLEDB provider, assumes that the database has the same name as the application and resides in the application folder. If the database does not exist, XPO creates it.</p><p>Please note the XPO specifics - to which fields appointment, resource and dependency identifiers are mapped:<br />
</p>

```cs
this.schedulerStorage1.Appointments.Mappings.AppointmentId = "Oid";
this.schedulerStorage1.Resources.Mappings.Id = "Oid";
this.schedulerStorage1.Resources.Mappings.ParentId = "ParentResource!Key";
this.schedulerStorage1.AppointmentDependencies.Mappings.DependentId = "DependentApt!Key";
this.schedulerStorage1.AppointmentDependencies.Mappings.ParentId = "ParentApt!Key";
this.schedulerStorage1.AppointmentDependencies.Mappings.Type = "Type";



```

<p>and how the XPO objects themselves are implemented. </p><p>The following events of the SchedulerStorage are handled in a special way:</p><p>AppointmentDependenciesInserted <br />
AppointmentDependenciesChanged<br />
AppointmentsInserted<br />
AppointmentsChanged</p>

<br/>


