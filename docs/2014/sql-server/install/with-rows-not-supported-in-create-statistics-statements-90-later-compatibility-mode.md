---
title: MIT Zeilen wird in CREATE STATISTICS-Anweisungen im Kompatibilitätsmodus 90 oder höher nicht unterstützt | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- database-engine
ms.topic: conceptual
helpviewer_keywords:
- WITH ROWS in CREATE STATISTICS statement
ms.assetid: 197b2ecf-a1a3-4a3a-a523-a0ee919c1dde
author: mashamsft
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 7318340d5bf5e5861c1a95d6fa8cc9e54679f4a5
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/02/2018
ms.locfileid: "48137510"
---
# <a name="with-rows-is-not-supported-in-create-statistics-statements-in-the-compatibility-mode-of-90-or-later"></a>Im Kompatibilitätsmodus 90 oder höher wird WITH ROWS in CREATE STATISTICS-Anweisungen nicht unterstützt
  Wenn Sie [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ausführen und der Kompatibilitätsmodus auf 90 oder höher festgelegt ist, wird die Angabe von WITH ROWS in CREATE STATISTICS-Anweisungen nicht unterstützt.  
  
## <a name="component"></a>Komponente  
 [!INCLUDE[ssDE](../../includes/ssde-md.md)]  
  
## <a name="corrective-action"></a>Korrekturmaßnahme  
 Ändern Sie CREATE STATISTICS-Anweisungen, die WITH ROWS enthalten, durch Angabe von WITH SAMPLE *Anzahl* Zeilen oder durch Angabe der anderen Optionen, die kompatibel mit der dokumentierten Syntax. Weitere Informationen hierzu finden Sie im Thema "CREATE STATISTICS (Transact-SQL) in der SQL Server-Onlinedokumentation.  
  
## <a name="see-also"></a>Siehe auch  
 [Datenbank-Engine-Upgrade-Probleme](../../../2014/sql-server/install/database-engine-upgrade-issues.md)   
 [SQL Server 2014 Upgrade Advisor &#91;neu&#93;](/sql/2014/sql-server/install/sql-server-2014-upgrade-advisor)  
  
  
