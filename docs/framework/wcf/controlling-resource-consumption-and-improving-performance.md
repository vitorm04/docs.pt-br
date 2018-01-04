---
title: Controlando o consumo de recursos e a melhoria de desempenho
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 9a829669-5f76-4c88-80ec-92d0c62c0660
caps.latest.revision: "18"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: ecb8ae5edfb35ccaffecbfb4e960d3f4a46bad0e
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="controlling-resource-consumption-and-improving-performance"></a>Controlando o consumo de recursos e a melhoria de desempenho
Este tópico descreve várias propriedades em áreas diferentes do [!INCLUDE[indigo1](../../../includes/indigo1-md.md)] arquitetura que funcionam para controlar o consumo de recursos e afetar o desempenho.  
  
## <a name="properties-that-constrain-resource-consumption-in-wcf"></a>Propriedades que restringem o consumo de recursos no WCF  
 [!INCLUDE[indigo1](../../../includes/indigo1-md.md)]Aplica restrições em determinados tipos de processos para fins de segurança ou desempenho. Essas restrições têm duas formas principais, cotas e limitações. *Cotas* são os limites que quando atingido ou excedido disparam uma exceção imediata em algum momento no sistema. *Limita* são os limites que não causam imediatamente uma exceção seja lançada. Em vez disso, quando um limite for atingido, o processamento continuará, mas dentro dos limites definida por esse valor do acelerador. Esse processamento limitado pode disparar uma exceção em outro lugar, mas isso depende do aplicativo.  
  
 A diferença entre as cotas e limitações, além de algumas propriedades de restrições estão localizadas no nível de serialização, alguns no nível do transporte e alguns no nível do aplicativo. Por exemplo, a cota <xref:System.ServiceModel.Channels.TransportBindingElement.MaxReceivedMessageSize%2A?displayProperty=nameWithType>, que é implementado por todos os elementos de associação de transporte fornecida pelo sistema, é definido como 65.536 bytes por padrão para impedir clientes mal-intencionado de envolvidos em ataques de negação de serviço em relação a um serviço fazendo excessivo de memória consumo. (Normalmente, você pode aumentar o desempenho ao diminuir esse valor.)  
  
 Um exemplo de uma cota de serialização é o <xref:System.Runtime.Serialization.DataContractSerializer.MaxItemsInObjectGraph%2A?displayProperty=nameWithType> propriedade, que especifica o número máximo de objetos que o serializador serializa ou desserializa em uma única <xref:System.Runtime.Serialization.DataContractSerializer.ReadObject%2A> chamada de método. Um exemplo de uma restrição de nível de aplicativo é o <xref:System.ServiceModel.Dispatcher.ServiceThrottle.MaxConcurrentSessions%2A?displayProperty=nameWithType> propriedade, que restringe o número de conexões simultâneas de canal de sessão para 10 por padrão. (Ao contrário de cotas, se esse valor de limite é atingido, o aplicativo continua o processamento mas não aceita nenhum canal de sessão nova, que significa que os novos clientes não podem se conectar até que um dos outros canais de sessão é encerrado.)  
  
 Esses controles são projetados para fornecer uma redução de fora da caixa contra determinados tipos de ataques ou para melhorar o desempenho, como espaço de memória, tempo de inicialização e assim por diante. No entanto, dependendo do aplicativo, esses controles podem impedir o desempenho do aplicativo de serviço ou impedir que o aplicativo funcione em todos os. Por exemplo, um aplicativo projetado para o fluxo de vídeo pode facilmente ultrapassam o padrão de <xref:System.ServiceModel.Channels.TransportBindingElement.MaxReceivedMessageSize%2A?displayProperty=nameWithType> propriedade. Este tópico fornece uma visão geral dos vários controles aplicada a aplicativos em todos os níveis de [!INCLUDE[indigo2](../../../includes/indigo2-md.md)]descreve várias formas de obter mais informações sobre se uma configuração é obstruindo o seu aplicativo e descreve maneiras de corrigir vários problemas. A maioria das limitações e algumas cotas estão disponíveis no nível do aplicativo, mesmo quando a propriedade base é uma restrição de serialização ou de transporte. Por exemplo, você pode definir o <xref:System.Runtime.Serialization.DataContractSerializer.MaxItemsInObjectGraph%2A?displayProperty=nameWithType> propriedade usando o <xref:System.ServiceModel.ServiceBehaviorAttribute.MaxItemsInObjectGraph%2A?displayProperty=nameWithType> propriedade na classe de serviço.  
  
> [!NOTE]
>  Se você tiver um problema específico, você deve primeiro ler o [início rápido de solução de problemas do WCF](../../../docs/framework/wcf/wcf-troubleshooting-quickstart.md) para ver se o problema (e uma solução) estão listadas.  
  
 Propriedades que restringem os processos de serialização são listadas em [considerações de segurança para dados](../../../docs/framework/wcf/feature-details/security-considerations-for-data.md). Propriedades que restringem o consumo de recursos relacionados a todos os transportes são listadas em [cotas de transporte](../../../docs/framework/wcf/feature-details/transport-quotas.md). Propriedades que restringem o consumo de recursos na camada de aplicativo são os membros de <xref:System.ServiceModel.Dispatcher.ServiceThrottle> classe.  
  
