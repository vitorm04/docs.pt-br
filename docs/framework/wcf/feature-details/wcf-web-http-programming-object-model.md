---
title: "Modelo de objeto de programação HTTP Web do WCF"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: ed96b5fc-ca2c-4b0d-bdba-d06b77c3cb2a
caps.latest.revision: "40"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: d71a373d3410c90f405a37e104e7d1b440a7aa14
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="wcf-web-http-programming-object-model"></a>Modelo de objeto de programação HTTP Web do WCF
O modelo de programação WCF WEB HTTP permite aos desenvolvedores expor [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] Web services por meio de solicitações HTTP básicas sem a necessidade de SOAP. O modelo de programação WCF WEB HTTP é criado sobre existente [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] modelo de extensibilidade. Define as classes a seguir:  
  
 **Modelo de programação:**  
  
-   <xref:System.ServiceModel.Web.AspNetCacheProfileAttribute>  
  
-   <xref:System.ServiceModel.Web.WebGetAttribute>  
  
-   <xref:System.ServiceModel.Web.WebInvokeAttribute>  
  
-   <xref:System.ServiceModel.Web.WebServiceHost>  
  
 **Canais e infraestrutura de Dispatcher:**  
  
-   <xref:System.ServiceModel.WebHttpBinding>  
  
-   <xref:System.ServiceModel.Description.WebHttpBehavior>  
  
 **Pontos de extensibilidade e Classes de utilitário:**  
  
-   <xref:System.UriTemplate>  
  
-   <xref:System.UriTemplateTable>  
  
-   <xref:System.ServiceModel.Dispatcher.QueryStringConverter>  
  
-   <xref:System.ServiceModel.Dispatcher.WebHttpDispatchOperationSelector>  
  
## <a name="aspnetcacheprofileattribute"></a>AspNetCacheProfileAttribute  
 O <xref:System.ServiceModel.Web.AspNetCacheProfileAttribute>, quando aplicado a uma operação de serviço, indica o ASP.NET de saída de perfil de cache no arquivo de configuração que deve ser usado por para respostas de cache da operação no Cache de saída do ASP .NET. Essa propriedade tem apenas um parâmetro, o nome do perfil de cache que especifica as configurações de cache no arquivo de configuração.  
  
## <a name="webgetattribute"></a>WebGetAttribute  
 O <xref:System.ServiceModel.Web.WebGetAttribute> atributo é usado para marcar uma operação de serviço como um que responde às solicitações HTTP GET. É um comportamento de operação passivo (o <xref:System.ServiceModel.Description.IOperationBehavior> métodos não fazem nada) que adiciona metadados para a descrição da operação. Aplicar o <xref:System.ServiceModel.Web.WebGetAttribute> não tem nenhum efeito a menos que um comportamento que procura por esses metadados na descrição da operação (especificamente, o <xref:System.ServiceModel.Description.WebHttpBehavior>) é adicionado à coleção de comportamento do serviço. O <xref:System.ServiceModel.Web.WebGetAttribute> atributo tem os parâmetros opcionais são mostrados na tabela a seguir.  
  
|Parâmetro|Descrição|  
|---------------|-----------------|  
|`BodyStyle`|Controla a quebra de linha de solicitações e respostas enviadas e recebidas da operação de serviço, a que o atributo é aplicado.|  
|`RequestFormat`|Controla como as mensagens de solicitação são formatadas.|  
|`ResponseFormat`|Controla como as mensagens de resposta são formatadas.|  
|`UriTemplate`|Especifica o modelo URI que controla quais solicitações HTTP são mapeadas para o atributo é aplicado para a operação de serviço.|  
  
## <a name="webhttpbinding"></a>WebHttpBinding  
 O <xref:System.ServiceModel.WebHttpBinding> classe incorpora o suporte para XML, JSON e dados binários brutos usando o <xref:System.ServiceModel.Channels.WebMessageEncodingBindingElement>. Ele é composto de um <xref:System.ServiceModel.Channels.HttpsTransportBindingElement>, <xref:System.ServiceModel.Channels.HttpTransportBindingElement> e um <xref:System.ServiceModel.WebHttpSecurity> objeto. O <xref:System.ServiceModel.WebHttpBinding> foi projetado para ser usado em conjunto com o <xref:System.ServiceModel.Description.WebHttpBehavior>.  
  
## <a name="webinvokeattribute"></a>WebInvokeAttribute  
 O <xref:System.ServiceModel.Web.WebInvokeAttribute> atributo é semelhante do <xref:System.ServiceModel.Web.WebGetAttribute>, mas ele é usado para marcar uma operação de serviço como uma resposta HTTP solicita diferente de GET. É um comportamento de operação passivo (o <xref:System.ServiceModel.Description.IOperationBehavior> métodos não fazem nada) que adiciona metadados para a descrição da operação. Aplicar o <xref:System.ServiceModel.Web.WebInvokeAttribute> não tem nenhum efeito a menos que um comportamento que procura por esses metadados na descrição da operação (especificamente, o <xref:System.ServiceModel.Description.WebHttpBehavior>) é adicionado à coleção de comportamento do serviço.  
  
 O <xref:System.ServiceModel.Web.WebInvokeAttribute> atributo tem os parâmetros opcionais são mostrados na tabela a seguir.  
  
