---
title: Estendendo distribuidores
ms.date: 03/30/2017
helpviewer_keywords:
- dispatcher extensions [WCF]
ms.assetid: d0ad15ac-fa12-4f27-80e8-7ac2271e5985
ms.openlocfilehash: c34a923d70c9079a3736732d6815df0329dfd557
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54715889"
---
# <a name="extending-dispatchers"></a>Estendendo distribuidores
Distribuidores são responsáveis por puxando as mensagens recebidas fora de canais subjacentes, convertendo-os em invocações de método no código do aplicativo e enviar os resultados para o chamador. Extensões de Dispatcher permitem que você modifique esse processamento.  Você pode implementar os inspetores de mensagem ou de parâmetro que inspecionam ou modificar o conteúdo de mensagens ou parâmetros.  Você pode alterar o modo como as mensagens são roteadas para operações ou fornecem algumas outras funcionalidades.  
  
 Este tópico descreve como usar o <xref:System.ServiceModel.Dispatcher.DispatchRuntime> e <xref:System.ServiceModel.Dispatcher.DispatchOperation> classes em um Windows Communication Foundation (WCF) serviço de aplicativo para modificar o comportamento de execução padrão de um dispatcher para interceptar ou modificar as mensagens, parâmetros ou retornar valores antes ou após enviar ou recuperá-los da camada de canal. Para obter mais informações sobre o processamento de mensagens de tempo de execução do cliente equivalente, consulte [estendendo clientes](../../../../docs/framework/wcf/extending/extending-clients.md). Entender a função que <xref:System.ServiceModel.IExtensibleObject%601> tipos de reprodução ao acessar o estado compartilhado entre vários objetos de personalização de tempo de execução, consulte [objetos extensíveis](../../../../docs/framework/wcf/extending/extensible-objects.md).  
  
## <a name="dispatchers"></a>Distribuidores  
 A camada de modelo de serviço realiza a conversão entre o modelo de programação do desenvolvedor e a troca de mensagens subjacente, normalmente chamado de camada do canal. O canal do WCF e os dispatchers de ponto de extremidade (<xref:System.ServiceModel.Dispatcher.ChannelDispatcher> e <xref:System.ServiceModel.Dispatcher.EndpointDispatcher>, respectivamente) são os componentes de serviço responsável por aceitar novos canais e receber mensagens, expedição da operação e invocação e processamento da resposta. Objetos de Dispatcher são objetos de destinatário, mas as implementações de contrato de retorno de chamada em serviços duplex também expõem seus objetos dispatcher para inspeção, modificação ou extensão.  
  
 O dispatcher do canal (e complementar <xref:System.ServiceModel.Channels.IChannelListener>) efetua pull das mensagens fora do canal subjacente e transmite as mensagens para seus dispatchers de ponto de extremidade respectivo. O dispatcher de cada ponto de extremidade tem um <xref:System.ServiceModel.Dispatcher.DispatchRuntime> que encaminhe mensagens para apropriado <xref:System.ServiceModel.Dispatcher.DispatchOperation>, que é responsável por chamar o método que implementa a operação. Várias classes de extensão obrigatórios e opcionais são invocadas ao longo do caminho. Este tópico explica como essas peças se encaixam, e como você pode modificar as propriedades e conectar seu próprio código para estender a funcionalidade básica.  
  
 Propriedades do distribuidor e objetos de personalização modificada são inseridos por meio de objetos de comportamento de serviço, ponto de extremidade, contrato ou operação. Este tópico descreve como usar comportamentos. Para obter mais informações sobre os tipos usados para inserir as modificações de dispatcher, consulte [Configurando e estendendo o tempo de execução com comportamentos](../../../../docs/framework/wcf/extending/configuring-and-extending-the-runtime-with-behaviors.md).  
  
 O gráfico a seguir fornece uma visão geral dos itens em um serviço de arquiteturas.  
  
 ![A arquitetura de tempo de execução de expedição](../../../../docs/framework/wcf/extending/media/wcfc-dispatchruntimearchc.gif "wcfc_DispatchRuntimeArchc")  
  
