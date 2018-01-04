---
title: Estendendo distribuidores
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: dispatcher extensions [WCF]
ms.assetid: d0ad15ac-fa12-4f27-80e8-7ac2271e5985
caps.latest.revision: "16"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 4240a19401d97cd0636d13a94fd07ad4ef753388
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="extending-dispatchers"></a>Estendendo distribuidores
Distribuidores são responsáveis por recebendo mensagens de entrada fora dos canais subjacentes, convertendo-os em invocações do método no código do aplicativo e enviar os resultados de volta para o chamador. Extensões de distribuidores permitem que você modifique esse processamento.  Você pode implementar inspetores de mensagem ou parâmetro que inspecionar ou modifiquem o conteúdo de mensagens ou parâmetros.  Você pode alterar o modo como as mensagens são roteadas para operações ou fornecem algumas outras funcionalidades.  
  
 Este tópico descreve como usar o <xref:System.ServiceModel.Dispatcher.DispatchRuntime> e <xref:System.ServiceModel.Dispatcher.DispatchOperation> classes em um [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] serviço de aplicativo para modificar o comportamento de execução padrão de um distribuidor ou para interceptar ou modificar as mensagens, parâmetros, ou retornar valores antes ou subsequentes para enviar ou recuperá-los de camada do canal. Para obter mais informações sobre o processamento de mensagem de tempo de execução do cliente equivalente, consulte [estendendo clientes](../../../../docs/framework/wcf/extending/extending-clients.md). Para compreender a função que <xref:System.ServiceModel.IExtensibleObject%601> tipos reproduzir ao acessar o estado compartilhado entre vários objetos de personalização de tempo de execução, consulte [objetos extensíveis](../../../../docs/framework/wcf/extending/extensible-objects.md).  
  
## <a name="dispatchers"></a>Distribuidores  
 A camada de modelo de serviço executará a conversão entre o modelo de programação do desenvolvedor e a troca de mensagens subjacente, comumente chamado de camada do canal. Em [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] os distribuidores de canal e o ponto de extremidade (<xref:System.ServiceModel.Dispatcher.ChannelDispatcher> e <xref:System.ServiceModel.Dispatcher.EndpointDispatcher>, respectivamente) são os componentes de serviços responsáveis por aceitar novos canais, recebendo mensagens, despacho de operação e invocação e processamento de resposta. Objetos do distribuidor são objetos de destinatário, mas implementações de contrato de retorno de chamada no serviços de duplex também expõem seus objetos de dispatcher para inspeção, modificação ou extensão.  
  
 O dispatcher do canal (e complementar <xref:System.ServiceModel.Channels.IChannelListener>) recebe mensagens fora do canal subjacente e transmite as mensagens para seus distribuidores do respectivos do ponto de extremidade. O dispatcher de cada ponto de extremidade tem um <xref:System.ServiceModel.Dispatcher.DispatchRuntime> que encaminha mensagens ao apropriado <xref:System.ServiceModel.Dispatcher.DispatchOperation>, que é responsável por chamar o método que implementa a operação. Várias classes de extensão necessários e opcionais é invocado ao longo do caminho. Este tópico explica como essas partes se encaixam e como você pode modificar as propriedades e conecte seu próprio código para estender a funcionalidade de base.  
  
 Propriedades do distribuidor e objetos de personalização modificados são inseridos usando objetos de comportamento de serviço, ponto de extremidade, contrato ou operação. Este tópico descreve como usar comportamentos. Para obter mais informações sobre os tipos usados para inserir as modificações de distribuidor, consulte [Configurando e estendendo o tempo de execução com comportamentos](../../../../docs/framework/wcf/extending/configuring-and-extending-the-runtime-with-behaviors.md).  
  
 O gráfico a seguir fornece uma visão geral dos itens de arquitetura em um serviço.  
  
 ![A arquitetura de tempo de execução de despacho](../../../../docs/framework/wcf/extending/media/wcfc-dispatchruntimearchc.gif "wcfc_DispatchRuntimeArchc")  
  
