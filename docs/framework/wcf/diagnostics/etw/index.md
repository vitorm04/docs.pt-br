---
title: "Rastreamento analítico com ETW"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- diagnostics [WCF], analytic tracing
- administration [WCF], analytic tracing
- analytic tracing [WCF]
ms.assetid: 1d518e47-a38d-41e8-93d7-8c3b361f6a56
caps.latest.revision: "6"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: a16f66ed8443749764e66d2616ae566ad788d571
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="analytic-tracing-with-etw"></a>Rastreamento analítico com ETW
[!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)]rastreamento analítico oferece uma maneira de capturar informações de diagnóstico durante a execução de um [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] serviço. [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)]eventos de rastreamento analítico são emitidos em pontos importantes a [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] pilha para permitir a solução de problemas de [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] serviços em um ambiente de produção. Rastreamento analítico para [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] services tem um impacto mínimo sobre o desempenho de um produto de servidor que hospeda [!INCLUDE[netfx_current_long](../../../../../includes/netfx-current-long-md.md)] [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] serviços como esses eventos são emitidos com muita eficiência em uma sessão de rastreamento de eventos para Windows (ETW).  
  
## <a name="in-this-section"></a>Nesta seção  
 [Visão geral de rastreamento analítico](../../../../../docs/framework/wcf/diagnostics/etw/analytic-tracing-overview.md)  
 Discute como [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] rastreamento analítico funciona em [!INCLUDE[netfx_current_long](../../../../../includes/netfx-current-long-md.md)].  
  
 [Rastreamento analítico habilitado dinamicamente](../../../../../docs/framework/wcf/diagnostics/etw/dynamically-enabling-analytic-tracing.md)  
 Descreve como habilitar ou desabilitar o rastreamento dinamicamente com o ETW.  
  
 [Configurando o rastreamento de fluxo de mensagem](../../../../../docs/framework/wcf/diagnostics/etw/configuring-message-flow-tracing.md)  
 Descreve como configurar o rastreamento de fluxo de mensagem.  
  
 [Referência de evento de rastreamento analítico](../../../../../docs/framework/wcf/diagnostics/etw/analytic-trace-event-reference.md)  
 Mostra uma tabela de IDs de eventos com níveis de evento, mensagens de eventos e as palavras-chave.  
  
## <a name="see-also"></a>Consulte também  
 [Serviços do WCF e Rastreamento de Eventos para Windows](../../../../../docs/framework/wcf/samples/wcf-services-and-event-tracing-for-windows.md)  
 [Acompanhamento de eventos de rastreamento de evento no Windows](../../../../../docs/framework/windows-workflow-foundation/samples/tracking-events-into-event-tracing-in-windows.md)
