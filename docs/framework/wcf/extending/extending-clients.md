---
title: Estendendo clientes
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- proxy extensions [WCF]
ms.assetid: 1328c61c-06e5-455f-9ebd-ceefb59d3867
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 2444488418b7647111cf4b89db0c41a8e66470d4
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="extending-clients"></a>Estendendo clientes
Em um aplicativo de chamada, a camada de modelo de serviço é responsável pela conversão de invocações do método no código do aplicativo em mensagens de saída, enviar por push para os canais subjacentes, converter resultados de volta para valores de retorno e parâmetros out em código do aplicativo e retornar os resultados de volta ao chamador. Extensões do modelo de serviço modificam ou implementam a execução ou o comportamento de comunicação e recursos que envolvem a funcionalidade de cliente ou o distribuidor, comportamentos personalizados, mensagem e interceptação de parâmetro e outras funcionalidades de extensibilidade.  
  
 Este tópico descreve como usar o <xref:System.ServiceModel.Dispatcher.ClientRuntime> e <xref:System.ServiceModel.Dispatcher.ClientOperation> classes em um [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] aplicativo cliente para modificar o comportamento de execução padrão de um [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] cliente ou para interceptar ou modificar as mensagens, parâmetros ou retornar valores antes ou subsequentes ao envio ou recuperá-los de camada do canal. Para obter mais informações sobre como estender o tempo de execução do serviço, consulte [estendendo Dispatchers](../../../../docs/framework/wcf/extending/extending-dispatchers.md). Para obter mais informações sobre os comportamentos que modificam e inserir objetos de personalização em tempo de execução do cliente, consulte [Configurando e estendendo o tempo de execução com comportamentos](../../../../docs/framework/wcf/extending/configuring-and-extending-the-runtime-with-behaviors.md).  
  
## <a name="clients"></a>Clientes  
 Em um cliente, um [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] objeto do cliente ou canal cliente converte invocações de método em mensagens de saída e as mensagens de entrada para resultados de operação são retornados ao aplicativo de chamada. (Para obter mais informações sobre os tipos de cliente, consulte [arquitetura do cliente WCF](../../../../docs/framework/wcf/feature-details/client-architecture.md).)  
  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]tipos de cliente têm tipos de tempo de execução que lidar com essa funcionalidade de nível de operação e de ponto de extremidade. Quando um aplicativo chama uma operação, o <xref:System.ServiceModel.Dispatcher.ClientOperation> converte os objetos de saída em uma mensagem, processa interceptadores, confirma que a chamada de saída está em conformidade com o contrato de destino e todas as mensagens de saída para o <xref:System.ServiceModel.Dispatcher.ClientRuntime>, que é responsável por criar e gerenciar canais de saída (e canais de entrada no caso de serviços de duplex), tratamento de mensagens de saída muito processamento (por exemplo, a modificação de cabeçalho), os interceptadores de mensagem em ambas as direções de processamento e roteamento de entrada chamadas duplex ao lado do cliente apropriado <xref:System.ServiceModel.Dispatcher.DispatchRuntime> objeto. Tanto o <xref:System.ServiceModel.Dispatcher.ClientOperation> e <xref:System.ServiceModel.Dispatcher.ClientRuntime> fornecem serviços semelhantes quando mensagens (incluindo falhas) são retornadas ao cliente.  
  
 Essas duas classes de tempo de execução são a principal extensão para personalizar o processamento de [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] objetos de cliente e canais. O <xref:System.ServiceModel.Dispatcher.ClientRuntime> classe permite que os usuários interceptar e estender a execução do cliente em todas as mensagens no contrato. O <xref:System.ServiceModel.Dispatcher.ClientOperation> classe permite que os usuários interceptar e estender a execução do cliente para todas as mensagens em uma determinada operação.  
  
 Modificando as propriedades ou inserindo as personalizações são feitas usando o contrato, ponto de extremidade e comportamentos de operação. Para obter mais informações sobre como usar esses tipos de comportamentos para fazer as personalizações de tempo de execução do cliente, consulte [Configurando e estendendo o tempo de execução com comportamentos](../../../../docs/framework/wcf/extending/configuring-and-extending-the-runtime-with-behaviors.md).  
  
## <a name="scenarios"></a>Cenários  
 Há vários motivos para estender o sistema do cliente, incluindo:  
  
