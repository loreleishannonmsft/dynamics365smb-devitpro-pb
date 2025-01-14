---
title: "OnValidate (Page fields) Trigger"
ms.custom: na
ms.date: 04/01/2019
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.service: "dynamics365-business-central"
ms.assetid: c9a4c961-c9c2-4afb-8493-fbeefdad27ca
author: SusanneWindfeldPedersen
manager: edupont
---



# OnValidate (Page fields) Trigger
Runs when a field loses focus after its value has been changed.  
  
## Syntax  
  
```  
trigger OnValidate()
begin
    ...
end;
```  
  
## Applies To  
  
-   Pages  
  
## Remarks  
 Use this trigger to validate user entries in a page field. If validation fails, then the field is marked with an error and its value is not saved.  
  
 The OnValidate trigger is also a field trigger at the table level. For more information, see [OnValidate (Fields) Trigger](devenv-onvalidate-fields-trigger.md). If both the table field and page field triggers are defined, then the OnValidate trigger on the table field is run before the OnValidate trigger on the page field.  
  
> [!NOTE]  
>  You can use this trigger to write to the database. You cannot call the UPDATE from this trigger.

## See Also  
 [OnValidate (Fields) Trigger](devenv-onvalidate-fields-trigger.md)  
 [Page and Action Triggers](devenv-page-and-action-triggers.md)  
 [Page Properties](../properties/devenv-page-properties.md)  
 [Triggers](devenv-triggers.md)  
