---
title: "Eventos ETW de monitoramento de recursos de domínio de aplicativo (ARM)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- ETW, application domain monitoring events
- application domain monitoring events [.NET Framework]
ms.assetid: d38ff268-a2ee-434e-b504-d570880e0289
caps.latest.revision: 8
author: mairaw
ms.author: mairaw
manager: wpickett
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: a93e8cc1ab0b7488f920b556d2073d2813c3b7a9
ms.contentlocale: pt-br
ms.lasthandoff: 08/21/2017

---
# <a name="application-domain-resource-monitoring-arm-etw-events"></a>Eventos ETW de monitoramento de recursos de domínio de aplicativo (ARM)
<a name="top"></a> Esses eventos fornecem informações de diagnóstico detalhadas sobre o estado de um domínio do aplicativo. Use esses eventos ou o recurso ARM (monitoramento de recursos do domínio do aplicativo) para obter as mesmas informações.  
  
 Esta categoria consiste nos seguintes eventos:  
  
-   [Evento ThreadCreated](#threadcreated_event)  
  
-   [Evento AppDomainMemAllocated](#appdomainmemallocated_event)  
  
-   [Evento AppDomainMemSurvived](#appdomainmemsurvived_event)  
  
-   [Evento ThreadAppDomainEnter](#threadappdomainenter_event)  
  
-   [Evento ThreadTerminated](#threadterminated_event)  
  
<a name="threadcreated_event"></a>   
## <a name="threadcreated-event"></a>Evento ThreadCreated  
 Esse evento também é acionado no provedor de encerramento como `ThreadDC` (com a palavra-chave `AppDomainResourceManagementRundownKeyword`). Esse é o único evento acionado no provedor de encerramento nessa categoria.  
  
 A tabela a seguir mostra a palavra-chave e o nível. (Para obter mais informações, consulte [Palavras-chaves e níveis CLR ETW](../../../docs/framework/performance/clr-etw-keywords-and-levels.md).)  
  
|Palavra-chave para acionar o evento|Nível|  
|-----------------------------------|-----------|  
|`AppDomainResourceManagementKeyword` (0x800)|Informativo(4)|  
|`ThreadingKeyword` (0x10000)|Informativo(4)|  
  
 A tabela a seguir mostra as informações do evento.  
  
|Evento|ID do evento|Acionado quando|  
|-----------|--------------|-----------------|  
|`ThreadCreated`|85|Um thread foi criado para o domínio do aplicativo.|  
  
 A tabela a seguir mostra os dados do evento.  
  
|Nome do campo|Tipo de dados|Descrição|  
|----------------|---------------|-----------------|  
|ThreadID|win:UInt64|ID do thread que foi criado.|  
|AppDomainID|win:UInt64|Identificador do domínio do aplicativo para o qual a atividade do thread está sendo relatada.|  
|Sinalizadores|win:UInt32|Sinalizadores de criação do thread.|  
|ManagedThreadIndex|win:UInt32|Índice gerenciado do thread que foi criado.|  
|OSThreadID|win:UInt32|ID do sistema operacional do thread que foi criado.|  
|ClrInstanceID|win:UInt16|ID exclusiva da instância do CLR ou do CoreCLR.|  
  
 [Voltar ao início](#top)  
  
<a name="appdomainmemallocated_event"></a>   
## <a name="appdomainmemallocated-event"></a>Evento AppDomainMemAllocated  
 A tabela a seguir mostra a palavra-chave e o nível.  
  
|Palavra-chave para acionar o evento|Nível|  
|-----------------------------------|-----------|  
|`AppDomainResourceManagementKeyword` (0x800)|Informativo(4)|  
  
 A tabela a seguir mostra as informações do evento.  
  
|Evento|ID do evento|Acionado quando|  
|-----------|--------------|-----------------|  
|`AppDomainMemAllocated`|83|Cada 4 MB de memória (aproximadamente) é alocado no domínio do aplicativo.|  
  
 A tabela a seguir mostra os dados do evento.  
  
|Nome do campo|Tipo de dados|Descrição|  
|----------------|---------------|-----------------|  
|AppDomainID|win:UInt64|Identificador do domínio do aplicativo para o qual o uso de recursos está sendo relatado.|  
|Alocado|win:UInt64|O número total de bytes alocados nesse domínio do aplicativo desde que o domínio do aplicativo foi criado (a quantidade de memória liberada não é subtraída).|  
|ClrInstanceID|win:UInt16|ID exclusiva da instância do CLR ou do CoreCLR.|  
  
 [Voltar ao início](#top)  
  
<a name="appdomainmemsurvived_event"></a>   
## <a name="appdomainmemsurvived-event"></a>Evento AppDomainMemSurvived  
 A tabela a seguir mostra a palavra-chave e o nível.  
  
|Palavra-chave para acionar o evento|Nível|  
|-----------------------------------|-----------|  
|`AppDomainResourceManagementKeyword` (0x800)|Informativo(4)|  
  
 A tabela a seguir mostra as informações do evento.  
  
|Evento|ID do evento|Acionado quando|  
|-----------|--------------|-----------------|  
|`AppDomainMemSurvived`|84|Cada coleta de lixo é encerrada.|  
  
 A tabela a seguir mostra os dados do evento.  
  
|Nome do campo|Tipo de dados|Descrição|  
|----------------|---------------|-----------------|  
|AppDomainID|win:UInt64|Identificador do domínio para o qual o uso de recursos está sendo relatado.|  
|Survived|win:UInt64|O número de bytes que sobreviveram após a última coleta e que são conhecidos por serem mantidos por este domínio do aplicativo. Esse número é preciso e completo após uma coleta completa, mas pode estar incompleto após uma coleta efêmera.|  
|ProcessSurvived|win:UInt64|O total de bytes que sobreviveram da última coleta. Após uma coleta completa, esse número representa o número de bytes que estão sendo mantidos ativos em heaps gerenciados. Após uma coleta efêmera, esse número representa o número de bytes mantidos ativos em gerações efêmeras.|  
|ClrInstanceID|win:UInt16|ID exclusiva da instância do CLR ou do CoreCLR.|  
  
 [Voltar ao início](#top)  
  
<a name="threadappdomainenter_event"></a>   
## <a name="threadappdomainenter-event"></a>Evento ThreadAppDomainEnter  
 A tabela a seguir mostra a palavra-chave e o nível.  
  
|Palavra-chave para acionar o evento|Nível|  
|-----------------------------------|-----------|  
|`AppDomainResourceManagementKeyword` (0x800)|Informativo(4)|  
|`ThreadingKeyword` (0x10000)|Informativo(4)|  
  
 A tabela a seguir mostra as informações do evento.  
  
|Evento|ID do evento|Acionado quando|  
|-----------|--------------|-----------------|  
|`ThreadAppDomainEnter`|87|Um thread entra em um domínio do aplicativo.|  
  
 A tabela a seguir mostra os dados do evento.  
  
|Nome do campo|Tipo de dados|Descrição|  
|----------------|---------------|-----------------|  
|ThreadID|win:UInt64|O identificador de thread.|  
|AppDomainID|win:UInt64|O identificador do domínio do aplicativo.|  
|ClrInstanceID|win:UInt16|ID exclusiva da instância do CLR ou do CoreCLR.|  
  
 [Voltar ao início](#top)  
  
<a name="threadterminated_event"></a>   
## <a name="threadterminated-event"></a>Evento ThreadTerminated  
 A tabela a seguir mostra a palavra-chave e o nível.  
  
|Palavra-chave para acionar o evento|Nível|  
|-----------------------------------|-----------|  
|`AppDomainResourceManagementKeyword` (0x800)|Informativo(4)|  
|`ThreadingKeyword` (0x10000)|Informativo(4)|  
  
 A tabela a seguir mostra as informações do evento.  
  
|Evento|ID do evento|Acionado quando|  
|-----------|--------------|-----------------|  
|`ThreadTerminated`|86|Um thread termina.|  
  
 A seguinte tabela mostra os dados do evento:  
  
|Nome do campo|Tipo de dados|Descrição|  
|----------------|---------------|-----------------|  
|ThreadID|win:UInt64|O identificador de thread.|  
|AppDomainID|win:UInt64|O identificador do domínio do aplicativo.|  
|ClrInstanceID|win:UInt16|ID exclusiva da instância do CLR ou do CoreCLR.|  
  
## <a name="see-also"></a>Consulte também  
 [Eventos de CLR ETW](../../../docs/framework/performance/clr-etw-events.md)