-   Validação de mensagem personalizada. Um usuário pode ser necessário impor que uma mensagem é válida para um determinado esquema. Isso pode ser feito através da implementação de <xref:System.ServiceModel.Dispatcher.IClientMessageInspector> interface e atribuindo a implementação para o <xref:System.ServiceModel.Dispatcher.DispatchRuntime.MessageInspectors%2A> propriedade. Para obter exemplos, consulte [como: inspecionar ou modificar mensagens no cliente](../../../../docs/framework/wcf/extending/how-to-inspect-or-modify-messages-on-the-client.md) e [como: inspecionar ou modificar mensagens no cliente](../../../../docs/framework/wcf/extending/how-to-inspect-or-modify-messages-on-the-client.md).  
  
-   Log de mensagem personalizada. Um usuário pode querer inspecionar e um conjunto de mensagens de aplicativo por meio de um ponto de extremidade de fluxo de log. Isso também pode ser feito com as interfaces de interceptor de mensagem.  
  
-   Transformações de mensagem personalizada. Em vez de modificar o código do aplicativo, o usuário talvez queira aplicar determinadas transformações para a mensagem no tempo de execução (por exemplo, para controle de versão). Isso pode ser feito, novamente, com as interfaces de interceptor de mensagem.  
  
-   Modelo de dados personalizados. Um usuário pode desejar ter um modelo de dados ou de serialização não suportados por padrão em [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] (ou seja, <xref:System.Runtime.Serialization.DataContractSerializer?displayProperty=nameWithType>, <xref:System.Xml.Serialization.XmlSerializer?displayProperty=nameWithType>, e <xref:System.ServiceModel.Channels.Message?displayProperty=nameWithType> objetos). Isso pode ser feito ao implementar as interfaces de formatador de mensagem. Para obter mais informações, consulte <xref:System.ServiceModel.Dispatcher.IClientMessageFormatter?displayProperty=nameWithType> e <xref:System.ServiceModel.Dispatcher.ClientOperation.Formatter%2A?displayProperty=nameWithType> propriedade.  
  
-   Validação de parâmetro personalizado. Um usuário pode ser necessário impor que parâmetros de tipo são válidos (em vez de XML). Isso pode ser feito usando as interfaces do Inspetor de parâmetro. Para obter um exemplo, consulte [como: inspecionar ou modificar parâmetros](../../../../docs/framework/wcf/extending/how-to-inspect-or-modify-parameters.md) ou [validação do cliente](../../../../docs/framework/wcf/samples/client-validation.md).  
  
### <a name="using-the-clientruntime-class"></a>Usando a classe ClientRuntime  
 O <xref:System.ServiceModel.Dispatcher.ClientRuntime> classe é um ponto de extensibilidade para que você pode adicionar objetos de extensão que interceptam mensagens e estendem o comportamento do cliente. Objetos de interceptação podem processar todas as mensagens em um contrato específico, processar somente as mensagens para operações específicas, executar a inicialização do canal personalizado e implementar outro comportamento de aplicativo de cliente personalizadas.  
  
-   O <xref:System.ServiceModel.Dispatcher.ClientRuntime.CallbackDispatchRuntime%2A> propriedade retorna o objeto de tempo de execução de despacho para clientes iniciadas pelo serviço de retorno de chamada.  
  
-   O <xref:System.ServiceModel.Dispatcher.ClientRuntime.OperationSelector%2A> propriedade aceita um objeto de seletor de operação personalizada.  
  
-   O <xref:System.ServiceModel.Dispatcher.ClientRuntime.ChannelInitializers%2A> propriedade permite a adição de um inicializador de canal que pode inspecionar ou modificar o canal do cliente.  
  
-   O <xref:System.ServiceModel.Dispatcher.ClientRuntime.Operations%2A> propriedade obtém uma coleção de <xref:System.ServiceModel.Dispatcher.ClientOperation> objetos aos quais você pode adicionar interceptores de mensagem personalizada que fornecem funcionalidade específica para as mensagens dessa operação.  
  
-   O <xref:System.ServiceModel.Dispatcher.ClientRuntime.ManualAddressing%2A> propriedade permite que um aplicativo desativar alguns cabeçalhos de endereçamento automático para controlar o endereçamento diretamente.  
  
-   O <xref:System.ServiceModel.Dispatcher.ClientRuntime.Via%2A> propriedade define o valor de destino da mensagem no nível de transporte para dar suporte a outros cenários e intermediários.  
  
