---
title: 64-Bit-ODBC-Informationen | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: ed9851ce-44ee-4c8e-b626-1d0b52da30fe
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 62497d2249131db94d2169e6138a67ee48e73a34
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/01/2018
ms.locfileid: "47677728"
---
# <a name="odbc-64-bit-information"></a>64-Bit-ODBC-Informationen
Ab Windows Server 2003, müssen Microsoft-Betriebssystemen die 64-Bit-ODBC-Bibliotheken unterstützt. Die ODBC-Header und Bibliotheken, die zuerst im Lieferumfang von MDAC 2.7 SDK enthalten Änderungen, um Programmierern, leicht Schreiben von Code für den neuen 64-Bit-Plattformen zu ermöglichen. Sicherstellen, dass Ihr Code, die ODBC verwendet-definierten Typen, die unten aufgeführten, können Sie sowohl für 64-Bit und 32-Bit-Plattformen basierend auf demselben Quellcode kompilieren der **_WIN64** oder **WIN32** Makros.  
  
 Es gibt einige Punkte zu bedenken, bei der Programmierung für eine 64-Bit-Prozessor:  
  
-   Obwohl die Größe eines Zeigers auf 8 Bytes aus 4 Bytes geändert wurde, sind ganze Zahlen und Long-Werte immer noch 4-Byte-Werte. Die Typen **INT64** und **UINT64** für 8-Byte-Ganzzahlen definiert wurden. Die neuen ODBC-Typen **SQLLEN** und **SQLULEN** werden definiert, in der ODBC-Headerdatei als **INT64** und **UINT64** beim **_WIN64**  definiert wurde.  
  
-   Mehrere Funktionen in ODBC werden deklariert, dass erwartet einen Parameter für Zeiger. In 32-Bit-ODBC die definierten Parameter wie Zeiger häufig verwendet wurden, entweder ein ganzzahliger Wert oder ein Zeiger auf einen Puffer, je nach Kontext des Aufrufs zu übergeben. Dies war natürlich möglich, Zeiger und ganze Zahlen die gleiche Größe haben. In 64-Bit-Windows ist dies nicht der Fall.  
  
-   Einige ODBC-Funktionen, die zuvor mit definierten **SQLINTEGER** und **SQLUINTEGER** gegebenenfalls für die Verwendung der neuen Parameter geändert wurden **SQLLEN** und  **SQLULEN** Typdefinitionen. Diese Änderungen werden im nächsten Abschnitt Deklaration Funktionsänderungen aufgeführt.  
  
-   Einige der deskriptorfelder, die über die verschiedenen festgelegt werden können **SQLSet** und **SQLGet** Funktionen wurden geändert, um die 64-Bit-Werte verarbeiten zu können, während andere noch 32-Bit-Werte sind. Stellen Sie sicher, dass Sie die entsprechende Größe Variable beim Festlegen und Abrufen von diese Felder verwenden. Besonderheiten, die von der, die Deskriptor Felder geändert wurden, werden unter Deklaration Funktionsänderungen aufgeführt.  
  
## <a name="function-declaration-changes"></a>Deklaration von Funktionsänderungen  
 Die folgenden Funktionssignaturen für 64-Bit-Programmierung geändert. Die Elemente in fett formatiertem Text werden die einzelnen Parameter, die unterschiedlich sind.  
  