### <a name="channel-dispatchers"></a>Distribuidores de canal  
 Um <xref:System.ServiceModel.Dispatcher.ChannelDispatcher> objeto é criado para associar um <xref:System.ServiceModel.Channels.IChannelListener> em um URI específico (chamado de um URI de escuta) com uma instância de um serviço. Cada <xref:System.ServiceModel.ServiceHost> objeto pode ter muitos <xref:System.ServiceModel.Dispatcher.ChannelDispatcher> objetos, cada um associado a somente um ouvinte e URI de escuta. Quando uma mensagem chega, o <xref:System.ServiceModel.Dispatcher.ChannelDispatcher> consulta cada um dos <xref:System.ServiceModel.Dispatcher.EndpointDispatcher> objetos se o ponto de extremidade pode aceitar a mensagem e passa a mensagem para aquele que pode.  
  
 Todas as propriedades que controlam o comportamento de uma sessão de canal e tempo de vida estão disponíveis para a inspeção ou modificação no <xref:System.ServiceModel.Dispatcher.ChannelDispatcher> objeto. Isso inclui os inicializadores de canal personalizado, a escuta de canal, o host, associado <xref:System.ServiceModel.InstanceContext>, e assim por diante.  
  
### <a name="endpoint-dispatchers"></a>Distribuidores de ponto de extremidade  
 O <xref:System.ServiceModel.Dispatcher.EndpointDispatcher> objeto é responsável pelo processamento de mensagens de um <xref:System.ServiceModel.Dispatcher.ChannelDispatcher> quando o endereço de destino de uma mensagem corresponde a <xref:System.ServiceModel.Dispatcher.EndpointDispatcher.AddressFilter%2A> e as correspondências de ação de mensagem de <xref:System.ServiceModel.Dispatcher.EndpointDispatcher.ContractFilter%2A> propriedade. Se dois <xref:System.ServiceModel.Dispatcher.EndpointDispatcher> objetos podem aceitar uma mensagem, o <xref:System.ServiceModel.Dispatcher.EndpointDispatcher.FilterPriority%2A> o valor da propriedade determina o ponto de extremidade de prioridade mais alto.  
  
 Use o <xref:System.ServiceModel.Dispatcher.EndpointDispatcher> para adquirir os dois pontos de extensão de modelo principal de serviço – o <xref:System.ServiceModel.Dispatcher.DispatchRuntime> e <xref:System.ServiceModel.Dispatcher.DispatchOperation> classes – que você pode usar para personalizar o processamento do dispatcher. O <xref:System.ServiceModel.Dispatcher.DispatchRuntime> classe permite que os usuários interceptar e estender o dispatcher no escopo do contrato (ou seja, para todas as mensagens em um contrato). O <xref:System.ServiceModel.Dispatcher.DispatchOperation> classe permite que os usuários interceptar e estender o distribuidor em um escopo de operação (ou seja, para todas as mensagens em uma operação).  
  
## <a name="scenarios"></a>Cenários  
 Há vários motivos para estender o dispatcher:  
  
-   Validação de mensagem personalizada. Os usuários podem impor que uma mensagem é válida para um determinado esquema. Isso pode ser feito ao implementar as interfaces de interceptor de mensagem. Para obter um exemplo, consulte [inspetores de mensagem](../../../../docs/framework/wcf/samples/message-inspectors.md).  
  
-   Log de mensagem personalizada. Os usuários podem inspecionar e um conjunto de mensagens de aplicativo por meio de um ponto de extremidade de fluxo de log. Isso também pode ser feito com as interfaces de interceptor de mensagem.  
  
-   Transformações de mensagem personalizada. Os usuários podem aplicar determinadas transformações para a mensagem no tempo de execução (por exemplo, para controle de versão). Isso pode ser feito, novamente, com as interfaces de interceptor de mensagem.  
  
-   Modelo de dados personalizados. Os usuários podem ter um modelo de serialização de dados não suportados por padrão em [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] (ou seja, <xref:System.Runtime.Serialization.DataContractSerializer?displayProperty=nameWithType>, <xref:System.Xml.Serialization.XmlSerializer?displayProperty=nameWithType>e mensagens brutas). Isso pode ser feito por implementar as interfaces de formatador de mensagem. Para obter um exemplo, consulte [formatador de operação e seletor de operação](../../../../docs/framework/wcf/samples/operation-formatter-and-operation-selector.md).  
  
