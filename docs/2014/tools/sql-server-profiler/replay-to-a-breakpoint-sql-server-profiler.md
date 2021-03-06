---
title: Wiedergabe bis zu einem Breakpoint (SQL Server Profiler) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- database-engine
ms.topic: conceptual
helpviewer_keywords:
- breakpoints [SQL Server]
- traces [SQL Server], replaying
ms.assetid: 3caf751e-df3b-40c7-b5e8-4490ae178e0c
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: d40fd8e92eb7c3453c700eb2ae7f2a45ea6c0b41
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/02/2018
ms.locfileid: "48166410"
---
# <a name="replay-to-a-breakpoint-sql-server-profiler"></a>Wiedergeben bis zu einem Breakpoint (SQL Server Profiler)
  In diesem Thema wird das Festlegen von Breakpoints in einer Ablaufverfolgungsdatei oder -tabelle beschrieben, die Sie mit [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)]wiedergeben möchten. Durch das Festlegen von Breakpoints in einer Ablaufverfolgungsdatei oder in einer Tabelle können Sie die Wiedergabe der Ablaufverfolgung bei speziellen Ereignissen anhalten. Die Verwendung von Breakpoints bei der Wiedergabe einer Ablaufverfolgung unterstützt das Debuggen, da Sie die Wiedergabe langer Ablaufverfolgungsskripts in kurze Segmente unterteilen und sie jeweils inkrementell analysieren können.  
  
### <a name="to-replay-to-a-breakpoint"></a>So geben Sie bis zu einem Breakpoint wieder  
  
1.  Öffnen Sie die Ablaufverfolgungsdatei oder -tabelle, die Sie wiedergeben möchten. Weitere Informationen finden Sie unter [Öffnen einer Ablaufverfolgungsdatei &#40;SQL Server Profiler&#41;](open-a-trace-file-sql-server-profiler.md) oder unter [Öffnen einer Ablaufverfolgungstabelle &#40;SQL Server Profiler&#41;](open-a-trace-table-sql-server-profiler.md).  
  
     Stellen Sie sicher, dass die geöffnete Ablaufverfolgungsdatei oder -tabelle die Ereignisklassen enthält, die für die Wiedergabe erforderlich sind. Weitere Informationen finden Sie unter [Replay Requirements](replay-requirements.md).  
  
2.  Klicken Sie im Ablaufverfolgungsfenster auf ein Ereignis, das Sie als Breakpoint verwenden möchten. Wenden Sie zum Festlegen eines Breakpoints eine der drei folgenden Methoden an:  
  
    -   Drücken Sie F9.  
  
    -   Klicken Sie im Menü **Wiedergeben** auf **Breakpoint ein/aus**  
  
    -   Klicken Sie mit der rechten Maustaste auf das Ereignis, und klicken Sie anschließend auf **Breakpoint ein/aus**.  
  
     Neben dem ausgewählten Ablaufverfolgungsereignis wird ein rotes Aufzählungszeichen angezeigt, mit dem das Ereignis als Breakpoint in der Ablaufverfolgung gekennzeichnet wird.  
  
     Wiederholen Sie diesen Schritt, um mehrere Breakpoints festzulegen.  
  
3.  Klicken Sie im Menü **Wiedergeben** auf **Starten**, und stellen Sie dann eine Verbindung mit dem Server her, auf dem die Ablaufverfolgung wiedergegeben werden soll.  
  
4.  Überprüfen Sie im Dialogfeld **Wiedergabekonfiguration** die Einstellungen, und klicken Sie dann auf **OK**.  
  
     Die Wiedergabe wird gestartet und hält an, wenn ein Breakpoint erreicht wird.  
  
5.  Drücken Sie F5, um die Wiedergabe fortzusetzen, und zum nächsten Breakpoint überzugehen.  
  
6.  Wiederholen Sie Schritt 5 bis zum Ende der Ablaufverfolgung.  
  
## <a name="see-also"></a>Siehe auch  
 [Wiedergeben bis zu einem Cursor &#40;SQL Server Profiler&#41;](replay-to-a-cursor-sql-server-profiler.md)   
 [Wiedergeben von Ablaufverfolgungen](replay-traces.md)   
 [SQL Server Profiler](sql-server-profiler.md)  
  
  
