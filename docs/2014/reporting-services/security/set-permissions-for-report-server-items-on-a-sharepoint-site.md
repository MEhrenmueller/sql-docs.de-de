---
title: Festlegen von Berechtigungen für Berichtsserverelemente auf einer SharePoint-Website (Reporting Services im integrierten SharePoint-Modus) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- permissions [Reporting Services], SharePoint integrated mode
- SharePoint integration [Reporting Services], permissions
ms.assetid: 2467c657-a3bf-4ec3-a88c-8877df19823d
author: markingmyname
ms.author: maghan
manager: craigg
ms.openlocfilehash: ad14d7005dc01c700b99c4a41cc8f95cac30da02
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/02/2018
ms.locfileid: "48078641"
---
# <a name="set-permissions-for-report-server-items-on-a-sharepoint-site-reporting-services-in-sharepoint-integrated-mode"></a>Festlegen von Berechtigungen für Berichtsserverelemente auf einer SharePoint-Website (Reporting Services im integrierten SharePoint-Modus)
  Wenn von den standardmäßigen Sicherheitseinstellungen nicht die gewünschte Zugriffsebene bereitgestellt wird, können Sie neue Berechtigungen erstellen, die Zugriff auf bestimmte Berichtsserverelemente oder -vorgänge bieten. Benutzerdefinierte Sicherheitseinstellungen können nützlich sein, wenn Sie den Zugriff auf einen bestimmten Bericht einschränken möchten.  
  
 Sie müssen der Websitebesitzer sein, um Berechtigungsebenen und -gruppen erstellen zu können. Berechtigungsebenen werden in einer Website global verwendet. Wenn Sie eine neue Berechtigungsebene erstellen, ist diese auch für andere Websitebesitzer verfügbar.  
  
 Die meisten Berechtigungen werden von einer übergeordneten Website geerbt. Wenn Sie Berechtigungen für eine bestimmte Bibliothek oder ein bestimmtes Element zuweisen, unterbrechen Sie die Berechtigungsvererbung und verursachen zusätzlichen Verwaltungsaufwand für die Berechtigungen für diesen Zweig der Websitehierarchie.  
  
 Sie können Berechtigungen für Berichtsdefinitionen (RDL-Dateien), Modelle (SMDL-Dateien) und freigegebene Datenquellen (RSDS-Dateien) festlegen. Sie können vererbte und verwaltete Berechtigungen nicht für dasselbe Element kombinieren. Wenn Sie Berechtigungen direkt verwalten möchten, haben vererbte Berechtigungen keine Auswirkungen auf das aktuelle Element. Wenn Sie die Berechtigungsvererbung später wiederherstellen möchten, können Sie im Menü **Aktionen** die Option **Berechtigungen erben** auswählen.  
  
 Um Berechtigungen für Entitäten und Perspektiven in einem Modell festlegen zu können, müssen Sie für das Modell über die Berechtigungsebene Vollzugriff verfügen. Die Berechtigung Vollzugriff enthält die Berechtigung "Berechtigungen verwalten". Diese Berechtigung auf Websiteebene wird Websitebesitzern und anderen SharePoint-Gruppen erteilt, die über die Berechtigungsebene Vollzugriff verfügen. Wenn Sie bestimmten Benutzern die Möglichkeit bieten möchten, die Modellelementsicherheit festzulegen, müssen Sie die Berechtigungsvererbung unterbrechen und dem Benutzer oder der Gruppe erhöhte Berechtigungen für die Modelldatei erteilen (z. B. Vollzugriff). Wenn Sie Vollzugriff für ein Element, z. B. eine Datei in der Bibliothek, erteilen, sind die Berechtigungen auf dieses Element beschränkt und gelten nicht für das übergeordnete Element oder andere Elemente in derselben Bibliothek. Sobald der Benutzer über die Berechtigung Berechtigungen verwalten für das Modell verfügt, kann er die Modellelementsicherheit über die SharePoint-Website oder im Modell-Designer festlegen.  
  
