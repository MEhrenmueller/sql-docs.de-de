---
title: 'Gewusst wie: Abrufen von Eingabe-/Ausgabeparametern mit dem SQLSRV-Treiber | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 04/11/2018
ms.prod: sql
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- stored procedure support
ms.assetid: 1157bab7-6ad1-4bdb-a81c-662eea3e7fcd
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 969de4ba4e28398c540636e8f3c6f6649c0dcb30
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MTE75
ms.contentlocale: de-DE
ms.lasthandoff: 10/01/2018
ms.locfileid: "47700458"
---
# <a name="how-to-retrieve-output-parameters-using-the-sqlsrv-driver"></a>Vorgehensweise: Abrufen von Eingabe-/Ausgabeparametern mit dem SQLSRV-Treiber
[!INCLUDE[Driver_PHP_Download](../../includes/driver_php_download.md)]

In diesem Thema wird veranschaulicht, wie eine gespeicherten Prozedur aufgerufen wird, in der ein Parameter als Ausgabeparameter definiert wurde. Beim Abrufen eines Ausgabe- oder Eingabe-/Ausgabeparameters müssen alle von der gespeicherten Prozedur zurückgegebenen Ergebnisse verarbeitet werden, bevor auf den Wert des zurückgegebenen Parameters zugegriffen werden kann.  
  
> [!NOTE]  
> Variablen, die auf **NULL**, **DateTime**oder Streamtypen aktualisiert oder initialisiert werden, können nicht als Ausgabeparameter verwendet werden.  
  
Es kann vorkommen, dass Daten abgeschnitten werden, wenn Streamtypen wie z. B. SQLSRV_SQLTYPE_VARCHAR('max') als Ausgabeparameter verwendet werden. Streamtypen werden nicht als Ausgabeparameter unterstützt. Bei nicht-Streamtypen kann es vorkommen, dass Daten abgeschnitten werden, wenn die Länge der Ausgabeparameter nicht angegeben wird oder wenn die angegebene Länge nicht groß genug für den Ausgabeparameter ist.  
  
## <a name="example-1"></a>Beispiel 1
Das folgende Beispiel ruft eine gespeicherte Prozedur auf, die die Jahr-bis-heute-Verkäufe eines bestimmten Mitarbeiters zurückgibt. Die PHP-Variable *$lastName* ist ein Eingabeparameter und *$salesYTD* ist ein Ausgabeparameter.  
  
> [!NOTE]  
> Initialisieren von *$salesYTD* auf 0.0 setzt den zurückgegebenen PHPTYPE auf **float**zurück. Um Datentypintegrität sicherzustellen, sollten Ausgabeparameter vor dem Aufruf der gespeicherten Prozedur initialisiert werden, oder der gewünschte PHPTYPE angegeben werden. Informationen zum Angeben des PHPTYPE finden Sie unter [How to: Specify PHP Data Types](../../connect/php/how-to-specify-php-data-types.md).  
  
Da nur ein Ergebnis von der gespeicherten Prozedur zurückgegeben wird, enthält *$salesYTD* sofort den zurückgegebenen Wert des Ausgabeparameters, nachdem die gespeicherte Prozedur ausgeführt wurde.  
  
> [!NOTE]  
> Die Verwendung kanonischer Syntax stellt die empfohlene Vorgehensweise für das Abrufen gespeicherter Prozeduren dar. Weitere Informationen zur kanonischen Syntax finden Sie unter [Aufrufen einer gespeicherten Prozedur](../../relational-databases/native-client-odbc-stored-procedures/calling-a-stored-procedure.md).  
  