-   O <xref:System.ServiceModel.Dispatcher.ClientRuntime.MessageInspectors%2A> propriedade obtém uma coleção de <xref:System.ServiceModel.Dispatcher.IClientMessageInspector> objetos aos quais você pode adicionar interceptores de mensagem personalizada para todas as mensagens viajando através de um [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] cliente.  
  
 Além disso, há um número de outras propriedades que recuperar as informações de contrato:  
  
-   <xref:System.ServiceModel.Dispatcher.ClientRuntime.ContractName%2A>  
  
-   <xref:System.ServiceModel.Dispatcher.ClientRuntime.ContractNamespace%2A>  
  
-   <xref:System.ServiceModel.Dispatcher.ClientRuntime.ContractClientType%2A>  
  
 Se o [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] cliente é um duplex [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] cliente, as propriedades a seguir também recuperar o retorno de chamada [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] informações do cliente:  
  
-   <xref:System.ServiceModel.Dispatcher.ClientRuntime.CallbackClientType%2A>  
  
-   <xref:System.ServiceModel.Dispatcher.ClientRuntime.CallbackDispatchRuntime%2A>  
  
 Para estender [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] execução de cliente em todo um [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] cliente, examine as propriedades disponíveis na <xref:System.ServiceModel.Dispatcher.ClientRuntime> classe para ver se a modificação de uma propriedade ou implementando uma interface e adicioná-la a uma propriedade criam a funcionalidade Você está procurando. Depois de ter escolhido uma extensão específica para criar, inserir sua extensão apropriada <xref:System.ServiceModel.Dispatcher.ClientRuntime> propriedade implementando um comportamento do cliente que fornece acesso para o <xref:System.ServiceModel.Dispatcher.ClientRuntime> classe quando invocado.  
  
 Você pode inserir objetos de extensão personalizada em uma coleção usando o comportamento de uma operação (um objeto que implementa <xref:System.ServiceModel.Description.IOperationBehavior>), um comportamento de contrato (um objeto que implementa <xref:System.ServiceModel.Description.IContractBehavior>), ou um comportamento de ponto de extremidade (um objeto que implementa <xref:System.ServiceModel.Description.IEndpointBehavior> ). O objeto de comportamento da instalação é adicionado à coleção apropriada de comportamentos programaticamente, declarativamente (Implementando um atributo personalizado), ou pela implementação de uma <xref:System.ServiceModel.Configuration.BehaviorExtensionElement> objeto para habilitar o comportamento a ser inserido usando um arquivo de configuração do aplicativo. Para obter detalhes, consulte [Configurando e estendendo o tempo de execução com comportamentos](../../../../docs/framework/wcf/extending/configuring-and-extending-the-runtime-with-behaviors.md).  
  
 Para obter exemplos que demonstram a interceptação em uma [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] cliente, consulte [como: inspecionar ou modificar mensagens no cliente](../../../../docs/framework/wcf/extending/how-to-inspect-or-modify-messages-on-the-client.md).  
  
### <a name="using-the-clientoperation-class"></a>Usando a classe ClientOperation  
 O <xref:System.ServiceModel.Dispatcher.ClientOperation> classe é o local para modificações de tempo de execução do cliente e a inserção de ponto para extensões personalizadas que têm o escopo para apenas uma operação de serviço. (Para modificar o comportamento de tempo de execução do cliente para todas as mensagens em um contrato, use o <xref:System.ServiceModel.Dispatcher.ClientRuntime> classe.)  
  
 Use o <xref:System.ServiceModel.Dispatcher.ClientRuntime.Operations%2A> propriedade para localizar o <xref:System.ServiceModel.Dispatcher.ClientOperation> objeto que representa uma operação de serviço específico. As propriedades a seguir permitem que você inserir objetos personalizados para o [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] sistema cliente:  
  
-   Use o <xref:System.ServiceModel.Dispatcher.ClientOperation.Formatter%2A> propriedade para inserir um personalizado <xref:System.ServiceModel.Dispatcher.IClientMessageFormatter> implementação de uma operação ou modificar o formatador atual.  
  
-   Use o <xref:System.ServiceModel.Dispatcher.ClientOperation.ParameterInspectors%2A> propriedade para inserir um personalizado <xref:System.ServiceModel.Dispatcher.IParameterInspector> implementação ou para modificar o atual.  
  
 As propriedades a seguir permitem que você modifique o sistema de interação com o formatador e inspetores de parâmetro personalizado:  
  
