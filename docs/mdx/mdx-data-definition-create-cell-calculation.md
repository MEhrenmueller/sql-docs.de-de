---
title: Erstellen von CELL CALCULATION-Anweisung (MDX) | Microsoft Docs
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 7e69aa9e3da29abe054aaf272c5fe3ed12172a4d
ms.sourcegitcommit: 97bef3f248abce57422f15530c1685f91392b494
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/04/2018
ms.locfileid: "34741299"
---
# <a name="mdx-data-definition---create-cell-calculation"></a>MDX-Datendefinition - CELL CALCULATION erstellen


  Erstellt eine Berechnung, die einen MDX-Ausdruck (Multidimensional Expressions) für eine angegebene Tupelmenge in einem Cube auswertet.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
[WITH <CELL CALCULATION clause> Calculation_Name  
   [,WITH <CELL CALCULATION clause> Calculation_Name...n]  
CREATE CELL CALCULATION CURRENTCUBE | Cube_Name.Calculation_Name   
  
<CELL CALCULATION clause> ::=  
   FOR Set_Expression AS 'MDX_Expression'   
      [ [ CONDITION = 'Logical_Expression' ]   
    | [ DISABLED = { TRUE | FALSE } ]   
    | [ DESCRIPTION =String ]   
    | [ CALCULATION_PASS_NUMBER = Integer]   
    | [ CALCULATION_PASS_DEPTH = Integer]   
    | [ SOLVE_ORDER = Integer]   
    | [ Calculation_Name= Scalar_Expression ], ...n]  
```  
  
## <a name="arguments"></a>Argumente  
 *Cube_Name*  
 Eine gültige Zeichenfolge, die einen Cubenamen bereitstellt.  
  
 *Calculation_Name*  
 Eine gültige Zeichenfolge, die den Namen einer Zellenberechnung bereitstellt.  
  
 *Set_Expression*  
 Ein gültiger MDX-Ausdruck, der eine Menge zurückgibt.  
  
 *String*  
 Ein gültiger Zeichenfolgenwert.  
  
 *MDX_Expression*  
 Ein gültiger MDX-Ausdruck.  
  
 *Logical_Expression*  
 Ein gültiger logischer MDX-Ausdruck.  
  
 *Integer*  
 Ein gültiger ganzzahliger Wert.  
  
 *Calculation_Name*  
 Eine gültige Zeichenfolge, die den Namen der Zellenberechnungseigenschaft bereitstellt.  
  
 *"Scalar_expression"*  
 Ein gültiger skalarer MDX-Ausdruck.  
  
## <a name="remarks"></a>Hinweise  
 Mithilfe berechneter Zellen kann die Clientanwendung einen Rollupwert für eine bestimmte Menge von Zellen angeben, statt für eine ganze Menge von Zellen, wie bei einer benutzerdefinierten Rollupformel oder einem berechneten Element. So kann beispielsweise angegeben werden, dass jede Zelle in der durch `{[Canada],[Time].[2000]}` definierten Menge einen Wert enthalten kann, der durch eine Formel definiert ist. Alle anderen Zellen, die nicht in dieser Menge enthalten sind, werden normal berechnet.  
  
> [!NOTE]  
>  Die Backus-Naur-Form (BNF) von `{*(<comment> | <whitespace> | <newline>)}` wird aus Gründen der Abwärtskompatibilität als `{*}` analysiert.  
  
## <a name="see-also"></a>Siehe auch  
 [Erstellen berechneter Zellen im Bereich einer Sitzung](../analysis-services/multidimensional-models/mdx/mdx-cell-calculations-session-scoped-calculated-cells.md)   
 [Erstellen von Zellenberechnungen im Bereich einer Abfrage &#40;MDX&#41;](../analysis-services/multidimensional-models/mdx/mdx-cell-calculations-query-scoped-cell-calculations.md)   
 [Erstellen von Zellenberechnungen in MDX &#40;MDX&#41;](../analysis-services/multidimensional-models/mdx/mdx-cell-calculations-build-cell-calculations.md)   
 [Verwenden von Zelleneigenschaften &#40;MDX&#41;](../analysis-services/multidimensional-models/mdx/mdx-cell-properties-using-cell-properties.md)   
 [FORMAT_STRING-Inhalt &#40;MDX&#41;](../analysis-services/multidimensional-models/mdx/mdx-cell-properties-format-string-contents.md)   
 [FORE_COLOR- und BACK_COLOR-Inhalte &#40;MDX&#41;](../analysis-services/multidimensional-models/mdx/mdx-cell-properties-fore-color-and-back-color-contents.md)   
 [MDX-Datendefinitionsanweisungen &#40;MDX&#41;](../mdx/mdx-data-definition-statements-mdx.md)  
  
  
