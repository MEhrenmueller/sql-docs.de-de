---
title: Log_shipping_secondary (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- log_shipping_secondary
- log_shipping_secondary_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- log_shipping_secondary system table
ms.assetid: 69723419-4544-49c6-a517-adb30ffa5741
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: c65e57f65311a01a337594b702cc4dc19d35f321
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/01/2018
ms.locfileid: "47815170"
---
# <a name="logshippingsecondary-transact-sql"></a>log_shipping_secondary (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Speichert einen Datensatz pro sekundärer ID. Diese Tabelle wird in der **msdb** -Datenbank gespeichert.  
  
|Spaltenname|Datentyp|Description|  
|-----------------|---------------|-----------------|  
|**secondary_id**|**uniqueidentifier**|Die ID für den sekundären Server in der Protokollversandkonfiguration.|  
|**primary_server**|**sysname**|Der Name der primären Instanz der SQL Server-Datenbank-Engine in der Protokollversandkonfiguration|  
|**primary_database**|**sysname**|Der Name der primären Datenbank in der Protokollversandkonfiguration|  
|**backup_source_directory**|**nvarchar(500)**|Das Verzeichnis, in dem die Dateien der Transaktionsprotokollsicherung gespeichert werden.|  
|**backup_destination_directory**|**nvarchar(500)**|Das Verzeichnis auf dem sekundären Server, in das Sicherungsdateien kopiert werden|  
|**file_retention_period**|**int**|Gibt an, wie lange (in Minuten) eine Sicherungsdatei auf dem sekundären Server aufbewahrt wird, bevor sie gelöscht wird|  
|**copy_job_id**|**uniqueidentifier**|Die dem Kopierauftrag zugeordnete ID auf dem sekundären Server|  
|**restore_job_id**|**uniqueidentifier**|Die dem Wiederherstellungsauftrag zugeordnete ID auf dem sekundären Server|  
|**monitor_server**|**sysname**|Der Name der Instanz von der [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] als Überwachungsserver in der Protokollversandkonfiguration verwendet wird.|  
|**monitor_server_security_mode**|**bit**|Der Sicherheitsmodus, der zum Herstellen einer Verbindung mit dem Überwachungsserver verwendet wird.<br /><br /> 1 = Windows-Authentifizierung<br /><br /> 0 = [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Authentifizierung.|  
|**last_copied_file**|**nvarchar(500)**|Der Dateiname der letzten Sicherungsdatei, die auf den sekundären Server kopiert wurde.|  
|**last_copied_date**|**datetime**|Datum und Uhrzeit des letzten Kopiervorgangs auf den sekundären Server|  
  
## <a name="remarks"></a>Hinweise  
 Wenn es für eine bestimmte primäre Datenbank mehrere sekundäre Datenbanken auf demselben sekundären Server gibt, nutzen diese einige Einstellungen in der **log_shipping_secondary** -Tabelle gemeinsam. Wenn eine freigegebene Einstellung für eine der Datenbanken geändert wird, ändert sich diese Einstellung für alle Datenbanken.  
  
## <a name="see-also"></a>Siehe auch  
 [Über den Protokollversand &#40;SQLServer&#41;](../../database-engine/log-shipping/about-log-shipping-sql-server.md)   
 [Sp_add_log_shipping_secondary_database &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-add-log-shipping-secondary-database-transact-sql.md)   
 [Sp_change_log_shipping_secondary_database &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-change-log-shipping-secondary-database-transact-sql.md)   
 [Sp_delete_log_shipping_secondary_database &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-delete-log-shipping-secondary-database-transact-sql.md)   
 [sp_help_log_shipping_secondary_database &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-help-log-shipping-secondary-database-transact-sql.md)   
 [Systemtabellen &#40;Transact-SQL&#41;](../../relational-databases/system-tables/system-tables-transact-sql.md)  
  
  
