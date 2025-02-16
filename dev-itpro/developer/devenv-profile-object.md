---
title: "Profile Object"
description: "Description of the page object."
author: SusanneWindfeldPedersen
ms.custom: na
ms.date: 04/01/2019
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.service: "dynamics365-business-central"
ms.author: solsen
---

# Profile Object
The profile object in [!INCLUDE[d365fin_long_md](includes/d365fin_long_md.md)] allows you to build an individual experience for each user profile. The Profile object performs a validation to check whether the specified role center page exists, and [page customization objects](devenv-page-customization-object.md) exists, when you define a new profile object. On a page customization you can add changes to the page layout, and actions; but you cannot add variables, procedures, or triggers. 

> [!NOTE]  
> Page customizations only apply to the RoleCenter they are specified for. In order to see them, in [!INCLUDE[d365fin_long_md](includes/d365fin_long_md.md)] under **My Settings**, **Role Center** change to the specific RoleCenter that a page customization is defined for.

> [!NOTE]  
> Extension objects can have a name with a maximum length of 30 characters.

## Snippet support
Typing the shortcut `tprofile` will create the basic layout for a profile object when using the [!INCLUDE[d365al_ext_md](../includes/d365al_ext_md.md)] in Visual Studio Code.

[!INCLUDE[intelli_shortcut](includes/intelli_shortcut.md)]

## Profile example
The following profile object example performs a validation to check if the `Business Manager` page of type RoleCenter exists, and if `MyCustomization` exists, and if it is a page customization object. Then the page customization modifies the layout of the **Customer List** to make the `Name` field invisible using the `modify` method. 

```
profile TheBoss
{
    Description = 'The Boss';
    RoleCenter = "Business Manager";
    Customizations = MyCustomization;
}

pagecustomization MyCustomization customizes "Customer List"
{
    layout
    {
        modify(Name)
        {
            Visible = false;
        }
    }
}

```

## See Also  
[AL Development Environment](devenv-reference-overview.md)  
[Developing Extensions](devenv-dev-overview.md)  
[Pages Overview](devenv-pages-overview.md)  
[Page Customization Object](devenv-page-customization-object.md)
