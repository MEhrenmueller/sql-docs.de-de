---
title: Sys. dm_fts_semantic_similarity_population (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- dm_fts_semantic_similarity_population_TSQL
- sys.dm_fts_semantic_similarity_population
- dm_fts_semantic_similarity_population
- sys.dm_fts_semantic_similarity_population_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sys.dm_fts_semantic_similarity_population dynamic management view
ms.assetid: 33666f28-c370-47e2-a932-190316ed5f69
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: d65ba08739cde5dede23745c1a891246a6194360
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/01/2018
ms.locfileid: "47644238"
---
# <a name="sysdmftssemanticsimilaritypopulation-transact-sql"></a>sys.dm_fts_semantic_similarity_population (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Gibt eine Zeile mit Statusinformationen über die Auffüllung des Dokumentähnlichkeitsindex für jeden Ähnlichkeitsindex in jeder Tabelle zurück, der ein semantischer Index zugeordnet ist.  
  
 Der Auffüllungsschritt wird nach dem Extraktionsschritt ausgeführt. Statusinformationen zu dem Ähnlichkeit extraktionsschritt ausgeführt, finden Sie unter [Sys. dm_fts_index_population &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-fts-index-population-transact-sql.md).  
    
||||  
|-|-|-|  
|**Spaltenname**|**Typ**|**Beschreibung**|  
|**database_id**|**int**|ID der Datenbank, die den aufzufüllenden Volltextindex enthält.|  
|**catalog_id**|**int**|ID des Volltextkatalogs, in dem dieser Volltextindex enthalten ist.|  
|**table_id**|**int**|ID der Tabelle, für die der Volltextindex aufgefüllt wird.|  
|**document_count**|**int**|Gesamtzahl der Dokumente in der Auffüllung|  
|**document_processed_count**|**int**|Anzahl der Dokumente, die seit dem Start dieses Auffüllungszyklus verarbeitet wurden|  
|**completion_type**|**int**|Status des Abschlusses dieser Auffüllung.|  
|**completion_type_description**|**nvarchar(120)**|Beschreibung des Abschlusstyps.|  
|**worker_count**|**int**|Anzahl der Arbeitsthreads, die der Ähnlichkeitsextraktion zugeordnet sind|  
|**status**|**int**|Status dieser Auffüllung. Hinweis: Einige Status sind vorübergehend. Einer der folgenden Typen:<br /><br /> 3 = Wird gestartet<br /><br /> 5 = Normal verarbeiten<br /><br /> 7 = Verarbeitung wurde angehalten<br /><br /> 11 = Auffüllen abgebrochen|  
|**status_description**|**nvarchar(120)**|Beschreibung des Status der Auffüllung.|  
|**start_time**|**datetime**|Zeit des Starts der Auffüllung.|  
|**incremental_timestamp**|**timestamp**|Stellt den Timestamp des Starts einer vollständigen Auffüllung dar. Für alle anderen Auffüllungstypen ist dieser Wert der letzte Prüfpunkt, für den ein Commit ausgeführt wurde, der den Fortschritt der Auffüllung darstellt.|  
  
## <a name="general-remarks"></a>Allgemeine Hinweise  
 Weitere Informationen finden Sie unter [verwalten und Überwachen der semantischen Suche](../../relational-databases/search/manage-and-monitor-semantic-search.md).  
  
## <a name="metadata"></a>Metadaten  
 Weitere Informationen über den Status der semantischen Indizierung, Abfrage [Sys. dm_fts_index_population &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-fts-index-population-transact-sql.md).  
  
## <a name="security"></a>Security  
  
### <a name="permissions"></a>Berechtigungen  
 Erfordert die VIEW SERVER STATE-Berechtigung auf dem Server.  
  
## <a name="examples"></a>Beispiele  
 Im folgenden Beispiel wird gezeigt, wie der Status der Auffüllungen des Dokumentähnlichkeitsindex für alle Tabellen, denen ein semantischer Index zugeordnet ist, abgefragt wird.  
  
```  
SELECT * FROM sys.dm_fts_semantic_similarity_population;  
GO  
```  
  
## <a name="see-also"></a>Siehe auch  
 [Verwalten und Überwachen der semantischen Suche](../../relational-databases/search/manage-and-monitor-semantic-search.md)  
  
  
