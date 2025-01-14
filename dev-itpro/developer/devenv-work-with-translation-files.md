---
title: "Working with Translation Files"
description: "How to work with translations, multilanguage, and XLIFF files in Business Central"
ms.custom: na
ms.date: 04/01/2019
ms.topic: article
ms.service: "dynamics365-business-central"
ms.author: solsen
author: SusanneWindfeldPedersen
---

# Working with Translation Files
[!INCLUDE[d365fin_long_md](includes/d365fin_long_md.md)] is multilanguage enabled, which means that you can display the user interface (UI) in different languages. To add a new language to the extension you have built, you must first enable the generation of XLIFF files. The XLIFF file extension is .xlf. The generated XLIFF file contains the strings that are specified in properties such as **Caption** and **Tooltip**.

> [!NOTE]  
> To submit an app to AppSource, you must use .xliff translation files.

> [!IMPORTANT]  
> You can use the .xlf translation files approach only for objects from your extension. For translating the base application you still need to use the .txt files approach. For more information, see the **Translation and Localization apps** section below.

## Translation and Localization apps
The .xlf files approach cannot be used for translating the base application. If you are working on a translation or localization app (for example for a [country/region localization](readiness/readiness-develop-localization.md)), you must take the .txt file containing the base application translation, and place the file in the root folder of your extension. When the extension is compiled, the .txt file is then packaged with the extension. 

We recommend that you use only one .txt file per language. There is no enforced naming on the .txt files, but a suggested good practice is to name it `<extensionname>.<language>.txt`.  

For more information about importing and exporting .txt files, see [How to: Add Translated Strings By Importing and Exporting Multilanguage Files in Dynamics NAV](https://docs.microsoft.com/en-us/dynamics-nav/how-to--add-translated-strings-by-importing-and-exporting-multilanguage-files).

## Generating the XLIFF file
To enable generation of the translation file, you must add a setting in the manifest. In the app.json file of your extension, add the following line:

```
  "features": [ "TranslationFile" ]
```

Now, when you run the build command (Ctrl+Shift+B) in Visual Studio Code, a `\Translations` folder will be generated and populated with the .xlf file that contains all the labels, label properties, and report labels that you are using in the extension. The generated .xlf file can now be translated.

> [!IMPORTANT]
> Make sure to rename the translated file to avoid that the file is overwritten next time the extension is built.

## Label syntax
The label syntax is shown in the example below for the **Caption** property: 

```
Caption = 'Developer translation for %1',  Comment = '%1 is extension name', locked = false, MaxLength=999; 
```
> [!NOTE]
> The `comment`, `locked`, and `maxLength` attributes are optional and the order is not enforced. For more information, see [Label Data Type](methods-auto/label/label-data-type.md).

Use the same syntax for report labels:  

```
labels
{
  LabelName = 'Label Text', Comment='Foo', MaxLength=999, Locked=true;
} 
```

And the following is the syntax for **Label** data types:

```
var
    a : Label 'Label Text', Comment='Foo', MaxLength=999, Locked=true;
```


The **ML** versions of properties are **not** included in the .xlf file:

- [CaptionML](properties/devenv-captionml-property.md)
- [ConstValueML](properties/devenv-constvalueml-property.md)
- [InstructionalTextML](properties/devenv-instructionaltextml-property.md)
- [OptionCaptionML](properties/devenv-optioncaptionml-property.md)
- [PromotedActionCategoriesML](properties/devenv-promotedactioncategoriesml-property.md)
- [ReqFilterHeadingML](properties/devenv-reqfilterheadingml-property.md)
- [RequestFilterHeadingML](properties/devenv-requestfilterheadingml-property.md)
- [ToolTipML](properties/devenv-tooltipml-property.md)

The [TextConst Data Type](methods-auto/textconst/textconst-data-type.md) is not included in the .xlf file either.


## The XLIFF file
In the generated .xlf file, you can see a `<source>` element for each label. For the translation, you will now have to add the `target-language` and a `<target>` element per label. This is illustrated in the example below.

```
<ding="utf-8"?>
<xliff version="1.2" xmlns="urn:oasis:names:tc:xliff:document:1.2" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="urn:oasis:names:tc:xliff:document:1.2 xliff-core-1.2-transitional.xsd">
  <file datatype="xml" source-language="en-US" target-language=”da-DK” original="ALProject16">
    <body>
      <group id="body">
        <trans-unit id="PageExtension 1255613137 - Property 2879900210" maxWidth="999" size-unit="char" translate="yes" xml:space="preserve">
          <source>Developer translation for %1</source>
          <target>Udvikleroversættelse for %1</target>
          <note from="Developer" annotates="general" priority="2">%1 is extension name</note>
          <note from="Xliff Generator" annotates="general" priority="3">PageExtension - PageExtension</note>
        </trans-unit>
      </group>
    </body>
  </file>
</xliff>
```

> [!NOTE]  
> You can have only one .xlf file per language. If you translate your extension to multiple languages, you must have a translation file per language. There is no enforced naming on the file, but a suggested good practice is to name it `<extensionname>.<language>.xlf`.

When the extension is built and published, you change the language of [!INCLUDE[d365fin_long_md](includes/d365fin_long_md.md)] to view the UI in the translated language. 

## See Also
[How to: Add Translated Strings By Importing and Exporting Multilanguage Files in Dynamics NAV](https://docs.microsoft.com/dynamics-nav/how-to--add-translated-strings-by-importing-and-exporting-multilanguage-files)  
