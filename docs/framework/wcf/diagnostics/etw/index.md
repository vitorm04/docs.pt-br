---
title: Rastreamento analítico com ETW
ms.date: 03/30/2017
helpviewer_keywords:
- diagnostics [WCF], analytic tracing
- administration [WCF], analytic tracing
- analytic tracing [WCF]
ms.assetid: 1d518e47-a38d-41e8-93d7-8c3b361f6a56
ms.openlocfilehash: cff13439995d8a90da15b7afa15723f21574e35e
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59193703"
---
# <a name="analytic-tracing-with-etw"></a>Rastreamento analítico com ETW
Rastreamento analítico do Windows Communication Foundation (WCF) oferece uma maneira de capturar informações de diagnóstico durante a execução de um serviço WCF. Eventos de rastreamento analítico do WCF são emitidos nos pontos-chave na pilha do WCF para permitir que a solução de problemas de serviços do WCF em um ambiente de produção. Rastreamento analítico para os serviços WCF tem impacto mínimo sobre o desempenho de um produto de servidor que hospeda [!INCLUDE[netfx_current_long](../../../../../includes/netfx-current-long-md.md)] serviços WCF como esses eventos são emitidos com muita eficiência a uma sessão de rastreamento de eventos para Windows (ETW).  
  
## <a name="in-this-section"></a>Nesta seção  
 [Visão geral de rastreamento analítico](../../../../../docs/framework/wcf/diagnostics/etw/analytic-tracing-overview.md)  
 Discute como o rastreamento analítico de WCF funciona no [!INCLUDE[netfx_current_long](../../../../../includes/netfx-current-long-md.md)].  
  
 [Rastreamento analítico habilitado dinamicamente](../../../../../docs/framework/wcf/diagnostics/etw/dynamically-enabling-analytic-tracing.md)  
 Descreve como habilitar ou desabilitar o rastreamento dinamicamente usando o ETW.  
  
 [Configurando rastreamento de fluxo de mensagem](../../../../../docs/framework/wcf/diagnostics/etw/configuring-message-flow-tracing.md)  
 Descreve como configurar o rastreamento de fluxo de mensagem.  
  
 [Referência de evento de rastreamento analítico](../../../../../docs/framework/wcf/diagnostics/etw/analytic-trace-event-reference.md)  
 Mostra uma tabela de IDs de eventos com seus níveis de evento, as mensagens de evento e palavras-chave.  
  
## <a name="see-also"></a>Consulte também

- [Serviços e rastreamento de eventos WCF para Windows](../../../../../docs/framework/wcf/samples/wcf-services-and-event-tracing-for-windows.md)
- [Eventos de rastreamento no rastreamento de evento no Windows](../../../../../docs/framework/windows-workflow-foundation/samples/tracking-events-into-event-tracing-in-windows.md)
