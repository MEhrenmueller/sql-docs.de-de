---
title: "' MSmerge_identity_range ' (Transact-SQL) | Microsoft-Dokumentation"
ms.custom: ''
ms.date: 03/04/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology:
- replication
ms.topic: language-reference
f1_keywords:
- MSmerge_identity_range_TSQL
- MSmerge_identity_range
dev_langs:
- TSQL
helpviewer_keywords:
- MSmerge_identity_range system table
ms.assetid: 493a2028-88a0-4e83-ad89-ae5661d9f477
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 623914f556064f690c0883e41316c76e84c3c7e3
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/01/2018
ms.locfileid: "47854768"
---
# <a name="msmergeidentityrange-transact-sql"></a>MSmerge_identity_range (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Die **' MSmerge_identity_range '** Tabelle wird verwendet, um die numerischen Bereiche, die Identitätsspalten zur Abonnierung von Veröffentlichungen zugewiesen nachverfolgen auf dem die Replikation automatisch diese bereichszuweisungen verwaltet wird. Diese Tabelle wird in der Veröffentlichungs- und in der Abonnementdatenbank gespeichert.  
  
|Spaltenname|Datentyp|Description|  
|-----------------|---------------|-----------------|  
|**subid**|**uniqueidentifier**|Die eindeutige ID für ein bestimmtes Abonnement.|  
|**artid**|**uniqueidentifier**|Die eindeutige ID des angegebenen Artikels.|  
|**' range_begin '**|**numeric(38)**|Der Identitätswert am Anfang des aktuellen Bereichs.|  
|**' range_end '**|**numeric(38)**|Der Identitätswert am Ende des aktuellen Bereichs.|  
|**' next_range_begin '**|**numeric(38)**|Der Identitätswert am Anfang des neuen Bereichs, der zugewiesen werden soll.|  
|**' next_range_end '**|**numeric(38)**|Der Identitätswert am Ende des neuen Bereichs, der zugewiesen werden soll.|  
|**is_pub_range**|**bit**|Der Wert **1** , wenn die Veröffentlichung der Identitätsbereich zugewiesen wird.|  
|**max_used**|**numeric(38)**|Der maximale Identitätswert, der zugewiesen werden kann.|  
  
## <a name="see-also"></a>Siehe auch  
 [Replikationstabellen &#40;Transact-SQL&#41;](../../relational-databases/system-tables/replication-tables-transact-sql.md)   
 [Replikationssichten &#40;Transact-SQL&#41;](../../relational-databases/system-views/replication-views-transact-sql.md)  
  
  
