---
title: Rastreamento analítico habilitado dinamicamente
ms.date: 03/30/2017
ms.assetid: 58b63cfc-307a-427d-b69d-9917ff9f44ac
ms.openlocfilehash: bea64ac9a9312d17b7f47e72a46d876552e20a12
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70798104"
---
# <a name="dynamically-enabling-analytic-tracing"></a>Rastreamento analítico habilitado dinamicamente
Usando as ferramentas fornecidas com o sistema operacional Windows, você pode habilitar ou desabilitar o rastreamento dinamicamente usando o ETW (rastreamento de eventos para Windows). Para todos [!INCLUDE[netfx_current_long](../../../../../includes/netfx-current-long-md.md)] os serviços de Windows Communication Foundation (WCF), o rastreamento analítico pode ser habilitado e desabilitado dinamicamente sem modificar o arquivo Web. config do aplicativo ou reiniciar o serviço. Isso permite que o aplicativo que emite os eventos de rastreamento permaneça inalterado.  
  
 As opções de rastreamento do WCF podem ser configuradas de forma semelhante. Por exemplo, você pode alterar o nível de severidade de **erro** para **informações** sem perturbar o aplicativo. Isso pode ser feito usando as seguintes ferramentas:  
  
- **Logman** – uma ferramenta de linha de comando para configurar, controlar e consultar dados de rastreamento. Para obter mais informações, consulte [logman Create Trace](https://go.microsoft.com/fwlink/?LinkId=165426) e [logman update Trace](https://go.microsoft.com/fwlink/?LinkId=165427).  
  
- **Visualizador** -ferramenta de gerenciamento gráfico do Windows para exibir os resultados do rastreamento. Para obter mais informações, consulte [Serviços WCF e rastreamento de eventos para Windows](../../samples/wcf-services-and-event-tracing-for-windows.md) e [Visualizador de eventos](https://go.microsoft.com/fwlink/?LinkId=165428).  
  
- **Perfmon** – ferramenta de gerenciamento gráfico do Windows que usa contadores para monitorar contadores de rastreamento e os efeitos de rastreamento no desempenho. Para obter mais informações, consulte [criar um conjunto de coletores de dados manualmente](https://go.microsoft.com/fwlink/?LinkId=165429).  
  
### <a name="keywords"></a>Palavras-chave  
 Ao usar a <xref:System.ServiceModel.Activation.Configuration.ServiceModelActivationSectionGroup.Diagnostics%2A> classe, .NET Framework mensagens de rastreamento são geralmente filtradas pelo nível de severidade (por exemplo, erro, aviso e informações). O ETW dá suporte ao conceito de nível de severidade, mas apresenta um mecanismo de filtro novo e flexível usando palavras-chave. As palavras-chave são valores textuais arbitrários que permitem que eventos de rastreamento forneçam contexto adicional sobre o que esse evento significa.  
  
 Para o rastreamento analítico do WCF, cada evento de rastreamento tem dois tipos de palavras-chave. Primeiro, cada evento tem uma ou mais palavras-chave de cenário. Essas palavras-chave denotam os cenários aos quais esse evento se destina a dar suporte. Há três palavras-chave de cenário, cada uma projetada para uma finalidade específica, conforme mostrado na tabela a seguir. A filtragem usando palavras-chave pode ser alterada dinamicamente sem perturbar o serviço WCF. Isso significa que você pode alterar dinamicamente seu cenário de rastreamento atual e a quantidade de informações de rastreamento que você coleta. Por exemplo, você pode alterar `HealthMonitoring` para `Troubleshooting` e aumentar a granularidade do evento de rastreamento.  
  
|Palavra-chave|Descrição|  
|-------------|-----------------|  
|`HealthMonitoring`|O rastreamento mínimo muito leve que permite monitorar a atividade do serviço.|  
|`EndToEndMonitoring`|Eventos usados para dar suporte ao rastreamento de fluxo de mensagens.|  
|`Troubleshooting`|Eventos mais granulares em relação aos pontos de extensibilidade do WCF.|  
  
 O segundo grupo de palavras-chave define qual componente do .NET Framework emitiu o evento.  
  
|Palavra-chave|Descrição|  
|-------------|-----------------|  
|`UserEvents`|Eventos emitidos pelo código do usuário e não pelo .NET Framework.|  
|`ServiceModel`|Eventos emitidos pelo tempo de execução do WCF.|  
|`ServiceHost`|Eventos emitidos pelo host de serviço.|  
|`WCFMessageLogging`|Eventos de log de mensagens do WCF.|  
  
## <a name="see-also"></a>Consulte também

- [Serviços do WCF e Rastreamento de Eventos para Windows](../../samples/wcf-services-and-event-tracing-for-windows.md)
