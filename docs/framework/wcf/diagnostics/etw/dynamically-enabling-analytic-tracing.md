---
title: Rastreamento analítico habilitado dinamicamente
ms.date: 03/30/2017
ms.assetid: 58b63cfc-307a-427d-b69d-9917ff9f44ac
ms.openlocfilehash: 219561b1acd2259daad4c984dcf0b15517166c3f
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59197471"
---
# <a name="dynamically-enabling-analytic-tracing"></a>Rastreamento analítico habilitado dinamicamente
Usando as ferramentas fornecidas com o sistema operacional Windows, você pode habilitar ou desabilitar o rastreamento dinamicamente usando o rastreamento de eventos para Windows (ETW). Para todos os [!INCLUDE[netfx_current_long](../../../../../includes/netfx-current-long-md.md)] serviços Windows Communication Foundation (WCF), o rastreamento analítico pode ser habilitados e desabilitados dinamicamente sem modificar o arquivo do aplicativo Web. config ou reiniciar o serviço. Isso permite que o aplicativo que emite os eventos de rastreamento para permanecer inalterado.  
  
 As opções de rastreamento do WCF podem ser configuradas de maneira semelhante. Por exemplo, você pode alterar o nível de severidade de **erro** à **informações** sem afetar o aplicativo. Isso pode ser feito usando as seguintes ferramentas:  
  
-   **Logman** – uma ferramenta de linha de comando para configurar, controlar e consultar dados de rastreamento. Para obter mais informações, consulte [Logman criar rastreamento](https://go.microsoft.com/fwlink/?LinkId=165426) e [Logman atualização rastreamento](https://go.microsoft.com/fwlink/?LinkId=165427).  
  
-   **Visualizar eventos** -ferramenta de gerenciamento gráfico do Windows para exibir os resultados de rastreamento. Para obter mais informações, consulte [os serviços WCF e rastreamento de eventos para Windows](../../../../../docs/framework/wcf/samples/wcf-services-and-event-tracing-for-windows.md) e [Visualizador de eventos](https://go.microsoft.com/fwlink/?LinkId=165428).  
  
-   **PerfMon** – ferramenta de gerenciamento gráfico do Windows que usa contadores de contadores do monitor de rastreamento e os efeitos do rastreamento sobre o desempenho. Para obter mais informações, consulte [criar um Data Collector definir manualmente](https://go.microsoft.com/fwlink/?LinkId=165429).  
  
### <a name="keywords"></a>Palavras-chave  
 Ao usar o <xref:System.ServiceModel.Activation.Configuration.ServiceModelActivationSectionGroup.Diagnostics%2A> de classe do .NET Framework, geralmente, as mensagens de rastreamento são filtradas pelo nível de gravidade (por exemplo, erro, aviso e informações). ETW suporta o conceito de nível de severidade, mas apresenta um mecanismo de filtro de nova e flexível usando palavras-chave. Palavras-chave são valores arbitrários de textuais que permitem que os eventos de rastreamento de fornecer contexto adicional sobre o que significa que o evento.  
  
 Para o rastreamento analítico do WCF, cada evento de rastreamento tem dois tipos de palavras-chave. Em primeiro lugar, cada evento tem um ou mais palavras-chave de cenário. Essas palavras-chave denota os cenários que esse evento é destinado ao suporte. Há três palavras-chave de cenário, cada um projetado para uma finalidade específica, conforme mostrado na tabela a seguir. Filtragem usando palavras-chave pode ser alterado dinamicamente sem afetar o serviço WCF. Isso significa que você pode alterar dinamicamente seu cenário de rastreamento atual e a quantidade de você coletar as informações de rastreamento. Por exemplo, você pode alterar `HealthMonitoring` para `Troubleshooting` e aumentar a granularidade de rastreamento de eventos.  
  
|Palavra-chave|Descrição|  
|-------------|-----------------|  
|`HealthMonitoring`|Muito simples e mínima de rastreamento que permite que você monitore a atividade do seu serviço.|  
|`EndToEndMonitoring`|Eventos usados para dar suporte ao rastreamento de fluxo de mensagem.|  
|`Troubleshooting`|Eventos mais granulares em torno dos pontos de extensibilidade do WCF.|  
  
 O segundo grupo de palavras-chave definem qual componente do [!INCLUDE[dnprdnshort](../../../../../includes/dnprdnshort-md.md)] emitiu o evento.  
  
|Palavra-chave|Descrição|  
|-------------|-----------------|  
|`UserEvents`|Eventos emitidos pelo código do usuário e não o [!INCLUDE[dnprdnshort](../../../../../includes/dnprdnshort-md.md)].|  
|`ServiceModel`|Eventos emitidos pelo runtime do WCF.|  
|`ServiceHost`|Eventos emitidos pelo host de serviço.|  
|`WCFMessageLogging`|Eventos de registro em log de mensagem do WCF.|  
  
## <a name="see-also"></a>Consulte também

- [Serviços do WCF e Rastreamento de Eventos para Windows](../../../../../docs/framework/wcf/samples/wcf-services-and-event-tracing-for-windows.md)
