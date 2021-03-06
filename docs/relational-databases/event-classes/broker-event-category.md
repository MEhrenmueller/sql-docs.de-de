---
title: Broker (Ereigniskategorie) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- SQL Server event classes, Broker event category
- Broker event category [SQL Server]
- event classes [SQL Server], Broker event category
ms.assetid: 470dc93c-0dda-4d89-829b-937738d59b31
author: stevestein
ms.author: sstein
manager: craigg
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: 8f62304b466f5de4716b702f014e39dc72b759b8
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/01/2018
ms.locfileid: "47856138"
---
# <a name="broker-event-category"></a>Broker (Ereigniskategorie)
[!INCLUDE[appliesto-ss-asdb-xxxx-xxx-md](../../includes/appliesto-ss-asdb-xxxx-xxx-md.md)]
  Die **Broker** -Ereigniskategorie enthält allgemeine Service Broker-Ereignisse.  
  
## <a name="in-this-section"></a>In diesem Abschnitt  
  
|Thema|und Beschreibung|  
|-----------|-----------------|  
|[Broker:Activation (Ereignisklasse)](../../relational-databases/event-classes/broker-activation-event-class.md)|Ein Ereignis, das generiert wird, wenn durch eine Warteschlangenüberwachung eine gespeicherte Aktivierungsprozedur gestartet wird.|  
|[Broker:Connection (Ereignisklasse)](../../relational-databases/event-classes/broker-connection-event-class.md)|Ein Ereignis, das generiert wird, um den Status einer von Service Broker verwalteten Transportverbindung zu melden.|  
|[Broker:Conversation (Ereignisklasse)](../../relational-databases/event-classes/broker-conversation-event-class.md)|Ein Ereignis, das generiert wird, um den Fortschritt einer Konversation zu melden.|  
|[Broker:Conversation Group (Ereignisklasse)](../../relational-databases/event-classes/broker-conversation-group-event-class.md)|Ein Ereignis, das generiert wird, wenn die Datenbank eine Konversationsgruppe erstellt oder löscht.|  
|[Broker:Corrupted Message (Ereignisklasse)](../../relational-databases/event-classes/broker-corrupted-message-event-class.md)|Ein Ereignis, das zum Angeben einer fehlerhaften, von der Datenbank erhaltenen Nachricht generiert wird.|  
|[Broker:Forwarded Message Dropped (Ereignisklasse)](../../relational-databases/event-classes/broker-forwarded-message-dropped-event-class.md)|Ein Ereignis, das generiert wird, wenn SQL Server eine Service Broker-Nachricht löscht, die hätte weitergeleitet werden sollen.|  
|[Broker:Forwarded Message Sent (Ereignisklasse)](../../relational-databases/event-classes/broker-forwarded-message-sent-event-class.md)|Ein Ereignis, das generiert wird, wenn SQL Server eine Service Broker-Nachricht weiterleitet.|  
|[Broker:Message Classify (Ereignisklasse)](../../relational-databases/event-classes/broker-message-classify-event-class.md)|Ein Ereignis, das generiert wird, wenn Service Broker das Routing für eine Nachricht bestimmt.|  
|[Broker:Message Drop (Ereignisklasse)](../../relational-databases/event-classes/broker-message-drop-event-class.md)|Ein Ereignis, das generiert wird, wenn Service Broker eine empfangene Nachricht nicht beibehalten kann, die in dieser Instanz an einen Dienst weitergeleitet werden sollte.|  
|[Broker:Remote Message Ack (Ereignisklasse)](../../relational-databases/event-classes/broker-remote-message-ack-event-class.md)|Ein Ereignis, das generiert wird, wenn Service Broker eine Nachrichtenbestätigung sendet oder empfängt.|  
  
 Service Broker bietet auch zwei Sicherheitsüberwachungsereignisse. Weitere Informationen zu diesen Ereignissen finden Sie unter [Audit Broker Login (Ereignisklasse)](../../relational-databases/event-classes/audit-broker-login-event-class.md) und [Audit Broker Conversation (Ereignisklasse)](../../relational-databases/event-classes/audit-broker-conversation-event-class.md).  
  
## <a name="see-also"></a>Weitere Informationen finden Sie unter  
 [Sicherheitsüberwachung-Ereigniskategorie](../../analysis-services/trace-events/security-audit-event-category.md)  
  
  