### <a name="channel-dispatchers"></a>Dispatchers do canal  
 Um <xref:System.ServiceModel.Dispatcher.ChannelDispatcher> objeto é criado para associar um <xref:System.ServiceModel.Channels.IChannelListener> em um URI específico (chamado de um URI de escuta) com uma instância de um serviço. Cada <xref:System.ServiceModel.ServiceHost> objeto pode ter muitas <xref:System.ServiceModel.Dispatcher.ChannelDispatcher> objetos, cada um associado a somente um ouvinte e URI de escuta. Quando uma mensagem chega, o <xref:System.ServiceModel.Dispatcher.ChannelDispatcher> consulta cada um associado <xref:System.ServiceModel.Dispatcher.EndpointDispatcher> objetos se o ponto de extremidade pode aceitar a mensagem e passa a mensagem para aquele que pode.  
  
 Todas as propriedades que controlam o tempo de vida e o comportamento de uma sessão de canal estão disponíveis para inspeção ou modificação no <xref:System.ServiceModel.Dispatcher.ChannelDispatcher> objeto. Isso inclui os inicializadores de canal personalizado, o ouvinte de canais, o host, associado <xref:System.ServiceModel.InstanceContext>e assim por diante.  
  
### <a name="endpoint-dispatchers"></a>Dispatchers de ponto de extremidade  
 O <xref:System.ServiceModel.Dispatcher.EndpointDispatcher> objeto é responsável pelo processamento de mensagens de uma <xref:System.ServiceModel.Dispatcher.ChannelDispatcher> quando o endereço de destino de uma mensagem corresponde a <xref:System.ServiceModel.Dispatcher.EndpointDispatcher.AddressFilter%2A> e as correspondências de ação da mensagem a <xref:System.ServiceModel.Dispatcher.EndpointDispatcher.ContractFilter%2A> propriedade. Se duas <xref:System.ServiceModel.Dispatcher.EndpointDispatcher> objetos podem aceitar uma mensagem, o <xref:System.ServiceModel.Dispatcher.EndpointDispatcher.FilterPriority%2A> valor da propriedade determina o ponto de extremidade de prioridade mais alta.  
  
 Use o <xref:System.ServiceModel.Dispatcher.EndpointDispatcher> para adquirir os dois pontos de extensão de modelo principal de serviço – o <xref:System.ServiceModel.Dispatcher.DispatchRuntime> e <xref:System.ServiceModel.Dispatcher.DispatchOperation> classes – que você pode usar para personalizar o processamento do dispatcher. O <xref:System.ServiceModel.Dispatcher.DispatchRuntime> classe permite que os usuários interceptar e estender o dispatcher no escopo do contrato (ou seja, para todas as mensagens em um contrato). O <xref:System.ServiceModel.Dispatcher.DispatchOperation> classe permite que os usuários interceptar e estender o dispatcher em um escopo de operação (ou seja, para todas as mensagens em uma operação).  
  
## <a name="scenarios"></a>Cenários  
 Há uma série de motivos para estender o dispatcher:  
  
-   Validação de mensagem personalizada. Os usuários podem impor que uma mensagem é válida para um determinado esquema. Isso pode ser feito ao implementar as interfaces de interceptador de mensagem. Por exemplo, consulte [inspetores de mensagem](../../../../docs/framework/wcf/samples/message-inspectors.md).  
  
-   Registro em log de mensagem personalizada. Os usuários podem inspecionar e um conjunto de mensagens de aplicativo por meio de um ponto de extremidade de fluxo de log. Isso também pode ser feito com as interfaces de interceptador de mensagem.  
  
-   Transformações de mensagens personalizadas. Os usuários podem aplicar determinadas transformações para a mensagem no tempo de execução (por exemplo, para controle de versão). Isso pode ser feito, novamente, com as interfaces de interceptador de mensagem.  
  
-   Modelo de dados personalizado. Os usuários podem ter um modelo de serialização de dados não suportados por padrão no WCF (ou seja, <xref:System.Runtime.Serialization.DataContractSerializer?displayProperty=nameWithType>, <xref:System.Xml.Serialization.XmlSerializer?displayProperty=nameWithType>e mensagens brutas). Isso pode ser feito por implementar as interfaces de formatador de mensagem. Por exemplo, consulte [formatador de operação e seletor de operação](../../../../docs/framework/wcf/samples/operation-formatter-and-operation-selector.md).  
  
