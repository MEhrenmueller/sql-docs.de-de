---
title: 'Lektion 6: Hinzufügen eines ReportViewer-Steuerelements zur Anwendung | Microsoft-Dokumentation'
ms.date: 05/18/2016
ms.prod: reporting-services
ms.prod_service: reporting-services-native
ms.technology: reporting-services
ms.topic: conceptual
ms.assetid: f9492a97-5609-4059-ae76-0fba111d4968
author: markingmyname
ms.author: maghan
ms.openlocfilehash: a3892815dee3002e06abf6c76e4604225a29749a
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/01/2018
ms.locfileid: "47777348"
---
# <a name="lesson-6-add-a-reportviewer-control-to-the-application"></a>Lektion 6: Hinzufügen eines ReportViewer-Steuerelements zur Anwendung
Nachdem Sie den untergeordneten Bericht mit dem Berichts-Assistenten entworfen haben, fügen Sie der Websiteanwendung im nächsten Schritt ein ReportViewer-Steuerelement hinzu. Wenn Sie die ASP.NET-Berichtswebsite verwenden, wurde das ReportViewer-Steuerelement bereits zur Seite „default.aspx“ hinzugefügt.   
  
### <a name="to-add-a-reportviewer-control-to-the-application"></a>So fügen Sie der Anwendung das ReportViewer-Steuerelement hinzu  
  
1.  Klicken Sie im **Projektmappen-Explorer**mit der rechten Maustaste auf **Default.aspx**, und klicken Sie auf **Sicht-Designer**.  
  
2.  Wenn das ReportViewer-Steuerelement bereits zu default.aspx hinzugefügt wurde, gehen Sie direkt zu **Schritt 4**. Ist dies nicht der Fall, dann ziehen Sie ein **ScriptManager** -Steuerelement aus der Gruppe **AJAX-Erweiterungen** im Fenster **Toolbox** auf die Entwurfsoberfläche.  
  
3.  Ziehen Sie ein **ReportViewer** -Steuerelement aus der Gruppe **Berichterstellung** unterhalb des **ScriptManager** -Steuerelements auf die Entwurfsoberfläche.  
  
4.  Öffnen Sie das Fenster **ReportViewer-Aufgaben** , indem Sie auf den Pfeil in der oberen rechten Ecke des **ReportViewer** -Steuerelements klicken.  
  
5.  Wählen Sie im Feld **Bericht auswählen** den erstellten übergeordneten Bericht aus.  
  
    Nachdem Sie einen Bericht ausgewählt haben, werden automatisch Instanzen der im Bericht verwendeten Datenquellen erstellt. Der Code wird generiert, um jede DataTable (und den zugehörigen [DataSet](http://msdn.microsoft.com/library/system.data.dataset.aspx) -Container) zu instanziieren. Gemäß den einzelnen, im Bericht verwendeten Datenquellen wird der Entwurfsoberfläche ein [ObjectDataSource](http://msdn.microsoft.com/library/system.web.ui.webcontrols.objectdatasource.aspx) -Steuerelement hinzugefügt. Dieses Datenquellen-Steuerelement wird automatisch konfiguriert.  
  
6.  Klicken Sie im Menü Erstellen auf Website erstellen.  
  
    Der Bericht wird kompiliert und alle Fehler, z. B. Syntaxfehler in einem Berichtsausdruck, werden im Bereich **Fehlerliste** angezeigt. Klicken Sie unten im Visual Studio-Fenster auf **Fehlerliste** , um den Bereich **Fehlerliste** anzuzeigen.  
  
## <a name="next-task"></a>Nächste Aufgabe  
Sie haben der Websiteanwendung erfolgreich ein ReportViewer-Steuerelement hinzugefügt. Als Nächstes fügen Sie dem übergeordneten Bericht eine Drillthroughaktion hinzu. Weitere Informationen finden Sie unter [Lektion 7: Hinzufügen einer Drillthroughaktion für den übergeordneten Bericht](../reporting-services/lesson-7-add-drillthrough-action-on-parent-report.md).  
  

