---
title: Flatfile-Quellen-Editor (Seite Verbindungs-Manager) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.flatfilesourceadapter.connection.f1
helpviewer_keywords:
- Flat File Source Editor
ms.assetid: 2efd6baa-ed75-4f3f-b667-514024cebdb8
author: douglaslms
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 5ff623b3a360cf1a77962135fe288e03b3b83d2d
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/02/2018
ms.locfileid: "48147180"
---
# <a name="flat-file-source-editor-connection-manager-page"></a>Quellen-Editor für Flatfiles (Seite Verbindungs-Manager)
  Wählen Sie auf der Seite **Verbindungs-Manager** des Dialogfelds **Quellen-Editor für Flatfiles** den Verbindungs-Manager aus, den die Flatfilequelle verwenden soll. Die Flatfilequelle liest die Daten aus einer Textdatei, die in den Formaten mit Trennzeichen, fester Breite oder mit gemischten Inhalten vorliegen kann.  
  
 Eine Flatfilequelle kann einen der folgenden Typen von Verbindungs-Manager verwenden:  
  
-   Einen Verbindungs-Manager für Flatfiles, wenn es sich bei der Quelle um eine einzelne Flatfile handelt. Weitere Informationen finden Sie unter [Flat File Connection Manager](connection-manager/file-connection-manager.md).  
  
-   Einen Verbindungs-Manager für mehrere Flatfiles, wenn es bei der Quelle um mehrere Flatfiles handelt und der Datenflusstask sich in einem Schleifencontainer wie dem For-Schleifencontainer befindet. In jeder Schleife des Containers werden von der Flatfilequelle Daten vom nächsten Dateinamen geladen, der vom Verbindungs-Manager für mehrere Flatfiles bereitgestellt wird. Weitere Informationen finden Sie unter [Multiple Flat Files Connection Manager](connection-manager/multiple-flat-files-connection-manager.md).  
  
 Weitere Informationen zur Flatfilequelle finden Sie unter [Flat File Source](data-flow/flat-file-source.md).  
  
## <a name="options"></a>Tastatur  
 **Flat file connection manager**  
 Wählen Sie einen vorhandenen Verbindungs-Manager aus der Liste aus, oder erstellen Sie einen neuen Verbindungs-Manager, indem Sie auf **Neu**klicken.  
  
 **Neu**  
 Erstellen Sie mithilfe des Dialogfelds **Verbindungs-Manager-Editor für Flatfiles** einen neuen Verbindungs-Manager.  
  
 **NULL-Werte aus der Quelle als NULL-Werte im Datenfluss beibehalten**  
 Geben Sie an, ob NULL-Werte erhalten werden, wenn Daten extrahiert werden. Der Standardwert dieser Eigenschaft ist **false**. Wenn dieser Wert f`alse` ist, ersetzt die Flatfilequelle die NULL-Werte aus den Quelldaten mit entsprechenden Standardwerten für jede Spalte, z. B. mit leeren Zeichenfolgen in Zeichenfolgenspalten und Nullen in numerischen Spalten.  
  
 **Vorschau**  
 Zeigen Sie mithilfe des Dialogfelds **Datenansicht** eine Vorschau der Ergebnisse an. In der Vorschau können bis zu 200 Zeilen angezeigt werden.  
  
## <a name="see-also"></a>Siehe auch  
 [Erstellen und Meldungsreferenz von Integration Services-Fehler](../../2014/integration-services/integration-services-error-and-message-reference.md)   
 [Quellen-Editor für Flatfiles &#40;Seite "Spalten"&#41;](../../2014/integration-services/flat-file-source-editor-columns-page.md)   
 [Quellen-Editor für Flatfiles &#40;Seite "Fehlerausgabe"&#41;](../../2014/integration-services/flat-file-source-editor-error-output-page.md)   
 [Verbindungs-Manager für Flatfiles](connection-manager/file-connection-manager.md)  
  
  
