---
title: Rastreamentos significativos
ms.date: 03/30/2017
ms.assetid: 40a1770e-3b09-4142-b0dd-f9ef73642074
ms.openlocfilehash: c230c65b4d3fd45c4905d4ae5f4cbbf90e10faad
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61784938"
---
# <a name="significant-traces"></a>Rastreamentos significativos
Este tópico lista alguns dos principais rastreamentos emitidos pelo Windows Communication Foundation (WCF).  
  
## <a name="significant-traces"></a>Rastreamentos significativos  
  
|Rastrear|Descrição|  
|-----------|-----------------|  
|Rastreamento de log de mensagem|O rastreamento é emitido quando uma mensagem WCF for registrada pelo log de mensagens de recursos quando o `System.ServiceModel.MessageLogging` origem de rastreamento está habilitada. Clicar neste rastreamento exibe a mensagem. Há quatro pontos de registro em log configurável para uma mensagem: `ServiceLevelSendRequest`, `TransportSend`, `TransportReceive`, `ServiceLevelReceiveRequest`, também indicado pelo atributo de origem da mensagem no rastreamento de log de mensagem.|  
|Rastreamento de mensagem recebida|Esse rastreamento é emitido quando uma mensagem do WCF é recebida se a `System.ServiceModel` origem de rastreamento está habilitada no nível detalhado ou informações. Esse rastreamento é necessário para ver a seta de correlação da mensagem no modo de gráfico de atividade.|  
|Rastreamento de mensagens enviadas|Esse rastreamento é emitido quando uma mensagem WCF será enviada se o `System.ServiceModel` origem de rastreamento está habilitada no nível detalhado ou informações. Esse rastreamento é necessário para ver a seta de correlação da mensagem no modo de gráfico de atividade.|  
|Získat Element ChannelEndpointElement|Esse rastreamento é emitido na fábrica de canais de construção em nível de informações. Ele fornece uma descrição do ponto de extremidade o cliente está se comunicando com (endereço remoto, associação, nome do contrato).|  
|Získat Element ServiceElement|Esse rastreamento é emitido no host de serviço de construção, no nível de informações. Ele fornece uma descrição do contrato de serviço e associação.|  
|Criar SocketConnection|Esse rastreamento é emitido na primeira ação de processo realizadas pelo cliente e na atividade de bytes de recebimento no serviço. Ele fornece os endereços IP locais e remotos. Ele é emitido no nível de informações.|
