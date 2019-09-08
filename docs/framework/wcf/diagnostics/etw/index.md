---
title: Rastreamento analítico com ETW
ms.date: 03/30/2017
helpviewer_keywords:
- diagnostics [WCF], analytic tracing
- administration [WCF], analytic tracing
- analytic tracing [WCF]
ms.assetid: 1d518e47-a38d-41e8-93d7-8c3b361f6a56
ms.openlocfilehash: dd745730ca186b9489c547f790c546e95bf96372
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70798082"
---
# <a name="analytic-tracing-with-etw"></a>Rastreamento analítico com ETW
O rastreamento analítico do Windows Communication Foundation (WCF) oferece uma maneira de capturar informações de diagnóstico durante a execução de um serviço WCF. Os eventos de rastreamento analítico do WCF são emitidos em pontos-chave na pilha do WCF para permitir a solução de problemas de serviços WCF em um ambiente de produção. O rastreamento analítico para serviços WCF tem um impacto mínimo sobre o desempenho de um servidor de [!INCLUDE[netfx_current_long](../../../../../includes/netfx-current-long-md.md)] produtos que hospeda serviços WCF, pois esses eventos são emitidos com muita eficiência para uma sessão do ETW (rastreamento de eventos para Windows).  
  
## <a name="in-this-section"></a>Nesta seção  
 [Visão geral de rastreamento analítico](analytic-tracing-overview.md)  
 Discute como o rastreamento analítico do WCF funciona [!INCLUDE[netfx_current_long](../../../../../includes/netfx-current-long-md.md)]no.  
  
 [Rastreamento analítico habilitado dinamicamente](dynamically-enabling-analytic-tracing.md)  
 Discute como habilitar ou desabilitar o rastreamento dinamicamente usando o ETW.  
  
 [Configurando o rastreamento de fluxo de mensagem](configuring-message-flow-tracing.md)  
 Descreve como configurar o rastreamento de fluxo de mensagens.  
  
 [Referência de evento de rastreamento analítico](analytic-trace-event-reference.md)  
 Mostra uma tabela de IDs de evento com seus níveis de evento, mensagens de evento e palavras-chave.  
  
## <a name="see-also"></a>Consulte também

- [Serviços do WCF e Rastreamento de Eventos para Windows](../../samples/wcf-services-and-event-tracing-for-windows.md)
- [Acompanhamento de eventos de rastreamento de evento no Windows](../../../windows-workflow-foundation/samples/tracking-events-into-event-tracing-in-windows.md)