|Parâmetro|Descrição|  
|---------------|-----------------|  
|`BodyStyle`|Controla a quebra de linha de solicitações e respostas enviadas e recebidas da operação de serviço, a que o atributo é aplicado.|  
|`Method`|Especifica o método HTTP mapeada para a operação de serviço.|  
|`RequestFormat`|Controla como as mensagens de solicitação são formatadas.|  
|`ResponseFormat`|Controla como as mensagens de resposta são formatadas.|  
|`UriTemplate`|Especifica o modelo URI que controla quais solicitações GET são mapeadas para o atributo é aplicado para a operação de serviço.|  
  
## <a name="uritemplate"></a>UriTemplate  
 O <xref:System.UriTemplate> classe permite que você defina um conjunto de URIs estruturalmente semelhantes. Modelos são compostos de duas partes, um caminho e uma consulta. Um caminho consiste em uma série de segmentos delimitadas por uma barra (/). Cada segmento pode ter um valor literal, um valor de variável (gravado em chaves [{}], restrita para corresponder ao conteúdo de exatamente um segmento) ou um caractere curinga (gravado como um asterisco [\*], que corresponde a "o restante do caminho"), que deve aparecer no o final do caminho. A expressão de consulta pode ser totalmente omitida. Se estiver presente, especifica uma série não ordenada de pares nome/valor. Elementos da expressão de consulta podem ser qualquer um dos pares literal (? x = 2) ou pares de variável (? x = {*valor*}). Não são permitidos valores ímpares. <xref:System.UriTemplate>é usado internamente pelo [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] modelo de programação HTTP WEB mapear específico URIs ou grupos de URIs para operações de serviço.  
  
## <a name="uritemplatetable"></a>UriTemplateTable  
 O <xref:System.UriTemplateTable> classe representa um conjunto de associação de <xref:System.UriTemplate> objetos associados a um objeto do desenvolvedor da escolha. Ele permite a correspondência candidato URIs Uniform Resource Identifier () com os modelos no conjunto e recuperar os dados associados com os modelos correspondentes. <xref:System.UriTemplateTable>é usado internamente pelo [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] modelo de programação HTTP WEB mapear específico URIs ou grupos de URIs para operações de serviço.  
  
## <a name="webservicehost"></a>WebServiceHost  
 <xref:System.ServiceModel.Web.WebServiceHost>estende o <xref:System.ServiceModel.ServiceHost> para tornar mais fácil hospedar um serviço da Web estilo não SOAP. Se <xref:System.ServiceModel.Web.WebServiceHost> não encontra nenhum ponto de extremidade na descrição do serviço, ele cria automaticamente um ponto de extremidade padrão no endereço base do serviço. Ao criar um ponto de extremidade HTTP padrão, o <xref:System.ServiceModel.Web.WebServiceHost> também desabilita a página de ajuda HTTP e a funcionalidade GET de WSDL Web Services Description Language () para o ponto de extremidade de metadados não interfere com o ponto de extremidade HTTP padrão. <xref:System.ServiceModel.Web.WebServiceHost>também garante que todos os pontos de extremidade que usam <xref:System.ServiceModel.WebHttpBinding> ter necessários <xref:System.ServiceModel.Description.WebHttpBehavior> anexado. Por fim, <xref:System.ServiceModel.Web.WebServiceHost> configura automaticamente a associação do ponto de extremidade para trabalhar com as configurações de segurança do Internet Information Services (IIS) associado quando usado em um diretório virtual seguro.  
  
## <a name="webservicehostfactory"></a>WebServiceHostFactory  
 O <xref:System.ServiceModel.Activation.WebServiceHostFactory> classe é usada para criar dinamicamente uma <xref:System.ServiceModel.Web.WebServiceHost> quando um serviço é hospedado no Internet Information Services (IIS) ou o serviço de ativação de processos do Windows (WAS). Ao contrário de um serviço auto-hospedado onde o aplicativo de hospedagem instancia o <xref:System.ServiceModel.Web.WebServiceHost>, serviços hospedados em IIS ou foi usar essa classe para criar o <xref:System.ServiceModel.Web.WebServiceHost> para o serviço. O <xref:System.ServiceModel.Activation.WebServiceHostFactory.CreateServiceHost%28System.Type%2CSystem.Uri%5B%5D%29> método é chamado quando uma solicitação de entrada para o serviço é recebida.  
  
