---
title: PropertyList-Element (XMLA) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.topic: reference
api_name:
- PropertyList Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- http://schemas.microsoft.com/analysisservices/2003/engine#PropertyList
- microsoft.xml.analysis.propertylist
- urn:schemas-microsoft-com:xml-analysis#PropertyList
helpviewer_keywords:
- PropertyList element
ms.assetid: 58e63bd9-8aac-438d-adba-1868b4d123f5
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: d3eb6da43b5487efa93f3901c866a1183e77d978
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/02/2018
ms.locfileid: "48068910"
---
# <a name="propertylist-element-xmla"></a>PropertyList-Element (XMLA)
  Enthält eine Auflistung von XML für Analysis (XMLA) Eigenschaften ein, die die [Discover](../xml-elements-methods-discover.md) und [Execute](../xml-elements-methods-execute.md) Methoden.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
<Properties>  
   <PropertyList>  
      <!-- Zero or more XMLA properties -->  
   </PropertyList>  
</Properties>  
```  
  
## <a name="element-characteristics"></a>Elementmerkmale  
  
|Merkmal|Description|  
|--------------------|-----------------|  
|Datentyp und -länge|None|  
|Standardwert|None|  
|Cardinality|0-1: Optionales Element, das nur einmal auftreten kann.|  
  
## <a name="element-relationships"></a>Elementbeziehungen  
  
|Beziehung|Element|  
|------------------|-------------|  
|Übergeordnete Elemente|[Eigenschaften](properties-element-xmla.md)|  
|Untergeordnete Elemente|XMLA-Eigenschaften (siehe Hinweise)|  
  
## <a name="remarks"></a>Hinweise  
 Die `PropertyList` Element enthält eine Auflistung von XMLA-Eigenschaften. Jede Eigenschaft ermöglicht dem Benutzer, einige Aspekte der `Discover`-Methode und der `Execute`-Methode zu steuern. Dazu gehört das Definieren von Informationen, die für die Verbindung mit der Datenquelle erforderlich sind, das Angeben des Rückgabeformats des Resultsets oder das Angeben des Gebietsschemas, für das die Daten formatiert werden sollen. Jede XMLA-Eigenschaft in der `PropertyList` -Element wird durch ein separates XML-Element definiert. Beim Wert der XMLA-Eigenschaft handelt es sich um die Daten, die im XML-Element enthalten sind. Der Name der XMLA-Eigenschaft entspricht dem Namen des XML-Elements.  
  
 Die verfügbaren Eigenschaften und deren Werte erhalten Sie mithilfe des Anforderungstyps DISCOVER_PROPERTIES mit der `Discover` Methode. Es gibt keine erforderliche Reihenfolge für die im `PropertyList`-Element aufgelisteten Eigenschaften.  
  
 Weitere Informationen zu den XMLA-Eigenschaften, die von unterstützt [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)], finden Sie unter [unterstützte XMLA-Eigenschaften &#40;XMLA&#41;](propertylist-element-supported-xmla-properties.md).  
  
## <a name="example"></a>Beispiel  
  
```  
<Properties>  
   <PropertyList>  
      <DataSourceInfo>  
         Provider=MSOLAP;Data Source=local;  
      </DataSourceInfo>  
      <Catalog>  
         Foodmart 2000  
      </Catalog>  
      <Format>  
         Multidimensional  
      </Format>  
   </PropertyList>  
</Properties>  
```  
  
## <a name="see-also"></a>Siehe auch  
 [Eigenschaften &#40;XMLA&#41;](xml-elements-properties.md)  
  
  
