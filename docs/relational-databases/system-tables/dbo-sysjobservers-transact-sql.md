---
title: dbo.sysjobservers (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sysjobservers
- sysjobservers_TSQL
- dbo.sysjobservers
- dbo.sysjobservers_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sysjobservers system table
ms.assetid: 9abcc20f-a421-4591-affb-62674d04575e
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 635c71efaeed6d41a9b9e62ef3e8c79b4e9aae95
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/01/2018
ms.locfileid: "47607278"
---
# <a name="dbosysjobservers-transact-sql"></a>dbo.sysjobservers (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Speichert die Zuordnung oder Beziehung eines bestimmten Auftrags zu einem oder mehreren Zielservern. Diese Tabelle wird in der msdb-Datenbank gespeichert.  
  
|Spaltenname|Datentyp|Description|  
|-----------------|---------------|-----------------|  
|job_id|**uniqueidentifier**|ID des Auftrags.|  
|server_id|**int**|Server-ID.|  
|last_run_outcome|**tinyint**|Ergebnis der letzten Ausführung des Auftrags:<br /><br /> **0** = Fehler<br /><br /> **1** = Erfolg<br /><br /> **3** = "Abbrechen"|  
|Last_outcome_-Nachricht|**nvarchar(1024)**|Zugeordnete Meldung, falls vorhanden, zu der last_run_outcome-Spalte.|  
|last_run_date|**int**|Datum, an dem der Auftrag zuletzt ausgeführt wurde.|  
|last_run_time|**int**|Uhrzeit, zu der der Auftrag zuletzt ausgeführt wurde.|  
|last_run_duration|**int**|Dauer der Ausführung des Auftrags in Stunden, Minuten und Sekunden. Mithilfe der Formel berechnet: (*Stunden*\*10000) + (*Minuten*\*100) + *Sekunden*.|  
  
## <a name="see-also"></a>Siehe auch  
 [SQL Server-Agent-Tabellen &#40;Transact-SQL&#41;](../../relational-databases/system-tables/sql-server-agent-tables-transact-sql.md)  
  
  