## <a name="detecting-application-and-performance-issues-related-to-quota-settings"></a>Detecção de aplicativos e problemas de desempenho relacionados às configurações de cota  
 Os padrões dos valores anteriores foram escolhidos para habilitar a funcionalidade básica de aplicativo em uma grande variedade de tipos de aplicativos, proporcionando proteção básica em relação a problemas de segurança comuns. No entanto, designs de aplicativo diferente poderá exceder uma ou mais configurações de limitação, embora o aplicativo é seguro e pode funcionar como planejado. Nesses casos, você deve identificar quais valores de limitação estiver sendo excedidos e, em que nível e decidir sobre o curso de ação apropriado para aumentar a taxa de transferência do aplicativo.  
  
 Normalmente, ao escrever o aplicativo e depurá-lo, definir o <xref:System.ServiceModel.Description.ServiceDebugBehavior.IncludeExceptionDetailInFaults%2A?displayProperty=nameWithType> propriedade `true` no arquivo de configuração ou programaticamente. Isso instrui [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] para retornar os rastreamentos de pilha de exceção do serviço para o aplicativo cliente para exibição. Esse recurso relata a maioria das exceções de nível de aplicativo de forma a exibir as configurações de cota podem estar envolvidas, se esse é o problema.  
  
 Algumas exceções ocorrem em tempo de execução abaixo a visibilidade da camada de aplicativo e não são retornadas usando esse mecanismo, e não pode ser manipuladas por um personalizado <xref:System.ServiceModel.Dispatcher.IErrorHandler?displayProperty=nameWithType> implementação. Se você estiver em um ambiente de desenvolvimento, como o Microsoft Visual Studio, a maioria dessas exceções é exibida automaticamente. No entanto, algumas exceções podem ser mascaradas pelas configurações de ambiente de desenvolvimento, como o [Just My Code](http://go.microsoft.com/fwlink/?LinkId=82174) configurações no Visual Studio 2005.  
  
 Independentemente dos recursos do ambiente de desenvolvimento, você pode usar os recursos de [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] rastreamento e o registro de mensagem para todas as exceções de depurar e ajustar o desempenho de seus aplicativos. Para obter mais informações, consulte [usando rastreamento para solucionar problemas de seu aplicativo](../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md).  
  
## <a name="performance-issues-and-xmlserializer"></a>Problemas de desempenho e de XmlSerializer  
 Serviços e aplicativos cliente que usam tipos de dados pode ser serializado usando o <xref:System.Xml.Serialization.XmlSerializer> gerar e compilar o código de serialização para esses tipos de dados em tempo de execução, o que pode resultar em desempenho de inicialização lenta.  
  
> [!NOTE]
>  Código de serialização gerado pode ser usado apenas em aplicativos cliente e não em serviços.  
  
 O [Ferramenta Utilitária de metadados ServiceModel (Svcutil.exe)](../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) pode melhorar o desempenho de inicialização para esses aplicativos por meio da geração de código de serialização necessários dos assemblies compilados para o aplicativo. Para obter mais informações, consulte [como: melhorar a inicialização do tempo de WCF aplicativos cliente que usam o XmlSerializer](../../../docs/framework/wcf/feature-details/startup-time-of-wcf-client-applications-using-the-xmlserializer.md).  
  
## <a name="performance-issues-when-hosting-wcf-services-under-aspnet"></a>Problemas de desempenho ao hospedar serviços WCF no ASP.NET  
 Quando um serviço WCF é hospedado em IIS e ASP.NET, as definições de configuração do IIS e ASP.NET podem afetar o taxa de transferência e volume de memória do serviço WCF.  [!INCLUDE[crabout](../../../includes/crabout-md.md)]Desempenho do ASP.NET, consulte [melhorando o desempenho do ASP.NET](http://go.microsoft.com/fwlink/?LinkId=186462).  Uma configuração que pode ter consequências não intencionais é <xref:System.Web.Configuration.ProcessModelSection.MinWorkerThreads%2A>, que é uma propriedade do <xref:System.Web.Configuration.ProcessModelSection>. Se seu aplicativo tiver um número fixo ou pequeno de clientes, a configuração <xref:System.Web.Configuration.ProcessModelSection.MinWorkerThreads%2A> 2 pode fornecer um aumento da taxa de transferência em um computador multiprocessador que tem uma utilização da CPU próximo a 100%. Esse aumento no desempenho vem com um custo: também causará um aumento no uso de memória, que pode reduzir escalabilidade.  
  
## <a name="see-also"></a>Consulte também  
 [Administração e diagnósticos](../../../docs/framework/wcf/diagnostics/index.md)  
 [Dados grandes e streaming](../../../docs/framework/wcf/feature-details/large-data-and-streaming.md)
