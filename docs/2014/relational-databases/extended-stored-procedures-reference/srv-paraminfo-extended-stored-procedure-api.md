---
title: srv_paraminfo (API für erweiterte gespeicherte Prozeduren) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/08/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- database-engine
- docset-sql-devref
ms.topic: reference
api_name:
- srv_paraminfo
api_location:
- opends60.dll
topic_type:
- apiref
dev_langs:
- C++
helpviewer_keywords:
- srv_paraminfo
ms.assetid: ee2afd4e-0d91-462b-9403-98d481546330
author: rothja
ms.author: jroth
manager: craigg
ms.openlocfilehash: 2e017d225dd4f4a0d46c4b0bc6f3cb064eb75bd4
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/02/2018
ms.locfileid: "48158270"
---
# <a name="srvparaminfo-extended-stored-procedure-api"></a>srv_paraminfo (API für erweiterte gespeicherte Prozeduren)
    
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureDontUse](../../includes/ssnotedepfuturedontuse-md.md)] Verwenden Sie stattdessen die CLR-Integration.  
  
 Gibt Informationen zu einem Parameter zurück. Diese Funktion ersetzt folgende Funktionen: [srv_paramtype](srv-paramtype-extended-stored-procedure-api.md), [srv_paramlen](srv-paramlen-extended-stored-procedure-api.md), [srv_parammaxlen](srv-parammaxlen-extended-stored-procedure-api.md) und [srv_paramdata](srv-paramdata-extended-stored-procedure-api.md). **srv_paraminfo** unterstützt die Datentypen unter [Datentypen](data-types-extended-stored-procedure-api.md) und Daten der Länge 0 (null).  
  
## <a name="syntax"></a>Syntax  
  
```  
  
int srv_paraminfo (  
SRV_PROC *  
srvproc  
,  
int  
n  
,  
BYTE *  
pbType  
,  
ULONG *  
pcbMaxLen  
,  
ULONG *  
pcbActualLen  
,  
BYTE *  
pbData  
,  
BOOL *  
pfNull  
);  
  
```  
  
## <a name="arguments"></a>Argumente  
 *srvproc*   
 Ein Handle für eine Clientverbindung.  
  
 *n*  
 Die Ordnungszahl des festzulegenden Parameters. Der erste Parameter ist 1.  
  
 *pbType*  
 Der Datentyp des Parameters.  
  
 *pcbMaxLen*  
 Zeiger auf die maximale Länge des Parameters.  
  
 *pcbActualLen*  
 Zeiger auf die tatsächliche Länge des Parameters. Der Wert 0 (\**pcbActualLen* == 0) gibt Daten der Länge 0 (null) an, wenn **pfNull* auf FALSE festgelegt ist.  
  
 *pbData*  
 Zeiger auf den Puffer für Parameterdaten. Wenn *pbData* nicht NULL ist, schreibt die API für erweiterte gespeicherte Prozeduren \**pcbActualLen*-Datenbytes in \**pbData*. Wenn *pbData* NULL ist, werden keine Daten in \**pbData* geschrieben, die Funktion gibt jedoch \**pbType*, \**pcbMaxLen*, \**pcbActualLen*, und **pfNull* zurück. Der Arbeitsspeicher für diesen Puffer muss von der Anwendung verwaltet werden.  
  
 *pfNull*  
 Zeiger auf ein NULL-Flag. **pfNull* ist auf TRUE festgelegt, wenn der Wert des Parameters NULL ist.  
  
## <a name="returns"></a>Rückgabewert  
 Wenn die Parameterinformationen erfolgreich abgerufen wurden, wird SUCCEED zurückgegeben, andernfalls FAIL. Es wird FAIL zurückgegeben, wenn keine aktuelle remote gespeicherte Prozedur vorhanden ist und wenn kein remote gespeicherter *n*-Prozedurparameter vorhanden ist.  
  
## <a name="remarks"></a>Hinweise  
 **Sicherheitshinweis** Sie sollten den Quellcode der erweiterten gespeicherten Prozeduren gründlich überprüfen. Außerdem sollten Sie die kompilierten DLLs vor der Installation auf einem Produktionsserver testen. Weitere Informationen zum Überprüfen und Testen der Sicherheit finden Sie auf dieser [Microsoft-Website](http://go.microsoft.com/fwlink/?LinkID=54761&amp;clcid=0x409http://msdn.microsoft.com/security/).  
  
## <a name="see-also"></a>Siehe auch  
 [Programmierreferenz für erweiterte gespeicherte Prozeduren](database-engine-extended-stored-procedures-reference.md)  
  
  
