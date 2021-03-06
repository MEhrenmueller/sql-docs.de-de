---
title: ROUND (SSIS-Ausdruck) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- integration-services
ms.topic: conceptual
helpviewer_keywords:
- rounding expressions
- ROUND function [SSIS]
ms.assetid: 376f1947-4fc5-4611-ad86-823e4db1b468
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 950d2c8aa3bd67327eb184017a71bc3851cb2abf
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/02/2018
ms.locfileid: "48212260"
---
# <a name="round-ssis-expression"></a>ROUND (SSIS-Ausdruck)
  Gibt einen numerischen Ausdruck zurück, der auf die angegebene Länge oder Genauigkeit gerundet wurde. Der length-Parameter muss zu einer ganzen Zahl ausgewertet werden.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
ROUND(numeric_expression,length)  
```  
  
## <a name="arguments"></a>Argumente  
 *numeric_expression*  
 Ein Ausdruck eines gültigen numerischen Datentyps. Weitere Informationen finden Sie unter [Integration Services Datentypen](../data-flow/integration-services-data-types.md).  
  
 *length*  
 Ein ganzzahliger Ausdruck. Dies ist die Genauigkeit, auf die *numeric_expression* gerundet wird.  
  
## <a name="result-types"></a>Ergebnistypen  
 Der Typ entspricht dem Typ von *numeric*_*expression*.  
  
## <a name="remarks"></a>Hinweise  
 Das *length* -Argument muss zu einer positiven ganzen Zahl oder 0 (null) ausgewertet werden.  
  
 ROUND gibt ein NULL-Ergebnis zurück, wenn das Argument NULL ist.  
  
## <a name="expression-examples"></a>Beispiele für Ausdrücke  
 Diese Beispiele runden numerische Literale auf eine Länge von drei. Als erstes Ergebnis wird 137.1570 zurückgegeben und als zweites Ergebnis 137.1580.  
  
```  
ROUND(137.1574,3)  
ROUND(137.1575,3)  
```  
  
## <a name="see-also"></a>Siehe auch  
 [Funktionen &#40;SSIS-Ausdruck&#41;](functions-ssis-expression.md)  
  
  