-   Use o <xref:System.ServiceModel.Dispatcher.ClientOperation.SerializeRequest%2A> propriedade para controlar a serialização de uma mensagem de saída.  
  
-   Use o <xref:System.ServiceModel.Dispatcher.ClientOperation.DeserializeReply%2A> propriedade para controlar a desserialização de uma mensagem de entrada.  
  
-   Use o <xref:System.ServiceModel.Dispatcher.ClientOperation.Action%2A> propriedade para controlar a ação WS-Addressing da mensagem de solicitação.  
  
-   Use o <xref:System.ServiceModel.Dispatcher.ClientOperation.BeginMethod%2A> e <xref:System.ServiceModel.Dispatcher.ClientOperation.EndMethod%2A> para especificar qual [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] métodos de cliente estão associados com uma operação assíncrona.  
  
-   Use o <xref:System.ServiceModel.Dispatcher.ClientOperation.FaultContractInfos%2A> como o tipo de detalhe de falhas de propriedade para obter uma coleção que contém os tipos que podem aparecer em SOAP.  
  
-   Use o <xref:System.ServiceModel.Dispatcher.ClientOperation.IsInitiating%2A> e <xref:System.ServiceModel.Dispatcher.ClientOperation.IsTerminating%2A> propriedades para controlar se uma sessão é iniciada ou interrompida para baixo, respectivamente, quando a operação é chamada.  
  
-   Use o <xref:System.ServiceModel.Dispatcher.ClientOperation.IsOneWay%2A> propriedade para controlar se a operação é uma operação unidirecional.  
  
-   Use o <xref:System.ServiceModel.Dispatcher.ClientOperation.Parent%2A> propriedade para obter o contendo <xref:System.ServiceModel.Dispatcher.ClientRuntime> objeto.  
  
-   Use o <xref:System.ServiceModel.Dispatcher.ClientOperation.Name%2A> propriedade para obter o nome da operação.  
  
-   Use o <xref:System.ServiceModel.Dispatcher.ClientOperation.SyncMethod%2A> propriedade para controlar qual método é mapeado para a operação.  
  
 Para estender [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] execução do cliente em apenas uma operação de serviço, examine as propriedades disponíveis na <xref:System.ServiceModel.Dispatcher.ClientOperation> classe para ver se a modificação de uma propriedade ou implementando uma interface e adicioná-la a uma propriedade criam a funcionalidade que você está busca. Depois de ter escolhido uma extensão específica para criar, inserir sua extensão apropriada <xref:System.ServiceModel.Dispatcher.ClientOperation> propriedade implementando um comportamento do cliente que fornece acesso para o <xref:System.ServiceModel.Dispatcher.ClientOperation> classe quando invocado. Dentro desse comportamento, em seguida, você pode modificar o <xref:System.ServiceModel.Dispatcher.ClientRuntime> propriedade de acordo com suas necessidades.  
  
 Normalmente, Implementando um comportamento de operação (um objeto que implementa o <xref:System.ServiceModel.Description.IOperationBehavior> interface) é suficiente, mas você também pode usar comportamentos de ponto de extremidade e comportamentos para realizar a mesma coisa com a localização do contrato de <xref:System.ServiceModel.Description.OperationDescription> para um determinado operação e anexando o comportamento existe. Para obter detalhes, consulte [Configurando e estendendo o tempo de execução com comportamentos](../../../../docs/framework/wcf/extending/configuring-and-extending-the-runtime-with-behaviors.md).  
  
 Para usar o comportamento personalizado de configuração, instale seu comportamento usando um manipulador de seção de configuração de comportamento personalizado. Você também pode instalar seu comportamento, criando um atributo personalizado.  
  
 Para obter exemplos que demonstram a interceptação em uma [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] cliente, consulte [como: inspecionar ou modificar parâmetros](../../../../docs/framework/wcf/extending/how-to-inspect-or-modify-parameters.md).  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.ServiceModel.Dispatcher.ClientRuntime>  
 <xref:System.ServiceModel.Dispatcher.ClientOperation>  
 [Como inspecionar ou modificar as mensagens no cliente](../../../../docs/framework/wcf/extending/how-to-inspect-or-modify-messages-on-the-client.md)  
 [Como inspecionar ou modificar parâmetros](../../../../docs/framework/wcf/extending/how-to-inspect-or-modify-parameters.md)
