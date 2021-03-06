---
title: Azure Feature Pack für Integration Services (SSIS) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 07/09/2018
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- SQL13.SSIS.AZURE.F1
- SQL14.SSIS.AZURE.F1
ms.assetid: 31de555f-ae62-4f2f-a6a6-77fea1fa8189
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: cb19d30afa0f1f1a8f5c9a7db6aaa060d7c92f5a
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/01/2018
ms.locfileid: "47686238"
---
# <a name="azure-feature-pack-for-integration-services-ssis"></a>Azure Feature Pack für Integration Services (SSIS)
Das SQL Server Integration Services-Feature Pack (SSIS) für Azure ist eine Erweiterung, die die auf dieser Seite für SSIS aufgelisteten Komponenten für Verbindungen mit Azure-Diensten, für die Übertragung von Daten zwischen Azure und lokalen Datenquellen und für die Verarbeitung der in Azure gespeicherten Daten bereitstellt.

[![Herunterladen des SSIS-Feature Packs für Azure](../analysis-services/media/download.png)](https://www.microsoft.com/download/details.aspx?id=54798) **Herunterladen**

- Für SQL Server 2017 – [Microsoft SQL Server 2017 Integration Services-Feature Pack für Azure](https://www.microsoft.com/download/details.aspx?id=54798)
- Für SQL Server 2016 – [Microsoft SQL Server 2016 Integration Services-Feature Pack für Azure](https://www.microsoft.com/download/details.aspx?id=49492)
- Für SQL Server 2014 – [Microsoft SQL Server 2014 Integration Services-Feature Pack für Azure](https://www.microsoft.com/download/details.aspx?id=47366)
- Für SQL Server 2012 – [Microsoft SQL Server 2012 Integration Services-Feature Pack für Azure](https://www.microsoft.com/download/details.aspx?id=47367)

Die Downloadseiten enthalten auch Informationen zu erforderlichen Komponenten. Stellen Sie sicher, dass Sie SQL Server installieren, bevor Sie Azure Feature Pack auf einem Server installieren, andernfalls sind die Komponenten im Feature Pack womöglich nicht verfügbar, wenn Sie Pakete für die SSIS-Katalogdatenbank (SSISDB) auf dem Server bereitstellen.

## <a name="components-in-the-feature-pack"></a>Komponenten im Feature Pack
-   Verbindungs-Manager

    -   [Azure Data Lake Analytics-Verbindungs-Manager](connection-manager/azure-data-lake-analytics-connection-manager.md)

    -   [Azure Data Lake Store Connection Manager (Azure Data Lake Store-Verbindungs-Manager)](../integration-services/connection-manager/azure-data-lake-store-connection-manager.md)
    
    -   [Azure HDInsight-Verbindungs-Manager](../integration-services/connection-manager/azure-hdinsight-connection-manager.md)

    -   [Azure Resource Manager-Verbindungs-Manager](../integration-services/connection-manager/azure-resource-manager-connection-manager.md)
    
    -   [Azure Storage-Verbindungs-Manager](../integration-services/connection-manager/azure-storage-connection-manager.md)

    -   [Azure-Abonnementverbindungs-Manager](../integration-services/connection-manager/azure-subscription-connection-manager.md)
    
-   Aufgaben

    -   [Azure Blob-Download-Task](../integration-services/control-flow/azure-blob-download-task.md)

    -   [Azure-Blob-Uploadtask](../integration-services/control-flow/azure-blob-upload-task.md)

    -   [Azure Data Lake Analytics-Task](control-flow/azure-data-lake-analytics-task.md)

    -   [Azure Data Lake Store-Dateisystemtask](../integration-services/control-flow/azure-data-lake-store-file-system-task.md)

    -   [Azure HDInsight Create Cluster-Task](../integration-services/control-flow/azure-hdinsight-create-cluster-task.md)

    -   [Azure HDInsight-Delete Cluster-Task](../integration-services/control-flow/azure-hdinsight-delete-cluster-task.md)
    
    -   [Azure HDInsight Hive-Task](../integration-services/control-flow/azure-hdinsight-hive-task.md)

    -   [Azure HDInsight Pig-Task](../integration-services/control-flow/azure-hdinsight-pig-task.md)

    -   [Azure SQL DW-Uploadtask](../integration-services/control-flow/azure-sql-dw-upload-task.md)

-   Datenflusskomponenten

    -   [Azure-Blob-Quelle](../integration-services/data-flow/azure-blob-source.md)

    -   [Azure-BLOB-Ziel](../integration-services/data-flow/azure-blob-destination.md)
    
    -   [Azure Data Lake Store Source](../integration-services/data-flow/azure-data-lake-store-source.md)
    
    -   [Azure Data Lake Store Destination](../integration-services/data-flow/azure-data-lake-store-destination.md)

-   Azure Blob und Azure Data Lake Store-Datei-Enumerator. Siehe [Foreach Loop Container](http://msdn.microsoft.com/library/95a19dde-61ca-4d9b-aa3d-131fa4264296) (Foreach-Schleifencontainer).

## <a name="scenario-processing-big-data"></a>Szenario: Verarbeitung großer Datenmengen
 Verwenden Sie den Azure Connector zum Ausführen der folgenden Big Data-Verarbeitungsaufgaben:

1.  Verwenden Sie den Azure Blob Upload-Task zum Hochladen von Eingabedaten in den Azure BLOB-Speicher.

2.  Verwenden Sie den Azure HDInsight Create Cluster-Task zum Erstellen eines Azure HDInsight-Clusters. Dieser Schritt ist optional, wenn Sie einen eigenen Cluster verwenden möchten.

3.  Verwenden Sie den Azure HDInsight Hive-Task oder Azure HDInsight Pig-Task zum Aufrufen eines Pig- oder Hive-Auftrags auf dem Azure HDInsight-Cluster.

4.  Verwenden Sie den Azure HDInsight Delete Cluster-Task zum Löschen des HDInsight-Clusters nach der Verwendung, wenn Sie in Schritt 2 einen HDInsight-Bedarfscluster erstellt haben.

5.  Verwenden Sie den Azure HDInsight Blob Download-Task zum Herunterladen der Pig/Hive-Ausgabedaten vom Azure BLOB-Speicher.

![SSIS-AzureConnector-BigDataScenario](../integration-services/media/ssis-azureconnector-bigdatascenario.png)
 
## <a name="scenario-managing-data-in-the-cloud"></a>Szenario: Verwalten von Daten in der Cloud
 Verwenden Sie das Azure BLOB-Ziel in einem SSIS-Paket, um Ausgabedaten in einen Azure BLOB-Speicher zu schreiben, oder verwenden Sie die Azure Blob-Quelle zum Lesen von Daten aus einem Azure BLOB-Speicher.

![SSIS-AzureConnector-CloudArchive-1](../integration-services/media/ssis-azureconnector-cloudarchive-1.png)
 
 ![SSIS-AzureConnector-CloudArchive-2](../integration-services/media/ssis-azureconnector-cloudarchive-2.png)

 Verwenden Sie den Foreach-Schleifencontainer mit dem Azure Blob-Enumerator, um Daten in mehreren BLOB-Dateien zu verarbeiten.

![SSIS-AzureConnector-CloudArchive-3](../integration-services/media/ssis-azureconnector-cloudarchive-3.png)
  