-   Validação de parâmetro personalizado. Os usuários podem impor que parâmetros de tipo são válidos (em vez de XML). Isso pode ser feito usando as interfaces do Inspetor de parâmetro.  
  
-   Distribuindo operação personalizada. Os usuários podem implementar expedição em algo diferente de ação – por exemplo, no elemento body ou em uma propriedade de mensagem personalizada. Isso pode ser feito usando o <xref:System.ServiceModel.Dispatcher.IDispatchOperationSelector> interface. Para obter um exemplo, consulte [formatador de operação e seletor de operação](../../../../docs/framework/wcf/samples/operation-formatter-and-operation-selector.md).  
  
-   Ao pool de objetos. Os usuários podem pool instâncias, em vez de alocar um novo para cada chamada. Isso pode ser implementado usando as interfaces de provedor de instância. Para obter um exemplo, consulte [Pooling](../../../../docs/framework/wcf/samples/pooling.md).  
  
-   Concessão de instância. Os usuários podem implementar um padrão de concessão para a instância tempo de vida, semelhante de comunicação remota do .NET Framework. Isso pode ser feito usando as interfaces de tempo de vida de contexto de instância.  
  
-   Tratamento de erros personalizado. Os usuários podem controlar como os dois erros locais são processados e como as falhas são comunicadas aos clientes. Isso pode ser implementado usando o <xref:System.ServiceModel.Dispatcher.IErrorHandler> interfaces.  
  
-   Comportamentos de autorização personalizada. Os usuários podem implementar o controle de acesso personalizadas estendendo as partes de tempo de execução de contrato ou de operação e adicionando as verificações de segurança com base em tokens presentes na mensagem. Isso pode ser feito usando o interceptor de mensagem ou interfaces de interceptador de parâmetro. Para obter exemplos, consulte [extensibilidade de segurança](../../../../docs/framework/wcf/samples/security-extensibility.md).  
  
    > [!CAUTION]
    >  Como alterar as propriedades de segurança tem o potencial de comprometer a segurança de [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] aplicativos, é altamente recomendável que você realizar modificações relacionadas à segurança com cuidado e teste cuidadosamente antes da implantação.  
  
-   Validadores de tempo de execução do WCF personalizado. Você pode instalar validadores personalizados que examinam os serviços, contratos e associações para impor as políticas de nível empresarial com relação ao [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] aplicativos. (Por exemplo, consulte [como: bloqueio para pontos de extremidade na empresa](../../../../docs/framework/wcf/extending/how-to-lock-down-endpoints-in-the-enterprise.md).)  
  
### <a name="using-the-dispatchruntime-class"></a>Usando a classe DispatchRuntime  
 Use o <xref:System.ServiceModel.Dispatcher.DispatchRuntime> classe para modificar o comportamento padrão de um serviço ou um ponto de extremidade individual ou para inserir objetos que implementam modificações personalizadas para um ou ambos os seguintes processos de serviço (ou processos de cliente no caso de um cliente duplex):  
  
-   A transformação de mensagens de entrada em objetos e liberar esses objetos como invocações de método em um objeto de serviço.  
  
-   A transformação de objetos recebidos de resposta para uma invocação de operação de serviço em mensagens de saída.  
  
 O <xref:System.ServiceModel.Dispatcher.DispatchRuntime> permite interceptar e estender o dispatcher de canal ou de ponto de extremidade para todas as mensagens em um contrato específico, mesmo quando uma mensagem não é reconhecida. Quando chega uma mensagem que não corresponde a nenhum declarado no contrato que ele é enviado para a operação retornada pelo <xref:System.ServiceModel.Dispatcher.DispatchRuntime.UnhandledDispatchOperation%2A> propriedade. Para interceptar ou estender em todas as mensagens de uma determinada operação, consulte o <xref:System.ServiceModel.Dispatcher.DispatchOperation> classe.  
  
 Há quatro áreas principais de extensibilidade do dispatcher expostos pelo <xref:System.ServiceModel.Dispatcher.DispatchRuntime> classe:  
  
