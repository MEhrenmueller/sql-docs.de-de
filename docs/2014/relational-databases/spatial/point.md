---
title: Punkt | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- dbe-spatial
ms.topic: conceptual
helpviewer_keywords:
- Point geometry subtype [SQL Server]
- geometry data type [SQL Server], spatial data
ms.assetid: 2a596ec4-8b2f-4962-bcb4-e5c8f77edad5
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: c74251c9c1224dbbd376b57d81d5d180d03cb9c1
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/02/2018
ms.locfileid: "48146870"
---
# <a name="point"></a>Punkt
  In [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] räumliche Daten, eine `Point` ist ein 0-dimensionalen-Objekt, eine einzelne Position darstellt, und Z (Höhe) und M (Measure)-Werte enthalten kann.  
  
## <a name="geography-data-type"></a>geography-Datentyp  
 Der Point-Typ für den geography-Datentyp stellt einen einzelnen Ort dar, wobei *Lat* für den Breitengrad und *Long* für den Längengrad steht. Die Werte für die Breite und Länge werden in Grad gemessen. Die Werte für den Breitengrad liegen immer im Bereich [-90, 90], und eingegebene Werte, die außerhalb dieses Bereichs liegen, lösen eine Ausnahme aus. Werte für den Längengrad liegen immer im Bereich [-180, 180], und eingegebene Werte, die außerhalb dieses Bereichs liegen, werden entsprechend angepasst. Wird etwa für den Längengrad der Wert 190 eingegeben, wird dieser Wert automatisch in den Wert -170 konvertiert. *SRID* stellt die SRID (Spatial Reference ID) der **geography** -Instanz dar, die Sie zurückgeben möchten.  
  
## <a name="geometry-data-type"></a>geometry-Datentyp  
 Der Point-Typ für den geometry-Datentyp stellt einen einzelnen Ort dar, wobei *X* die X-Koordinate und *Y* die Y-Koordinate des generierten Punkts darstellt. *SRID* stellt die SRID (Spatial Reference ID) der **geometry** -Instanz dar, die Sie zurückgeben möchten.  
  
## <a name="examples"></a>Beispiele  
 Im folgenden Beispiel wird eine einfache `geometry Point`-Instanz erstellt, die den Punkt (3, 4) mit dem SRID 0 darstellt.  
  
```  
DECLARE @g geometry;  
SET @g = geometry::STGeomFromText('POINT (3 4)', 0);  
```  
  
 Im nächsten Beispiel wird eine `geometry``Point` -Instanz erstellt, die den Punkt (3, 4) mit dem Z-Wert (Höhe) 7, dem M-Wert (Maßeinheit) 2,5 und dem Standard-SRID 0 darstellt.  
  
```  
DECLARE @g geometry;  
SET @g = geometry::Parse('POINT(3 4 7 2.5)');  
```  
  
 Im abschließenden Beispiel werden die Werte X, Y, Z, und M für die `geometry``Point` -Instanz zurückgegeben.  
  
```  
SELECT @g.STX;  
SELECT @g.STY;  
SELECT @g.Z;  
SELECT @g.M;  
```  
  
 Z-Wert und M-Wert können explizit als NULL angegeben werden, wie im folgenden Beispiel gezeigt.  
  
```  
DECLARE @g geometry;  
SET @g = geometry::Parse('POINT(3 4 NULL NULL)');  
```  
  
## <a name="see-also"></a>Siehe auch  
 [MultiPoint](multipoint.md)   
 [STX &#40;geometry-Datentyp&#41;](/sql/t-sql/spatial-geometry/stx-geometry-data-type)   
 [STY &#40;geometry-Datentyp&#41;](/sql/t-sql/spatial-geometry/sty-geometry-data-type)   
 [Räumliche Daten &#40;SQL Server&#41;](spatial-data-sql-server.md)  
  
  