-   Validação de parâmetro personalizado. Os usuários podem impor que os parâmetros de tipo são válidos (em vez de XML). Isso pode ser feito usando as interfaces do Inspetor de parâmetro.  
  
-   Expedição de operação personalizado. Os usuários podem implementar a expedição em algo diferente de ação – por exemplo, no elemento body ou em uma propriedade de mensagem personalizada. Isso pode ser feito usando o <xref:System.ServiceModel.Dispatcher.IDispatchOperationSelector> interface. Por exemplo, consulte [formatador de operação e seletor de operação](../../../../docs/framework/wcf/samples/operation-formatter-and-operation-selector.md).  
  
-   Ao pool de objetos. Os usuários podem o pool de instâncias em vez de alocar um novo para cada chamada. Isso pode ser implementado usando as interfaces de provedor de instância. Por exemplo, consulte [Pooling](../../../../docs/framework/wcf/samples/pooling.md).  
  
-   Instância de concessão. Os usuários podem implementar um padrão de concessão, por exemplo tempo de vida, semelhante de comunicação remota do .NET Framework. Isso pode ser feito usando as interfaces de tempo de vida do contexto de instância.  
  
-   Tratamento de erros personalizado. Os usuários podem controlar como os dois erros locais são processados e como as falhas serão comunicadas aos clientes. Isso pode ser implementado usando o <xref:System.ServiceModel.Dispatcher.IErrorHandler> interfaces.  
  
-   Comportamentos de autorização personalizado. Os usuários podem implementar o controle de acesso personalizadas estendendo as partes de tempo de execução do contrato ou de operação e adicionando as verificações de segurança com base em tokens presentes na mensagem. Isso pode ser feito usando o interceptador de mensagem ou interfaces de interceptor de parâmetro. Para obter exemplos, consulte [extensibilidade de segurança](../../../../docs/framework/wcf/samples/security-extensibility.md).  
  
    > [!CAUTION]
    >  Como alterar as propriedades de segurança tem o potencial de comprometer a segurança de aplicativos do WCF, é altamente recomendável que você empreender relacionadas à segurança modificações com cuidado e testar minuciosamente antes da implantação.  
  
-   Validadores de tempo de execução do WCF personalizados. Você pode instalar validadores personalizados que examinam os serviços, contratos e associações para impor políticas de nível empresarial em relação a aplicativos WCF. (Por exemplo, consulte [como: Bloquear pontos de extremidade na empresa](../../../../docs/framework/wcf/extending/how-to-lock-down-endpoints-in-the-enterprise.md).)  
  
### <a name="using-the-dispatchruntime-class"></a>Usando a classe DispatchRuntime  
 Use o <xref:System.ServiceModel.Dispatcher.DispatchRuntime> classe para modificar o comportamento padrão de um serviço ou um ponto de extremidade individual ou inserir objetos que implementam modificações personalizadas para um ou ambos os seguintes processos de serviço (ou processos de cliente no caso de um cliente duplex):  
  
-   A transformação de mensagens de entrada em objetos e liberar esses objetos como invocações de método em um objeto de serviço.  
  
-   A transformação de objetos recebidos de resposta para uma invocação de operação de serviço para as mensagens de saída.  
  
 O <xref:System.ServiceModel.Dispatcher.DispatchRuntime> lhe permite interceptar e estender o dispatcher do canal ou ponto de extremidade para todas as mensagens em um contrato específico, mesmo quando uma mensagem não é reconhecida. Quando chega uma mensagem que não corresponde a nenhum declarado no contrato que ela seja expedida para a operação retornada pelo <xref:System.ServiceModel.Dispatcher.DispatchRuntime.UnhandledDispatchOperation%2A> propriedade. Para interceptar ou estender em todas as mensagens de uma determinada operação, consulte o <xref:System.ServiceModel.Dispatcher.DispatchOperation> classe.  
  
 Há quatro áreas principais de extensibilidade do dispatcher expostos pelo <xref:System.ServiceModel.Dispatcher.DispatchRuntime> classe:  
  