1.  Usam as propriedades de componentes de canal a <xref:System.ServiceModel.Dispatcher.DispatchRuntime> e o distribuidor de canal associado retornado pelo <xref:System.ServiceModel.Dispatcher.DispatchRuntime.ChannelDispatcher%2A> propriedade para personalizar como o distribuidor de canal aceita e fecha canais. Essa categoria inclui o <xref:System.ServiceModel.Dispatcher.ChannelDispatcher.ChannelInitializers%2A> e <xref:System.ServiceModel.Dispatcher.DispatchRuntime.InputSessionShutdownHandlers%2A> propriedades.  
  
2.  Componentes de mensagem personalizados para cada mensagem processada. Essa categoria inclui o <xref:System.ServiceModel.Dispatcher.DispatchRuntime.MessageInspectors%2A>, <xref:System.ServiceModel.Dispatcher.DispatchRuntime.OperationSelector%2A>, <xref:System.ServiceModel.Dispatcher.DispatchRuntime.Operations%2A>e o <xref:System.ServiceModel.Dispatcher.ChannelDispatcher.ErrorHandlers%2A> propriedades.  
  
3.  Componentes da instância personalizar a criação, o tempo de vida e a disposição das instâncias do tipo de serviço. Para obter mais informações sobre os tempos de vida de objeto de serviço, consulte o <xref:System.ServiceModel.ServiceBehaviorAttribute.InstanceContextMode%2A> propriedade. Essa categoria inclui o <xref:System.ServiceModel.Dispatcher.DispatchRuntime.InstanceContextInitializers%2A> e <xref:System.ServiceModel.Dispatcher.DispatchRuntime.InstanceProvider%2A> propriedades.  
  
4.  Componentes de segurança podem usar as seguintes propriedades:  
  
    -   <xref:System.ServiceModel.Dispatcher.DispatchRuntime.SecurityAuditLogLocation%2A>indica onde os eventos de auditoria são gravados.  
  
    -   <xref:System.ServiceModel.Dispatcher.DispatchRuntime.ImpersonateCallerForAllOperations%2A>Controla se o serviço tenta representar usando as credenciais fornecidas pela mensagem de entrada.  
  
    -   <xref:System.ServiceModel.Dispatcher.DispatchRuntime.MessageAuthenticationAuditLevel%2A>Controla se os eventos de autenticação de mensagem bem-sucedida são gravados no log de eventos especificado pelo <xref:System.ServiceModel.Dispatcher.DispatchRuntime.SecurityAuditLogLocation%2A>.  
  
    -   <xref:System.ServiceModel.Dispatcher.DispatchRuntime.PrincipalPermissionMode%2A>Controla como o <xref:System.Threading.Thread.CurrentPrincipal%2A> está definida.  
  
    -   <xref:System.ServiceModel.Dispatcher.DispatchRuntime.ServiceAuthorizationAuditLevel%2A>Especifica como a auditoria de eventos de autorização é executada.  
  
    -   <xref:System.ServiceModel.Dispatcher.DispatchRuntime.SuppressAuditFailure%2A>Especifica se deve ser suprimida não críticos exceções que ocorrem durante o processo de registro em log.  
  
 Normalmente, os objetos de extensão personalizada são atribuídos a um <xref:System.ServiceModel.Dispatcher.DispatchRuntime> propriedade ou inseridos em uma coleção por um comportamento de serviço (um objeto que implementa <xref:System.ServiceModel.Description.IServiceBehavior>), um comportamento de contrato (um objeto que implementa <xref:System.ServiceModel.Description.IContractBehavior>), ou um ponto de extremidade comportamento (um objeto que implementa <xref:System.ServiceModel.Description.IEndpointBehavior>). Em seguida, o objeto de comportamento da instalação é adicionado à coleção apropriada de comportamentos programaticamente ou pela implementação de uma <xref:System.ServiceModel.Configuration.BehaviorExtensionElement> objeto para habilitar o comportamento a ser inserido usando um arquivo de configuração do aplicativo.  
  
 Clientes duplex (clientes que implementam um contrato de retorno de chamada especificado por um serviço duplex) também têm um <xref:System.ServiceModel.Dispatcher.DispatchRuntime> objeto que pode ser acessado usando o <xref:System.ServiceModel.Dispatcher.ClientRuntime.CallbackDispatchRuntime%2A> propriedade.  
  