## <a name="webhttpbehavior"></a>WebHttpBehavior  
 O <xref:System.ServiceModel.Description.WebHttpBehavior> classe fornece a formatadores necessárias, os seletores de operação e assim por diante, é necessário para suporte do serviço Web estilo na camada de modelo de serviço. Isso é implementado como um comportamento de ponto de extremidade (usado em conjunto com o <xref:System.ServiceModel.WebHttpBinding>) e permite que os formatadores e seletores de operação deve ser especificado para cada ponto de extremidade, o que permite a implementação do serviço para expor pontos de extremidade SOAP e POX.  
  
### <a name="extending-webhttpbehavior"></a>Estendendo WebHttpBehavior  
 <xref:System.ServiceModel.Description.WebHttpBehavior>é extensível, usando um número de métodos virtuais: <xref:System.ServiceModel.Description.WebHttpBehavior.GetOperationSelector%28System.ServiceModel.Description.ServiceEndpoint%29>, <xref:System.ServiceModel.Description.WebHttpBehavior.GetReplyClientFormatter%28System.ServiceModel.Description.OperationDescription%2CSystem.ServiceModel.Description.ServiceEndpoint%29>, <xref:System.ServiceModel.Description.WebHttpBehavior.GetRequestClientFormatter%28System.ServiceModel.Description.OperationDescription%2CSystem.ServiceModel.Description.ServiceEndpoint%29>, <xref:System.ServiceModel.Description.WebHttpBehavior.GetReplyDispatchFormatter%28System.ServiceModel.Description.OperationDescription%2CSystem.ServiceModel.Description.ServiceEndpoint%29>, e <xref:System.ServiceModel.Description.WebHttpBehavior.GetRequestDispatchFormatter%28System.ServiceModel.Description.OperationDescription%2CSystem.ServiceModel.Description.ServiceEndpoint%29>. Os desenvolvedores podem derivar uma classe de <xref:System.ServiceModel.Description.WebHttpBehavior> e substituir estes métodos para personalizar o comportamento padrão.  
  
 O <xref:System.ServiceModel.Description.WebScriptEnablingBehavior> é um exemplo de extensão <xref:System.ServiceModel.Description.WebHttpBehavior>. <xref:System.ServiceModel.Description.WebScriptEnablingBehavior>permite [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] pontos de extremidade para receber solicitações HTTP de um cliente do ASP.NET AJAX com base em navegador. O [AJAX Service usando HTTP POST](../../../../docs/framework/wcf/samples/ajax-service-using-http-post.md) é um exemplo de como usar esse ponto de extensibilidade.  
  
> [!WARNING]
>  Ao usar o <xref:System.ServiceModel.Description.WebScriptEnablingBehavior>, <xref:System.UriTemplate> não têm suporte em <xref:System.ServiceModel.Web.WebGetAttribute> ou <xref:System.ServiceModel.Web.WebInvokeAttribute> atributos.  
  
## <a name="webhttpdispatchoperationselector"></a>WebHttpDispatchOperationSelector  
 O <xref:System.ServiceModel.Dispatcher.WebHttpDispatchOperationSelector> classe usa <xref:System.UriTemplate> e <xref:System.UriTemplateTable> classes para enviar chamadas para operações de serviço.  
  
## <a name="compatibility"></a>Compatibilidade  
 O [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] modelo de programação HTTP WEB não usa mensagens de baseado em SOAP e, portanto, não suporta o WS-* protocolos. No entanto, você pode expor o mesmo contrato pelo ponto de extremidade duas diferentes: uma usando SOAP e outros não usando SOAP. Consulte [como: expor um contrato para clientes SOAP e Web](../../../../docs/framework/wcf/feature-details/how-to-expose-a-contract-to-soap-and-web-clients.md) para obter um exemplo.  
  
## <a name="security"></a>Segurança  
 Porque o [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] não oferece suporte a modelo de programação HTTP WEB WS-* protocolos a única maneira de proteger um serviço Web criado no [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] modelo de programação HTTP WEB é expor seu serviço usando SSL. [!INCLUDE[crabout](../../../../includes/crabout-md.md)]Configurar o SSL com [!INCLUDE[iisver](../../../../includes/iisver-md.md)] consulte [como implementar o SSL no IIS](http://go.microsoft.com/fwlink/?LinkId=131613)  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.ServiceModel.WebHttpBinding>  
 <xref:System.ServiceModel.Web.WebGetAttribute>  
 <xref:System.ServiceModel.Web.WebInvokeAttribute>  
 <xref:System.ServiceModel.Description.WebHttpBehavior>  
 <xref:System.ServiceModel.Dispatcher.WebHttpDispatchOperationSelector>  
 [Visão geral do modelo de programação HTTP Web do WCF](../../../../docs/framework/wcf/feature-details/wcf-web-http-programming-model-overview.md)
