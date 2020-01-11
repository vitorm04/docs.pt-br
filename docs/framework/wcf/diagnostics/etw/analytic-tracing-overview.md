---
title: Visão geral de rastreamento analítico
ms.date: 03/30/2017
helpviewer_keywords:
- analytic tracing [WCF], overview
ms.assetid: ae55e9cc-0809-442f-921f-d644290ebf15
ms.openlocfilehash: 7718c8f2a82178bedc080eda0cd0fdf728213a27
ms.sourcegitcommit: 7088f87e9a7da144266135f4b2397e611cf0a228
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/11/2020
ms.locfileid: "75900634"
---
# <a name="analytic-tracing-overview"></a>Visão geral do rastreamento analítico

O rastreamento analítico no [!INCLUDE[netfx_current_long](../../../../../includes/netfx-current-long-md.md)] é um conjunto de recursos de rastreamento de alto desempenho e baixo nível de detalhes na parte superior do ETW (rastreamento de eventos para Windows). O ETW é executado no nível de kernel para reduzir muito a sobrecarga das operações de rastreamento. Ele armazena com eficiência os eventos de modo kernel e de usuário e permite a habilitação dinâmica de log sem a necessidade de reinicializações do serviço. Os dados de rastreamento estão disponíveis nos logs de eventos após serem emitidos e recebidos.

Para obter mais informações sobre o ETW, consulte [melhorar a depuração e ajuste de desempenho com o ETW](https://docs.microsoft.com/archive/msdn-magazine/2007/april/event-tracing-improve-debugging-and-performance-tuning-with-etw).

 Além de usar o sistema Windows, a segurança e os logs de eventos do aplicativo para analisar o aplicativo, o Windows Vista e o Windows Server 2008 introduziram logs adicionais no nó de nível superior de logs de aplicativos e serviços. A finalidade desses novos logs é armazenar eventos para um determinado aplicativo ou componente específico em vez de eventos globais que têm um impacto em todo o sistema (como o tipo de eventos que o log de eventos de segurança pode registrar). [!INCLUDE[netfx_current_short](../../../../../includes/netfx-current-short-md.md)] unifica e correlaciona o registro em log de eventos de rastreamento do WCF, logs de mensagens do WCF e [!INCLUDE[wf1](../../../../../includes/wf1-md.md)] registros de rastreamento para os logs de aplicativos e serviços.

As seções a seguir abrangem conceitos e funcionalidades que se aplicam ao rastreamento analítico do WCF.

## <a name="enable-wcf-diagnostics-settings"></a>Habilitar configurações de diagnóstico do WCF

O diagnóstico do WCF está habilitado na seção de configuração do `<system.serviceModel><diagnostics>`.

```xml
<system.serviceModel>
  <diagnostics>
```

As configurações de diagnóstico do WCF para um aplicativo virtual do IIS hospedado na Web são habilitadas em seu arquivo *Web. config* . Outra opção é criar um arquivo *Web. config* em um subdiretório dentro do aplicativo. Essa opção aplica as configurações a todos os serviços em um subdiretório. Para garantir que as configurações de diagnóstico sejam inicializadas consistentemente para todos os serviços no aplicativo, as configurações devem estar no arquivo *Web. config* no diretório do aplicativo e não em um dos subdiretórios individuais dentro do aplicativo.

## <a name="channels"></a>Canais

O ETW permite que os componentes de software direcionem eventos de rastreamento para um público específico por meio do uso de canais. Por exemplo, você pode enviar eventos para administradores do sistema para um canal e eventos que os desenvolvedores de aplicativos se preocupam com outro canal. Os canais são nomeados e registrados com o Windows para que os consumidores possam exibir os eventos de um canal usando Visualizador de Eventos.

 O recurso de rastreamento analítico para WCF no [!INCLUDE[netfx_current_short](../../../../../includes/netfx-current-short-md.md)] grava no canal Microsoft-Windows-Application-Server-Applications. Esse canal é projetado para usuários que desejam monitorar a integridade dos serviços WCF em produção. Ele define um pequeno conjunto de eventos que podem ser usados em muitos cenários de monitoramento e solução de problemas de integridade.

 Para habilitar o manifesto de rastreamento de eventos do Windows para que as mensagens sejam decodificadas corretamente no log de eventos, use a ferramenta ServiceModelReg na linha de comando da seguinte maneira:

 `ServiceModelReg.exe -i -c:etw`

## <a name="dynamic-configuration"></a>Configuração dinâmica

A infraestrutura de ETW permite que o rastreamento seja habilitado e configurado dinamicamente usando ferramentas padrão do Windows. Para obter mais informações, consulte [habilitando dinamicamente o rastreamento analítico](dynamically-enabling-analytic-tracing.md).

## <a name="message-flow-tracing"></a>Rastreamento de fluxo de mensagens

Para obter mais informações sobre como habilitar o rastreamento de fluxo de mensagens, consulte [Configurando o rastreamento de fluxo de mensagens](configuring-message-flow-tracing.md).

## <a name="keywords"></a>Palavras-chave

As palavras-chave são usadas para filtrar mensagens de rastreamento e definir qual componente do .NET Framework emitiu o evento. Para obter mais informações, consulte [habilitando dinamicamente o rastreamento analítico](dynamically-enabling-analytic-tracing.md).
