
# Report.DefaultControl Property (Access)

The  **DefaultControl** property returns a ** [Control](ce2362e5-4390-590e-06c0-6f27e8d988cd.md)**object with which you can set the default properties for a particular type of control on a particular report. Read-only.


## Syntax

 _expression_. **DefaultControl**( **_ControlType_**)

 _expression_A variable that represents a  **Report** object.


### Parameters



|**Name**|**Required/Optional**|**Data Type**|**Description**|
|:-----|:-----|:-----|:-----|
|ControlType|Required| **Long**|An  ** [AcControlType](562ecad2-5cb5-7624-8f5a-236f42bd0104.md)** constant that indicates the type of control for which default property settings are to be set.|

## Remarks

The  **DefaultControl** property enables you to set a control's default properties from code. Once you have set the default properties for a particular type of control, each subsequently created control of that type will have the same default values.

For example, if you set the  **FontSize** property of the default command button to 12, each new command button will have a font size of 12 points.

Not all of a control's properties are available as default properties. The default properties available for a control depend on the type of control.

The  **DefaultControl** property returns a **Control** object of the type specified by thecontroltype argument. This **Control** object doesn't represent an actual control on a form, but rather a default control that is a template for all subsequently created controls of that type. You set the default control properties for the **Control** object returned by the **DefaultControl** property in the same manner that you would set properties for an individual control on a form.

The  **DefaultControl** property can be used only in form Design view or report Design view. If you try to apply this property to a form or report that is not in Design view, a run-time error will result.

If you try to set a property that can't be set as a default property with the  **DefaultControl** property, a run-time error will result. To determine which properties can be default properties, list the **Properties** collection of the **Control** object returned by the **DefaultControl** property.


## Example

The following example creates a new form and uses the  **DefaultControl** property to return a **Control** object representing the default command button. The procedure sets some of the default properties for the command button, then creates a new command button on the form.


```
Sub SetDefaultProperties() 
 Dim frm As Form, ctlDefault As Control, ctlNew As Control 
 
 ' Create new form. 
 Set frm = CreateForm 
 ' Return Control object representing default command button. 
 Set ctlDefault = frm.DefaultControl(acCommandButton) 
 ' Set some default properties. 
 With ctlDefault 
 .FontWeight = 700 
 .FontSize = 12 
 .Width = 3000 
 .Height = 1000 
 End With 
 ' Create new command button. 
 Set ctlNew = CreateControl(frm.Name, acCommandButton, , , , 500, 500) 
 ' Set control's caption. 
 ctlNew.caption = "New Command Button" 
 ' Restore form. 
 DoCmd.Restore 
End Sub
```


## See also


#### Concepts


 [Report Object](6f77c1b4-a9ce-7caa-204c-fe0755c6f9df.md)
#### Other resources


 [Report Object Members](73370a33-1ca0-da4d-9e36-88011bc2b93e.md)