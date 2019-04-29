---
title: Controlando o consumo de recursos e a melhoria de desempenho
ms.date: 03/30/2017
ms.assetid: 9a829669-5f76-4c88-80ec-92d0c62c0660
ms.openlocfilehash: 11d1333ed0ae8b46f8f87fa6f4643d4b31fac3ff
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61785054"
---
# <a name="controlling-resource-consumption-and-improving-performance"></a>Controlando o consumo de recursos e a melhoria de desempenho
Este tópico descreve as várias propriedades em áreas diferentes da arquitetura do Windows Communication Foundation (WCF) que funcionam para consumo de recursos de controle e afetam as métricas de desempenho.

## <a name="properties-that-constrain-resource-consumption-in-wcf"></a>Propriedades que restringem o consumo de recursos no WCF
 Windows Communication Foundation (WCF) se aplica a restrições em determinados tipos de processos para fins de segurança ou de desempenho. Essas restrições têm duas formas principais, cotas e limites. *Cotas* são os limites que quando atingido ou excedido disparam uma exceção imediata em algum momento no sistema. *Limita* são os limites que não causam uma exceção seja lançada imediatamente. Em vez disso, quando um limite for atingido, o processamento continuará, mas dentro dos limites definida por esse valor de limitação. Esse processamento limitado pode disparar uma exceção em outro lugar, mas isso depende do aplicativo.

 A distinção entre as cotas e restrições, além de algumas propriedades de restrições estão localizadas no nível da serialização, alguns no nível de transporte e alguns no nível do aplicativo. Por exemplo, a cota <xref:System.ServiceModel.Channels.TransportBindingElement.MaxReceivedMessageSize%2A?displayProperty=nameWithType>, que é implementado por todos os elementos de associação de transporte fornecido pelo sistema, é definido como 65.536 bytes por padrão para impedir os clientes mal-intencionados de envolvidos em ataques de negação de serviço em relação a um serviço, fazendo com que a memória excessiva consumo. (Normalmente, você pode aumentar o desempenho ao reduzir esse valor.)

 Um exemplo de uma cota de serialização é o <xref:System.Runtime.Serialization.DataContractSerializer.MaxItemsInObjectGraph%2A?displayProperty=nameWithType> propriedade, que especifica o número máximo de objetos que o serializador serializa ou desserializa em uma única <xref:System.Runtime.Serialization.DataContractSerializer.ReadObject%2A> chamada de método. Um exemplo de uma restrição de nível de aplicativo é o <xref:System.ServiceModel.Dispatcher.ServiceThrottle.MaxConcurrentSessions%2A?displayProperty=nameWithType> propriedade, que restringe o número de conexões simultâneas de canal de sessão para 10 por padrão. (Ao contrário de cotas, se esse valor limitador for atingido, o aplicativo continua o processamento, mas aceita sem novos canais de sessão, que significa que novos clientes não podem se conectar até que um dos outros canais de sessão é encerrado.)

 Esses controles são projetados para fornecer uma mitigação out-of-the-box contra determinados tipos de ataques ou para melhorar as métricas de desempenho, como volume de memória, tempo de inicialização e assim por diante. No entanto, dependendo do aplicativo, esses controles podem impedir o desempenho do aplicativo de serviço ou impedir que o aplicativo funcionando em todos os. Por exemplo, um aplicativo projetado para transmitir vídeo facilmente pode exceder o padrão <xref:System.ServiceModel.Channels.TransportBindingElement.MaxReceivedMessageSize%2A?displayProperty=nameWithType> propriedade. Este tópico fornece uma visão geral dos diversos controles aplicada a aplicativos em todos os níveis do WCF, descreve várias maneiras de obter mais informações sobre se uma configuração está obstruindo o seu aplicativo e descreve maneiras de corrigir vários problemas. A maioria das restrições e algumas cotas estão disponíveis no nível do aplicativo, mesmo quando a propriedade base é uma restrição de serialização ou de transporte. Por exemplo, você pode definir as <xref:System.Runtime.Serialization.DataContractSerializer.MaxItemsInObjectGraph%2A?displayProperty=nameWithType> propriedade usando o <xref:System.ServiceModel.ServiceBehaviorAttribute.MaxItemsInObjectGraph%2A?displayProperty=nameWithType> propriedade na classe de serviço.

> [!NOTE]
> Se você tiver um problema específico, você deve primeiro ler o [início rápido de solução de problemas do WCF](../../../docs/framework/wcf/wcf-troubleshooting-quickstart.md) para ver se o problema (e uma solução) estão listados.

 As propriedades que restringem os processos de serialização são listadas na [considerações sobre segurança para dados](../../../docs/framework/wcf/feature-details/security-considerations-for-data.md). As propriedades que restringem o consumo de recursos relacionados a todos os transportes são listadas na [cotas de transporte](../../../docs/framework/wcf/feature-details/transport-quotas.md). Propriedades que restringem o consumo de recursos na camada de aplicativo são os membros de <xref:System.ServiceModel.Dispatcher.ServiceThrottle> classe.

