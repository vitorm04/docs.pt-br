---
title: Rastreamento analítico com ETW
ms.date: 03/30/2017
helpviewer_keywords:
- diagnostics [WCF], analytic tracing
- administration [WCF], analytic tracing
- analytic tracing [WCF]
ms.assetid: 1d518e47-a38d-41e8-93d7-8c3b361f6a56
ms.openlocfilehash: 210418b8a8765a1fc59658e9df57c92ce087c95f
ms.sourcegitcommit: 15109844229ade1c6449f48f3834db1b26907824
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/07/2018
ms.locfileid: "33809258"
---
# <a name="analytic-tracing-with-etw"></a>Rastreamento analítico com ETW
Rastreamento analítico do Windows Communication Foundation (WCF) oferece uma maneira de capturar informações de diagnóstico durante a execução de um serviço WCF. Eventos de rastreamento analítico do WCF são emitidos nos pontos-chave na pilha do WCF para permitir a solução de problemas de serviços do WCF em um ambiente de produção. Rastreamento analítico para serviços WCF tem um impacto mínimo sobre o desempenho de um produto de servidor que hospeda [!INCLUDE[netfx_current_long](../../../../../includes/netfx-current-long-md.md)] dos serviços WCF como esses eventos são emitidos com muita eficiência em uma sessão de rastreamento de eventos para Windows (ETW).  
  
## <a name="in-this-section"></a>Nesta seção  
 [Visão geral de rastreamento analítico](../../../../../docs/framework/wcf/diagnostics/etw/analytic-tracing-overview.md)  
 Discute como rastreamento analítico do WCF funciona no [!INCLUDE[netfx_current_long](../../../../../includes/netfx-current-long-md.md)].  
  
 [Rastreamento analítico habilitado dinamicamente](../../../../../docs/framework/wcf/diagnostics/etw/dynamically-enabling-analytic-tracing.md)  
 Descreve como habilitar ou desabilitar o rastreamento dinamicamente com o ETW.  
  
 [Configurando o rastreamento de fluxo de mensagem](../../../../../docs/framework/wcf/diagnostics/etw/configuring-message-flow-tracing.md)  
 Descreve como configurar o rastreamento de fluxo de mensagem.  
  
 [Referência de evento de rastreamento analítico](../../../../../docs/framework/wcf/diagnostics/etw/analytic-trace-event-reference.md)  
 Mostra uma tabela de IDs de eventos com níveis de evento, mensagens de eventos e as palavras-chave.  
  
## <a name="see-also"></a>Consulte também  
 [Serviços do WCF e Rastreamento de Eventos para Windows](../../../../../docs/framework/wcf/samples/wcf-services-and-event-tracing-for-windows.md)  
 [Acompanhamento de eventos de rastreamento de evento no Windows](../../../../../docs/framework/windows-workflow-foundation/samples/tracking-events-into-event-tracing-in-windows.md)
