---
title: RunningValue-Funktion (Berichts-Generator und SSRS) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- reporting-services-native
ms.topic: conceptual
ms.assetid: 6bee2f15-0e69-49c8-9689-b04544063b1d
author: maggiesMSFT
ms.author: maggies
manager: craigg
ms.openlocfilehash: fce2675b361b3b6d4d8ffc46afdabb0b6d128cc7
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/02/2018
ms.locfileid: "48180860"
---
# <a name="runningvalue-function-report-builder-and-ssrs"></a>RunningValue-Funktion (Berichts-Generator und SSRS)
  Gibt ein laufendes Aggregat aller numerischen Werte ungleich NULL aus dem angegebenen Ausdruck für den Kontext des angegebenen Bereichs ausgewertet zurück.  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
## <a name="syntax"></a>Syntax  
  
```  
  
RunningValue(expression, function, scope)  
```  
  
#### <a name="parameters"></a>Parameter  
 *expression*  
 Der Ausdruck, für den die Aggregation auszuführen ist, z.B. `[Quantity]`.  
  
 *Funktion*  
 (`Enum`) Der Name der Aggregatfunktion, die auf den Ausdruck, z. B. angewendet `Sum`. Diese Funktion kann nicht `RunningValue`, `RowNumber`, oder `Aggregate`.  
  
 *Bereich*  
 (`String`) Eine Zeichenfolgenkonstante als Name eines Datasets, eines Datenbereichs oder einer Gruppe oder NULL (`Nothing` in [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)]), der den Kontext angibt, in dem die Aggregation ausgewertet wird. `Nothing` Gibt an, der äußerste Kontext angegeben, normalerweise das Berichtsdataset.  
  
## <a name="return-type"></a>Rückgabetyp  
 Wird durch die im *function* -Parameter angegebene Aggregatfunktion bestimmt.  
  
## <a name="remarks"></a>Hinweise  
 Der Wert für `RunningValue` für jede neue Instanz des Bereichs auf 0 zurückgesetzt. Wenn eine Gruppe angegeben wird, wird der laufende Wert zurückgesetzt, wenn sich der Gruppenausdruck ändert. Wenn ein Datenbereich angegeben wird, wird der laufende Wert für jede neue Instanz des Datenbereichs zurückgesetzt. Wenn ein Dataset angegeben wird, wird der laufende Wert für das gesamte Dataset nicht zurückgesetzt.  
  
 `RunningValue` darf nicht in einem Filter- oder Sortierausdruck verwendet werden.  
  
 Der Datensatz, für den der ausgeführte Wert berechnet wird, muss den gleichen Datentyp aufweisen. Zum Konvertieren von Daten, die mehreren numerischen Datentypen in den gleichen Datentyp aufweist, verwenden Sie Konvertierungsfunktionen wie `CInt`, `CDbl` oder `CDec`. Weitere Informationen finden Sie unter [Funktionen für die Typkonvertierung](http://go.microsoft.com/fwlink/?LinkId=96142).  
  
 *Scope* darf kein Ausdruck sein.  
  
 Das*Expression* -Objekt kann Aufrufe von geschachtelten Aggregatfunktionen enthalten. Dabei gelten folgende Ausnahmen und Bedingungen:  
  
-   Der Bereich für geschachtelte Aggregate muss dem Bereich des äußeren Aggregats entsprechen oder darin enthalten sein. In allen eindeutigen Bereichen des Ausdrucks muss ein Bereich eine untergeordnete Beziehung zu allen anderen Bereichen haben.  
  
-   Der Bereich für geschachtelte Aggregate darf nicht der Name eines Datasets sein.  
  
-   *Ausdruck* darf keinen `First`, `Last`, `Previous`, oder `RunningValue` Funktionen.  
  
-   Das*Expression* -Objekt darf keine geschachtelten Aggregate enthalten, die ein *recursive*-Objekt angeben.  
  
 Verwenden Sie `RowNumber` zur Berechnung des laufenden Werts für die Zeilenanzahl. Weitere Informationen finden Sie unter [RowNumber-Funktion (Berichts-Generator und SSRS)](report-builder-functions-rownumber-function.md).  
  
 Weitere Informationen finden Sie in der [Aggregatfunktionsreferenz (Berichts-Generator und SSRS)](report-builder-functions-aggregate-functions-reference.md) und unter [Ausdrucksbereich für Gesamtwerte, Aggregate und integrierte Auflistungen (Berichts-Generator und SSRS)](expression-scope-for-totals-aggregates-and-built-in-collections.md).  
  
 Weitere Informationen zu rekursiven Aggregaten finden Sie unter [Creating Recursive Hierarchy Groups (Report Builder and SSRS) (Erstellen von rekursiven Hierarchiegruppen (Berichts-Generator und SSRS))](creating-recursive-hierarchy-groups-report-builder-and-ssrs.md).  
  
## <a name="examples"></a>Beispiele  
 Das folgende Codebeispiel generiert eine laufende Summe für das Feld mit dem Namen `Cost` im äußersten Bereich, den das Dataset darstellt.  
  
```  
=RunningValue(Fields!Cost.Value, Sum, Nothing)  
```  
  
 Das folgende Codebeispiel generiert eine laufende Summe für das Feld mit dem Namen `Score` im Dataset mit dem Namen `DataSet1`.  
  
```  
=RunningValue(Fields!Score.Value,sum,"DataSet1")  
```  
  
 Das folgende Codebeispiel generiert eine laufende Summe für das Feld mit dem Namen `Traffic Charges` im äußersten Bereich.  
  
```  
=RunningValue(Fields!Traffic Charges.Value, Sum, Nothing)  
```  
  
## <a name="see-also"></a>Siehe auch  
 [Ausdrucksverwendungen in Berichten &#40;Berichts-Generator und SSRS&#41;](expression-uses-in-reports-report-builder-and-ssrs.md)   
 [Beispiele für Ausdrücke &#40;Berichts-Generator und SSRS&#41;](expression-examples-report-builder-and-ssrs.md)   
 [Datentypen in Ausdrücken (Berichts-Generator und SSRS)](expressions-report-builder-and-ssrs.md)   
 [Ausdrucksbereich für Gesamtwerte, Aggregate und integrierte Auflistungen &#40;Berichts-Generator und SSRS&#41;](expression-scope-for-totals-aggregates-and-built-in-collections.md)  
  
  