## <a name="detecting-application-and-performance-issues-related-to-quota-settings"></a>Detectando problemas de desempenho relacionados às configurações de cota e de aplicativo
 Os padrões dos valores anteriores foram escolhidos para habilitar a funcionalidade básica do aplicativo em uma ampla variedade de tipos de aplicativos, fornecendo proteção básica em relação a problemas comuns de segurança. No entanto, designs de aplicativos diferentes podem exceder um ou mais configurações de limitação, embora o aplicativo caso contrário, é seguro e funcionará como projetado. Nesses casos, você deve identificar quais valores de limitação estiver sendo excedidos e em qual nível e decidir sobre o curso de ação apropriado para aumentar a produtividade do aplicativo.

 Normalmente, ao escrever o aplicativo e depurá-lo, definir a <xref:System.ServiceModel.Description.ServiceDebugBehavior.IncludeExceptionDetailInFaults%2A?displayProperty=nameWithType> propriedade para `true` no arquivo de configuração ou programaticamente. Isso instrui o WCF para retornar os rastreamentos de pilha de exceção do serviço para o aplicativo cliente para exibição. Esse recurso relata a maioria das exceções de nível de aplicativo na forma como para exibir quais configurações de cota podem estar envolvidas, se esse for o problema.

 Algumas exceções ocorrem em tempo de execução abaixo a visibilidade da camada de aplicativo e não são retornadas usando esse mecanismo, e não pode ser manipuladas por um personalizado <xref:System.ServiceModel.Dispatcher.IErrorHandler?displayProperty=nameWithType> implementação. Se você estiver em um ambiente de desenvolvimento como o Microsoft Visual Studio, a maioria dessas exceções é exibida automaticamente. No entanto, algumas exceções podem ser mascaradas por configurações de ambiente de desenvolvimento, como [Just My Code](/visualstudio/debugger/just-my-code) Visual Studio.

 Independentemente dos recursos do seu ambiente de desenvolvimento, você pode usar recursos de rastreamento do WCF e o log de mensagens para todas as exceções de depurar e ajustar o desempenho de seus aplicativos. Para obter mais informações, consulte [usando o rastreamento para solucionar problemas de seu aplicativo](../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md).

## <a name="performance-issues-and-xmlserializer"></a>Problemas de desempenho e de XmlSerializer
 Serviços e aplicativos cliente que usam tipos de dados que são serializados usando o <xref:System.Xml.Serialization.XmlSerializer> gerar e compilar o código de serialização para esses tipos de dados em tempo de execução, o que pode resultar em desempenho de inicialização lento.

> [!NOTE]
> Código de serialização pré-gerado pode ser usado apenas em aplicativos cliente e não em serviços.

 O [ferramenta de utilitário de metadados ServiceModel (Svcutil.exe)](../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) pode melhorar o desempenho de inicialização para esses aplicativos, gerando o código de serialização necessários a partir de assemblies compilados para o aplicativo. Para obter mais informações, confira [Como: Melhorar o tempo de inicialização do WCF cliente aplicativos usando o XmlSerializer](../../../docs/framework/wcf/feature-details/startup-time-of-wcf-client-applications-using-the-xmlserializer.md).

## <a name="performance-issues-when-hosting-wcf-services-under-aspnet"></a>Problemas de desempenho ao hospedar serviços WCF em ASP.NET
 Quando um serviço do WCF é hospedado no IIS e ASP.NET, as definições de configuração do IIS e ASP.NET podem afetar o taxa de transferência e volume de memória do serviço WCF.  Para obter mais informações sobre o desempenho do ASP.NET, consulte [melhorando o desempenho do ASP.NET](https://go.microsoft.com/fwlink/?LinkId=186462).  Uma configuração que pode ter consequências não intencionais está <xref:System.Web.Configuration.ProcessModelSection.MinWorkerThreads%2A>, que é uma propriedade do <xref:System.Web.Configuration.ProcessModelSection>. Se seu aplicativo tiver um número fixo ou pequeno de clientes, a configuração <xref:System.Web.Configuration.ProcessModelSection.MinWorkerThreads%2A> 2 pode fornecer um aumento de taxa de transferência em um computador multiprocessador que tem o próximo de 100% de utilização de CPU. Esse aumento no desempenho é fornecido com um custo: também causará um aumento no uso de memória, que pode reduzir a escalabilidade.

## <a name="see-also"></a>Consulte também

- [Administração e diagnósticos](../../../docs/framework/wcf/diagnostics/index.md)
- [Dados grandes e streaming](../../../docs/framework/wcf/feature-details/large-data-and-streaming.md)
