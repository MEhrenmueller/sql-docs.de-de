---
title: Verknüpfen von Tabellen über mehrere Spalten (Visual Database Tools) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
helpviewer_keywords:
- multiple column joins
- joins [SQL Server], multiple columns
ms.assetid: 56a158bc-a42a-4b78-baad-4721d2d22cd3
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: a72138ce4385734378c2e74a86d4ec08d96e25fc
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/02/2018
ms.locfileid: "48228560"
---
# <a name="join-tables-on-multiple-columns-visual-database-tools"></a>Verknüpfen von Tabellen über mehrere Spalten (Visual Database Tools)
  Sie können Tabellen über mehrere Spalten verknüpfen. Dies bedeutet, dass Sie eine Abfrage erstellen können, die Übereinstimmungen von Zeilen aus den zwei Tabellen nur herstellt, wenn diese mehrere Bedingungen erfüllen. Wenn die Datenbank eine Beziehung enthält, in der mehrere Fremdschlüsselspalten einer Tabelle einem mehrspaltigen Primärschlüssel in der anderen Tabelle entsprechen, können Sie mit dieser Beziehung ein Join über mehrere Spalten erstellen. Ausführliche Informationen finden Sie unter [Automatisches Verknüpfen von Tabellen &#40;Visual Database Tools&#41;](visual-database-tools.md).  
  
 Sie können den Join auch dann manuell erstellen, wenn die Datenbank keine mehrspaltige Fremdschlüsselbeziehung enthält.  
  
### <a name="to-manually-create-a-multicolumn-join"></a>So erstellen Sie manuell einen Join über mehrere Spalten  
  
1.  Fügen Sie dem [Diagrammbereich](diagram-pane-visual-database-tools.md) die zu verknüpfenden Tabellen hinzu.  
  
2.  Ziehen Sie den Namen der ersten Joinspalte aus dem Fenster der ersten Tabelle, und legen Sie diesen auf der entsprechenden Spalte im Fenster der zweiten Tabelle ab. Einen Join kann nicht auf der Grundlage von text-, ntext- oder image-Spalten erstellt werden.  
  
    > [!NOTE]  
    >  Im Allgemeinen müssen die Joinspalten denselben (oder einen kompatiblen) Datentyp aufweisen. Wenn z. B. die Joinspalte in der ersten Tabelle eine Datenspalte ist, müssen Sie diese mit einer Datenspalte in der zweiten Tabelle verknüpfen. Wenn es sich jedoch bei der ersten Joinspalte um eine Integer-Spalte handelt, muss die zu verknüpfende Spalte ebenfalls vom Integer-Datentyp sein, kann jedoch eine andere Größe aufweisen. In einzelnen Fällen ist ein Join scheinbar inkompatibler Spalten dank impliziter Datentypkonvertierungen jedoch möglich.  
    >   
    >  Der [Abfrage- und Sicht-Designer](query-and-view-designer-tools-visual-database-tools.md) überprüft die Datentypen der für einen Join verwendeten Spalten nicht. Wenn Sie jedoch die Abfrage ausführen, zeigt die Datenbank bei nicht kompatiblen Datentypen einen Fehler an.  
  
3.  Ziehen Sie den Namen der zweiten Joinspalte aus dem Fenster der ersten Tabelle, und legen Sie diesen auf der entsprechenden Spalte im Fenster der zweiten Tabelle ab.  
  
4.  Wiederholen Sie Schritt drei für jedes weitere Paar von Joinspalten in den beiden Tabellen.  
  
5.  Führen Sie die Abfrage aus.  
  
## <a name="see-also"></a>Siehe auch  
 [Erstellen von Abfragen mit Joins &#40;Visual Database Tools&#41;](query-with-joins-visual-database-tools.md)  
  
  