```  
SQLBindCol (SQLHSTMT StatementHandle, SQLUSMALLINT ColumnNumber,  
   SQLSMALLINT TargetType, SQLPOINTER TargetValuePtr, SQLLEN BufferLength,   SQLLEN * StrLen_or_Ind);  
  
SQLBindParam (SQLHSTMT StatementHandle, SQLUSMALLINT ParameterNumber,  
   SQLSMALLINT ValueType, SQLSMALLINT ParameterType,   
   SQLULEN ColumnSize, SQLSMALLINT DecimalDigits,   
   SQLPOINTER ParameterValuePtr, SQLLEN *StrLen_or_Ind);  
  
SQLBindParameter (SQLHSTMT StatementHandle, SQLUSMALLINT ParameterNumber,   
   SQLSMALLINT InputOutputType, SQLSMALLINT ValueType,   
   SQLSMALLINT ParameterType, SQLULEN ColumnSize, SQLSMALLINT DecimalDigits,   
   SQLPOINTER ParameterValuePtr, SQLLEN BufferLength, SQLLEN *StrLen_or_IndPtr);  
  
SQLColAttribute (SQLHSTMT StatementHandle, SQLUSMALLINT ColumnNumber,  
    SQLUSMALLINT FieldIdentifier, SQLPOINTER CharacterAttributePtr,   
   SQLSMALLINT BufferLength, SQLSMALLINT * StringLengthPtr,   
   SQLLEN* NumericAttributePtr)  
  
SQLColAttributes (SQLHSTMT hstmt, SQLUSMALLINT icol,   
   SQLUSMALLINT fDescType, SQLPOINTER rgbDesc,   
   SQLSMALLINT cbDescMax, SQLSMALLINT *pcbDesc, SQLLEN * pfDesc);  
  
SQLDescribeCol (SQLHSTMT StatementHandle, SQLUSMALLINT ColumnNumber,   
   SQLCHAR *ColumnName, SQLSMALLINT BufferLength,   
   SQLSMALLINT *NameLengthPtr, SQLSMALLINT *DataTypePtr, SQLULEN *ColumnSizePtr,   
   SQLSMALLINT *DecimalDigitsPtr, SQLSMALLINT *NullablePtr);  
  
SQLDescribeParam (SQLHSTMT StatementHandle, SQLUSMALLINT ParameterNumber,   
   SQLSMALLINT *DataTypePtr, SQLULEN *ParameterSizePtr, SQLSMALLINT *DecimalDigitsPtr,   
   SQLSMALLINT *NullablePtr);  
  
SQLExtendedFetch(SQLHSTMT StatementHandle, SQLUSMALLINT FetchOrientation, SQLLEN FetchOffset,   
   SQLULEN * RowCountPtr, SQLUSMALLINT * RowStatusArray);  
  
SQLFetchScroll (SQLHSTMT StatementHandle, SQLSMALLINT FetchOrientation,   
   SQLLEN FetchOffset);  
  
SQLGetData (SQLHSTMT StatementHandle, SQLUSMALLINT ColumnNumber,   
   SQLSMALLINT TargetType, SQLPOINTER TargetValuePtr, SQLLEN BufferLength,    SQLLEN *StrLen_or_Ind);  
  
SQLGetDescRec (SQLHDESC DescriptorHandle, SQLSMALLINT RecNumber,   
   SQLCHAR *Name, SQLSMALLINT BufferLength,   
   SQLSMALLINT *StringLengthPtr, SQLSMALLINT *TypePtr,   
   SQLSMALLINT *SubTypePtr, SQLLEN *LengthPtr,   
   SQLSMALLINT *PrecisionPtr, SQLSMALLINT *ScalePtr,   
   SQLSMALLINT *NullablePtr);  
  
SQLParamOptions(SQLHSTMT hstmt, SQLULEN crow, SQLULEN * pirow);  
  
SQLPutData (SQLHSTMT StatementHandle, SQLPOINTER DataPtr,   
   SQLLEN StrLen_or_Ind);  
  
SQLRowCount (SQLHSTMT StatementHandle, SQLLEN* RowCountPtr);  
  
SQLSetConnectOption(SQLHDBC ConnectHandle, SQLUSMALLINT Option,   
   SQLULEN Value);  
  
SQLSetPos (SQLHSTMT StatementHandle, SQLSETPOSIROW RowNumber, SQLUSMALLINT Operation,  
   SQLUSMALLINT LockType);  
  
SQLSetParam (SQLHSTMT StatementHandle, SQLUSMALLINT ParameterNumber,   
   SQLSMALLINT ValueType, SQLSMALLINT ParameterType,   
   SQLULEN LengthPrecision, SQLSMALLINT ParameterScale,   
   SQLPOINTER ParameterValue, SQLLEN *StrLen_or_Ind);  
  
SQLSetDescRec (SQLHDESC DescriptorHandle, SQLSMALLINT RecNumber,   
   SQLSMALLINT Type, SQLSMALLINT SubType, SQLLEN Length,   
   SQLSMALLINT Precision, SQLSMALLINT Scale, SQLPOINTER DataPtr,   
   SQLLEN *StringLengthPtr, SQLLEN *IndicatorPtr);  
  
SQLSetScrollOptions (SQLHSTMT hstmt, SQLUSMALLINT fConcurrency,   
   SQLLEN crowKeyset, SQLUSMALLINT crowRowset);  
  
SQLSetStmtOption (SQLHSTMT StatementHandle, SQLUSMALLINT Option,   
   SQLULEN Value);  
```  
  
## <a name="changes-in-sql-data-types"></a>Änderungen in SQL-Datentypen  
 Die folgenden vier SQL-Typen werden weiterhin auf 32-Bit unterstützt; Sie sind nicht für 64-Bit-Compiler definiert. Diese Typen werden nicht mehr für Parameter in MDAC 2.7 verwendet. Compiler-Fehler bewirkt, Verwendung dieser Typen auf 64-Bit-Plattformen.  
  
