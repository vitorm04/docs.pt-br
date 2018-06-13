---
title: Estrutura de serviço
ms.date: 03/30/2017
ms.assetid: 75f60b87-f80e-4377-ba7c-8e6becaa2b28
ms.openlocfilehash: 859e718a56ab63c8e012e1851c0730f53cb707be
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33474916"
---
# <a name="service-framework"></a>Estrutura de serviço
Este tópico lista todas as exceções geradas pelo serviço de estrutura de dados.  
  
## <a name="exception-list"></a>Lista de exceções  
  
|Código do recurso|Cadeia de caracteres de recurso|  
|-------------------|---------------------|  
|ABindingInstanceHasAlreadyBeenAssociatedTo1|Uma instância de ligação já foi associada para escutar o identificador de recurso uniforme especificado. Se dois pontos de extremidade quiserem compartilhar o mesmo indicador de recurso ListenUniform, também deverão compartilhar a mesma instância de objeto de associação. Os dois pontos de extremidade conflitantes foram especificados nas chamadas AddServiceEndpoint (), em um arquivo de configuração ou uma combinação de AddServiceEndpoint () e configuração.|  
|AChannelServiceEndpointIsNull0|Um ponto de extremidade de canal ou de serviço é nulo.|  
|AChannelServiceEndpointSContractSNameIsNull0|Um nome de contrato de ponto de extremidade de canal/serviço é nulo ou vazio.|  
|AChannelServiceEndpointSContractSNamespace0|Um namespace de contrato de ponto de extremidade de canal/serviço é nulo.|  
|BaseAddressCannotHaveFragment|Um endereço base não pode conter um fragmento de identificador de recurso uniforme.|  
|BaseAddressCannotHaveQuery|Um endereço base não pode conter uma cadeia de caracteres de consulta de identificador de recurso uniforme.|  
|BaseAddressCannotHaveUserInfo|Um endereço base não pode conter uma seção de informações de usuário do uniform resource identificador.|  
|BaseAddressDuplicateScheme|Esta coleção já contém um endereço com o esquema especificado. Apenas um endereço é permitido para cada esquema nesta coleção.|  
|BaseAddressMustBeAbsolute|Apenas um identificador de recurso uniforme absoluto pode ser usado como um endereço base.|  
|BindingDoesnTSupportAnyChannelTypes1|A associação especificada não oferece suporte à criação de tipos de canal. Os elementos de associação em uma associação personalizada são empilhados incorretamente ou na ordem errada. Transport é necessário na parte inferior para a pilha. A ordem recomendada para elementos de associação é: TransactionFlow, ReliableSession, Security, CompositeDuplex, OneWay, StreamSecurity, MessageEncoding, Transport.|  
|BindingDoesnTSupportDuplexButContractRequires1|Contrato requer Duplex. A associação especificada não dá suporte ou não está configurada corretamente para oferecer suporte a ele.|  
|BindingDoesnTSupportOneWayButContractRequires1|Contrato requer OneWay. A associação especificada não dá suporte ou não está configurada corretamente para oferecer suporte a ele.|  
|BindingDoesnTSupportRequestReplyButContract1|Contrato requer solicitação/resposta. A associação especificada não dá suporte ou não está configurada corretamente para oferecer suporte a ele.|  
|BindingDoesnTSupportSessionButContractRequires1|Contrato requer Session.  A associação especificada não dá suporte ou não está configurada corretamente para oferecer suporte a ele.|  
|BindingDoesnTSupportTwoWayButContractRequires1|Contrato requer bidirecional (solicitação / resposta ou duplex). A associação especificada não dá suporte ou não está configurada corretamente para oferecer suporte a ele.|  
|BindingRequirementsAttributeDisallowsQueuedDelivery1|DeliveryRequirementsAttribute não permite QueuedDelivery. A associação para o ponto de extremidade com o contrato especificado oferece suporte a ele.|  
|BindingRequirementsAttributeRequiresQueuedDelivery1|DeliveryRequirementsAttribute requer QueuedDelivery. A associação para o ponto de extremidade com o contrato especificado não dá suporte ou não está configurada corretamente para oferecer suporte a ele.|  
|channelDoesNotHaveADuplexSession0|O canal atual não oferece suporte para fechar a sessão de saída. Este canal não implementa ISessionChannel\<IDuplexSession >.|  
|ClientRuntimeRequiresFormatter0|ClientOperation especificado requer um formatador, porque o valor de SerializeRequest e DeserializeReply não é false.|  
|CommunicationObjectAborted1|O objeto de comunicação especificado não pode ser usado para comunicação porque foi interrompido.|  
|CommunicationObjectAbortedStack2|O objeto de comunicação especificado não pode ser usado para comunicação porque foi interrompida: {1}|  
|CommunicationObjectBaseClassMethodNotCalled|O objeto de comunicação especificado substituiu a função virtual {1} , mas não chama a versão definida na classe base.|  
|ContractIsNotSelfConsistentItHasOneOrMore2|O contrato especificado tem um ou mais IsTerminating ou não IsInitiating operações. Ele não tem a propriedade SessionMode definida como SessionMode. Os atributos IsInitiating e IsTerminating somente podem ser usados no contexto de uma sessão.|  
|CouldnTCreateChannelForChannelType2|O tipo de canal especificado foi solicitado, mas a associação especificada não dá suporte ou não está configurada corretamente para oferecer suporte a ele.|  
|DispatchRuntimeRequiresFormatter0|DispatchOperation especificado requer um formatador, porque o valor de DeserializeRequest e SerializeReply não é false.|  
|EndMethodsCannotBeDecoratedWithOperationContractAttribute|Não pode ser usado o método End com OperationContractAttribute ao usar o padrão de design IAsyncResult. Apenas o método Begin correspondente pode ser usado com OperationContractAttribute. Esse atributo aplica-se ao par de métodos Begin-End.|  
|EndpointListenerRequirementsCannotBeMetBy3|Os requisitos de ChannelDispatcher não podem ser atendidos por IChannelListener para a associação especificada porque o contrato requer suporte para um desses tipos de canal especificado. Mas a associação apenas oferece suporte a esses tipos de canal especificado.|  
|EndpointsMustHaveAValidBinding0|Pontos de extremidade devem ter uma associação válida.|  
|InvalidOrUnrecognizedAction|A mensagem não pode ser processada porque a ação especificada é inválida ou não reconhecida.|  
|MultipleMebesInParameters|Mais de uma classe MessageEncodingBindingElement foi encontrado em BindingParameters de BindingContext. CustomBinding não pode ter vários MessageEncodingBindingElements. Remova todos deixando apenas um desses elementos.|  
|MultipleStreamUpgradeProvidersInParameters|Mais de uma classe IStreamUpgradeProviderElement foi encontrada em BindingParameters de BindingContext. CustomBinding não pode ter mais de um IStreamUpgradeProviderElements. Remova todos deixando apenas um desses elementos.|  
|NoChannelBuilderAvailable|A associação não pode ser usada para criar uma fábrica de canais ou um ouvinte de canal porque ele não tem um TransportBindingElement. Todas as associações devem ter pelo menos um elemento de associação derivado de TransportBindingElement.|  
|NotAllBindingElementsBuilt|Alguns dos elementos de associação nesta associação não foram usadas ao criar a fábrica de canal e ouvinte de canal. Os elementos de associação não são ordenados corretamente. A ordem recomendada para elementos de associação é: TransactionFlow, ReliableSession, Security, CompositeDuplex, OneWay, StreamSecurity, MessageEncoding, Transport.  Observe que TransportBindingElement deve vir por último. Os elementos de associação especificada não foram criados.|  
|RuntimeRequiresInvoker0|A operação de distribuição requer um chamador.|  
|ServiceHasZeroAppEndpoints|O serviço especificado não tem nenhum ponto de extremidade do aplicativo (não-infraestrutura). Isso pode ser porque nenhum arquivo de configuração foi encontrado para o seu aplicativo ou porque nenhum elemento de serviço correspondente ao nome do serviço foi encontrado no arquivo de configuração ou porque nenhum ponto de extremidade foi definido no elemento de serviço.|  
|SFxActionMismatch|Não é possível criar uma mensagem tipada devido a uma incompatibilidade de ação. Esperando que a ação especificada mas encontrou outro|  
|SFxAnonymousTypeNotSupported|A parte especificada na mensagem especificada não pode ser exportada com RPC ou codificada porque seu tipo é anônimo.|  
|SFxBadMetadataLocationNoAppropriateBaseAddress|A URL fornecida para ServiceMetadataBehavior usando a propriedade ExternalMetadataLocation ou atributo externalMetadataLocation na seção serviceMetadata na seção de configuração era uma URL relativa e não há nenhum endereço base com a qual resolver ele.|  
|SFxBadMetadataMustBePolicy|Forneça uma XmlElement que tem o namespace especificado e o nome da política. Este XmlElement tem o namespace especificado e o nome.|  
|SFxBodyObjectTypeCannotBeInherited|O tipo especificado não pode herdar de qualquer classe que não seja o objeto a ser usado como o objeto do corpo no estilo RPC.|  
|SFxBodyObjectTypeCannotBeInterface|O tipo especificado implementa a interface especificada, não há suporte para o objeto do corpo no estilo RPC.|  
|SFxCallbackBehaviorAttributeOnlyOnDuplex|CallbackBehaviorAttribute só pode ser executado como um comportamento em um ponto de extremidade com um contrato duplex. O contrato especificado não é duplex e não contém nenhuma operação de retorno de chamada.|  
|SFxCallbackRequestReplyInOrder1|Não é possível receber a resposta dessa operação até que a mensagem atual Complete o processamento. Se você quiser permitir o processamento de mensagem fora de ordem, especifique ConcurrencyMode no Reentrante ou múltiplo em especificado.|  
|SfxCallbackTypeCannotBeNull|Para usar o contrato especificado com DuplexChannelFactory, o contrato deve especificar um contrato de retorno de chamada válido. Se o contrato tiver um contrato de retorno de chamada, use ChannelFactory em vez da DuplexChannelFactory.|  
|SFxCannotGetMetadataFromLocation|MetadataExchangeClient só pode obter metadados de HTTP e HTTPS MetadataLocations. Não é possível obter metadados especificado.|  
|SFxCannotHttpGetMetadataFromAddress|MetadataExchangeClient só pode obter metadados de endereços HTTP ou HTTPS quando usar o HttpGet do MetadataExchangeClientMode. Não é possível obter metadados especificado.|  
|SFxCannotImportAsParameters_Bare|Gerando contrato de mensagem porque a operação especificada não é RPC nem documento codificado.|  
|SFxCannotImportAsParameters_DifferentWrapperName|Gerando contrato de mensagem porque o nome de wrapper da mensagem especificada não coincide com o valor padrão.|  
|SFxCannotImportAsParameters_DifferentWrapperNs|Gerando contrato de mensagem porque o namespace do conteúdo da mensagem especificada não coincide com o valor padrão.|  
|SFxCannotImportAsParameters_ElementIsNotNillable|Gerar um contrato de mensagem porque o nome do elemento especificado do namespace especificado não está marcado como nulo.|  
|SFxCannotImportAsParameters_HeadersAreUnsupported|Gerando contrato de mensagem porque a mensagem especificada tem cabeçalhos.|  
|SFxCannotImportAsParameters_Message|Gerar um contrato de mensagem porque a operação especificada tem uma mensagem não tipada como argumento ou tipo de retorno.|  
|SFxCannotImportAsParameters_MessageHasProtectionLevel|Gerando contrato de mensagem porque a mensagem especificada requer proteção.|  
|SFxCannotImportAsParameters_NamespaceMismatch|Gerando contrato de mensagem porque o namespace de parte de mensagem especificada não coincide com o valor padrão.|  
|SFxCannotRequireBothSessionAndDatagram3|O contrato especificado Especifica SessionMode e o contrato especificado Especifica SessionMode. Alterar um dos valores de SessionMode ou especificar um endereço diferente ou ListenURI, para cada ponto de extremidade.|  
|SFxCannotSetExtensionsByIndex|Esta coleção não oferece suporte a configuração de extensões por índice. Use os métodos InsertItem ou RemoveItem.|  
|SFxChannelDispatcherDifferentHost0|O ChannelDispatcher não está atualmente anexado ao ServiceHost fornecido.|  
|SFxChannelDispatcherMultipleHost0|O ChannelDispatcher não pode ser adicionado a mais de um ServiceHost.|  
|SFxChannelDispatcherNoHost0|O ChannelDispatcher não pode ser aberto porque ele não está anexado a um ServiceHost.|  
|SfxChannelFactoryDisposed|Este ChannelFactory não pode ser aberto como a ChannelFactory já foi descartada. Crie a ChannelFactory novamente antes de usá-lo.|  
|SFxChannelFactoryNoBinding|A ChannelFactory não pode ser aberta porque nenhuma associação foi associada a seu ponto de extremidade. Especifique uma associação com o construtor ou a propriedade de ponto de extremidade.|  
|SFxChannelTerminated0|Uma operação marcada como IsTerminating já foi invocada neste canal, causando a conexão de canal encerrar. Nenhuma outra operação pode ser invocada neste canal. Recrie o canal para continuar a comunicação.|  
|SFxCloseTimedOut1|A operação de fechamento ServiceHost interrompido após especificado. Isso pode ser porque um cliente falha ao fechar um canal de sessão no tempo necessário. O tempo permitido para esta operação pode ter sido parte de um tempo limite maior.|  
|SfxCloseTimedOutWaitingForDispatchToComplete|O processo de fechamento atingiu o tempo limite ao aguardar a conclusão da distribuição de serviço.|  
|SFxCodeGenIsNotAssignableFrom|Especificado não pode ser atribuído.|  
|SFxConfigChannelConfigurationNotFound|Não foi encontrado o elemento de ponto de extremidade com o nome especificado e o contrato na seção de configuração do ServiceModel cliente.|  
|SFxConflictingGlobalElement|O elemento XML de nível superior com o nome especificado no namespace especificado não pode fazer referência ao tipo especificado. Já faz referência a um tipo diferente. Use um nome de operação diferente ou MessageBodyAttribute para especificar um nome diferente para a mensagem ou partes da mensagem.|  
|SFxContractHasZeroInitiatingOperations|Um contrato deve ter pelo menos um IsInitiating = true operação.|  
|SFxContractHasZeroOperations|Um contrato deve ter pelo menos uma operação.|  
|SFxContractInheritanceRequiresInterfaces|A classe de serviço do tipo especificado define um ServiceContract e herda um ServiceContract do tipo especificado. Herança de contrato só pode ser usada entre tipos de interface. Se uma classe está marcada com ServiceContractAttribute, ela deverá ser o único tipo na hierarquia com ServiceContractAttribute.  Mova ServiceContractAttribute no tipo especificado para uma interface separada que implementa o tipo especificado.|  
|SFxCreateDuplexChannel1|O contrato de retorno de chamada do contrato especificado não existe ou não define nenhuma operação. Se não for um contrato duplex, use a ChannelFactory em vez da DuplexChannelFactory.|  
|SFxCreateDuplexChannelNoCallback|Esta sobrecarga do CreateChannel não pode ser chamada na instância da DuplexChannelFactory. A DuplexChannelFactory foi inicializada com um InstanceContext. Chame a sobrecarga de CreateChannel que recebe um InstanceContext.|  
|SFxCreateDuplexChannelNoCallback1|Esta sobrecarga do CreateChannel não pode ser chamada na instância da DuplexChannelFactory. A DuplexChannelFactory foi inicializada com um tipo e nenhum InstanceContext válido foi fornecido. Chame a sobrecarga de CreateChannel que recebe um InstanceContext.|  
|SFxCreateDuplexChannelNoCallbackUserObject|Esta sobrecarga do CreateChannel não pode ser chamada na instância da DuplexChannelFactory. A InstanceContext fornecida para a DuplexChannelFactory não contém um UserObject válido.|  
|SFxCreateNonDuplexChannel1|ChannelFactory não oferece suporte para o contrato especificado. ChannelFactory define um contrato de retorno de chamada com uma ou mais operações. Use DuplexChannelFactory em vez de ChannelFactory.|  
|SFxCustomBindingNeedsTransport1|A CustomBinding no ServiceEndpoint com contrato especificado não tem um TransportBindingElement. Todas as associações devem ter pelo menos um elemento de associação derivado de TransportBindingElement.|  
|SFxCustomBindingWithoutTransport|O esquema não pode ser computado para esta associação personalizado porque ele não tem um TransportBindingElement. Todas as associações devem ter pelo menos um elemento de associação derivado de TransportBindingElement.|  
|SFxDataContractSerializerDoesNotSupportBareArray|DataContractSerializer não oferece suporte para a coleção especificada no elemento especificado.|  
|SFxDictionaryIsEmpty|A operação não pode ser executada porque o dicionário está vazio.|  
|SFxDocEncodedNotSupported|Erro ao refletir especificado. Não há suporte para o documento codificado. Altere 'Use' para Literal ou estilo RPC.|  
|SFxDuplicateInitiatingActionAtSameVia|Este serviço tem vários pontos de extremidade escutando no local especificado. Os pontos de extremidade compartilham a mesma ação inicial especificada. Mensagens com essa ação serão ignoradas porque o distribuidor não poderá determinar o ponto de extremidade correto para manipular a mensagem.|  
|SFXEndpointBehaviorUsedOnWrongSide|O IEndpointBehavior especificado não pode ser usado no servidor. Esse comportamento só pode se aplica aos clientes.|  
|SFxEndpointNoMatchingScheme|O endereço base que corresponda ao esquema especificado para o ponto de extremidade com a associação especificada não pode ser encontrado. Endereço base registrado esquemas são especificadas.|  
|SFxErrorCreatingMtomReader|Ocorreu um erro ao criar uma leitora para a mensagem de mecanismo de otimização de transmissão de mensagem.|  
|SFxErrorDeserializingFault|O servidor retornou uma falha de protocolo de acesso de objeto simples inválido. Consulte a InnerException para obter mais detalhes.|  
|SFxErrorDeserializingHeader|Ocorreu um erro durante a desserialização de um dos cabeçalhos da mensagem especificado. Consulte a InnerException para obter mais detalhes.|  
|SFxErrorReflectingOnMethod3|Ocorreu um erro ao carregar o atributo especificado no método especificado no tipo especificado.  Consulte a InnerException para obter mais detalhes.|  
|SFxErrorReflectingOnParameter4|Ocorreu um erro ao carregar o atributo especificado no parâmetro especificado do método especificado no tipo especificado. Consulte a InnerException para obter mais detalhes.|  
|SFxErrorReflectingOnType2|Ocorreu um erro ao carregar o atributo especificado no tipo especificado.  Consulte a InnerException para obter mais detalhes.|  
|SFxErrorSerializingBody|Ocorreu um erro ao serializar o corpo da mensagem especificada. Consulte a InnerException para obter mais detalhes.|  
|SFxErrorSerializingHeader|Ocorreu um erro durante a serialização de um dos cabeçalhos da mensagem especificado. Consulte a InnerException para obter mais detalhes.|  
|SFxExpectedIMethodCallMessage|Erro interno. A mensagem deve ser uma IMethodCallMessage válida.|  
|SFxExportMustHaveType|A parte especificada na operação especificada não pode ser exportada porque ele não tem um tipo CLR válido.|  
|SFxHeaderNotUnderstood|A mensagem não foi processada. O cabeçalho especificado do namespace especificado não foi entendido pelo destinatário desta mensagem. Esse erro normalmente indica que o remetente desta mensagem habilitou um protocolo de comunicação que o receptor não pode processar. Certifique-se de que a configuração de ligação do cliente é consistente com a associação do serviço.|  
|SFxHeadersAreNotSupportedInEncoded|A mensagem especificada não deve ter cabeçalhos para ser usada no estilo codificado de chamada de procedimento remoto.|  
|SFxInconsistentWsdlOperationStyleInMessageParts|Todas as partes da mensagem na operação especificada devem conter um tipo ou um elemento.|  
|SFxInconsistentWsdlOperationStyleInOperationMessages|O estilo especificado inferido nas mensagens na operação especificada não coincide com o estilo esperado especificado especificado usando associações.|  
|SFxInvalidCallbackIAsyncResult|IAsyncResult não fornecido ou é do tipo errado.|  
|SFxInvalidMessageBody|O OperationFormatter encontrou um corpo de mensagem inválido. O tipo de nó com o nome especificado e o namespace 'Element' era esperado. O tipo de nó especificado com o nome especificado e o namespace foi encontrado.|  
|SFxInvalidMessageBodyEmptyMessage|O OperationFormatter não é possível desserializar nenhuma informação da mensagem porque a mensagem está vazia.|  
|SFxInvalidMessageBodyErrorDeserializingParameter|Ocorreu um erro ao tentar desserializar o parâmetro especificado. Consulte a InnerException para obter mais informações.|  
|SFxInvalidMessageBodyErrorSerializingParameter|Ocorreu um erro ao tentar desserializar o parâmetro especificado. A mensagem da InnerException foi especificada.  Consulte a InnerException para obter mais detalhes.|  
|SFxInvalidMessageBodyUnexpectedNode|Encontrado nó inesperado especificado, do namespace especificado durante a desserialização de parâmetros.|  
|SFxInvalidMessageContractSignature|A operação especificada tem um parâmetro ou um tipo de retorno é marcado com MessageContractAttribute. Ao usar um contrato de mensagem para representar uma mensagem de solicitação, a operação deve ter um único parâmetro que está marcado com MessageContractAttribute. Ao usar um contrato de mensagem para representar a mensagem de resposta, o valor de retorno da operação deve ser um tipo que está marcado com MessageContractAttribute. A operação não pode ter 'out' ou 'ref' parâmetros.|  
|SFxInvalidReplyAction|A mensagem de resposta de saída para a operação tem a ação especificada, mas o contrato para essa operação especifica ReplyAction outro. A ação especificada na mensagem deve corresponder à ReplyAction no contrato, ou o contrato de operação deve especificar ReplyAction ='* '.|  
|SFxInvalidRequestAction|A mensagem de solicitação de saída para a operação tem a ação especificada, mas o contrato para essa operação Especifica outro RequestAction. A ação especificada na mensagem deve corresponder a RequestAction no contrato, ou o contrato de operação deve especificar RequestAction ='* '.|  
|SFxInvalidStaticOverloadCalledForDuplexChannelFactory1|O método CreateChannel estático não pode ser usado com o contrato especificado porque esse contrato define um contrato de retorno de chamada. Use uma das sobrecargas CreateChannel estáticas em DuplexChannelFactory\<TChannel >.|  
|SFxInvalidStreamInRequest|Para a solicitação na operação especificada ser um fluxo, a operação deve ter um parâmetro único cujo tipo é Stream.|  
|SFxInvalidStreamInResponse|Para a resposta na operação especificada para ser um fluxo, a operação deve ter um único parâmetro out ou retornar o valor cujo tipo é Stream.|  
|SFxInvalidStreamInTypedMessage|Para usar streams com o modelo de programação de contrato de mensagem, o tipo especificado deve ter um único membro MessageBody cujo tipo é Stream.|  
|SFxInvalidUseOfPrimitiveOperationFormatter|Para PrimitiveOperationFormatter foi fornecido um parâmetro ou que não dá suporte a tipo de retorno.|  
|SFxMessageContractBaseTypeNotValid|O tipo especificado define um MessageContract e deriva de um tipo especificado que não define um MessageContract. Todos os objetos na hierarquia de herança especificado devem definir um MessageContract.|  
|SFxMethodNotSupported1|Não há suporte para o método especificado no objeto. Isso pode acontecer se o método não está marcado com OperationContractAttribute ou se o tipo de interface não está marcado com ServiceContractAttribute.|  
|SFxMethodNotSupportedByType2|O tipo de implementação do ServiceHost não implementa o contrato de serviço especificado.|  
|SFxMethodNotSupportedOnCallback1|O método de retorno de chamada especificado não é suportado. Isso pode acontecer se o método não está marcado com OperationContractAttribute ou se seu tipo de interface não é o destino de CallbackContract de ServiceContractAttribute.|  
|SFxMismatchedOperationParent|Um DispatchOperation ou ClientOperation só pode ser adicionado ao seu pai DispatchRuntime ou ClientRuntime respectivamente.|  
|SFxNameCannotBeEmpty|A propriedade Name não pode ser uma cadeia de caracteres vazia.|  
|SfxNoTypeSpecifiedForParameter|Nenhum tipo CLR foi especificado para o parâmetro, o que impede que a operação fosse gerada.|  
|SFxOperationBehaviorAttributeOnlyOnServiceClass|OperationBehaviorAttribute só pode pertencer à classe de serviço. Ele não pode ser colocado na interface ServiceContract. O método especificado no tipo especificado viola essa regra.|  
|SFxOperationContractOnNonServiceContract|O método especificado está marcado com OperationContractAttribute, mas o tipo de delimitador especificado não está marcado com ServiceContractAttribute. O OperationContractAttribute só pode ser usado em métodos nos tipos ServiceContractAttribute ou em seus tipos CallbackContract.|  
|SFxParameterCountMismatch|Ocorreu uma incompatibilidade entre o número de argumentos fornecidos e o número de argumentos esperados. Especificamente, o argumento especificado tem o número especificado de elementos enquanto o argumento esperado tem o número especificado de elementos.|  
|SFxPartNameMustBeUniqueInRpc|O nome da parte de mensagem especificada não é exclusivo em uma mensagem de chamada de procedimento remoto.|  
|SFxReplyActionMismatch3|Uma mensagem de resposta foi recebida para a operação especificada com a ação especificada. No entanto, o código do cliente requer a ação especificada.|  
|SFxRequestReplyNone|Foi recebida uma mensagem com um cabeçalho de WS-Addressing ReplyTo ou FaultTo destinado "None" endereço. Esses valores não são válidos para operações de solicitação-resposta. Use uma operação unidirecional ou habilitar ManualAddressing se você precisar oferecer suporte a valores ReplyTo ou FaultTo de "None".|  
|SFxRequestTimedOut1|Esta operação de solicitação não recebeu uma resposta no tempo especificado configurado. O tempo permitido pode ter sido parte de um tempo limite maior. Isso pode ocorrer porque o serviço ainda está processando a operação ou porque o serviço não conseguiu enviar uma mensagem de resposta.|  
|SFxRequestTimedOut2|A operação de solicitação enviada para o local especificado não recebeu uma resposta no tempo especificado configurado. O tempo permitido pode ter sido parte de um tempo limite maior. Isso pode ocorrer porque o serviço ainda está processando a operação ou porque o serviço não conseguiu enviar uma mensagem de resposta.|  
|SFxSchemaDoesNotContainType|Esquema com o namespace de destino especificado não contém um tipo com o nome especificado.|  
|SfxServiceContractAttributeNotFound|O tipo de contrato especificado não é atribuído com ServiceContractAttribute. Para definir um contrato válido, o tipo especificado deve ser atribuído com ServiceContractAttribute. O tipo pode ser uma interface de contrato ou uma classe de serviço.|  
|SFxServiceContractGeneratorConfigRequired|Para gerar informações de configuração usando o método GenerateServiceEndpoint, a instância da ServiceContractGenerator deve ser inicializada com um objeto de configuração válido.|  
|SFxServiceHostBaseCannotAddEndpointAfterOpen|Pontos de extremidade não podem ser adicionados após o ServiceHost está em um dos seguintes estados:<br /><br /> -Aberto<br />-Com falha<br />-Encerrada<br />-Fechado|  
|SFxServiceHostBaseCannotAddEndpointWithoutDescription|Pontos de extremidade não podem ser adicionados antes que a propriedade Description seja inicializada.|  
|SFxServiceMetadataBehaviorNoHttpBaseAddress|O HttpGetEnabled de ServiceMetadataBehavior está definida como true e a propriedade HttpGetUrl é um endereço relativo, mas não há nenhum endereço base HTTP. Forneça um endereço base HTTP ou defina HttpGetUrl como um endereço absoluto.|  
|SFxServiceMetadataBehaviorNoHttpsBaseAddress|O HttpsGetEnabled de ServiceMetadataBehavior está definida como true e a propriedade HttpsGetUrl é um endereço relativo, mas não há nenhum endereço base HTTPS. Forneça um endereço base HTTPS ou defina HttpsGetUrl como um endereço absoluto.|  
|SFxServiceMetadataBehaviorUrlMustBeHttpOrRelative|A Url de comportamento deve ser um identificador de recurso uniforme relativo ou um identificador de recurso uniforme absoluto com o esquema especificado. A Url especificada é um identificador de recurso uniforme absoluto com o esquema especificado.|  
|SFxStreamRequestMessageClosed|A mensagem que contém este fluxo foi fechada. Fluxos de solicitação não podem ser acessados após a operação de serviço retorna.|  
|SFxStreamResponseMessageClosed|A mensagem que contém este fluxo foi fechada.|  
|SFxTerminateRequestProcessingException|Uma extensão no pipeline de operação deve encerrar processando a mensagem.|  
|SFxTerminatingOperationAlreadyCalled1|Este canal não pode enviar mais mensagens porque a operação IsTerminating foi chamada.|  
|SFxThrottleLimitMustBeGreaterThanZero0|O limite deve ser maior que zero. Para desabilitar o limite, defina o valor de Int32. MaxValue.|  
|SFxTypedOrUntypedMessageCannotBeMixedWithVoidInRpc|Ao usar o estilo de codificação RPC, tipos de contrato de mensagem ou o tipo de Channels não pode ser usado se a operação não tem parâmetros ou tem um valor de retorno void. Adicionar um tipo de contrato de mensagem em branco como um parâmetro ou tipo de retorno à operação especificada.|  
|SFxUserCodeThrewException|A operação de usuário especificado lançou uma exceção sem tratamento no código do usuário. Se esse for um problema recorrente, isso pode indicar um erro na implementação do método especificado.|  
|SfxUseTypedMessageForCustomAttributes|O parâmetro especificado não pode ser mapeado para o parâmetro de operação, porque ele requer atributos adicionais.|  
|SFxVersionMismatchInOperationContextAndMessage2|Não é possível adicionar cabeçalhos de saída à mensagem, pois MessageVersion em OperationContext não coincide com a versão de cabeçalho da mensagem que está sendo processada|  
|SFxWellKnownNonSingleton0|Para usar um dos construtores ServiceHost que utiliza uma instância de serviço, o InstanceContextMode do serviço deve ser definido como InstanceContextMode. Isso pode ser configurado usando o ServiceBehaviorAttribute. Caso contrário, use os construtores ServiceHost que utilizam um argumento de tipo.|  
|SFxWrapperTypeHasMultipleNamespaces|Tipo de wrapper para a mensagem especificada não pode ser projetado como um tipo de contrato de dados porque ele tem vários namespaces. Use o XmlSerializer.|  
|UriMustBeAbsolute|O URI deve ser absoluto.|
