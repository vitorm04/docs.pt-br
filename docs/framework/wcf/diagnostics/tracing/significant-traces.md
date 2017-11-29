---
title: Rastreamentos significativos
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 40a1770e-3b09-4142-b0dd-f9ef73642074
caps.latest.revision: "4"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 58322a472a59ee9d3ac9451ff1f20ed95405ac54
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="significant-traces"></a>Rastreamentos significativos
Este tópico lista alguns dos principais rastreamentos emitidos pelo [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)].  
  
## <a name="significant-traces"></a>Rastreamentos significativos  
  
|Rastrear|Descrição|  
|-----------|-----------------|  
|Rastreamento de log de mensagens|O rastreamento é emitido quando um [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] mensagem for registrada pelo log de mensagens de recursos quando o `System.ServiceModel.MessageLogging` origem de rastreamento está habilitada. Clicar neste rastreamento exibe a mensagem. Há quatro pontos de registro em log configurável para uma mensagem: `ServiceLevelSendRequest`, `TransportSend`, `TransportReceive`, `ServiceLevelReceiveRequest`, também é indicado pelo atributo de origem da mensagem no rastreamento de log de mensagem.|  
|Rastreamento de mensagem recebida|Este rastreamento é emitido quando um [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] mensagem é recebida, se o `System.ServiceModel` origem de rastreamento está habilitada no nível detalhado ou informações. Este rastreamento é necessário para ver a seta de correlação da mensagem na exibição de gráfico de atividade.|  
|Rastreamento de mensagem enviada|Este rastreamento é emitido quando um [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] mensagem é enviada se a `System.ServiceModel` origem de rastreamento está habilitada no nível detalhado ou informações. Este rastreamento é necessário para ver a seta de correlação da mensagem na exibição de gráfico de atividade.|  
|Obter ChannelEndpointElement|Este rastreamento é emitido na fábrica de canais de construção, no nível de informações. Ele fornece que uma descrição do ponto de extremidade do cliente estiver se comunicando (endereço remoto, associação, nome do contrato).|  
|Obter ServiceElement|Este rastreamento é emitido no host de serviço de construção, no nível de informações. Ele fornece uma descrição do contrato de serviço e associação.|  
|Criação de SocketConnection|Este rastreamento é emitido na ação de processo primeiro realizadas pelo cliente e na atividade de bytes de recebimento no serviço. Ele fornece os endereços IP locais e remotos. Ele é emitido no nível de informações.|