```  
#ifdef WIN32   
typedef SQLULEN SQLROWCOUNT;   
typedef SQLULEN SQLROWSETSIZE;   
typedef SQLULEN SQLTRANSID;   
typedef SQLLEN SQLROWOFFSET;   
#endif  
```  
  
 Die Definition der SQLSETPOSIROW wurde für 32-Bit- und 64-Bit-Compiler geändert:  
  
```  
#ifdef _WIN64   
typedef UINT64 SQLSETPOSIROW;   
#else   
#define SQLSETPOSIROW SQLUSMALLINT   
#endif  
```  
  
 Die Definitionen von SQLLEN und SQLULEN erstellt wurde, wurden für 64-Bit-Compiler geändert:  
  
```  
#ifdef _WIN64   
typedef INT64 SQLLEN;   
typedef UINT64 SQLULEN;   
#else   
#define SQLLEN SQLINTEGER   
#define SQLULEN SQLUINTEGER   
#endif  
```  
  
 Dieser Wert wurde geändert, obwohl SQL_C_BOOKMARK in ODBC 3.0 für 64-Bit-Compiler auf-Clients 2.0, veraltet ist:  
  
```  
#ifdef _WIN64   
#define SQL_C_BOOKMARK SQL_C_UBIGINT   
#else   
#define SQL_C_BOOKMARK SQL_C_ULONG   
#endif  
```  
  
 Der Lesezeichen-Typ ist anders als in den neueren Headern definiert:  
  
```  
typedef SQLULEN BOOKMARK;  
```  
  
