---
title: Beibehalten von NULL-Werten oder Verwenden von Standardwerten während des Massenimports (SQL Server) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: data-movement
ms.topic: conceptual
helpviewer_keywords:
- bulk importing [SQL Server], null values
- bulk importing [SQL Server], default values
- data formats [SQL Server], null values
- bulk rowset providers [SQL Server]
- bcp utility [SQL Server], null values
- BULK INSERT statement
- default values
- OPENROWSET function, bulk importing
- data formats [SQL Server], default values
ms.assetid: 6b91d762-337b-4345-a159-88abb3e64a81
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 4753e1097dee300d4d806c42b71954e6e557ed12
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/02/2018
ms.locfileid: "48186700"
---
# <a name="keep-nulls-or-use-default-values-during-bulk-import-sql-server"></a>Beibehalten von NULL-Werten oder Verwenden von Standardwerten während des Massenimports (SQL Server)
  Wenn Daten in eine Tabelle importiert werden, werden standardmäßig alle für die Spalten in der Tabelle definierten Standardwerte durch den Befehl **bcp** und die BULK INSERT-Anweisung überwacht. Wenn beispielsweise ein NULL-Feld in einem Datenfeld vorkommt, wird stattdessen der Standardwert für die Spalte geladen. Sowohl mit dem Befehl **bcp** als auch mit der BULK INSERT-Anweisung können Sie angeben, dass NULL-Werte beibehalten werden sollen.  
  
 Eine reguläre INSERT-Anweisung hingegen behält den NULL-Wert bei, statt einen Standardwert einzufügen. Die INSERT ... SELECT * FROM OPENROWSET(BULK...)-Anweisung zeigt dasselbe grundlegende Verhalten wie eine reguläre INSERT-Anweisung, unterstützt jedoch zusätzlich einen Tabellenhinweis zum Einfügen der Standardwerte.  
  
