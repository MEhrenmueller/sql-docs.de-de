---
title: SQLGetStmtAttr | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
apitype: DLLExport
helpviewer_keywords:
- SQLGetStmtAttr function
ms.assetid: e64f4f94-eb73-4477-9745-080b6cbdc751
author: MightyPen
ms.author: genemi
manager: craigg
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: f502d9e362bbc19704c69235bca1567a0b7cfdc8
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/01/2018
ms.locfileid: "47631968"
---
# <a name="sqlgetstmtattr"></a>'SQLGetStmtAttr'
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[SNAC_Deprecated](../../includes/snac-deprecated.md)]

  Die [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client ODBC-Treiber erweitert SQLGetStmtAttr um treiberspezifische Anweisungsattribute verfügbar zu machen.  
  
 [SQLSetStmtAttr](../../relational-databases/native-client-odbc-api/sqlsetstmtattr.md) listet Anweisungsattribute auf, die beide lesen und schreiben. In diesem Thema sind die schreibgeschützten Anweisungsattribute aufgeführt.  
  
## <a name="sqlsoptsscurrentcommand"></a>SQL_SOPT_SS_CURRENT_COMMAND  
 Das SQL_SOPT_SS_CURRENT_COMMAND-Attribut macht den aktuellen Befehl eines Befehlsbatches verfügbar. Zurückgegeben wird ein ganzzahliger Wert, der die Position des Befehls im Batch angibt. Der *ValuePtr* -Wert ist vom Typ SQLLEN.  
  
## <a name="sqlsoptssnocountstatus"></a>SQL_SOPT_SS_NOCOUNT_STATUS  
 Das SQL_SOPT_SS_NOCOUNT_STATUS-Attribut gibt an, die aktuelle Einstellung der NOCOUNT option steuert, ob [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] meldet die Anzahl der von einer Anweisung betroffenen Zeilen beim [SQLRowCount](../../relational-databases/native-client-odbc-api/sqlrowcount.md) aufgerufen wird. Der *ValuePtr* -Wert ist vom Typ SQLLEN.  
  
|value|Description|  
|-----------|-----------------|  
|SQL_NC_OFF|NOCOUNT ist OFF. SQLRowCount gibt die Anzahl der betroffenen Zeilen zurück.|  
|SQL_NC_ON|NOCOUNT ist ON. Die Anzahl der betroffenen Zeilen nicht durch SQLRowCount zurückgegeben, und der zurückgegebene Wert ist 0.|  
  
 Wenn SQLRowCount 0 zurückgibt, sollte die Anwendung SQL_SOPT_SS_NOCOUNT_STATUS testen. Wenn SQL_NC_ON zurückgegeben wird, der Wert 0 aus SQLRowCount nur gibt an, dass [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] wurden keine Zeilenanzahl zurückgegeben. Wird SQL_NC_OFF zurückgegeben, bedeutet dies, dass NOCOUNT deaktiviert und der Wert 0 aus SQLRowCount gibt an, dass alle Zeilen nicht in die Anweisung ausgewirkt hat.  
  
 Anwendungen sollten den Wert der SQLRowCount nicht angezeigt, wenn SQL_SOPT_SS_NOCOUNT_STATUS SQL_NC_OFF ist. Große Batches oder gespeicherte Prozeduren können mehrere SET NOCOUNT-Anweisungen enthalten. Daher kann nicht davon ausgegangen werden, dass SQL_SOPT_SS_NOCOUNT_STATUS konstant bleibt. Diese Option sollte jedes Mal getestet werden, die SQLRowCount 0 zurück.  
  
## <a name="sqlsoptssquerynotificationmsgtext"></a>SQL_SOPT_SS_QUERYNOTIFICATION_MSGTEXT  
 Das SQL_SOPT_SS_QUERYNOTIFICATION_MSGTEXT-Attribut gibt den Meldungstext für die Abfragebenachrichtigungsanforderung zurück.  
  
## <a name="sqlgetstmtattr-and-table-valued-parameters"></a>'SQLGetStmtAttr' und Tabellenwertparameter  
 SQLGetStmtAttr kann aufgerufen werden, um den Wert von SQL_SOPT_SS_PARAM_FOCUS im anwendungsparameterdeskriptor (APD) abzurufen, bei der Arbeit mit Tabellenwertparametern. Weitere Informationen zu SQL_SOPT_SS_PARAM_FOCUS finden Sie unter [SQLSetStmtAttr](../../relational-databases/native-client-odbc-api/sqlsetstmtattr.md).  
  
 Weitere Informationen zu Tabellenwertparametern finden Sie unter [Table-Valued Parameters &#40;ODBC&#41;](../../relational-databases/native-client-odbc-table-valued-parameters/table-valued-parameters-odbc.md).  
  
## <a name="see-also"></a>Siehe auch  
 [SQLSetStmtAttr-Funktion](http://go.microsoft.com/fwlink/?LinkId=59370)   
 [ODBC-API-Implementierungsdetails](../../relational-databases/native-client-odbc-api/odbc-api-implementation-details.md)  
  
  
