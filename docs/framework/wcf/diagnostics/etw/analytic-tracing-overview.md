---
title: "Visão geral de rastreamento analítico"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: analytic tracing [WCF], overview
ms.assetid: ae55e9cc-0809-442f-921f-d644290ebf15
caps.latest.revision: "22"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 2dd456401073d8c7f3c7bc9fbfbe5c11dbbd4e58
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/02/2017
---
# <a name="analytic-tracing-overview"></a>Visão geral de rastreamento analítico
Rastreamento analítico em [!INCLUDE[netfx_current_long](../../../../../includes/netfx-current-long-md.md)] é um alto desempenho e o recurso de rastreamento de verbosidade baixa conjunto sobre o evento de rastreamento para Windows (ETW). ETW é executado no nível do kernel para reduzir significativamente a sobrecarga de operações de rastreamento. Ele com eficiência armazena em buffer os eventos de modo de usuário e do kernel e permite habilitar dinâmico de log sem a necessidade de serviço será reiniciado. Os dados de rastreamento estão disponíveis no caso de logs depois que ele foi emitido e recebidas.  
  
 [!INCLUDE[crabout](../../../../../includes/crabout-md.md)]ETW, consulte [melhorar a depuração e ajuste de desempenho com o ETW](http://go.microsoft.com/fwlink/?LinkId=164781).  
  
 Além de usar os logs de eventos do sistema Windows, segurança e aplicativo para analisar o aplicativo, [!INCLUDE[wv](../../../../../includes/wv-md.md)] e [!INCLUDE[lserver](../../../../../includes/lserver-md.md)] introduzida logs adicionais sob o nó de nível superior de Logs de aplicativos e serviços. É a finalidade desses novos logs armazenar eventos para um determinado aplicativo ou componente específico em vez de eventos globais que têm um impacto de todo o sistema (como o tipo de evento que pode gravar no log de eventos de segurança). [!INCLUDE[netfx_current_short](../../../../../includes/netfx-current-short-md.md)]unifica e correlaciona o log de [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] eventos de rastreamento, [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] Logs de mensagens e [!INCLUDE[wf1](../../../../../includes/wf1-md.md)] registros de rastreamento para os Logs de aplicativos e serviços.  
  
## <a name="concepts-and-capabilities"></a>Conceitos e recursos  
 Os conceitos e recursos a seguir se aplicam a [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] rastreamento analítico.  
  
### <a name="enabling-wcf-diagnostics-settings"></a>Habilitar configurações de diagnóstico do WCF  
 Diagnóstico do WCF é habilitado no \<System. ServiceModel >\<diagnóstico > seção de configuração.  
  
```xml  
<system.serviceModel>  
  <diagnostics>  
```  
  
 Configurações de diagnóstico do WCF para um aplicativo virtual hospedado da Web IIS estão habilitadas no seu ' arquivo Web. config. Outra opção é criar um Web. config em um subdiretório no aplicativo.  Essa opção aplica as configurações para todos os serviços em um subdiretório.  Para garantir que as configurações de diagnóstico são inicializadas consistente para todos os serviços do aplicativo, as configurações devem ser em Web. config no diretório de aplicativo e não em um de seus subdiretórios individuais no aplicativo.  
  
### <a name="channels"></a>Canais  
 ETW permite que os componentes de software para eventos de rastreamento direta a um público específico através do uso de canais. Por exemplo, você pode enviar eventos para os administradores do sistema para um canal e eventos que cuidado de desenvolvedores do aplicativo sobre outro canal. Os canais são nomeados e registrados com o Windows para que os consumidores podem exibir eventos do canal usando o Visualizador de eventos.  
  
 O recurso de rastreamento analítico para [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] na [!INCLUDE[netfx_current_short](../../../../../includes/netfx-current-short-md.md)] grava o canal Microsoft-Windows-aplicativo--aplicativos de servidor. Esse canal é especificamente projetado para usuários que desejam monitorar a integridade de [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] serviços em produção. Define um pequeno conjunto de eventos que podem ser usados em muitas monitoramento de integridade e cenários de solução de problemas.  
  
 Para habilitar o manifesto de rastreamento de eventos do Windows para que as mensagens são decodificar corretamente no log de eventos, use a ferramenta ServiceModelReg na linha de comando da seguinte maneira:  
  
 `ServiceModelReg.exe -i -c:etw`  
  
### <a name="dynamic-configuration"></a>Configuração dinâmica  
 A infraestrutura ETW permite que o rastreamento para ser habilitado e configurado dinamicamente usando ferramentas padrão do Windows. [!INCLUDE[crdefault](../../../../../includes/crdefault-md.md)][Rastreamento analítico habilitado dinamicamente](../../../../../docs/framework/wcf/diagnostics/etw/dynamically-enabling-analytic-tracing.md).  
  
### <a name="message-flow-tracing"></a>Rastreamento de fluxo de mensagem  
 [!INCLUDE[crabout](../../../../../includes/crabout-md.md)]como habilitar o rastreamento de fluxo de mensagem, consulte [Configurando o rastreamento de fluxo de mensagem](../../../../../docs/framework/wcf/diagnostics/etw/configuring-message-flow-tracing.md).  
  
### <a name="keywords"></a>Palavras-chave  
 Palavras-chave são usadas para filtrar as mensagens de rastreamento e definir qual componente do [!INCLUDE[dnprdnshort](../../../../../includes/dnprdnshort-md.md)] emitido o evento. [!INCLUDE[crdefault](../../../../../includes/crdefault-md.md)][Rastreamento analítico habilitado dinamicamente](../../../../../docs/framework/wcf/diagnostics/etw/dynamically-enabling-analytic-tracing.md).
