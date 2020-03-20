---
title: Rastreamento analítico habilitado dinamicamente
ms.date: 03/30/2017
ms.assetid: 58b63cfc-307a-427d-b69d-9917ff9f44ac
ms.openlocfilehash: 22d122f802e82c2aa04d72a996cb872e06fcaeaa
ms.sourcegitcommit: 515469828d0f040e01bde01df6b8e4eb43630b06
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/06/2020
ms.locfileid: "78674951"
---
# <a name="dynamically-enabling-analytic-tracing"></a>Rastreamento analítico habilitado dinamicamente
Usando ferramentas que são fornecidas com o sistema operacional Windows, você pode ativar ou desativar o rastreamento dinamicamente usando o Event Tracing for Windows (ETW). Para [!INCLUDE[netfx_current_long](../../../../../includes/netfx-current-long-md.md)] todos os serviços do Windows Communication Foundation (WCF), o rastreamento analítico pode ser ativado e desativado dinamicamente sem modificar o arquivo Web.config do aplicativo ou reiniciar o serviço. Isso permite que a aplicação que emite os eventos de rastreamento permaneça intacta.  
  
 As opções de rastreamento WCF podem ser configuradas de forma semelhante. Por exemplo, você pode alterar o nível de gravidade de **Erro** para **Informação** sem perturbar o aplicativo. Isso pode ser feito usando as seguintes ferramentas:  
  
- **Logman** – Uma ferramenta de linha de comando para configurar, controlar e consultar dados de rastreamento. Para obter mais informações, consulte [Logman Create Trace](https://docs.microsoft.com/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc788036(v=ws.10)) e [Logman Update Trace](https://docs.microsoft.com/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc788128(v=ws.10)).  
  
- **EventViewer** - Ferramenta de gerenciamento gráfico do Windows para visualização dos resultados do rastreamento. Para obter mais informações, consulte [WCF Services and Event Tracing for Windows](../../samples/wcf-services-and-event-tracing-for-windows.md) and [Event Viewer](https://docs.microsoft.com/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc766042(v=ws.11)).  
  
- **Perfmon** – Ferramenta de gerenciamento gráfico do Windows que usa contadores para monitorar contadores de rastreamento e os efeitos do rastreamento no desempenho. Para obter mais informações, consulte [Criar um conjunto de coletor de dados manualmente](https://docs.microsoft.com/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc766404(v=ws.11)).  
  
### <a name="keywords"></a>Palavras-chave  
 Ao usar <xref:System.ServiceModel.Activation.Configuration.ServiceModelActivationSectionGroup.Diagnostics%2A> a classe, as mensagens de rastreamento do .NET Framework são geralmente filtradas pelo nível de gravidade (por exemplo, Erro, Aviso e Informações). O ETW suporta o conceito de nível de gravidade, mas introduz um novo mecanismo de filtro flexível usando palavras-chave. Palavras-chave são valores textuais arbitrários que permitem que os eventos de rastreamento forneçam contexto adicional sobre o que esse evento significa.  
  
 Para rastreamento analítico wcf, cada evento de rastreamento tem dois tipos de palavras-chave. Primeiro, cada evento tem uma ou mais palavras-chave de cenário. Essas palavras-chave denotam os cenários que este evento pretende suportar. Existem três palavras-chave de cenário, cada uma projetada para um propósito específico, conforme mostrado na tabela a seguir. A filtragem usando palavras-chave pode ser alterada dinamicamente sem perturbar o serviço WCF. Isso significa que você pode alterar dinamicamente o seu cenário atual de rastreamento e a quantidade de informações de rastreamento que você coleta. Por exemplo, você `HealthMonitoring` `Troubleshooting` pode alterar e aumentar a granularidade do Evento de Rastreamento.  
  
|Palavra-chave|Descrição|  
|-------------|-----------------|  
|`HealthMonitoring`|Rastreamento muito leve e mínimo que permite monitorar a atividade do seu serviço.|  
|`EndToEndMonitoring`|Eventos usados para suportar rastreamento de fluxo de mensagens.|  
|`Troubleshooting`|Mais eventos granulares em torno dos pontos de extensibilidade do WCF.|  
  
 O segundo grupo de palavras-chave define qual componente do Quadro .NET emitia o evento.  
  
|Palavra-chave|Descrição|  
|-------------|-----------------|  
|`UserEvents`|Eventos emitidos pelo código do usuário e não pelo Quadro .NET.|  
|`ServiceModel`|Eventos emitidos pelo tempo de execução do WCF.|  
|`ServiceHost`|Eventos emitidos pelo anfitrião do serviço.|  
|`WCFMessageLogging`|Eventos de registro de mensagens WCF.|  
  
## <a name="see-also"></a>Confira também

- [Serviços do WCF e Rastreamento de Eventos para Windows](../../samples/wcf-services-and-event-tracing-for-windows.md)
