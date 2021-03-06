---
title: Neuigkeiten zu SQL Server 2019 | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/27/2018
ms.prod: sql-server-2018
ms.reviewer: ''
ms.technology:
- server-general
ms.topic: article
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
monikerRange: '>=sql-server-ver15||=sqlallproducts-allversions'
ms.openlocfilehash: 015a6d65f1d225ab5a8752352d41fd2201f871b5
ms.sourcegitcommit: ef78cc196329a10fc5c731556afceaac5fd4cb13
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/19/2018
ms.locfileid: "49461115"
---
# <a name="whats-new-in-sql-server-2019"></a>Neuigkeiten zu SQL Server 2019

[!INCLUDE[tsql-appliesto-ssver15-xxxx-xxxx-xxx](../includes/tsql-appliesto-ssver15-xxxx-xxxx-xxx.md)]

[!INCLUDE[sql-server-2019](..\includes\sssqlv15-md.md)] ist eine Erweiterung der SQL Server-Plattform basierend auf früheren Releases, die Ihnen eine große Auswahl an Entwicklungssprachen, Datentypen und Betriebssystemen sowie die Arbeit mit einer lokalen Umgebung oder der Cloud bietet. Dieser Artikel beschreibt die Neuigkeiten zu SQL Server 2019. Weitere Informationen und bekannte Probleme finden Sie unter [SQL Server 2019 (Vorschau) – Anmerkungen zu dieser Version](sql-server-ver15-release-notes.md).

