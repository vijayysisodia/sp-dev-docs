---
title: AppPartConfigDefinition complexType
manager: soliver
ms.date: 9/16/2015
ms.audience: Developer
ms.topic: reference
ms.prod: sharepoint
ms.localizationpriority: medium
ms.assetid: 01abeb84-0904-12b8-c7ea-aae75a2b87e4
---

# AppPartConfigDefinition complexType 

(AppPartConfigDefinition)

**Applies to**: SharePoint Add-ins | SharePoint Foundation 2013 | SharePoint Server 2013

> [!NOTE] 
> The string `app` appears as part of or all of some element, attribute, and file names because SharePoint Add-ins were originally called "apps for SharePoint." To ensure backward compatibility, the schemas have not been changed.

## Type information

|   |   |
|---|---|
| **Namespace**  | `http://schemas.microsoft.com/sharepoint/2012/app/partconfiguration` |
| **Schema file**  | apppartconfig.xsd |
| **Extension base**  | None |

## Definition

```XML
    <xs:complexType name="AppPartConfigDefinition">
        <xs:all>
            <xs:element name="Id" type="GUID" minOccurs="1" maxOccurs="1"></xs:element>
        </xs:all>
    </xs:complexType>
```

## Elements and attributes

If the schema defines specific requirements, such as **sequence**, **minOccurs**, **maxOccurs**, and **choice**, see the definition section.

### Child elements

<table>
<colgroup>
<col width="33%" />
<col width="33%" />
<col width="33%" />
</colgroup>
<thead>
<tr class="header">
<th align="left"><p>Element</p></th>
<th align="left"><p>Type</p></th>
<th align="left"><p>Description</p></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left"><p><a href="id-element-apppartconfigdefinition-complextypeapppartconfigdefinition.md">Id</a></p></td>
<td align="left"><p><a href="guid-simpletype-apppartconfigdefinition.md">GUID</a></p></td>
<td align="left"><p>The unique identifier of the app part.</p></td>
</tr>
</tbody>
</table>

### Attributes

None.

<br/>

<br/>