> [!NOTE]  
>  Beispiele für Formatdateien, die eine Tabellenspalte auslassen, finden Sie unter [mithilfe einer Formatdatei zum Überspringen einer Tabellenspalte &#40;SQL Server&#41;](use-a-format-file-to-skip-a-table-column-sql-server.md).  
  
## <a name="sample-table-and-data-file"></a>Beispieltabelle und Datendatei  
 Zum Ausführen der Beispiele in diesem Thema müssen Sie eine Beispieltabelle und -datendatei erstellen.  
  
### <a name="sample-table"></a>Beispieltabelle  
 Die Beispiele erfordern, dass eine Tabelle mit dem Namen **MyTestDefaultCol2** in der **AdventureWorks**-Beispieldatenbank unter dem Schema **dbo** erstellt wird. Zum Erstellen dieser Tabelle in [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] Abfrage-Editor ausführen:  
  
```  
USE AdventureWorks;  
GO  
CREATE TABLE MyTestDefaultCol2   
(Col1 smallint,  
Col2 nvarchar(50) DEFAULT 'Default value of Col2',  
Col3 nvarchar(50)   
);  
GO  
  
```  
  
 Beachten Sie, dass die zweite Tabellenspalte `Col2` einen Standardwert hat.  
  
### <a name="sample-format-file"></a>Beispielformatdatei  
 Einige der Massenimportbeispiele verwenden die nicht im XML-Format vorliegende Datei `MyTestDefaultCol2-f-c.Fmt`, die der `MyTestDefaultCol2`-Tabelle genau entspricht. Geben Sie zum Erstellen dieser Formatdatei an der [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows-Eingabeaufforderung Folgendes ein:  
  
```  
bcp AdventureWorks..MyTestDefaultCol2 format nul -c -f C:\MyTestDefaultCol2-f-c.Fmt -t, -r\n -T  
  
```  
  
 Weitere Informationen zum Erstellen von Formatdateien finden Sie unter [Erstellen einer Formatdatei &#40;SQL Server&#41;](create-a-format-file-sql-server.md), um Standardwerte zu verwenden.  
  
### <a name="sample-data-file"></a>Beispieldatendatei  
 Das Beispiel verwendet die Beispieldatendatei `MyTestEmptyField2-c.Dat`, die im zweiten Feld keine Werte enthält. Die Datendatei `MyTestEmptyField2-c.Dat` enthält die folgenden Datensätze.  
  
```  
1,,DataField3  
2,,DataField3  
  
```  
  
## <a name="keeping-null-values-with-bcp-or-bulk-insert"></a>Beibehalten von NULL-Werten mit "bcp" oder BULK INSERT  
 Die folgenden Qualifizierer geben an, dass ein leeres Feld in der Datendatei seinen NULL-Wert während des Massenimportvorgangs beibehält, statt (ggf.) einen Standardwert für die Tabellenspalten zu übernehmen.  
  
|Befehl|Qualifizierer|Qualifizierertyp|  
|-------------|---------------|--------------------|  
|**bcp**|`-k`|Schalter|  
|BULK INSERT|KEEPNULLS<sup>1</sup>|Argument|  
  
 <sup>1</sup> für BULK INSERT, wenn Standardwerte nicht verfügbar ist, sind die Tabellenspalte definiert werden, um null-Werte zulassen.  
  
> [!NOTE]  
>  Diese Qualifizierer deaktivieren das Prüfen von DEFAULT-Definitionen in einer Tabelle durch diese Massenimportbefehle. Für gleichzeitige INSERT-Anweisungen werden jedoch DEFAULT-Definitionen erwartet.  
  
 Weitere Informationen finden Sie unter [Hilfsprogramm "Bcp"](../../tools/bcp-utility.md) und [BULK INSERT &#40;Transact-SQL&#41;](/sql/t-sql/statements/bulk-insert-transact-sql).  
  
### <a name="examples"></a>Beispiele  
 In den Beispielen dieses Abschnitts werden Massenimporte mithilfe von **bcp** oder BULK INSERT ausgeführt und NULL-Werte beibehalten.  
  
 Die zweite Tabellenspalte, **Col2**, hat einen Standardwert. Das entsprechende Feld der Datendatei enthält eine leere Zeichenfolge. Wenn **bcp** oder BULK INSERT zum Importieren von Daten aus dieser Datendatei in die **MyTestDefaultCol2**-Tabelle verwendet wird, wird standardmäßig der Standardwert von **Col2** eingefügt, sodass das folgende Ergebnis erzeugt wird:  
  
||||  
|-|-|-|  
|`1`|`Default value of Col2`|`DataField3`|  
|`2`|`Default value of Col2`|`DataField3`|  
  
 Zum Einfügen "`NULL`"anstelle von"`Default value of Col2`", müssen Sie die `-k` Switch oder die Option keepnull verwenden, wie im folgenden **Bcp** und BULK INSERT-Beispielen gezeigt.  
  
#### <a name="using-bcp-and-keeping-null-values"></a>Verwenden von "bcp" und Beibehalten von NULL-Werten  
 Das folgende Beispiel zeigt, wie NULL-Werte in einem **bcp**-Befehl beibehalten werden. Der Befehl **bcp** verfügt über folgende Schalter:  
  
|Schalter|Description|  
|------------|-----------------|  
|`-f`|Gibt an, dass der Befehl eine Formatdatei verwendet.|  
|`-k`|Gibt an, dass während des Vorgangs keine Standardwerte in leere Spalten eingefügt werden, sondern ein NULL-Wert für diese Spalten beibehalten werden soll.|  
|`-T`|Gibt an, dass das Hilfsprogramm "bcp" eine vertrauenswürdige Verbindung mit [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] herstellt.|  
  
 Geben Sie an der Windows-Eingabeaufforderung Folgendes ein.  
  
```  
bcp AdventureWorks..MyTestDefaultCol2 in C:\MyTestEmptyField2-c.Dat -f C:\MyTestDefaultCol2-f-c.Fmt -k -T  
  
```  
  
#### <a name="using-bulk-insert-and-keeping-null-values"></a>Verwenden von BULK INSERT und Beibehalten von NULL-Werten  
 Das folgende Beispiel zeigt, wie die Option KEEPNULLS in einer BULK INSERT-Anweisung verwendet wird. Von einem Abfragetool z. B. [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] Abfrage-Editor ausführen:  
  
```  
USE AdventureWorks;  
GO  
BULK INSERT MyTestDefaultCol2  
   FROM 'C:\MyTestEmptyField2-c.Dat'  
   WITH (  
      DATAFILETYPE = 'char',  
      FIELDTERMINATOR = ',',  
      KEEPNULLS  
   );  
GO  
  
```  
  
## <a name="keeping-default-values-with-insert--select--from-openrowsetbulk"></a>Beibehalten von Standardwerten mit INSERT ... SELECT * FROM OPENROWSET(BULK...)  
 Standardmäßig werden Spalten, die nicht in dem Massenladevorgang angegeben sind, durch INSERT ... SELECT * FROM OPENROWSET(BULK...). Sie können jedoch angeben, dass die entsprechende Tabellenspalte für ein leeres Feld in der Datendatei (ggf.) den Standardwert verwendet. Zum Verwenden von Standardwerten geben Sie den folgenden Tabellenhinweis an:  
  
|Befehl|Qualifizierer|Qualifizierertyp|  
|-------------|---------------|--------------------|  
|INSERT ... SELECT * FROM OPENROWSET(BULK...)|WITH(KEEPDEFAULTS)|Tabellenhinweis|  
  
> [!NOTE]  
>  Weitere Informationen finden Sie unter [einfügen &#40;Transact-SQL&#41;](/sql/t-sql/statements/insert-transact-sql), [wählen &#40;Transact-SQL&#41;](/sql/t-sql/queries/select-transact-sql), [OPENROWSET &#40;Transact-SQL&#41; ](/sql/t-sql/functions/openrowset-transact-sql), und [Tabellenhinweise &#40;Transact-SQL&#41;](/sql/t-sql/queries/hints-transact-sql-table)  
  
### <a name="examples"></a>Beispiele  
 Im folgenden INSERT ... SELECT * FROM OPENROWSET(BULK...)-Beispiel wird ein Massenimport von Daten ausgeführt, und die Standardwerte werden beibehalten.  
  
 Um die Beispiele auszuführen, müssen Sie die **MyTestDefaultCol2**-Beispieltabelle und die Datendatei `MyTestEmptyField2-c.Dat` erstellen und die Formatdatei `MyTestDefaultCol2-f-c.Fmt` verwenden. Weitere Informationen zum Erstellen dieser Beispiele finden Sie unter "Beispieltabelle und Datendatei" weiter oben in diesem Thema.  
  
 Die zweite Tabellenspalte, **Col2**, hat einen Standardwert. Das entsprechende Feld der Datendatei enthält eine leere Zeichenfolge. Wenn INSERT ... SELECT \* FROM OPENROWSET(BULK...) die Felder dieser Datendatei in die **MyTestDefaultCol2**-Tabelle importiert, wird statt des Standardwerts standardmäßig NULL in **Col2** eingefügt. Dieses Standardverhalten führt zu folgendem Ergebnis:  
  
||||  
|-|-|-|  
|`1`|`NULL`|`DataField3`|  
|`2`|`NULL`|`DataField3`|  
  
 Um den Standardwert "`Default value of Col2`" anstelle von "`NULL`" einzufügen, müssen Sie den Tabellenhinweis KEEPDEFAULTS verwenden, wie im folgenden Beispiel gezeigt. Von einem Abfragetool z. B. [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] Abfrage-Editor ausführen:  
  
```  
USE AdventureWorks;  
GO  
INSERT INTO MyTestDefaultCol2  
    WITH (KEEPDEFAULTS)  
    SELECT *  
      FROM OPENROWSET(BULK  'C:\MyTestEmptyField2-c.Dat',  
      FORMATFILE='C:\MyTestDefaultCol2-f-c.Fmt'       
      ) as t1 ;  
GO  
  
```  
  
##  <a name="RelatedTasks"></a> Verwandte Aufgaben  
  
-   [Beibehalten von Identitätswerten beim Massenimport von Daten &#40;SQL Server&#41;](keep-identity-values-when-bulk-importing-data-sql-server.md)  
  
-   [Vorbereiten von Daten für den Massenexport oder -import &#40;SQL Server&#41;](prepare-data-for-bulk-export-or-import-sql-server.md)  
  
 **So verwenden Sie eine Formatdatei**  
  
-   [Erstellen einer Formatdatei &#40;SQL Server&#41;](create-a-format-file-sql-server.md)  
  
-   [Massenimport von Daten mithilfe einer Formatdatei &#40;SQL Server&#41;](use-a-format-file-to-bulk-import-data-sql-server.md)  
  
-   [Verwenden einer Formatdatei zum Zuordnen von Tabellenspalten zu Datendateifeldern &#40;SQL Server&#41;](use-a-format-file-to-map-table-columns-to-data-file-fields-sql-server.md)  
  
-   [Auslassen eines Datenfelds mithilfe einer Formatdatei &#40;SQL Server&#41;](use-a-format-file-to-skip-a-data-field-sql-server.md)  
  
-   [Überspringen einer Tabellenspalte mithilfe einer Formatdatei &#40;SQL Server&#41;](use-a-format-file-to-skip-a-table-column-sql-server.md)  
  
 **So verwenden Sie Datenformate für Massenimport oder Massenexport**  
  
-   [Importieren von Daten aus früheren SQL Server-Versionen im systemeigenen Format oder im Zeichenformat](import-native-and-character-format-data-from-earlier-versions-of-sql-server.md)  
  
-   [Verwenden des Zeichenformats zum Importieren und Exportieren von Daten &#40;SQL Server&#41;](use-character-format-to-import-or-export-data-sql-server.md)  
  
-   [Verwenden des nativen Formats zum Importieren oder Exportieren von Daten &#40;SQL Server&#41;](use-native-format-to-import-or-export-data-sql-server.md)  
  
-   [Verwenden des Unicode-Zeichenformats zum Importieren und Exportieren von Daten &#40;SQL Server&#41;](use-unicode-character-format-to-import-or-export-data-sql-server.md)  
  
-   [Verwenden des nativen Unicode-Formats zum Importieren oder Exportieren von Daten &#40;SQL Server&#41;](use-unicode-native-format-to-import-or-export-data-sql-server.md)  
  
 **So geben Sie Datenformate für die Kompatibilität bei Verwendung von bcp an**  
  
-   [Angeben von Feld- und Zeilenabschlusszeichen &#40;SQL Server&#41;](specify-field-and-row-terminators-sql-server.md)  
  
-   [Angeben der Präfixlänge in Datendateien mittels bcp &#40;SQL Server&#41;](specify-prefix-length-in-data-files-by-using-bcp-sql-server.md)  
  
-   [Angeben des Dateispeichertyps mithilfe von bcp &#40;SQL Server&#41;](specify-file-storage-type-by-using-bcp-sql-server.md)  
  
## <a name="see-also"></a>Siehe auch  
 [BACKUP &#40;Transact-SQL&#41;](/sql/t-sql/statements/backup-transact-sql)   
 [OPENROWSET &#40;Transact-SQL&#41;](/sql/t-sql/functions/openrowset-transact-sql)   
 [bcp (Hilfsprogramm)](../../tools/bcp-utility.md)   
 [BULK INSERT &#40;Transact-SQL&#41;](/sql/t-sql/statements/bulk-insert-transact-sql)   
 [Tabellenhinweise &#40;Transact-SQL&#41;](/sql/t-sql/queries/hints-transact-sql-table)  
  
  