### <a name="to-set-permissions-on-an-individual-report-model-or-data-source"></a>So legen Sie Berechtigungen für einen einzelnen Bericht, ein Modell oder eine Datenquelle fest  
  
1.  Wenn die Bibliothek nicht bereits geöffnet ist, klicken Sie auf ihren Namen auf der Schnellstartleiste. Wenn der Name der Bibliothek nicht angezeigt wird, klicken Sie auf **Alle Websiteinhalte einblenden**und anschließend auf den Namen der Bibliothek.  
  
2.  Zeigen Sie auf die Datei mit dem Bericht, dem Berichtsmodell oder der freigegebenen Datenquelle.  
  
3.  Klicken Sie auf den Pfeil nach unten, und klicken Sie im Menü auf **Berechtigungen verwalten**.  
  
4.  Klicken Sie im Menü **Aktionen** auf **Berechtigungen bearbeiten**, und klicken Sie dann auf **OK** , um die Aktion zu bestätigen.  
  
5.  Wenn Sie einem Benutzer oder einer Gruppe ohne Berechtigungen zum Verwenden der Datei nun Berechtigungen erteilen möchten, klicken Sie auf **Neu**und dann auf **Benutzer hinzufügen**.  
  
6.  Wenn Sie Berechtigungen für einen vorhandenen Benutzer oder eine Gruppe entfernen oder ändern möchten, aktivieren Sie das Kontrollkästchen neben dem Benutzer bzw. der Gruppe, und klicken Sie auf **Aktionen**und dann auf **Benutzerberechtigungen entfernen** oder **Benutzerberechtigungen bearbeiten**.  
  
### <a name="to-set-permissions-that-enable-model-item-security"></a>So legen Sie Berechtigungen fest, mit denen die Modellelementsicherheit aktiviert wird  
  
1.  Melden Sie sich an der SharePoint-Website mit einem Konto an, das über die Berechtigung Berechtigungen verwalten für die Website verfügt.  
  
2.  Öffnen Sie die Bibliothek, die das Modell enthält.  
  
3.  Zeigen Sie auf das Modell.  
  
4.  Klicken Sie auf den Pfeil nach unten neben dem Modell, und klicken Sie auf **Berechtigungen verwalten**.  
  
5.  Klicken Sie auf **Aktionen**.  
  
6.  Klicken Sie auf **Berechtigungen bearbeiten**. Klicken Sie auf **OK**.  
  
7.  Klicken Sie auf **Neu**.  
  
8.  Klicken Sie auf **Benutzer hinzufügen**.  
  
9. Geben Sie in Benutzer/Gruppen das Benutzerkonto ein.  
  
10. Wählen Sie **Benutzern eine Berechtigung direkt erteilen**aus.  
  
11. Klicken Sie auf **Vollzugriff**.  
  
12. Klicken Sie auf **OK**. Wenn ein Benutzer Berechtigungen für ein bestimmtes Modell verwalten kann, kann dieser Benutzer das Modell öffnen, um Berechtigungen in diesem Modell zu bearbeiten.  
  
## <a name="see-also"></a>Siehe auch  
 [Verwenden der integrierten Sicherheit in Windows SharePointServices für Berichtsserverelemente](use-built-in-security-in-windows-sharepoint-services-for-report-server-items.md)   
 [Festlegen von Berechtigungen für Berichtsservervorgänge in einer SharePoint-Webanwendung](set-permissions-for-report-server-operations-in-a-sharepoint-web-application.md)   
 [Vergleichen der Rollen und Aufgaben in Reporting Services mit SharePoint-Gruppen und Berechtigungen](../reporting-services-roles-tasks-vs-sharepoint-groups-permissions.md)   
 [SharePoint-Website Referenz- und Listenberechtigungen für Berichtsserverelemente](sharepoint-site-and-list-permission-reference-for-report-server-items.md)   
 [Granting Permissions on Report Server Items on a SharePoint Site (Erteilen von Berechtigungen für Berichtsserverelemente auf einer SharePoint-Website)](granting-permissions-on-report-server-items-on-a-sharepoint-site.md)  
  
  
