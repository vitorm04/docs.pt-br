---
title: Visão geral de rastreamento analítico
ms.date: 03/30/2017
helpviewer_keywords:
- analytic tracing [WCF], overview
ms.assetid: ae55e9cc-0809-442f-921f-d644290ebf15
ms.openlocfilehash: 9918f07d9c26c1779a1eedfbc423c31e61659334
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/01/2018
ms.locfileid: "43401175"
---
# <a name="analytic-tracing-overview"></a>Visão geral de rastreamento analítico
Rastreamento analítico em [!INCLUDE[netfx_current_long](../../../../../includes/netfx-current-long-md.md)] é um alto desempenho e o recurso de rastreamento de baixo nível de detalhes definida sobre rastreamento de eventos para Windows (ETW). ETW é executado no nível do kernel para reduzir significativamente a sobrecarga de operações de rastreamento. Com eficiência ele armazena em buffer os eventos de modo de usuário e kernel e permite habilitando dinâmico de registro em log sem a necessidade de reinicialização do serviço. Os dados de rastreamento estão disponíveis no caso de logs depois que ele foi emitido e recebidas.  
  
 Para obter mais informações sobre o ETW, consulte [melhorar a depuração e ajuste de desempenho com o ETW](https://go.microsoft.com/fwlink/?LinkId=164781).  
  
 Além de usar os logs de eventos do sistema do Windows, segurança e aplicativo para analisar o aplicativo, [!INCLUDE[wv](../../../../../includes/wv-md.md)] e [!INCLUDE[lserver](../../../../../includes/lserver-md.md)] introduzido logs adicionais sob o nó Applications and Services Logs de nível superior. É a finalidade desses novos logs armazenar eventos para um determinado aplicativo ou componente específico em vez de eventos globais que têm um impacto de todo o sistema (como o tipo de eventos que o log de eventos de segurança poderia registrar). [!INCLUDE[netfx_current_short](../../../../../includes/netfx-current-short-md.md)] unifica e correlaciona o registro em log de eventos de rastreamento do WCF, Logs de mensagens do WCF, e [!INCLUDE[wf1](../../../../../includes/wf1-md.md)] registros de rastreamento para os Logs de aplicativos e serviços.  
  
## <a name="concepts-and-capabilities"></a>Conceitos e recursos  
 Os conceitos e recursos a seguir se aplicam a rastreamento analítico do WCF.  
  
### <a name="enabling-wcf-diagnostics-settings"></a>Habilitar as configurações de diagnóstico do WCF  
 Diagnóstico do WCF é habilitado na \<System. ServiceModel >\<diagnóstico > seção de configuração.  
  
```xml  
<system.serviceModel>  
  <diagnostics>  
```  
  
 As configurações de diagnóstico do WCF para um aplicativo virtual do hospedado na Web IIS estão habilitadas no seu ' arquivo Web. config. Outra opção é criar um Web. config em um subdiretório dentro do aplicativo.  Essa opção aplica as configurações para todos os serviços dentro de um subdiretório.  Para garantir que as configurações de diagnóstico são inicializadas de forma consistente para todos os serviços dentro do aplicativo, as configurações devem ser em Web. config no diretório do aplicativo e não em um dos subdiretórios individuais dentro do aplicativo.  
  
### <a name="channels"></a>Canais  
 ETW permite que os componentes de software para eventos de rastreamento direto para um determinado público-alvo pelo uso de canais. Por exemplo, você pode enviar eventos e eventos para os administradores do sistema para um canal que cuidado de desenvolvedores de aplicativo sobre a outro canal. Os canais são nomeados e registrados com o Windows para que os consumidores podem exibir eventos do canal usando o Visualizador de eventos.  
  
 O recurso de rastreamento analítico para o WCF no [!INCLUDE[netfx_current_short](../../../../../includes/netfx-current-short-md.md)] grava no canal do Microsoft-Windows-aplicativo-aplicativos de servidor. Esse canal é projetado especificamente para usuários que desejam monitorar a integridade dos serviços do WCF em produção. Ele define um pequeno conjunto de eventos que podem ser usados em muitas opções de monitoramento de integridade e cenários de solução de problemas.  
  
 Para habilitar o manifesto de rastreamento de eventos para Windows, de modo que as mensagens são decodificadas corretamente no log de eventos, use a ferramenta ServiceModelReg na linha de comando da seguinte maneira:  
  
 `ServiceModelReg.exe -i -c:etw`  
  
### <a name="dynamic-configuration"></a>Configuração dinâmica  
 A infraestrutura ETW permite que o rastreamento para ser habilitado e configurado dinamicamente usando ferramentas padrão do Windows. Para obter mais informações, consulte [dinamicamente habilitando analítica rastreamento](../../../../../docs/framework/wcf/diagnostics/etw/dynamically-enabling-analytic-tracing.md).  
  
### <a name="message-flow-tracing"></a>Rastreamento de fluxo de mensagem  
 Para obter mais informações sobre como habilitar o rastreamento de fluxo de mensagem, consulte [Configurando o rastreamento de fluxo de mensagem](../../../../../docs/framework/wcf/diagnostics/etw/configuring-message-flow-tracing.md).  
  
### <a name="keywords"></a>Palavras-chave  
 Palavras-chave são usadas para filtrar as mensagens de rastreamento e definir qual componente do [!INCLUDE[dnprdnshort](../../../../../includes/dnprdnshort-md.md)] emitiu o evento. Para obter mais informações, consulte [dinamicamente habilitando analítica rastreamento](../../../../../docs/framework/wcf/diagnostics/etw/dynamically-enabling-analytic-tracing.md).
