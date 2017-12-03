---
title: "Rastreamento analítico habilitado dinamicamente"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 58b63cfc-307a-427d-b69d-9917ff9f44ac
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 4984cb7fd89b69f0006c5294c24184bd8d1f1d09
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/02/2017
---
# <a name="dynamically-enabling-analytic-tracing"></a>Rastreamento analítico habilitado dinamicamente
Usando as ferramentas fornecidas com o sistema operacional Windows, você pode habilitar ou desabilitar o rastreamento dinamicamente usando o rastreamento de eventos para Windows (ETW). Para todos os [!INCLUDE[netfx_current_long](../../../../../includes/netfx-current-long-md.md)] [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] serviços, o rastreamento analítico pode ser habilitados e desabilitados dinamicamente sem modificar o arquivo do aplicativo Web. config ou reiniciar o serviço. Isso permite que o aplicativo que emite os eventos de rastreamento para permanecer inalterado.  
  
 [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)]Opções de rastreamento podem ser configurada de maneira semelhante. Por exemplo, você pode alterar o nível de severidade de **erro** para **informações** sem afetar o aplicativo. Isso pode ser feito usando as seguintes ferramentas:  
  
-   **Logman** – uma ferramenta de linha de comando para configurar, controlar e consultar dados de rastreamento. [!INCLUDE[crdefault](../../../../../includes/crdefault-md.md)][Logman criar rastreamento](http://go.microsoft.com/fwlink/?LinkId=165426) e [atualização Logman rastreamento](http://go.microsoft.com/fwlink/?LinkId=165427).  
  
-   **Visualizar eventos** -ferramenta de gerenciamento gráfico do Windows para exibir os resultados de rastreamento. [!INCLUDE[crdefault](../../../../../includes/crdefault-md.md)][Serviços WCF e rastreamento de eventos do Windows](../../../../../docs/framework/wcf/samples/wcf-services-and-event-tracing-for-windows.md) e [Visualizador de eventos](http://go.microsoft.com/fwlink/?LinkId=165428).  
  
-   **PerfMon** – ferramenta de gerenciamento gráfico do Windows que usa contadores de contadores de monitor de rastreamento e os efeitos do rastreamento sobre o desempenho. [!INCLUDE[crdefault](../../../../../includes/crdefault-md.md)][Criar um conjunto de Coletores de dados manualmente](http://go.microsoft.com/fwlink/?LinkId=165429).  
  
### <a name="keywords"></a>Palavras-chave  
 Ao usar o <xref:System.ServiceModel.Activation.Configuration.ServiceModelActivationSectionGroup.Diagnostics%2A> classe, as mensagens de rastreamento geralmente são filtradas pelo nível de severidade (por exemplo, erro, aviso e informações) do .NET Framework. ETW oferece suporte ao conceito de nível de severidade, mas apresenta um mecanismo flexível, novo filtro usando palavras-chave. Palavras-chave são valores arbitrários de textuais que permitem que os eventos de rastreamento de fornecer um contexto adicional sobre o que significa que o evento.  
  
 Para [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] analíticos rastreamento, cada evento de rastreamento tem dois tipos de palavras-chave. Primeiro, cada evento tem um ou mais palavras-chave de cenário. Essas palavras-chave indicam os cenários que esse evento é destinado para dar suporte. Há três palavras-chave de cenário, cada criado para uma finalidade específica, conforme mostrado na tabela a seguir. Filtrar usando palavras-chave pode ser alterado dinamicamente sem afetar o [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] service. Isso significa que você pode alterar dinamicamente seu cenário de rastreamento atual e a quantidade de você coletar as informações de rastreamento. Por exemplo, você pode alterar `HealthMonitoring` para `Troubleshooting` e aumentar a granularidade de evento de rastreamento.  
  
|Palavra-chave|Descrição|  
|-------------|-----------------|  
|`HealthMonitoring`|Muito simples, mínima de rastreamento que lhe permite monitorar a atividade do serviço.|  
|`EndToEndMonitoring`|Eventos usados para oferecer suporte a rastreamento de fluxo de mensagem.|  
|`Troubleshooting`|Eventos mais granulares em torno dos pontos de extensibilidade de [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)].|  
  
 O segundo grupo de palavras-chave definir qual componente do [!INCLUDE[dnprdnshort](../../../../../includes/dnprdnshort-md.md)] emitido o evento.  
  
|Palavra-chave|Descrição|  
|-------------|-----------------|  
|`UserEvents`|Eventos emitidos pelo código do usuário e não o [!INCLUDE[dnprdnshort](../../../../../includes/dnprdnshort-md.md)].|  
|`ServiceModel`|Eventos emitidos pelo [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] tempo de execução.|  
|`ServiceHost`|Eventos emitidos pelo host de serviço.|  
|`WCFMessageLogging`|[!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)]eventos de log de mensagem.|  
  
## <a name="see-also"></a>Consulte também  
 [Serviços WCF e rastreamento de eventos do Windows](../../../../../docs/framework/wcf/samples/wcf-services-and-event-tracing-for-windows.md)
