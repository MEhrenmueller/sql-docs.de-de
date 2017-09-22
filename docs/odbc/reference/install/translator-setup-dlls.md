---
title: Konvertierer Setup DLLs | Microsoft Docs
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- translator setup DLL [ODBC]
ms.assetid: b3ca79e9-01b9-4541-81de-bbbad24ca736
caps.latest.revision: 8
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: dc2fa42c2535d794dcf93160bf79b71d8c226640
ms.contentlocale: de-de
ms.lasthandoff: 09/09/2017

---
# <a name="translator-setup-dlls"></a>Konvertierer-Setup-DLLs
> [!NOTE]  
>  Ab Windows XP und Windows Server 2003, ist ODBC in der Windows-Betriebssystem enthalten. Sie sollten nur explizit ODBC in früheren Versionen von Windows installieren.  
  
 Das Konvertierungsprogramm-Setup-DLL enthält die **ConfigTranslator** Funktion, die die Standardoption für ein Konvertierungsprogramm zurückgibt. Falls erforderlich, wird diese Informationen vom Benutzer zur Eingabe aufgefordert. Eine vollständige Beschreibung dieser Funktion, finden Sie unter [Setup DLL-API-Referenz](../../../odbc/reference/syntax/setup-dll-api-reference.md).  
  
 Das Konvertierungsprogramm-Setup wird vom Entwickler Konvertierer DLL geschrieben. Teil des Konvertierungsprogramms möglich DLL oder eine separate DLL.