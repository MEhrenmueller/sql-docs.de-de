---
title: SQLAGENT90 (Anwendung) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: sql-tools
ms.reviewer: ''
ms.technology:
- database-engine
ms.topic: conceptual
helpviewer_keywords:
- starting SQL Server Agent
- sqlagent90 application
- SQL Server Agent, starting
- command prompt utilities [SQL Server], sqlagent90
ms.assetid: e8b80e8d-d0c9-4500-a868-0ce08233da08
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 9df8a9a63697f6fdc2cdf75b468dcb8e39b4eb4a
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MTE75
ms.contentlocale: de-DE
ms.lasthandoff: 10/01/2018
ms.locfileid: "47678448"
---
# <a name="sqlagent90-application"></a>sqlagent90 (Anwendung)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  Mit der Anwendung **sqlagent90** wird der [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] -Agent über die Eingabeaufforderung gestartet. Normalerweise sollte der [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] -Agent über [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] oder mithilfe von SQL-SMO-Methoden in einer Anwendung gestartet werden. Führen Sie **sqlagent90** nur dann über die Eingabeaufforderung aus, wenn Sie Probleme im [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] -Agent diagnostizieren, oder wenn Sie von Ihrem primären Anbieter für technischen Support dazu aufgefordert werden.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
sqlagent90  
-c [-v] [-i instance_name]  
```  
  
## <a name="arguments"></a>Argumente  
 **-c**  
 Zeigt an, dass der [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] -Agent über die Eingabeaufforderung ausgeführt wird und unabhängig vom Microsoft Windows-Dienststeuerungs-Manager ist. Wenn **-c** verwendet wird, kann der [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] -Agent weder über die Anwendung Dienste in der Verwaltung noch über den [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] -Konfigurations-Manager gesteuert werden. Dieses Argument ist verbindlich.  
  
 **-v**  
 Zeigt an, dass der [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] -Agent im ausführlichen Modus ausgeführt wird und dass Diagnoseinformationen im Eingabeaufforderungsfenster ausgegeben werden sollen. Die Diagnoseinformationen sind mit den Informationen identisch, die in das Fehlerprotokoll des [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] -Agents geschrieben werden.  
  
 **-i** *Instanzname*  
 Zeigt an, dass der [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] -Agent eine Verbindung mit der benannten [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] -Instanz herstellt, die mit *Instanzname*angegeben wird.  
  
## <a name="remarks"></a>Remarks  
 Nach dem Anzeigen einer Copyrightmeldung zeigt **sqlagent90** Ausgaben nur dann im Eingabeaufforderungsfenster an, wenn der Schalter **-v** angegeben ist. Zum Beenden von **sqlagent90**drücken Sie STRG+C an der Eingabeaufforderung. Schließen Sie das Eingabeaufforderungsfenster nicht, bevor Sie **sqlagent90**beendet haben.  
  
## <a name="see-also"></a>Weitere Informationen finden Sie unter  
 [Automatisierte Administrationstasks &#40;SQL Server Agent&#41;](http://msdn.microsoft.com/library/541ee5ac-2c9f-4b74-b4f0-13b7bd5920b0)  
  
  
