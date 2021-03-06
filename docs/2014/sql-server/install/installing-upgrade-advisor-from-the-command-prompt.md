---
title: Installieren des Upgrade Advisors über die Eingabeaufforderung | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- database-engine
ms.topic: conceptual
helpviewer_keywords:
- installing Upgrade Advisor
- command prompt [Upgrade Advisor]
- Setup [Upgrade Advisor]
- Upgrade Advisor [SQL Server], installing
ms.assetid: a6841cc2-ca13-4b1c-9343-9e4d54312c3a
author: mashamsft
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 7e834cb85458b7fd0e265e5077500ebc4dec5f45
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/02/2018
ms.locfileid: "48095410"
---
# <a name="installing-upgrade-advisor-from-the-command-prompt"></a>Installieren des Upgrade Advisors von der Eingabeaufforderung aus
  Sie können den Upgrade Advisor entweder mithilfe des Setup-Assistenten oder an der Eingabeaufforderung installieren. Die Eingabeaufforderung ermöglicht unbeaufsichtigte und automatisierte Installationen.  
  
## <a name="installation-syntax"></a>Installationssyntax  
 Die grundlegende Syntax für die Upgrade Advisor-Installation von der Eingabeaufforderung ist folgende:  
  
 `SQLUA.msi [options]`  
  
 In der folgenden Tabelle werden die gängigsten Optionen aufgelistet.  
  
|Argument|Description|  
|--------------|-----------------|  
|/ q [n&#124;b&#124;r&#124;f]|Legt die Benutzeroberflächenebene fest:<br /><br /> n = keine Benutzeroberfläche<br /><br /> b = grundlegende Benutzeroberfläche (nur Status, keine Eingabeaufforderungen)<br /><br /> r = reduzierte Benutzeroberfläche (Dialogfeld am Ende der Installation)<br /><br /> f = Vollständige Benutzeroberfläche|  
|/L|Gibt Protokolldateioptionen an. Um alle Meldungen in *Log_file_name*, verwenden Sie **-L\*V *** Log_file_name*. Um nur Fehlermeldungen zu protokollieren, verwenden `-Le` *Log_file_name*.|  
|ADDLOCAL = ALL&AMP;#124; ENTFERNEN = ALL&AMP;#124;REINSTALL = ALL|Gibt an, dass der Upgrade Advisor installiert (ADDLOCAL), entfernt (REMOVE) oder neu installiert (REINSTALL) wird.|  
|UAINSTALLDIR=path|Installiert den Upgrade Advisor am von "path" angegebenen Speicherort.|  
  
## <a name="installation-examples"></a>Installationsbeispiele  
 Im folgenden Beispiel wird gezeigt, wie der Upgrade Advisor mithilfe der Eingabeaufforderung installiert wird:  
  
```  
SQLUA.msi /qn ADDLOCAL=ALL UAINSTALLDIR="C:\Upgrade Advisor"  
```  
  
 Sie können auch das Programm Msiexec verwenden, wenn Sie diesen Befehl ausführen:  
  
```  
Msiexec.exe /i C:\Downloads\SQLUA.msi /qn ADDLOCAL=ALL UAINSTALLDIR="C:\Upgrade Advisor"  
```  
  
 Dies kann hilfreich sein, wenn Sie zusätzliche Installationsoptionen verwenden müssen.  
  
## <a name="removal-examples"></a>Beispiele für das Entfernen von Upgrade Advisor  
 Im folgenden Beispiel wird gezeigt, wie der Upgrade Advisor mithilfe der Eingabeaufforderung entfernt wird:  
  
```  
SQLUA.msi /qn REMOVE=ALL  
```  
  
 Sie können auch das Programm Msiexec verwenden, wenn Sie diesen Befehl ausführen:  
  
```  
Msiexec.exe /i C:\Downloads\SQLUA.msi /qn REMOVE=ALL  
```  
  
## <a name="see-also"></a>Siehe auch  
 [Installieren des Upgrade Advisors](../../../2014/sql-server/install/installing-upgrade-advisor.md)   
 [Voraussetzungen für den Upgrade Advisor](../../../2014/sql-server/install/upgrade-advisor-prerequisites.md)  
  
  
