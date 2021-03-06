---
title: SQLValidDSN-Funktion | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLValidDSN
apilocation:
- sqlsrv32.dll
apitype: dllExport
f1_keywords:
- SQLValidDSN
helpviewer_keywords:
- SQLValidDSN [ODBC]
ms.assetid: 930d1d89-337a-4429-85a2-84ee10555ac9
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 2e376d10f21fa00c6bbe86fc692b0185f3c8d8d4
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/01/2018
ms.locfileid: "47642848"
---
# <a name="sqlvaliddsn-function"></a>SQLValidDSN-Funktion
**Übereinstimmung mit Standards**  
 Version eingeführt: ODBC 2.0  
  
 **Zusammenfassung**  
 **SQLValidDSN** überprüft die Länge und die Gültigkeit der Namen der Datenquelle, bevor der Name der Systeminformationen hinzugefügt wird.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
BOOL SQLValidDSN(  
     LPCSTR    lpszDSN);  
```  
  
## <a name="arguments"></a>Argumente  
 *lpszDSN*  
 [Eingabe] Datenquellenname, die überprüft werden.  
  
## <a name="returns"></a>Rückgabewert  
 Die Funktion gibt "true" zurück, wenn der Name der Datenquelle gültig ist. Wenn der Name der Datenquelle ungültig ist, oder der Funktionsaufruf Fehler bei zurückgegeben "false".  
  
## <a name="diagnostics"></a>Diagnose  
 Wenn **SQLValidDSN** gibt "false", ein zugeordnetes  *\*PfErrorCode* Wert abgerufen werden kann, durch den Aufruf **SQLInstallerError**. Ein  *\*PfErrorCode* wird zurückgegeben, nur wenn der Funktionsaufruf fehlschlägt, nicht wenn "false" zurückgegeben wurde, weil der Name der Datenquelle ungültig ist. Die folgende Tabelle enthält die  *\*PfErrorCode* Werte, die zurückgegeben werden können **SQLInstallerError** und jeweils im Kontext dieser Funktion erläutert.  
  
|*\*pfErrorCode*|Fehler|Description|  
|---------------------|-----------|-----------------|  
|ODBC_ERROR_GENERAL_ERR|Allgemeine Installer-Fehler|Fehler für die gab es keine bestimmte Installer-Fehlers.|  
|ODBC_ERROR_OUT_OF_MEM|Nicht genügend Arbeitsspeicher.|Das Installationsprogramm konnte die Funktion aufgrund von unzureichendem Speicher nicht ausgeführt werden.|  
  
## <a name="comments"></a>Kommentare  
 **SQLValidDSN** wird aufgerufen, von eines Treibers der [ConfigDSN](../../../odbc/reference/syntax/configdsn-function.md) um die Länge der Namen der Datenquelle und die Gültigkeit der einzelnen Zeichen im Namen Datenquelle zu überprüfen. Er überprüft, ob die Länge des Namens SQL_MAX_DSN_LENGTH, größer ist, wie in Sqlext.h definiert. (Außerdem wird die Länge der Namen der Datenquelle durch überprüft [SQLWriteDSNToIni](../../../odbc/reference/syntax/sqlwritedsntoini-function.md).) **SQLValidDSN** überprüft, ob eine der folgenden ungültigen Zeichen im Namen Datenquelle enthalten sind:  
  
 [ ] { } ( ) , ; ? * = ! \@ \  
  
## <a name="related-functions"></a>Verwandte Funktionen  
  
|Informationen zu|Finden Sie unter|  
|---------------------------|---------|  
|Hinzufügen, ändern oder Entfernen einer Datenquelle|[ConfigDSN](../../../odbc/reference/syntax/configdsn-function.md) (in der Setup-DLL)|  
|Hinzufügen, ändern oder Entfernen einer Datenquelle|[SQLConfigDataSource](../../../odbc/reference/syntax/sqlconfigdatasource-function.md)|  
|Name der Datenquelle schreiben, um die Systeminformationen|[SQLWriteDSNToIni](../../../odbc/reference/syntax/sqlwritedsntoini-function.md)|