**Testen Sie SQL Server 2019!**
- [![Download from Evaluation Center](../includes/media/download2.png)](http://go.microsoft.com/fwlink/?LinkID=862101) [Laden Sie SQL Server 2019 für die Installation unter Windows herunter.](http://go.microsoft.com/fwlink/?LinkID=862101)
- Installieren Sie die Version unter Linux für [Red Hat Enterprise Server](../linux/quickstart-install-connect-red-hat.md), [SUSE Linux Enterprise Server](../linux/quickstart-install-connect-suse.md) und [Ubuntu](../linux/quickstart-install-connect-ubuntu.md).
- [Führen Sie SQL Server 2019 unter Docker aus](../linux/quickstart-install-connect-docker.md).

## <a name="ctp-20"></a>CTP 2.0 

Community Technology Preview (CTP) 2.0 ist das erste öffentliche Release von [!INCLUDE[sql-server-2019](..\includes\sssqlv15-md.md)]. Die folgenden Features wurden für [!INCLUDE[sql-server-2019](..\includes\sssqlv15-md.md)] CTP 2.0 hinzugefügt oder verbessert.

- [Big Data-Cluster](#bigdatacluster)
  - Bereitstellen eines Big Data-Clusters mit SQL und Spark-Linux-Containern in Kubernetes
  - Zugriff auf Big Data über HDFS
  - Ausführen von erweiterten Analysen und Machine Learning-Vorgängen mit Spark
  - Streamen von Daten an SQL Server-Datenpools mit Spark
  - Ausführen von Abfragebüchern zur Bereitstellung einer Notebookumgebung mit Azure Data Studio

- [Datenbank-Engine](#databaseengine)
  - Unterstützung für UTF-8
  - Fortsetzen der Indexerstellung nach einer Unterbrechung durch die Erstellung von fortsetzbaren Onlineindizes
  - Erstellung und Neuerstellung von gruppierten Columnstore-Onlineindizes
  - Always Encrypted mit Secure Enclaves
  - Intelligente Abfrageverarbeitung
  - Erweiterung für die Programmierbarkeit der Java-Sprache
  - SQL-Graphfeatures
  - Datenbankweit gültige Konfigurationseinstellung für Online- und fortsetzbare DDL-Vorgänge
  - Always On-Verfügbarkeitsgruppen – Umleitung von Verbindungen mit sekundären Replikaten
  - Nativ in SQL Server integrierte Datenermittlung und -klassifizierung
  - Erweiterte Unterstützung für Geräte mit persistentem Speicher
  - Unterstützung für Columnstore-Statistiken in `DBCC CLONEDATABASE`
  - Neue Optionen für `sp_estimate_data_compression_savings`
  - Failovercluster in SQL Server Machine Learning Services
  - Standardmäßig aktivierte LWP-Abfrageinfrastruktur (Lightweight Profiling)
  - Neue PolyBase-Connectors
  - Rückgabe von Seiteninformationen durch neue `sys.dm_db_page_info`-Systemfunktion

- [SQL Server unter Linux](#sqllinux)
  - Replikationsunterstützung
  - Unterstützung für den Microsoft Distributed Transaction Coordinator (MSDTC)
  - Always On-Verfügbarkeitsgruppe in Docker-Containern mit Kubernetes
  - OpenLDAP-Unterstützung für AD-Drittanbieter
  - Machine Learning unter Linux
  - Neue Containerregistrierung
  - Neue RHEL-basierte Containerimages
  - Benachrichtigung zur Speicherauslastung

- [Master Data Services](#mds)
  - Ersetzung der Silverlight-Steuerelemente

- [Security](#security)
  - Zertifikatverwaltung im SQL Server-Konfigurations-Manager

- [Tools](#tools)
  - SQL Server Management Studio (SSMS) 18.0 (Vorschau)
  - Azure Data Studio

Weitere Informationen zu diesen Features finden Sie weiter unten.

## <a id="bigdatacluster"></a>Big Data-Cluster

[!INCLUDE[sql-server-2019](../includes/sssqlv15-md.md)] [Big Data-Cluster](../big-data-cluster/big-data-cluster-overview.md) ermöglichen neue Szenarien wie die Folgenden:

- Bereitstellen eines Big Data-Clusters mit [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]- und Spark-Linux-Containern in Kubernetes
- Zugriff auf Big Data über HDFS
- Ausführen von erweiterten Analysen und Machine Learning-Vorgängen mit Spark
- Streamen von Daten an SQL Server-Datenpools mit Spark
- Ausführen von Abfragebüchern zur Bereitstellung einer Notebookumgebung in [**Azure Data Studio**](../sql-operations-studio/what-is.md)
  
[!INCLUDE [Big Data Clusters preview](../includes/big-data-cluster-preview-note.md)]

## <a id="databaseengine"></a> Datenbank-Engine

CTP 2.0 bietet die folgenden neuen Features für [!INCLUDE[ssdeNoVersion](../includes/ssdenoversion_md.md)].

### <a name="database-compatibility-level"></a>Datenbank-Kompatibilitätsgrad

Die Datenbank **COMPATIBILITY_LEVEL 150** wurde hinzugefügt. Um eine bestimmte Benutzerdatenbank verwenden zu können, führen Sie Folgendes aus:

   ```sql
   ALTER DATABASE database_name SET COMPATIBILITY_LEVEL =  150;
   ```

### <a name="utf-8-support"></a>Unterstützung für UTF-8

Vollständige Unterstützung für die weit verbreitete Zeichencodierung UTF-8 als Import- oder Exportcodierung oder als Sortierung für Textdaten auf Datenbank- oder Spaltenebene. UTF-8 ist für die Datentypen `CHAR` und `VARCHAR` zulässig und ist bei der Erstellung oder Änderung einer Objektsortierung in eine Sortierung mit dem Suffix `UTF8` aktiviert. 

Beispiel: `LATIN1_GENERAL_100_CI_AS_SC` in `LATIN1_GENERAL_100_CI_AS_SC_UTF8`. Die in SQL Server 2012 eingeführte UTF-8-Codierung ist nur für Windows-Sortierungen verfügbar, die Sonderzeichen unterstützen. `NCHAR` und `NVARCHAR` lassen nur die UTF-16-Codierung zu und bleiben unverändert.

Dieses Feature kann abhängig von dem verwendeten Zeichensatz beträchtliche Speichereinsparungen ermöglichen. Die Änderung eines vorhandenen Spaltendatentyps mit ASCII-Zeichenfolgen von `NCHAR(10)` in `CHAR(10)` mit einer UTF-8-fähigen Sortierung führt beispielsweise zu einer Verringerung der Speicheranforderungen um fast 50 %. Diese Verringerung ist darauf zurückzuführen, dass `NCHAR(10)` 22 Byte für den Speicher erfordert, wohingegen `CHAR(10)` 12 Byte für die gleiche Unicode-Zeichenfolge erfordert.

### <a name="resumable-online-index-create"></a>Erstellung von fortsetzbaren Onlineinidizes

- Durch die **Erstellung von fortsetzbaren Onlineindizes** kann ein Indexerstellungsvorgang angehalten und zu einem späteren Zeitpunkt an der Stelle fortgesetzt werden, an der der Vorgang angehalten wurde oder an der ein Fehler aufgetreten ist. So muss nicht von Anfang an begonnen werden.

  Die Erstellung fortsetzbarer Onlineindizes unterstützt folgende Szenarien:
  - Fortsetzen eines Indexerstellungsvorgangs nach einem Fehler bei der Indexerstellung (z.B. nach einem Datenbankfailover oder bei fehlendem Speicherplatz auf dem Datenträger)
  - Anhalten eines laufenden Indexerstellungsvorgangs und Fortsetzen zu einem späteren Zeitpunkt, um bei Bedarf vorübergehend Systemressourcen freizugeben und diesen Vorgang zu einem späteren Zeitpunkt fortzusetzen
  - Erstellen großer Indizes ohne Inanspruchnahme von umfassendem Protokollspeicherplatz und Transaktionen mit langer Laufzeit, die andere Wartungsaktivitäten blockieren, jedoch mit der Möglichkeit zur Protokollkürzung

  Ohne dieses Feature müsste ein Vorgang zur Onlineindexerstellung bei einem Fehler erneut von Anfang an ausgeführt werden.

Bei diesem Release erweitern wir die Funktionen für fortsetzbare Indizes, indem wir dieses Feature für verfügbare [Neuerstellungen von fortsetzbaren Onlineindizes](http://azure.microsoft.com/blog/modernize-index-maintenance-with-resumable-online-index-rebuild/) hinzufügen.

Darüber hinaus kann dieses Feature als Standardwert für eine bestimmte Datenbank mit einer [datenbankweit gültigen Standardeinstellung für Online- und fortsetzbare DDL-Vorgänge](../t-sql/statements/alter-database-scoped-configuration-transact-sql.md) festgelegt werden.

Weitere Informationen finden Sie unter [Erstellung von fortsetzbaren Onlineindizes](../t-sql/statements/create-index-transact-sql.md#resumable-indexes).

### <a name="build-and-rebuild-clustered-columnstore-indexes-online"></a>Erstellung und Neuerstellung von gruppierten Columnstore-Onlineindizes

Konvertieren Sie Rowstore-Tabellen in das Columnstore-Format. Die Erstellung von gruppierten Columnstore-Indizes (Clustered Columnstore Indexes, CCIs) war in früheren Versionen von [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] ein Offlinevorgang, bei dem alle Änderungen eingestellt werden mussten, während der CCI erstellt wird. Mit [!INCLUDE[sql-server-2019](../includes/sssqlv15-md.md)] und [!INCLUDE[ssSDSfull](../includes/sssdsfull-md.md)] können Sie einen CCI online erstellen bzw. neu erstellen. Die Workload wird nicht blockiert und alle Änderungen, die an den zugrunde liegenden Daten vorgenommen werden, werden transparent zur Columnstore-Zieltabelle hinzugefügt. Beispiele für die neuen [!INCLUDE[tsql](../includes/tsql-md.md)]-Anweisungen, die verwendet werden können:

  ```sql
  CREATE CLUSTERED COLUMNSTORE INDEX cci
    ON <tableName>
    WITH (ONLINE = ON);
  ```

  ```sql
  ALTER INDEX cci
    ON <tableName>
    REBUILD WITH (ONLINE = ON);
  ```

### <a name="always-encrypted-with-secure-enclaves"></a>Always Encrypted mit Secure Enclaves

Die Erweiterung basiert auf Always Encrypted mit direkter Verschlüsselung und umfangreichen Berechnungen. Die Erweiterungen basieren auf der Ermöglichung von Berechnungen auf Grundlage von Klartextdaten, die sich auf Serverseite in einer Secure Enclave befinden.

Kryptografische Vorgänge umfassen die Verschlüsselung von Spalten und das Rotieren von Spaltenverschlüsselungsschlüsseln. Diese Vorgänge können nun mithilfe von [!INCLUDE[tsql](../includes/tsql-md.md)] ausgegeben werden und erfordern kein Entfernen dieser Daten aus der Datenbank. Secure Enclaves bieten Always Encrypted, um ein breiteres Spektrum an Szenarien zu ermöglichen, die folgende Anforderungen nach sich ziehen:  

- Vertrauliche Daten müssen vor Benutzern mit erhöhten Rechten, die jedoch nicht autorisiert sind, geschützt werden (z.B. Datenbankadministratoren, Systemadministratoren, Cloudbetreibern oder Malware).
- Es müssen umfangreiche Berechnungen für geschützte Daten innerhalb des Datenbanksystems unterstützt sein.

Weitere Einzelheiten finden Sie unter [Always Encrypted mit Secure Enclaves](../relational-databases/security/encryption/always-encrypted-enclaves.md).

> [!NOTE]
> Always Encrypted mit Secure Enclaves ist nur unter dem Windows-Betriebssystem verfügbar.

### <a name="intelligent-query-processing"></a>Intelligente Abfrageverarbeitung

- Das **Feedback zur Speicherzuweisung im Zeilenmodus** erweitert das Feedbackfeature zur Speicherzuweisung, das [!INCLUDE[ssSQL17](../includes/sssql17-md.md)] eingeführt wurde, indem die Größe der Speicherzuweisung sowohl für Batch- als auch für Zeilenmodusoperatoren angepasst wird.  Wenn bei einer Bedingung mit einer zu großen Speicherzuweisung der zugewiesene Speicher mehr als doppelt so groß ist als der tatsächlich verwendete Speicher, berechnet das Feedback zur Speicherzuweisung diese neu. Nachfolgende Ausführungen erfordern dann weniger Arbeitsspeicher. Bei zu geringen Speicherzuweisungen, die zu einem Überlauf auf einen Datenträger führen, löst das Feedback zur Speicherzuweisung eine Neuberechnung der Speicherzuweisung aus. Nachfolgende Ausführungen erfordern dann mehr Arbeitsspeicher. Dieses Feature ist standardmäßig unter dem Datenbank-Kompatibilitätsgrad 150 aktiviert.

- **Approximate COUNT DISTINCT** gibt die ungefähre Anzahl von eindeutigen Werten ungleich NULL in einer Gruppe zurück. Diese Funktion ist für den Einsatz in Big Data-Szenarien bestimmt. Diese Funktion ist für Abfragen optimiert, bei denen alle der folgenden Bedingungen zutreffen:
   - Es wird auf Datasets mit Zeilen mindestens im Millionenbereich zugegriffen.
   - Es wird mindestens eine Spalte aggregiert, die eine große Anzahl von unterschiedlichen Werten enthält.
   - Reaktionsschnelligkeit ist wichtiger als absolute Präzision.
      - `APPROX_COUNT_DISTINCT` gibt Ergebnisse zurück, die in der Regel im 2-Prozent-Bereich der genauen Antwort liegen.
      - Zudem wird die ungefähre Antwort in einem Bruchteil der Zeit zurückgegeben, die für die genaue Antwort erforderlich ist.

- Für den **Batchmodus in Rowstore** ist kein Columnstore-Index mehr zur Verarbeitung von Abfragen im Batchmodus erforderlich. Im Batchmodus können Abfrageoperatoren verwendet werden, die die Verarbeitung von einer Gruppe von Zeilen statt nur von einer Zeile ermöglichen. Dieses Feature ist standardmäßig unter dem Datenbank-Kompatibilitätsgrad 150 aktiviert. Der Batchmodus beschleunigt somit Abfragen, die auf Rowstore-Tabellen zugreifen, sofern alle der folgenden Bedingungen zutreffen:
   - Die Abfrage verwendet Analyseoperatoren wie Joins oder Aggregationsoperatoren.
   - Die Abfrage umfasst mindestens 100.000 Zeilen.
   - Die Abfrage ist nicht an Eingabe-/Ausgabedaten gebunden, sondern an die CPU.
   - Die Erstellung und Verwendung eines Columnstore-Index weisen folgende Nachteile auf:
      - Sie würden den Overheadbedarf der Abfrage übersteigen.
      - Sie können nicht durchgeführt werden, da Ihre Anwendung von einem Feature abhängt, das noch nicht bei Columnstore-Indizes unterstützt wird.

- Die **verzögerte Kompilierung von Tabellenvariablen** verbessert die Qualität des Abfrageplans und die Gesamtleistung für Abfragen mit Verweisen auf Tabellenvariablen. Während der Optimierung und der ersten Kompilierung propagiert diese Funktion Kardinalitätsschätzungen, die auf tatsächlichen Tabellenvariablen-Zeilenzahlen basieren.  Diese genauen Zeilenzahlinformationen werden für die Optimierung der nachgelagerten Planvorgänge verwendet. Dieses Feature ist standardmäßig unter dem Datenbank-Kompatibilitätsgrad 150 aktiviert.

Um Features der intelligenten Abfrageverarbeitung verwenden zu können, legen Sie die Datenbank `COMPATIBILITY_LEVEL = 150` fest.

### <a id="programmability"></a> Erweiterungen für die Programmierbarkeit der Java-Sprache

- **Java-Spracherweiterung (Vorschau)**: Führen Sie Java-Code mithilfe der Java-Spracherweiterung [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] aus. Diese Erweiterung ist in [!INCLUDE[sql-server-2019](../includes/sssqlv15-md.md)] installiert, wenn Sie das Feature „Machine Learning Services (datenbankintern)“ zu Ihrer SQL Server-Instanz hinzufügen.

### <a id="sqlgraph"></a> SQL-Graphfeatures

- Dank des **Supports in `MERGE` DML** können Sie Graphbeziehungen statt in separaten `INSERT`-, `UPDATE`- oder `DELETE`-Anweisungen in einer einzigen Anweisung angeben. Führen Sie Ihre aktuellen Graphdaten aus Knoten- oder Edgetabellen mithilfe der `MATCH`-Prädikate in der `MERGE`-Anweisung mit neuen Daten zusammen. Dieses Feature ermöglicht `UPSERT`-Szenarien in Edgetabellen. Benutzer können nun eine einzelne MERGE-Anweisung verwenden, um einen neuen Edge einzufügen oder einen vorhandenen Edge zwischen zwei Knoten zu aktualisieren.

- Für Edgetabellen im SQL-Graph wurden **Edgeeinschränkungen** eingeführt. Edgetabellen können eine Verbindung zwischen beliebigen Knoten in der Datenbank herstellen. Mit der Einführung von Edgeeinschränkungen können Sie ab sofort einige Einschränkungen zu diesem Verhalten anwenden. Mit der neuen `CONNECTION`-Einschränkung kann der Knotentyp angegeben werden, mit dem eine bestimmte Edgetabelle eine Verbindung im Schema herstellen darf.

### <a name="database-scoped-default-setting-for-online-and-resumable-ddl-operations"></a>Datenbankweit gültige Standardeinstellung für Online- und fortsetzbare DDL-Vorgänge 

- Die **datenbankweit gültige Standardeinstellung für Online- und fortsetzbare DDL-Vorgänge** ermöglicht eine Standardverhaltenseinstellung für `ONLINE`- und `RESUMABLE`-Indexvorgänge auf Datenbankebene, statt diese Optionen für jede einzelne DDL-Indexanweisung definieren zu müssen (z.B. Indexerstellung oder -neuerstellung).

- Legen Sie diese Standardeinstellungen mithilfe der datenbankweit gültigen Konfigurationsoptionen `ELEVATE_ONLINE` und `ELEVATE_RESUMABLE` fest. Beide Optionen bewirken, dass die Engine unterstützte Vorgänge automatisch auf die Ausführung von Online- oder fortsetzbaren Indizes erhöht. Mit diesen Optionen können Sie die folgenden Verhaltensweisen ermöglichen:

  - Die Option `FAIL_UNSUPPORTED` ermöglicht alle Onlineindex- oder fortsetzbare und Fehlerindexvorgänge, die nicht für Online- oder fortsetzbare Indizes unterstützt werden.
  - Die Option `WHEN_SUPPPORTED` ermöglicht unterstützte Online- oder fortsetzbare und die Ausführung von nicht unterstützten Offline- oder nicht fortsetzbaren Indexvorgängen.
  - Die Option `OFF` lässt das aktuelle Verhalten zur Ausführung aller Offlineindexvorgänge und nicht fortsetzbare Indexvorgänge zu, sofern dies nicht explizit in der DDL-Anweisung angegeben ist.

Um die Standardeinstellung zu überschreiben, schließen Sie die ONLINE- oder die RESUMABLE-Option in die Indexerstellungs- und -neuerstellungsbefehle ein.  

Ohne dieses Feature müssen Sie die Online- und fortsetzbaren Indexoptionen direkt in der Index-DDL-Anweisung angeben, z.B. Indexerstellung und -neuerstellung.

Weitere Informationen zu fortsetzbaren Indexvorgängen finden Sie unter [Erstellung fortsetzbarer Onlineindizes in der öffentlichen Vorschau für Azure SQL-Datenbank](http://azure.microsoft.com/blog/resumable-online-index-create-is-in-public-preview-for-azure-sql-db/).

### <a id="ha"></a>Always On-Verfügbarkeitsgruppen: Erhöhung der synchronen Replikate 

- **Bis zu fünf synchrone Replikate**: In [!INCLUDE[sql-server-2019](../includes/sssqlv15-md.md)] wird die maximale Anzahl der synchronen Replikate von ehemals 3 in [!INCLUDE[ssSQL17](../includes/sssql17-md.md)] auf 5 erhöht. Sie können diese Gruppe aus 5 Replikaten für das automatische Failover in der Gruppe konfigurieren. Es gibt ein primäres Replikat sowie 4 synchrone sekundäre Replikate.

- **Umleitung der Verbindung vom sekundären zum primären Replikat**: Durch dieses Feature können Clientanwendungsverbindungen zum primären Replikat weitergeleitet werden, unabhängig davon, ob der Zielserver in der Verbindungszeichenfolge angegeben ist. Diese Funktion ermöglicht die Umleitung der Verbindung ohne einen Listener. Leiten Sie in den folgenden Fällen die Verbindung vom sekundären zum primären Replikat um:

  - Die Clustertechnologie bietet keine Listenerfunktion.
  - Es liegt eine Konfiguration mit mehreren Subnetzen vor, die eine komplexe Umleitung erfordert.
  - Im Mittelpunkt stehen Szenarien mit horizontaler Leseskalierung oder Notfallwiederherstellungszenarien mit dem Clustertyp `NONE`.

Weitere Informationen finden Sie unter [Umleitung von Lese-/Schreibverbindungen vom sekundären zum primären Replikat (Always On-Verfügbarkeitsgruppen)](../database-engine/availability-groups/windows/secondary-replica-connection-redirection-always-on-availability-groups.md).

### <a name="data-discovery-and-classification"></a>Datenermittlung und -klassifizierung

Die Datenermittlung und -klassifizierung bietet erweiterte Funktionen, die nativ in [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] integriert sind. Die Klassifizierung und Bezeichnung der wichtigsten vertraulichen Daten bietet folgende Vorteile:
- Bietet Unterstützung, um Datenschutzstandards und gesetzlich geregelte Complianceanforderungen zu erfüllen
- Unterstützt Sicherheitsszenarien, z.B. Überwachung und Benachrichtigung bei anomalem Zugriff auf vertrauliche Daten
- Vereinfacht den Vorgang der Ermittlung, wo sich vertrauliche Daten im Unternehmen befinden, damit Administratoren die richtigen Schritte zum Schutz der Datenbank durchführen können

Weitere Informationen finden Sie unter [Datenermittlung und -klassifizierung in SQL Server](../relational-databases/security/sql-data-discovery-and-classification.md).

Die [Überwachung](../relational-databases/security/auditing/sql-server-audit-database-engine.md) wurde zudem dahingehend verbessert, dass ein neues Feld in das Überwachungsprotokoll `data_sensitivity_information` eingeschlossen wurde, das die Vertraulichkeitsklassifizierungen (Bezeichnungen) der tatsächlichen Daten protokolliert, die von der Abfrage zurückgegeben wurden. Weitere Informationen und Beispiele finden Sie unter [ADD SENSITIVITY CLASSIFICATION (Transact-SQL)](../t-sql/statements/add-sensitivity-classification-transact-sql.md).

>[!NOTE]
>Es wurden keine Änderungen an der Art und Weise vorgenommen, wie die Überwachung aktiviert wird. Den Überwachungsdatensätzen wurde ein neues Feld namens `data_sensitivity_information` hinzugefügt, das die Vertraulichkeitsklassifizierungen (Bezeichnungen) der tatsächlichen Daten protokolliert, die von der Abfrage zurückgegeben wurden. Weitere Informationen finden Sie unter [Überwachen des Zugriffs auf vertrauliche Daten](https://docs.microsoft.com/azure/sql-database/sql-database-data-discovery-and-classification#subheading-3).

### <a name="expanded-support-for-persistent-memory-devices"></a>Erweiterte Unterstützung für Geräte mit persistentem Speicher

[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]-Dateien, die auf einem Gerät mit persistentem Speicher platziert werden, können ab sofort im *optimierten* Modus betrieben werden. [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] greift direkt auf das Gerät zu, wobei der Speicherstapel des Betriebssystems mithilfe von effizienten Speichervorgängen umgangen wird. Dieser Modus verbessert die Leistung, da er Eingaben/Ausgaben mit geringen Latenzen für solche Geräte ermöglicht.
    - Zu [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]-Dateien zählen beispielsweise Folgende:
        - Datenbankdateien
        - Transaktionsprotokolldateien
        - In-Memory-OLTP-Prüfpunktdateien
    - Persistente Speicher werden auch als Speicherklassenspeicher bezeichnet.
    - Persistente Speicher werden auf Websites, die nicht von Microsoft betrieben werden, gelegentlich informell *pmem* genannt.

> [!NOTE]
> Bei diesem Vorschaurelease ist die Optimierung von Dateien auf Geräten mit persistentem Speicher nur unter Linux verfügbar. Geräte mit persistentem Speicher werden unter Windows ab SQL Server 2016 unterstützt.

### <a name="support-for-columnstore-statistics-in-dbcc-clonedatabase"></a>Unterstützung für Columnstore-Statistiken in DBCC CLONEDATABASE

`DBCC CLONEDATABASE` erstellt eine rein schemabasierte Kopie einer Datenbank, die alle Elemente enthält, die zum Behandeln von Problemen mit der Abfrageleistung erforderlich sind, ohne das Daten kopiert werden.  In älteren Versionen von [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] wurden beim Befehl nicht die Statistiken kopiert, die für die Problembehandlung bei Columnstore-Indexabfragen erforderlich sind, weshalb manuelle Schritte zur Erfassung dieser Informationen nötig waren. In [!INCLUDE[sql-server-2019](../includes/sssqlv15-md.md)] erfasst DBCC CLONEDATABASE nun automatisch die Statistikblobs für Columnstore-Indizes, sodass keine manuellen Schritte erforderlich sind.

### <a name="new-options-added-to-spestimatedatacompressionsavings"></a>Neue Optionen zu „sp_estimate_data_compression_savings“ hinzugefügt

`sp_estimate_data_compression_savings` gibt die aktuelle Größe des angeforderten Objekts zurück und schätzt die Objektgröße für den angeforderten Komprimierungsstatus.  Diese Prozedur unterstützt derzeit drei Optionen: `NONE`, `ROW` und `PAGE`. In SQL Server 2019 werden zwei neue Optionen eingeführt: `COLUMNSTORE` und `COLUMNSTORE_ARCHIVE`. Diese neuen Optionen ermöglichen es Ihnen, die Speicherplatzeinsparungen abzuschätzen, wenn mit der Columnstore-Standard- oder -Archivkomprimierung ein Columnstore-Index für die Tabelle erstellt wird.

### <a id="ml"></a> Failovercluster für SQL Server Machine Learning Services und partitionsbasierte Modellierung

- **Partitionsbasierte Modellierung**: `sp_execute_external_script` wurde um die partitionsbasierte Verarbeitung von externen Skripts Ihrer Daten mit den neuen Parameter erweitert. Diese Funktion unterstützt anstelle eines großen Modells das Trainieren von einer Vielzahl kleiner Modelle (ein Modell pro Datenpartition).

- **Windows Server-Failovercluster**: Konfigurieren Sie Hochverfügbarkeit für Machine Learning Services in einem Windows Server-Failovercluster.

Weitere Informationen finden Sie unter [Neuigkeiten zu SQL Server Machine Learning Services](../advanced-analytics/what-s-new-in-sql-server-machine-learning-services.md).

### <a name="lightweight-query-profiling-infrastructure-enabled-by-default"></a>Standardmäßig aktivierte LWP-Abfrageinfrastruktur (Lightweight Profiling)

Die LWP-Abfrageinfrastruktur (Lightweight Profiling) stellt Abfrageleistungsdaten effizienter bereit als standardmäßige Profilerstellungstechnologien. Lightweight Profiling ist ab sofort standardmäßig aktiviert. Diese Infrastruktur wurde in [!INCLUDE[ssSQL15](../includes/sssql15-md.md)] SP1 eingeführt. Lightweight Profiling bietet eine Methode zur Sammlung von Statistiken zur Abfrageausführung mit einem erwarteten CPU-Overhead von 2 % im Vergleich zu einem CPU-Overhead von bis zu 75 % für die Standardmethode zur Abfrageprofilerstellung. In älteren Versionen war diese Option standardmäßig deaktiviert. Datenbankadministratoren konnten diese mit dem [Ablaufverfolgungsflag 7412](../t-sql/database-console-commands/dbcc-traceon-trace-flags-transact-sql.md) aktivieren. 

Weitere Informationen zu Lightweight Profiling finden Sie unter [Wahl des Entwicklers: Abfragestatus – jederzeit und überall](http://blogs.msdn.microsoft.com/sql_server_team/query-progress-anytime-anywhere/).

### <a id="polybase"></a>Neue PolyBase-Connectors

- **Neue Connectors für [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)], Oracle, Teradata und MongoDB**: In [!INCLUDE[sql-server-2019](../includes/sssqlv15-md.md)] werden neue Connectors für externe Daten für [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)], Oracle, Teradata und MongoDB eingeführt.

### <a name="new-sysdmdbpageinfo-system-function-returns-page-information"></a>Rückgabe von Seiteninformationen durch neue sys.dm_db_page_info-Systemfunktion

`sys.dm_db_page_info(database_id, file_id, page_id, mode)` gibt Informationen zu einer Seite in einer Datenbank zurück. Die Funktion gibt eine Zeile zurück, die die Headerinformationen der Seite enthält, einschließlich `object_id`, `index_id` und `partition_id`. Dank dieser Funktion ist die Verwendung von `DBCC PAGE` in den meisten Fällen nicht mehr erforderlich.  

Um eine Problembehandlung für die seitenbezogenen Wartevorgänge zu ermöglichen, wurde außerdem eine neue Spalte namens „page_resource“ zu `sys.dm_exec_requests` und `sys.sysprocesses` hinzugefügt. Mit dieser neuen Spalte können Sie `sys.dm_db_page_info` durch eine weitere neue Systemfunktion namens `sys.fn_PageResCracker` mit diesen Ansichten verknüpfen. Sehen Sie sich als Beispiel das folgende Skript an:

```sql
SELECT page_info.* 
FROM sys.dm_exec_requests AS d 
  CROSS APPLY sys.fn_PageResCracker(d.page_resource) AS r
  CROSS APPLY sys.dm_db_page_info(r.db_id, r.file_id, r.page_id,'DETAILED')
    AS page_info;
```

## <a id="sqllinux"></a> SQL Server unter Linux

- **Replikationsunterstützung**: [!INCLUDE[sql-server-2019](../includes/sssqlv15-md.md)] unterstützt die SQL Server-Replikation unter Linux. Bei einem virtuellen Linux-Computer mit dem SQL Server-Agent kann es sich um einen Verleger, einen Verteiler oder einen Abonnenten handeln. 

  Erstellen Sie die folgenden Arten von Veröffentlichungen:
  - Transaktion
  - Momentaufnahme
  - Merge

  Konfigurieren Sie die Replikation [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] oder verwenden Sie [gespeicherte Replikationsprozeduren](../relational-databases/system-stored-procedures/replication-stored-procedures-transact-sql.md).

- **Unterstützung für den Microsoft Distributed Transaction Coordinator (MSDTC)**: SQL Server 2019 unter Linux unterstützt den Microsoft Distributed Transaction Coordinator (MSDTC). Weitere Informationen finden Sie unter [Gewusst wie: Konfigurieren des Microsoft Distributed Transaction Coordinator (MSDTC) unter Linux](../linux/sql-server-linux-configure-msdtc.md).

- **Always On-Verfügbarkeitsgruppe in Docker-Containern mit Kubernetes**: Kubernetes kann Container orchestrieren, auf denen [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]-Instanzen ausgeführt werden, um eine hochverfügbare Gruppe von Datenbanken mit SQL Server Always On-Verfügbarkeitsgruppen bereitzustellen. Ein Kubernetes-Operator stellt ein StatefulSet bereit, einschließlich eines Containers mit einem **mssql-server-Container** und einem Integritätsmonitor.

- **OpenLDAP-Unterstützung für AD-Drittanbieter**: [!INCLUDE[sql-server-2019](../includes/sssqlv15-md.md)] unter Linux unterstützt OpenLDAP, mit dem Drittanbieter zu Active Directory beitreten können.

- **Machine Learning unter Linux**: SQL Server 2019 Machine Learning Services (datenbankintern) wird ab sofort unter Linux unterstützt. Dies umfasst die Unterstützung für die gespeicherte `sp_execute_external_script`-Prozedur. Anweisungen zum Installieren von Machine Learning Services unter Linux finden Sie unter [Installieren von SQL Server 2019 Machine Learning Services (R, Python, Java) unter Linux](../linux/sql-server-linux-setup-machine-learning.md).

- **Neue Containerregistrierung**: Alle Containerimages für [!INCLUDE[sql-server-2019](../includes/sssqlv15-md.md)] sowie [!INCLUDE[ssSQL17](../includes/sssql17-md.md)] befinden sich nun in Microsoft Container Registry. Microsoft Container Registry ist die offizielle Containerregistrierung für die Verteilung von Microsoft-Produktcontainern. Darüber hinaus werden ab sofort zertifizierte RHEL-basierte Images veröffentlicht.

  - Microsoft Container Registry: `mcr.microsoft.com/mssql/server:vNext-CTP2.0`
  - Zertifizierte RHEL-basierte Containerimages: `mcr.microsoft.com/mssql/rhel/server:vNext-CTP2.0`

## <a id="mds"></a> Master Data Services (MDS)

- **Ersetzung der Silverlight-Steuerelemente durch HTML**: Das MDS-Portal (Master Data Services) ist nicht mehr von Silverlight abhängig. Alle veralteten Silverlight-Komponenten wurden durch HTML-Steuerelemente ersetzt.

## <a id="security"></a>Sicherheit

- **Zertifikatverwaltung im SQL Server-Konfigurations-Manager**: SSL/TLS-Zertifikate werden häufig zum Schutz des Zugriffs auf SQL Server-Instanzen verwendet. Die Zertifikatverwaltung ist ab sofort im SQL Server-Konfigurations-Manager integriert, was allgemeine Aufgaben wie die Folgenden vereinfacht:

  - Anzeigen und Überprüfen der auf einer [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]-Instanz installierten Zertifikate 
  - Anzeigen von bald ablaufenden Zertifikaten
  - Bereitstellen von Zertifikaten auf Computern, die Always On-Verfügbarkeitsgruppen angehören (auf dem Knoten, auf dem sich das primäre Replikat befindet)
  - Bereitstellen von Zertifikaten auf Computern, die einer Failoverclusterinstanz angehören (auf dem aktiven Knoten)

  > [!NOTE]
  > Benutzer müssen über Administratorberechtigungen auf allen Clusterknoten verfügen.

## <a id="tools"></a>Tools

- [**Azure Data Studio**](../azure-data-studio/what-is.md): Bei Azure Data Studio, das ehemals unter dem Vorschaunamen „SQL Operations Studio“ veröffentlicht wurde, handelt es sich um ein plattformübergreifendes Open Source-Desktoptool für die gängigsten Aufgaben in der Datenentwicklung und Verwaltung, das einfach und modern ist. Mit Azure Data Studio können Sie unter Windows, macOS und Linux eine Verbindung mit einer lokalen SQL Server-Instanz und in der Cloud herstellen. Mit Azure Data Studio können Sie Folgendes:

  - Bearbeiten und Ausführen von Abfragen in einer modernen Entwicklungsumgebung mit extrem schnellen IntelliSense-Informationen, Codeausschnitten und integrierter Quellcodeverwaltung.  
  - Schnelles Visualisieren von Daten mit integrierten Diagrammen zu Ihren Resultsets  
  - Erstellen von benutzerdefinierten Dashboards für Ihre Server und Datenbanken mithilfe von anpassbaren Widgets  
  - Einfaches Verwalten Ihrer größeren Umgebung mit dem integrierten Terminal  
  - Analysieren von Daten in einer integrierten Notebookumgebung, die auf Jupyter basiert  
  - Verbesserung der Benutzererfahrung durch benutzerdefinierte Designs und Erweiterungen  
  - Untersuchen von Azure-Ressourcen mit integriertem Abonnement und Ressourcenbrowser
  - Unterstützung für Szenarien mit SQL Server-Big Data-Clustern


- [**SQL Server Management Studio (SSMS) 18.0 (Vorschau)**](../ssms/sql-server-management-studio-ssms.md)

  - Unterstützung für [!INCLUDE[sql-server-2019](../includes/sssqlv15-md.md)]
  - Unterstützung für Always Encrypted mit Secure Enclaves
  - Geringere Downloadgröße
  - Ab sofort Visual Studio 2017 Isolated Shell als Grundlage
  - Eine vollständige Liste finden Sie unter [SQL Server Management Studio – Änderungsprotokoll (SSMS)](../ssms/sql-server-management-studio-changelog-ssms.md).

## <a name="other-services"></a>Weitere Dienste

In [!INCLUDE[sql-server-2019](../includes/sssqlv15-md.md)] CTP 2.0 werden für die folgenden Dienste keine neuen Features eingeführt:

- [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Analysis Services (SSAS)
- [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] (SSIS)
- [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] (SSRS)

## <a name="next-steps"></a>Nächste Schritte

- [Versionsanmerkungen zu SQL Server 2019](sql-server-ver15-release-notes.md)

- [Whitepaper zu Microsoft SQL Server 2019](https://info.microsoft.com/rs/157-GQE-382/images/EN-US-CNTNT-white-paper-DBMod-Microsoft-SQL-Server-2019-Technical-white-paper.pdf)<br />Veröffentlicht im September 2018. Gilt für Microsoft SQL Server 2019 CTP 2.0 für Windows-, Linux- und Docker-Container.


[!INCLUDE[get-help-options](../includes/paragraph-content/get-help-options.md)]