## <a name="values-returned-from-odbc-api-calls-through-pointers"></a>Werte, die von ODBC-API-Aufrufe durch Zeiger zurückgegeben werden.  
 Die folgenden ODBC-Funktionsaufrufe nutzen als Eingabeparameter einen Zeiger auf einem Puffer, in dem Daten aus dem Treiber zurückgegeben werden. Der Kontext und die Bedeutung der zurückgegebenen Daten wird durch andere Eingabeparameter für die Funktionen bestimmt. In einigen Fällen können diese Methoden jetzt 64-Bit (8-Byte-Ganzzahl)-Werte, anstatt die typischen 32-Bit (4-Byte) ganzzahligen Werte zurück. Diese Fälle sind wie folgt aus:  
  
 **SQLColAttribute**  
  
 Wenn die *FieldIdentifier* Parameter hat einen der folgenden Werte, 64-Bit-Wert wird zurückgegeben, **NumericAttribute*:  
  
 SQL_DESC_AUTO_UNIQUE_VALUE  
  
 SQL_DESC_CASE_SENSITIVE  
  
 SQL_DESC_CONCISE_TYPE  
  
 SQL_DESC_COUNT  
  
 SQL_DESC_DISPLAY_SIZE  
  
 SQL_DESC_FIXED_PREC_SCALE  
  
 SQL_DESC_LENGTH  
  
 SQL_DESC_NULLABLE  
  
 SQL_DESC_NUM_PREC_RADIX  
  
 SQL_DESC_OCTET_LENGTH  
  
 SQL_DESC_PRECISION  
  
 SQL_DESC_SCALE  
  
 SQL_DESC_SEARCHABLE  
  
 SQL_DESC_TYPE  
  
 SQL_DESC_UNNAMED  
  
 SQL_DESC_UNSIGNED  
  
 SQL_DESC_UPDATABLE  
  
 **SQLColAttributes**  
  
 Wenn die *fDescType* Parameter hat einen der folgenden Werte, 64-Bit-Wert wird zurückgegeben, **PfDesc*:  
  
 SQL_COLUMN_COUNT  
  
 SQL_COLUMN_DISPLAY_SIZE  
  
 SQL_COLUMN_LENGTH  
  
 SQL_DESC_AUTO_UNIQUE_VALUE  
  
 SQL_DESC_CASE_SENSITIVE  
  
 SQL_DESC_CONCISE_TYPE  
  
 SQL_DESC_FIXED_PREC_SCALE  
  
 SQL_DESC_SEARCHABLE  
  
 SQL_DESC_UNSIGNED  
  
 SQL_DESC_UPDATABLE  
  
 **SQLGetConnectAttr**  
  
 Wenn die *Attribut* Parameter hat einen der folgenden Werte, 64-Bit-Wert wird zurückgegeben, *Wert*:  
  
 SQL_ATTR_ASYNC_ENABLE  
  
 SQL_ATTR_ENLIST_IN_DTC  
  
 SQL_ATTR_ODBC_CURSORS  
  
 SQL_ATTR_QUIET_MODE  
  
 **SQLGetConnectOption**  
  
 Wenn die *Attribut* Parameter hat einen der folgenden Werte, 64-Bit-Wert wird zurückgegeben, *Wert*:  
  
 SQL_ATTR_QUIET_MODE  
  
 **SQLGetDescField**  
  
 Wenn die *FieldIdentifier* Parameter hat einen der folgenden Werte, 64-Bit-Wert wird zurückgegeben, **ValuePtr*:  
  
 SQL_DESC_ARRAY_SIZE  
  
 SQL_DESC_ARRAY_STATUS_PTR  
  
 SQL_DESC_BIND_OFFSET_PTR  
  
 SQL_DESC_DATA_PTR  
  
 SQL_DESC_DISPLAY_SIZE  
  
 SQL_DESC_INDICATOR_PTR  
  
 SQL_DESC_LENGTH  
  
 SQL_DESC_OCTET_LENGTH  
  
 SQL_DESC_OCTET_LENGTH_PTR  
  
 SQL_DESC_ROWS_PROCESSED_PTR  
  
 **SQLGetDiagField**  
  
 Wenn die *DiagIdentifier* Parameter hat einen der folgenden Werte, 64-Bit-Wert wird zurückgegeben, **DiagInfoPtr*:  
  
 SQL_DIAG_CURSOR_ROW_COUNT  
  
 SQL_DIAG_ROW_COUNT  
  
 SQL_DIAG_ROW_NUMBER  
  
 **SQLGetInfo**  
  
 Wenn die *Informationsart* Parameter hat einen der folgenden Werte, 64-Bit-Wert wird zurückgegeben, **InfoValuePtr*:  
  
 SQL_DRIVER_HDBC  
  
 SQL_DRIVER_HENV  
  
 SQL_DRIVER_HLIB  
  
 Wenn *Informationsart* verfügt über einen der folgenden Werte 2 **InfoValuePtr* ist 64-Bit für Eingabe und Ausgabe:  
  
 SQL_DRIVER_HDESC  
  
 SQL_DRIVER_HSTMT  
  
 **SQLGetStmtAttr**  
  
 Wenn die *Attribut* Parameter hat einen der folgenden Werte, 64-Bit-Wert wird zurückgegeben, **ValuePtr*:  
  
 SQL_ATTR_APP_PARAM_DESC  
  
 SQL_ATTR_APP_ROW_DESC  
  
 SQL_ATTR_ASYNC_ENABLE  
  
 SQL_ATTR_CONCURRENCY  
  
 SQL_ATTR_CURSOR_SCROLLABLE  
  
 SQL_ATTR_CURSOR_SENSITIVITY  
  
 SQL_ATTR_CURSOR_TYPE  
  
 SQL_ATTR_ENABLE_AUTO_IPD  
  
 SQL_ATTR_FETCH_BOOKMARK_PTR  
  
 SQL_ATTR_ROWS_FETCHED_PTR FEST  
  
 SQL_ATTR_IMP_PARAM_DESC  
  
 SQL_ATTR_IMP_ROW_DESC  
  
 SQL_ATTR_KEYSET_SIZE  
  
 SQL_ATTR_MAX_LENGTH  
  
 SQL_ATTR_MAX_ROWS  
  
 SQL_ATTR_METADATA_ID  
  
 SQL_ATTR_NOSCAN  
  
 SQL_ATTR_PARAM_BIND_OFFSET_PTR  
  
 SQL_ATTR_PARAM_BIND_TYPE  
  
 SQL_ATTR_PARAM_OPERATION_PTR  
  
 SQL_ATTR_PARAM_STATUS_PTR  
  
 SQL_ATTR_PARAMS_PROCESSED_PTR  
  
 SQL_ATTR_PARAMSET_SIZE  
  
 SQL_ATTR_QUERY_TIMEOUT  
  
 SQL_ATTR_RETRIEVE_DATA  
  
 SQL_ATTR_ROW_ARRAY_SIZE  
  
 SQL_ATTR_ROW_BIND_OFFSET_PTR  
  
 SQL_ATTR_ROW_NUMBER  
  
 SQL_ATTR_ROW_OPERATION_PTR  
  
 SQL_ATTR_ROW_STATUS_PTR  
  
 SQL_ATTR_SIMULATE_CURSOR  
  
 SQL_ATTR_USE_BOOKMARKS  
  
 **SQLGetStmtOption**  
  
 Wenn die *Option* Parameter hat einen der folgenden Werte, 64-Bit-Wert wird zurückgegeben, **Wert*:  
  
 SQL_KEYSET_SIZE  
  
 SQL_MAX_LENGTH  
  
 SQL_MAX_ROWS  
  
 SQL_ROWSET_SIZE SETZEN  
  
 **SQLSetConnectAttr**  
  
 Wenn die *Attribut* Parameter verfügt über einen der folgenden Werte, die ein 64-Bit-Wert übergeben *Wert*:  
  
 SQL_ATTR_ASYNC_ENABLE  
  
 SQL_ATTR_ENLIST_IN_DTC  
  
 SQL_ATTR_ODBC_CURSORS  
  
 SQL_ATTR_QUIET_MODE  
  
 **SQLSetConnectOption**  
  
 Wenn die *Attribut* Parameter verfügt über einen der folgenden Werte, die ein 64-Bit-Wert übergeben *Wert*:  
  
 SQL_ATTR_QUIET_MODE  
  
 **SQLSetDescField**  
  
 Wenn die *FieldIdentifier* Parameter verfügt über einen der folgenden Werte, die ein 64-Bit-Wert übergeben *ValuePtr*:  
  
 SQL_DESC_ARRAY_SIZE  
  
 SQL_DESC_ARRAY_STATUS_PTR  
  
 SQL_DESC_BIND_OFFSET_PTR  
  
 SQL_DESC_DATA_PTR  
  
 SQL_DESC_DISPLAY_SIZE  
  
 SQL_DESC_INDICATOR_PTR  
  
 SQL_DESC_LENGTH  
  
 SQL_DESC_OCTET_LENGTH  
  
 SQL_DESC_OCTET_LENGTH_PTR  
  
 SQL_DESC_ROWS_PROCESSED_PTR  
  
 **SQLSetStmtAttr**  
  
 Wenn die *Attribut* Parameter verfügt über einen der folgenden Werte, die ein 64-Bit-Wert übergeben *ValuePtr*:  
  
 SQL_ATTR_APP_PARAM_DESC  
  
 SQL_ATTR_APP_ROW_DESC  
  
 SQL_ATTR_ASYNC_ENABLE  
  
 SQL_ATTR_CONCURRENCY  
  
 SQL_ATTR_CURSOR_SCROLLABLE  
  
 SQL_ATTR_CURSOR_SENSITIVITY  
  
 SQL_ATTR_CURSOR_TYPE  
  
 SQL_ATTR_ENABLE_AUTO_IPD  
  
 SQL_ATTR_FETCH_BOOKMARK_PTR  
  
 SQL_ATTR_IMP_PARAM_DESC  
  
 SQL_ATTR_IMP_ROW_DESC  
  
 SQL_ATTR_KEYSET_SIZE  
  
 SQL_ATTR_MAX_LENGTH  
  
 SQL_ATTR_MAX_ROWS  
  
 SQL_ATTR_METADATA_ID  
  
 SQL_ATTR_NOSCAN  
  
 SQL_ATTR_PARAM_BIND_OFFSET_PTR  
  
 SQL_ATTR_PARAM_BIND_TYPE  
  
 SQL_ATTR_PARAM_OPERATION_PTR  
  
 SQL_ATTR_PARAM_STATUS_PTR  
  
 SQL_ATTR_PARAMS_PROCESSED_PTR  
  
 SQL_ATTR_PARAMSET_SIZE  
  
 SQL_ATTR_QUERY_TIMEOUT  
  
 SQL_ATTR_RETRIEVE_DATA  
  
 SQL_ATTR_ROW_ARRAY_SIZE  
  
 SQL_ATTR_ROW_BIND_OFFSET_PTR  
  
 SQL_ATTR_ROW_NUMBER  
  
 SQL_ATTR_ROW_OPERATION_PTR  
  
 SQL_ATTR_ROW_STATUS_PTR  
  
 SQL_ATTR_ROWS_FETCHED_PTR FEST  
  
 SQL_ATTR_SIMULATE_CURSOR  
  
 SQL_ATTR_USE_BOOKMARKS  
  
 **SQLSetStmtOption**  
  
 Wenn die *Option* Parameter verfügt über einen der folgenden Werte, die ein 64-Bit-Wert übergeben *Wert*:  
  
 SQL_KEYSET_SIZE  
  
 SQL_MAX_LENGTH  
  
 SQL_MAX_ROWS  
  
 SQL_ROWSET_SIZE SETZEN  
  
## <a name="see-also"></a>Siehe auch  
 [Einführung in ODBC](../../odbc/reference/introduction-to-odbc.md)
