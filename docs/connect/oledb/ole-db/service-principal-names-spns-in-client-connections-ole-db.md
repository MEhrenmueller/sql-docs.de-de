---
title: Dienstprinzipalnamen (SPN) in Clientverbindungen (OLE DB) | Microsoft-Dokumentation
description: Dienstprinzipalnamen (SPN) in Clientverbindungen (OLE DB)
ms.custom: ''
ms.date: 06/12/2018
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: connectivity
ms.topic: reference
author: pmasl
ms.author: pelopes
manager: craigg
ms.openlocfilehash: 1e00183ef3558cbad211fabeb063a81f25d5f29f
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MTE75
ms.contentlocale: de-DE
ms.lasthandoff: 10/01/2018
ms.locfileid: "47702228"
---
# <a name="service-principal-names-spns-in-client-connections-ole-db"></a>Dienstprinzipalnamen (SPN) in Clientverbindungen (OLE DB)
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

[!INCLUDE[Driver_OLEDB_Download](../../../includes/driver_oledb_download.md)]


  In diesem Thema werden OLE DB-Eigenschaften und Memberfunktionen beschrieben, die Dienstprinzipalnamen (SPN) in Clientanwendungen unterstützen. Weitere Informationen zu SPNs in Clientanwendungen finden Sie unter [Unterstützung von Dienstprinzipalnamen &#40;SPN&#41; in Clientverbindungen](../../oledb/features/service-principal-name-spn-support-in-client-connections.md). Ein Beispiel finden Sie unter [integrierte Kerberos-Authentifizierung &#40;OLE DB&#41;](../../oledb/ole-db-how-to/integrated-kerberos-authentication-ole-db.md).  
  
## <a name="provider-initialization-string-keywords"></a>Schlüsselwörter für Anbieter-Initialisierungszeichenfolgen  
 Die folgenden Schlüsselwörter für Anbieter-Initialisierungszeichenfolgen unterstützen SPNs in OLE DB-Anwendungen. In der folgenden Tabelle werden die Werte aus der Schlüsselwortspalte für die Anbieterzeichenfolge IDBInitialize::Initialize verwendet. Beim Herstellen einer Verbindung mit ADO oder IDataInitialize::GetDataSource werden die Werte aus der Beschreibungsspalte in Initialisierungszeichenfolgen verwendet.  
  
|Schlüsselwort|und Beschreibung|value|  
|-------------|-----------------|-----------|  
|ServerSPN|Server-SPN|Der SPN für den Server. Der Standardwert ist, dass eine leere Zeichenfolge, die OLE DB-Treiber für SQL Server, der Standardwert verwendet wird, vom Anbieter SPN erstellte.|  
|FailoverPartnerSPN|Failoverpartner-SPN|Der SPN für den Failoverpartner. Der Standardwert ist, dass eine leere Zeichenfolge, die OLE DB-Treiber für SQL Server, der Standardwert verwendet wird, vom Anbieter SPN erstellte.|  
  
## <a name="data-source-initialization-properties"></a>Eigenschaften zur Datenquelleninitialisierung  
 Die folgenden Eigenschaften in der **DBPROPSET_SQLSERVERDBINIT** -Eigenschaftengruppe ermöglichen es Anwendungen, SPNs anzugeben.  
  
|Name|Typ|Verwendung|  
|----------|----------|-----------|  
|SSPROP_INIT_SERVERSPN|VT_BSTR, Lese-/Schreibzugriff|Gibt den SPN für den Server an. Der Standardwert ist, dass eine leere Zeichenfolge, die OLE DB-Treiber für SQL Server, der Standardwert verwendet wird, vom Anbieter SPN erstellte.|  
|SSPROP_INIT_FAILOVERPARTNERSPN|VT_BSTR, Lese-/Schreibzugriff|Gibt den SPN für den Failoverpartner an. Der Standardwert ist, dass eine leere Zeichenfolge, die OLE DB-Treiber für SQL Server, der Standardwert verwendet wird, vom Anbieter SPN erstellte.|  
  
## <a name="data-source-properties"></a>Datenquelleneigenschaften  
 Die folgenden Eigenschaften in der **DBPROPSET_SQLSERVERDATASOURCEINFO** -Eigenschaftengruppe ermöglichen es Anwendungen, die Authentifizierungsmethode zu ermitteln.  
  
|Name|Typ|Verwendung|  
|----------|----------|-----------|  
|SSPROP_INTEGRATEDAUTHENTICATIONMETHOD|VT_BSTR, schreibgeschützt|Gibt die für die aktuelle Verbindung verwendete Authentifizierungsmethode zurück. Der zurückgegebene Wert für die Anwendung ist der Wert, den Windows, OLE DB-Treiber für SQL Server zurückgibt. Folgende Werte sind möglich: <br />"NTLM" wird zurückgegeben, wenn eine Verbindung mit der NTLM-Authentifizierung geöffnet wird.<br />"Kerberos" wird zurückgegeben, wenn eine Verbindung mit der Kerberos-Authentifizierung geöffnet wird.<br /><br /> Wenn eine Verbindung geöffnet wurde und die Authentifizierungsmethode nicht bestimmt werden kann, wird "VT_EMPTY" zurückgegeben.<br /><br /> Diese Eigenschaft kann nur gelesen werden, wenn eine Datenquelle initialisiert wurde. Wenn Sie versuchen, die Eigenschaft vor der Initialisierung einer Datenquelle zu lesen, gibt IDBProperties::GetProperies DB_S_ERRORSOCCURRED bzw. DB_E_ERRORSOCCURRED zurück, und DBPROPSTATUS_NOTSUPPORTED wird für diese Eigenschaft in DBPROPSET_PROPERTIESINERROR festgelegt. Dieses Verhalten entspricht der OLE DB-Kernspezifikation.|  
|SSPROP_MUTUALLYAUTHENICATED|VT_BOOL, schreibgeschützt|Gibt VARIANT_TRUE zurück, wenn die Server in der Verbindung gegenseitig authentifiziert wurden; andernfalls wird VARIANT_FALSE zurückgegeben.<br /><br /> Diese Eigenschaft kann nur gelesen werden, wenn eine Datenquelle initialisiert wurde. Wenn Sie versuchen, die Eigenschaft vor der Initialisierung einer Datenquelle zu lesen, gibt IDBProperties::GetProperies DB_S_ERRORSOCCURRED bzw. DB_E_ERRORSOCCURRED zurück, und DBPROPSTATUS_NOTSUPPORTED wird für diese Eigenschaft in DBPROPSET_PROPERTIESINERROR festgelegt. Dieses Verhalten entspricht der OLE DB-Kernspezifikation.<br /><br /> Wenn dieses Attribut für eine Verbindung abgefragt wird, für die keine Windows-Authentifizierung verwendet wurde, wird VARIANT_FALSE zurückgegeben.|  
  
## <a name="ole-db-api-support-for-spns"></a>OLE DB-API-Unterstützung für SPNs  
 In der folgenden Tabelle werden die OLE DB-Memberfunktionen beschrieben, die SPNs in Clientverbindungen unterstützen:  
  
|Memberfunktion|und Beschreibung|  
|---------------------|-----------------|  
|IDataInitialize::GetDataSource|*pwszInitializationString* kann die neuen Schlüsselwörter **ServerSPN** und **FailoverPartnerSPN**enthalten.|  
|IDataInitialize::GetInitializationString|Wenn SSPROP_INIT_SERVERSPN und SSPROP_INIT_FAILOVERPARTNERSPN Nichtstandardwerte aufweisen, werden sie durch *ppwszInitString* als Schlüsselwortwerte für **ServerSPN** und **FailoverPartnerSPN**in die Initialisierungszeichenfolge aufgenommen. Andernfalls sind diese Schlüsselwörter nicht in der Initialisierungszeichenfolge enthalten.|  
|IDBInitialize::Initialize|Sind durch die Einstellung von DBPROP_INIT_PROMPT in den Eigenschaften zur Datenquelleninitialisierung Aufforderungen aktiviert, wird das OLE DB-Anmeldedialogfeld angezeigt. Damit können SPNs sowohl für den Prinzipalserver als auch für seinen Failoverpartner eingegeben werden.<br /><br /> Sofern festgelegt, erkennt die Anbieterzeichenfolge in DPPROP_INIT_PROVIDERSTRING die neuen Schlüsselwörter **ServerSPN** und **FailoverPartnerSPN** und verwendet ihre Werte (sofern vorhanden) zur Initialisierung von SSPROP_INIT_SERVER_SPN und SSPROP_INIT_FAILOVER_PARTNER_SPN.<br /><br /> IDBProperties:: SetProperties kann aufgerufen werden, um die Eigenschaften SSPROP_INIT_SERVER_SPN und SSPROP_INIT_FAILOVER_PARTNER_SPN festzulegen, bevor IDBInitialize:: Initialize aufgerufen wird. Dies ist eine Alternative zum Verwenden einer Anbieterzeichenfolge.<br /><br /> Wird eine Eigenschaft mehrfach festgelegt, hat ein programmgesteuert festgelegter Wert Vorrang vor einem in der Anbieterzeichenfolge festgelegten Wert. Ein in einer Initialisierungszeichenfolge festgelegter Wert hat Vorrang vor einem in einem Anmeldedialogfeld festgelegten Wert.<br /><br /> Kommt ein Schlüsselwort mehrfach in der Anbieterzeichenfolge vor, hat der an erster Stelle stehende Wert Vorrang.|  
|IDBProperties::GetProperties|IDBProperties::GetProperties kann aufgerufen werden, um die Werte der neuen Eigenschaften zur Datenquelleninitialisierung SSPROP_INIT_SERVERSPN und SSPROP_INIT_FAILOVERPARTNERSPN sowie der neuen Datenquelleneigenschaften SSPROP_AUTHENTICATIONMETHOD und SSPROP_MUTUALLYAUTHENTICATED abzurufen.|  
|IdbProperties::GetPropertyInfo|IdbProperties::GetPropertyInfo beinhaltet die neuen Eigenschaften zur Datenquelleninitialisierung SSPROP_INIT_SERVERSPN und SSPROP_INIT_FAILOVERPARTNERSPN oder die neuen Datenquelleneigenschaften SSPROP_AUTHENTICATION_METHOD und SSPROP_MUTUALLYAUTHENTICATED.|  
|IDBProperties::SetProperties|IDBProperties::SetProperties kann aufgerufen werden, um die Werte der neuen Eigenschaften zur Datenquelleninitialisierung SSPROP_INITSERVERSPN und SSPROP_INIT_FAILOVERPARTNERSPN festzulegen.<br /><br /> Diese Eigenschaften können zu einem beliebigen Zeitpunkt festgelegt werden. Ist die Datenquelle jedoch bereits geöffnet, wird der folgende Fehler zurückgegeben: DB_E_ERRORSOCCURRED, "Fehler bei einem aus mehreren Schritten bestehenden OLE DB-Vorgang. Prüfen Sie die einzelnen OLE DB-Statuswerte, falls vorhanden. Daten wurden nicht verarbeitet."|  
  
## <a name="see-also"></a>Weitere Informationen finden Sie unter  
 [OLE DB-Treiber für SQL Server-Programmierung](../../oledb/ole-db/oledb-driver-for-sql-server-programming.md)  
  
  
