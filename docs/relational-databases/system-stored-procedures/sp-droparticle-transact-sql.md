---
title: Sp_droparticle (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology:
- replication
ms.topic: language-reference
f1_keywords:
- sp_droparticle_TSQL
- sp_droparticle
helpviewer_keywords:
- sp_droparticle
ms.assetid: 09fec594-53f4-48a5-8edb-c50731c7adb2
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: fee7899b0667d65ba35f3f768306d3850232e6a4
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/01/2018
ms.locfileid: "47852268"
---
# <a name="spdroparticle-transact-sql"></a>sp_droparticle (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Löscht einen Artikel aus einer Momentaufnahme- oder Transaktionsveröffentlichung. Ein Artikel kann nicht entfernt werden, solange ein Abonnement für den Artikel vorhanden ist. Diese gespeicherte Prozedur wird auf dem Verleger für die Veröffentlichungsdatenbank ausgeführt.  
  
 ![Themenlinksymbol](../../database-engine/configure-windows/media/topic-link.gif "Topic link icon") [Transact-SQL Syntax Conventions (Transact-SQL-Syntaxkonventionen)](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```  
  
sp_droparticle [ @publication= ] 'publication'  
        , [ @article= ] 'article'  
    [ , [ @ignore_distributor = ] ignore_distributor ]  
    [ , [ @force_invalidate_snapshot= ] force_invalidate_snapshot ]  
    [ , [ @publisher = ] 'publisher' ]  
    [ , [ @from_drop_publication = ] from_drop_publication ]  
```  
  
## <a name="arguments"></a>Argumente  
 [ **@publication=**] **'***publication***'**  
 Der Name der Veröffentlichung, die den zu löschenden Artikel enthält. *Veröffentlichung* ist **Sysname**, hat keinen Standardwert.  
  
 [  **@article=**] **"***Artikel***"**  
 Der Name des Artikels, der gelöscht werden soll. *Artikel* ist **Sysname**, hat keinen Standardwert.  
  
 [  **@ignore_distributor =**] *Ignore_distributor*  
 [!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]  
  
 [  **@force_invalidate_snapshot =** ] *Force_invalidate_snapshot*  
 Bestätigt, dass durch die von dieser gespeicherten Prozedur ausgeführte Aktion möglicherweise eine vorhandene Momentaufnahme ungültig wird. *Force_invalidate_snapshot* ist eine **Bit**, hat den Standardwert **0**.  
  
 **0** gibt an, dass Änderungen am Artikel bewirken nicht, die Momentaufnahme ungültig wird. Wenn die gespeicherte Prozedur erkennt, dass die Änderungen eine neue Momentaufnahme erfordern, tritt ein Fehler auf und es werden keine Änderungen vorgenommen.  
  
 **1** gibt an, dass Änderungen am Artikel kann dazu führen, dass die Momentaufnahme ungültig wird, und wenn es sind Abonnements vorhanden, die eine neue Momentaufnahme erfordern würden Berechtigung erteilt, die vorhandene Momentaufnahme als veraltet zu markieren und eine neue Momentaufnahme zu generieren.  
  
 [ **@publisher**=] **"***Verleger***"**  
 Gibt einen nicht-[!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Verleger. *Publisher* ist **Sysname**, hat den Standardwert NULL.  
  
> [!NOTE]  
>  *Publisher* sollte nicht verwendet werden, beim Ändern von Artikeleigenschaften auf einem [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Verleger.  
  
 [ **@from_drop_publication**=] *From_drop_publication*  
 [!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]  
  
## <a name="return-code-values"></a>Rückgabecodewerte  
 **0** (Erfolg) oder **1** (Fehler)  
  
## <a name="remarks"></a>Hinweise  
 **Sp_droparticle** wird bei der Momentaufnahme- und Transaktionsreplikation verwendet.  
  
 Bei horizontal gefilterten Artikeln **Sp_droparticle** überprüft die **Typ** Spalte des Artikels in der [Sysarticles &#40;Transact-SQL&#41; ](../../relational-databases/system-tables/sysarticles-transact-sql.md) Tabelle Bestimmen Sie, ob eine Sicht oder ein Filter ebenfalls gelöscht werden soll. Wenn eine Sicht oder ein Filter automatisch erzeugt wurde, wird sie bzw. er ebenfalls gelöscht. Manuell erstellte Sichten und Filter werden dagegen nicht gelöscht.  
  
 Ausführen von **Sp_droparticle** zum Löschen eines Artikels aus einer Veröffentlichung entfernt nicht das Objekt aus der Veröffentlichungsdatenbank bzw. das entsprechende Objekt aus der Abonnementdatenbank. Verwenden Sie `DROP <object>`, um diese Objekte ggf. manuell zu entfernen.  
  
## <a name="example"></a>Beispiel  
 [!code-sql[HowTo#sp_droparticle](../../relational-databases/replication/codesnippet/tsql/sp-droparticle-transact-_1.sql)]  
  
## <a name="permissions"></a>Berechtigungen  
 Nur Mitglieder der der **Sysadmin** -Serverrolle sein oder **Db_owner** feste Datenbankrolle können ausführen **Sp_droparticle**.  
  
## <a name="see-also"></a>Siehe auch  
 [Löschen eines Artikels](../../relational-databases/replication/publish/delete-an-article.md)   
 [Hinzufügen und Löschen von Artikeln aus vorhandenen Veröffentlichungen](../../relational-databases/replication/publish/add-articles-to-and-drop-articles-from-existing-publications.md)   
 [sp_addarticle &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-addarticle-transact-sql.md)   
 [sp_changearticle &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-changearticle-transact-sql.md)   
 [sp_helparticle &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-helparticle-transact-sql.md)   
 [Sp_helparticlecolumns &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-helparticlecolumns-transact-sql.md)   
 [Gespeicherte Automatisierungsprozeduren &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/replication-stored-procedures-transact-sql.md)  
  
  