Das Beispiel setzt voraus, dass SQL Server und die [AdventureWorks](https://github.com/Microsoft/sql-server-samples/tree/master/samples/databases/adventure-works) -Datenbank auf dem lokalen Computer installiert sind. Wenn das Beispiel über die Befehlszeile ausgeführt wird, werden alle Ausgaben in die Konsole geschrieben.  
  
```  
<?php  
/* Connect to the local server using Windows Authentication and   
specify the AdventureWorks database as the database in use. */  
$serverName = "(local)";  
$connectionInfo = array( "Database"=>"AdventureWorks");  
$conn = sqlsrv_connect( $serverName, $connectionInfo);  
if( $conn === false )  
{  
     echo "Could not connect.\n";  
     die( print_r( sqlsrv_errors(), true));  
}  
  
/* Drop the stored procedure if it already exists. */  
$tsql_dropSP = "IF OBJECT_ID('GetEmployeeSalesYTD', 'P') IS NOT NULL  
                DROP PROCEDURE GetEmployeeSalesYTD";  
$stmt1 = sqlsrv_query( $conn, $tsql_dropSP);  
if( $stmt1 === false )  
{  
     echo "Error in executing statement 1.\n";  
     die( print_r( sqlsrv_errors(), true));  
}  
  
/* Create the stored procedure. */  
$tsql_createSP = " CREATE PROCEDURE GetEmployeeSalesYTD  
                   @SalesPerson nvarchar(50),  
                   @SalesYTD money OUTPUT  
                   AS  
                   SELECT @SalesYTD = SalesYTD  
                   FROM Sales.SalesPerson AS sp  
                   JOIN HumanResources.vEmployee AS e   
                   ON e.EmployeeID = sp.SalesPersonID  
                   WHERE LastName = @SalesPerson";  
$stmt2 = sqlsrv_query( $conn, $tsql_createSP);  
if( $stmt2 === false )  
{  
     echo "Error in executing statement 2.\n";  
     die( print_r( sqlsrv_errors(), true));  
}  
  
/*--------- The next few steps call the stored procedure. ---------*/  
  
/* Define the Transact-SQL query. Use question marks (?) in place of  
 the parameters to be passed to the stored procedure */  
$tsql_callSP = "{call GetEmployeeSalesYTD( ?, ? )}";  
  
/* Define the parameter array. By default, the first parameter is an  
INPUT parameter. The second parameter is specified as an OUTPUT  
parameter. Initializing $salesYTD to 0.0 sets the returned PHPTYPE to  
float. To ensure data type integrity, output parameters should be  
initialized before calling the stored procedure, or the desired  
PHPTYPE should be specified in the $params array.*/  
$lastName = "Blythe";  
$salesYTD = 0.0;  
$params = array(   
                 array($lastName, SQLSRV_PARAM_IN),  
                 array(&$salesYTD, SQLSRV_PARAM_OUT)  
               );  
  
/* Execute the query. */  
$stmt3 = sqlsrv_query( $conn, $tsql_callSP, $params);  
if( $stmt3 === false )  
{  
     echo "Error in executing statement 3.\n";  
     die( print_r( sqlsrv_errors(), true));  
}  
  
/* Display the value of the output parameter $salesYTD. */  
echo "YTD sales for ".$lastName." are ". $salesYTD. ".";  
  
/*Free the statement and connection resources. */  
sqlsrv_free_stmt( $stmt1);  
sqlsrv_free_stmt( $stmt2);  
sqlsrv_free_stmt( $stmt3);  
sqlsrv_close( $conn);  
?>  
```  

> [!NOTE]
> Wenn Output-Parameter auf einen Bigint-Typ, zu binden, wenn der Wert außerhalb des Bereichs von anwachsen ein [ganze Zahl](../../t-sql/data-types/int-bigint-smallint-and-tinyint-transact-sql.md), Sie müssen die SQL-Feldtyp als SQLSRV_SQLTYPE_BIGINT angeben. Andernfalls kann dies zu einer Ausnahme "der Wert außerhalb des gültigen Bereichs" führen.

## <a name="example-2"></a>Beispiel 2
In diesem Codebeispiel wird veranschaulicht, wie einen große Bigint-Wert als Output-Parameter gebunden wird.  

```
<?php
$serverName = "(local)";
$connectionInfo = array("Database"=>"testDB");  
$conn = sqlsrv_connect($serverName, $connectionInfo);  
if ($conn === false) {  
    echo "Could not connect.\n";  
    die(print_r(sqlsrv_errors(), true));  
}  

// Assume the stored procedure spTestProcedure exists, which retrieves a bigint value of some large number
// e.g. 9223372036854
$bigintOut = 0;
$outSql = "{CALL spTestProcedure (?)}";
$stmt = sqlsrv_prepare($conn, $outSql, array(array(&$bigintOut, SQLSRV_PARAM_OUT, null, SQLSRV_SQLTYPE_BIGINT)));
sqlsrv_execute($stmt);
echo "$bigintOut\n";   // Expect 9223372036854

sqlsrv_free_stmt($stmt);  
sqlsrv_close($conn);  

?>
```

## <a name="see-also"></a>Weitere Informationen finden Sie unter  
[Gewusst wie: Angeben der Parameterrichtung mit dem SQLSRV-Treiber](../../connect/php/how-to-specify-parameter-direction-using-the-sqlsrv-driver.md)

[Gewusst wie: Abrufen von Eingabe- und Ausgabeparametern mit dem SQLSRV-Treiber](../../connect/php/how-to-retrieve-input-and-output-parameters-using-the-sqlsrv-driver.md)

[Abrufen von Daten](../../connect/php/retrieving-data.md)  
  