### <a name="using-the-dispatchoperation-class"></a>Usando a classe DispatchOperation  
 O <xref:System.ServiceModel.Dispatcher.DispatchOperation> classe é o local para modificações de tempo de execução e a inserção de ponto para extensões personalizadas que têm o escopo para apenas uma operação de serviço. (Para modificar o comportamento de tempo de execução de serviço para todas as mensagens em um contrato, use o <xref:System.ServiceModel.Dispatcher.DispatchRuntime> classe.)  
  
 Instalar <xref:System.ServiceModel.Dispatcher.DispatchOperation> modificações usando um objeto de comportamento de serviço personalizado.  
  
 Use o <xref:System.ServiceModel.Dispatcher.DispatchRuntime.Operations%2A> propriedade para localizar o <xref:System.ServiceModel.Dispatcher.DispatchOperation> objeto que representa uma operação de serviço específico.  
  
 As seguintes propriedades de controlam a execução de tempo de execução no nível da operação:  
  
-   O <xref:System.ServiceModel.Dispatcher.DispatchOperation.Action%2A>, <xref:System.ServiceModel.Dispatcher.DispatchOperation.ReplyAction%2A>, <xref:System.ServiceModel.Dispatcher.DispatchOperation.FaultContractInfos%2A>, <xref:System.ServiceModel.Dispatcher.DispatchOperation.IsOneWay%2A>, <xref:System.ServiceModel.Dispatcher.DispatchOperation.IsTerminating%2A>, e <xref:System.ServiceModel.Dispatcher.DispatchOperation.Name%2A> propriedades obtêm os respectivos valores para a operação.  
  
-   O <xref:System.ServiceModel.Dispatcher.DispatchOperation.TransactionAutoComplete%2A> e <xref:System.ServiceModel.Dispatcher.DispatchOperation.TransactionRequired%2A> especificar comportamento de transação.  
  
-   O <xref:System.ServiceModel.Dispatcher.DispatchOperation.ReleaseInstanceBeforeCall%2A> e <xref:System.ServiceModel.Dispatcher.DispatchOperation.ReleaseInstanceAfterCall%2A> propriedades controlam o tempo de vida do objeto de serviço definido pelo usuário relativo para o <xref:System.ServiceModel.InstanceContext>.  
  
-   O <xref:System.ServiceModel.Dispatcher.DispatchOperation.DeserializeRequest%2A>, <xref:System.ServiceModel.Dispatcher.DispatchOperation.SerializeReply%2A>e o <xref:System.ServiceModel.Dispatcher.DispatchOperation.Formatter%2A> propriedades permitem controle explícito sobre a conversão de mensagens em objetos e mensagens.  
  
-   O <xref:System.ServiceModel.Dispatcher.DispatchOperation.Impersonation%2A> propriedade especifica o nível de representação de operação.  
  
-   O <xref:System.ServiceModel.Dispatcher.DispatchOperation.CallContextInitializers%2A> propriedade insere personalizada chamada extensões de contexto para a operação.  
  
-   O <xref:System.ServiceModel.Dispatcher.DispatchOperation.AutoDisposeParameters%2A> propriedade controla quando os objetos de parâmetro são destruídos.  
  
-   O <xref:System.ServiceModel.Dispatcher.DispatchOperation.Invoker%2A> propriedade para inserir um objeto chamador personalizado.  
  
-   O <xref:System.ServiceModel.Dispatcher.DispatchOperation.ParameterInspectors%2A> propriedade permite que você insira um Inspetor de parâmetro personalizado que você pode usar para inspecionar ou modificar os parâmetros e valores de retorno.  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.ServiceModel.Dispatcher.DispatchRuntime>  
 <xref:System.ServiceModel.Dispatcher.DispatchOperation>  
 [Como inspecionar e modificar mensagens do serviço](../../../../docs/framework/wcf/extending/how-to-inspect-and-modify-messages-on-the-service.md)  
 [Como inspecionar ou modificar parâmetros](../../../../docs/framework/wcf/extending/how-to-inspect-or-modify-parameters.md)  
 [Como bloquear pontos de extremidade na empresa](../../../../docs/framework/wcf/extending/how-to-lock-down-endpoints-in-the-enterprise.md)
