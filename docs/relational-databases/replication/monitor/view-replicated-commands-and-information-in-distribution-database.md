---
title: Anzeigen replizierter Befehle und Informationen in der Verteilungsdatenbank | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/09/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
dev_langs:
- TSQL
helpviewer_keywords:
- sp_browsereplcmds
- transactional replication, monitoring
- distribution databases [SQL Server replication], viewing replicated commands
- viewing replicated commands
ms.assetid: 9c20acec-8fab-4483-b9c1-dfe3768f85dd
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: d332096aee2c38f2cd16c4fa90296ef80b2b15e0
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/01/2018
ms.locfileid: "47701148"
---
# <a name="view-replicated-commands-and-information-in-distribution-database"></a>Anzeigen replizierter Befehle und Informationen in der Verteilungsdatenbank
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  Bei Verwendung der Transaktionsreplikation werden Transaktionsbefehle in der Verteilungsdatenbank gespeichert, bis sie vom Verteilungs-Agent an alle Abonnenten weitergegeben oder bis die Änderungen von einem Verteilungs-Agent abgerufen werden. Diese ausstehenden Befehle in der Verteilungsdatenbank können programmgesteuert mit gespeicherten Replikationsprozeduren angezeigt werden. Weitere Informationen finden Sie unter [Gespeicherte Replikationsprozeduren &#40;Transact-SQL&#41;](../../../relational-databases/system-stored-procedures/replication-stored-procedures-transact-sql.md).  
  
### <a name="to-view-replicated-commands-from-all-transactional-publications-in-the-distribution-database"></a>So zeigen Sie replizierte Befehle für alle Transaktionsveröffentlichungen in der Verteilungsdatenbank an  
  
1.  Führen Sie auf dem Verteiler für die Verteilungsdatenbank [sp_browsereplcmds](../../../relational-databases/system-stored-procedures/sp-browsereplcmds-transact-sql.md)aus.  
  
### <a name="to-view-replicated-commands-in-the-distribution-database-from-a-specific-article-or-from-a-specific-database-published-using-transactional-replication"></a>So zeigen Sie replizierte Befehle in der Verteilungsdatenbank für einen bestimmten Artikel oder für eine bestimmte Datenbank an, der bzw. die mithilfe der Transaktionsreplikation veröffentlicht wurde  
  
1.  (Optional) Führen Sie auf dem Verleger für die Veröffentlichungsdatenbank [sp_helparticle](../../../relational-databases/system-stored-procedures/sp-helparticle-transact-sql.md)aus. Geben Sie **@publication** und **@article**. Beachten Sie den Wert von **article id** im Resultset.  
  
2.  Führen Sie auf dem Verteiler für die Verteilungsdatenbank [sp_browsereplcmds](../../../relational-databases/system-stored-procedures/sp-browsereplcmds-transact-sql.md)aus. (Optional) Geben Sie die Artikel-ID aus Schritt 2 für **@article_id**. (Optional) Geben Sie die ID der Veröffentlichungsdatenbank für **@publisher_database_id**an, die aus der **database_id** -Spalte in der [sys.databases](../../../relational-databases/system-catalog-views/sys-databases-transact-sql.md) -Katalogsicht abgerufen werden kann.  
  
## <a name="see-also"></a>Weitere Informationen finden Sie unter  
 [Programmgesteuertes Überwachen der Replikation](../../../relational-databases/replication/monitor/programmatically-monitor-replication.md)  
  
  
