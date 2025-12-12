# How to Load Data on Demand using Command in WPF TreeGrid?

This example illustrates how to load data on demand using command in [WPF TreeGrid](https://www.syncfusion.com/wpf-controls/treegrid) (SfTreeGrid).

You can load child items for the node in [Execute](https://docs.microsoft.com/en-us/dotnet/api/system.windows.input.icommand.execute?view=netframework-4.8) method of `LoadOnDemandCommand`. `Execute` method will get called when user expands the tree node. In `Execute` method, you can populate the child nodes by calling [TreeNode.PopulateChildNodes](https://help.syncfusion.com/cr/wpf/Syncfusion.UI.Xaml.TreeGrid.TreeNode.html#Syncfusion_UI_Xaml_TreeGrid_TreeNode_PopulateChildNodes) method by passing the child items collection.

``` csharp
public void Execute(object parameter)
{
    TreeNode node = (parameter as TreeNode);
    EmployeeInfo emp = node.Item as EmployeeInfo;
    if (emp != null)
    {
        node.PopulateChildNodes((App.Current.MainWindow.DataContext as ViewModel).GetReportees(emp.ID));
    }
}
```