1.  Componentes de canal usam as propriedades do <xref:System.ServiceModel.Dispatcher.DispatchRuntime> e aqueles do dispatcher do canal associado, retornado pelo <xref:System.ServiceModel.Dispatcher.DispatchRuntime.ChannelDispatcher%2A> propriedade para personalizar como o dispatcher do canal aceita e fecha canais. Essa categoria inclui as <xref:System.ServiceModel.Dispatcher.ChannelDispatcher.ChannelInitializers%2A> e <xref:System.ServiceModel.Dispatcher.DispatchRuntime.InputSessionShutdownHandlers%2A> propriedades.  
  
2.  Componentes de mensagens personalizadas para cada mensagem processada. Essa categoria inclui as <xref:System.ServiceModel.Dispatcher.DispatchRuntime.MessageInspectors%2A>, <xref:System.ServiceModel.Dispatcher.DispatchRuntime.OperationSelector%2A>, <xref:System.ServiceModel.Dispatcher.DispatchRuntime.Operations%2A>e o <xref:System.ServiceModel.Dispatcher.ChannelDispatcher.ErrorHandlers%2A> propriedades.  
  
3.  Componentes da instância personalizar a criação, tempo de vida e descarte de instâncias do tipo de serviço. Para obter mais informações sobre os tempos de vida de objeto de serviço, consulte o <xref:System.ServiceModel.ServiceBehaviorAttribute.InstanceContextMode%2A> propriedade. Essa categoria inclui as <xref:System.ServiceModel.Dispatcher.DispatchRuntime.InstanceContextInitializers%2A> e o <xref:System.ServiceModel.Dispatcher.DispatchRuntime.InstanceProvider%2A> propriedades.  
  
4.  Componentes de segurança podem usar as seguintes propriedades:  
  
    -   <xref:System.ServiceModel.Dispatcher.DispatchRuntime.SecurityAuditLogLocation%2A> indica onde os eventos de auditoria são gravados.  
  
    -   <xref:System.ServiceModel.Dispatcher.DispatchRuntime.ImpersonateCallerForAllOperations%2A> Controla se o serviço tentará representar usando as credenciais fornecidas pela mensagem de entrada.  
  
    -   <xref:System.ServiceModel.Dispatcher.DispatchRuntime.MessageAuthenticationAuditLevel%2A> Controla se os eventos de autenticação de mensagem bem-sucedida são gravados no log de eventos especificado pelo <xref:System.ServiceModel.Dispatcher.DispatchRuntime.SecurityAuditLogLocation%2A>.  
  
    -   <xref:System.ServiceModel.Dispatcher.DispatchRuntime.PrincipalPermissionMode%2A> controles como o <xref:System.Threading.Thread.CurrentPrincipal%2A> propriedade está definida.  
  
    -   <xref:System.ServiceModel.Dispatcher.DispatchRuntime.ServiceAuthorizationAuditLevel%2A> Especifica como a auditoria de eventos de autorização é executada.  
  
    -   <xref:System.ServiceModel.Dispatcher.DispatchRuntime.SuppressAuditFailure%2A> Especifica se deve ser suprimida exceções não críticas que ocorrem durante o processo de registro em log.  
  
 Normalmente, os objetos de extensão personalizada são atribuídos a um <xref:System.ServiceModel.Dispatcher.DispatchRuntime> propriedade ou inseridos em uma coleção por um comportamento de serviço (um objeto que implementa <xref:System.ServiceModel.Description.IServiceBehavior>), um comportamento de contrato (um objeto que implementa <xref:System.ServiceModel.Description.IContractBehavior>), ou um ponto de extremidade comportamento (um objeto que implementa <xref:System.ServiceModel.Description.IEndpointBehavior>). Em seguida, o objeto de comportamento de instalação é adicionado à coleção apropriada dos comportamentos de forma programática ou pela implementação de uma <xref:System.ServiceModel.Configuration.BehaviorExtensionElement> objeto para habilitar o comportamento a ser inserido usando um arquivo de configuração do aplicativo.  
  
 Clientes duplex (clientes que implementam um contrato de retorno de chamada especificado por um serviço duplex) também têm uma <xref:System.ServiceModel.Dispatcher.DispatchRuntime> objeto que pode ser acessado usando o <xref:System.ServiceModel.Dispatcher.ClientRuntime.CallbackDispatchRuntime%2A> propriedade.  
  
