---
title: Visão geral de rastreamento analítico
ms.date: 03/30/2017
helpviewer_keywords:
- analytic tracing [WCF], overview
ms.assetid: ae55e9cc-0809-442f-921f-d644290ebf15
ms.openlocfilehash: 6170accc01e837bba0afb446f67a6c6272e7dde7
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70798207"
---
# <a name="analytic-tracing-overview"></a>Visão geral de rastreamento analítico
O rastreamento analítico [!INCLUDE[netfx_current_long](../../../../../includes/netfx-current-long-md.md)] no é um conjunto de recursos de rastreamento de alto desempenho e baixo nível de detalhes sobre o ETW (rastreamento de eventos para Windows). O ETW é executado no nível de kernel para reduzir muito a sobrecarga das operações de rastreamento. Ele armazena com eficiência os eventos de modo kernel e de usuário e permite a habilitação dinâmica de log sem a necessidade de reinicializações do serviço. Os dados de rastreamento estão disponíveis nos logs de eventos após serem emitidos e recebidos.  
  
 Para obter mais informações sobre o ETW, consulte [melhorar a depuração e ajuste de desempenho com o ETW](https://go.microsoft.com/fwlink/?LinkId=164781).  
  
 Além de usar os logs de eventos do sistema Windows, segurança e aplicativo para analisar o aplicativo [!INCLUDE[wv](../../../../../includes/wv-md.md)] e [!INCLUDE[lserver](../../../../../includes/lserver-md.md)] introduziu logs adicionais no nó de nível superior dos logs de aplicativos e serviços. A finalidade desses novos logs é armazenar eventos para um determinado aplicativo ou componente específico em vez de eventos globais que têm um impacto em todo o sistema (como o tipo de eventos que o log de eventos de segurança pode registrar). [!INCLUDE[netfx_current_short](../../../../../includes/netfx-current-short-md.md)]unifica e correlaciona o registro em log de eventos de rastreamento do WCF, logs de mensagens [!INCLUDE[wf1](../../../../../includes/wf1-md.md)] do WCF e registros de rastreamento para os logs de aplicativos e serviços.  
  
## <a name="concepts-and-capabilities"></a>Conceitos e funcionalidades  
 Os conceitos e funcionalidades a seguir se aplicam ao rastreamento analítico do WCF.  
  
### <a name="enabling-wcf-diagnostics-settings"></a>Habilitando as configurações de diagnóstico do WCF  
 O diagnóstico do \<WCF está habilitado na seção System.\<ServiceModel > Diagnostics > de configuração.  
  
```xml  
<system.serviceModel>  
  <diagnostics>  
```  
  
 As configurações de diagnóstico do WCF para um aplicativo virtual do IIS hospedado na Web são habilitadas em seu arquivo ' Web. config '. Outra opção é criar um Web. config em um subdiretório dentro do aplicativo.  Essa opção aplica as configurações a todos os serviços em um subdiretório.  Para garantir que as configurações de diagnóstico sejam inicializadas consistentemente para todos os serviços dentro do aplicativo, as configurações devem estar dentro do Web. config no diretório do aplicativo e não em um dos subdiretórios individuais dentro do aplicativo.  
  
### <a name="channels"></a>Canais  
 O ETW permite que os componentes de software direcionem eventos de rastreamento para um público específico por meio do uso de canais. Por exemplo, você pode enviar eventos para administradores do sistema para um canal e eventos que os desenvolvedores de aplicativos se preocupam com outro canal. Os canais são nomeados e registrados com o Windows para que os consumidores possam exibir os eventos de um canal usando o Visualizador de Eventos.  
  
 O recurso de rastreamento analítico para WCF [!INCLUDE[netfx_current_short](../../../../../includes/netfx-current-short-md.md)] em grava no canal Microsoft-Windows-Application-Server-Applications. Esse canal foi projetado especificamente para os usuários que desejam monitorar a integridade dos serviços WCF em produção. Ele define um pequeno conjunto de eventos que podem ser usados em muitos cenários de monitoramento de integridade e solução de problemas.  
  
 Para habilitar o manifesto de rastreamento de eventos do Windows para que as mensagens sejam decodificadas corretamente no log de eventos, use a ferramenta ServiceModelReg na linha de comando da seguinte maneira:  
  
 `ServiceModelReg.exe -i -c:etw`  
  
### <a name="dynamic-configuration"></a>Configuração dinâmica  
 A infraestrutura de ETW permite que o rastreamento seja habilitado e configurado dinamicamente usando ferramentas padrão do Windows. Para obter mais informações, consulte [habilitando dinamicamente o rastreamento analítico](dynamically-enabling-analytic-tracing.md).  
  
### <a name="message-flow-tracing"></a>Rastreamento de fluxo de mensagens  
 Para obter mais informações sobre como habilitar o rastreamento de fluxo de mensagens, consulte [Configurando o rastreamento de fluxo de mensagens](configuring-message-flow-tracing.md).  
  
### <a name="keywords"></a>Palavras-chave  
 As palavras-chave são usadas para filtrar mensagens de rastreamento e definir qual componente do .NET Framework emitiu o evento. Para obter mais informações, consulte [habilitando dinamicamente o rastreamento analítico](dynamically-enabling-analytic-tracing.md).