### <a name="using-the-dispatchoperation-class"></a>Usando a classe DispatchOperation  
 O <xref:System.ServiceModel.Dispatcher.DispatchOperation> classe é o local para modificações de tempo de execução e a inserção de ponto para extensões personalizadas que estão no escopo para apenas uma operação de serviço. (Para modificar o comportamento de tempo de execução de serviço para todas as mensagens em um contrato, use o <xref:System.ServiceModel.Dispatcher.DispatchRuntime> classe.)  
  
 Instalar <xref:System.ServiceModel.Dispatcher.DispatchOperation> modificações usando um objeto de comportamento de serviço personalizado.  
  
 Use o <xref:System.ServiceModel.Dispatcher.DispatchRuntime.Operations%2A> propriedade para localizar o <xref:System.ServiceModel.Dispatcher.DispatchOperation> objeto que representa uma operação de serviço específico.  
  
 As seguintes propriedades controlam a execução de tempo de execução no nível da operação:  
  
-   O <xref:System.ServiceModel.Dispatcher.DispatchOperation.Action%2A>, <xref:System.ServiceModel.Dispatcher.DispatchOperation.ReplyAction%2A>, <xref:System.ServiceModel.Dispatcher.DispatchOperation.FaultContractInfos%2A>, <xref:System.ServiceModel.Dispatcher.DispatchOperation.IsOneWay%2A>, <xref:System.ServiceModel.Dispatcher.DispatchOperation.IsTerminating%2A>, e <xref:System.ServiceModel.Dispatcher.DispatchOperation.Name%2A> as propriedades obtêm os respectivos valores para a operação.  
  
-   O <xref:System.ServiceModel.Dispatcher.DispatchOperation.TransactionAutoComplete%2A> e <xref:System.ServiceModel.Dispatcher.DispatchOperation.TransactionRequired%2A> especificam o comportamento de transação.  
  
-   O <xref:System.ServiceModel.Dispatcher.DispatchOperation.ReleaseInstanceBeforeCall%2A> e <xref:System.ServiceModel.Dispatcher.DispatchOperation.ReleaseInstanceAfterCall%2A> propriedades controlam o tempo de vida do objeto de serviço definido pelo usuário relativo a <xref:System.ServiceModel.InstanceContext>.  
  
-   O <xref:System.ServiceModel.Dispatcher.DispatchOperation.DeserializeRequest%2A>, <xref:System.ServiceModel.Dispatcher.DispatchOperation.SerializeReply%2A>e o <xref:System.ServiceModel.Dispatcher.DispatchOperation.Formatter%2A> propriedades permitem o controle explícito sobre a conversão de mensagens em objetos e às mensagens.  
  
-   O <xref:System.ServiceModel.Dispatcher.DispatchOperation.Impersonation%2A> propriedade especifica o nível de representação de operação.  
  
-   O <xref:System.ServiceModel.Dispatcher.DispatchOperation.CallContextInitializers%2A> propriedade insere extensões de contexto de chamada personalizadas para a operação.  
  
-   O <xref:System.ServiceModel.Dispatcher.DispatchOperation.AutoDisposeParameters%2A> propriedade controla quando objetos de parâmetro são destruídos.  
  
-   O <xref:System.ServiceModel.Dispatcher.DispatchOperation.Invoker%2A> propriedade para inserir um objeto chamador personalizado.  
  
-   O <xref:System.ServiceModel.Dispatcher.DispatchOperation.ParameterInspectors%2A> propriedade permite que você insira um Inspetor de parâmetro personalizado que você pode usar para inspecionar ou modificar os parâmetros e valores de retorno.  
  
## <a name="see-also"></a>Consulte também
- <xref:System.ServiceModel.Dispatcher.DispatchRuntime>
- <xref:System.ServiceModel.Dispatcher.DispatchOperation>
- [Como: Inspecionar e modificar mensagens do serviço](../../../../docs/framework/wcf/extending/how-to-inspect-and-modify-messages-on-the-service.md)
- [Como: Inspecionar ou modificar parâmetros](../../../../docs/framework/wcf/extending/how-to-inspect-or-modify-parameters.md)
- [Como: Bloquear pontos de extremidade na empresa](../../../../docs/framework/wcf/extending/how-to-lock-down-endpoints-in-the-enterprise.md)
