---
title: Especificando comportamento de tempo de execução de serviço
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 5c5450ea-6af1-4b75-a267-613d0ac54707
ms.openlocfilehash: 246f16cee85633499a6a1c200e608ee7bccf133c
ms.sourcegitcommit: 7980a91f90ae5eca859db7e6bfa03e23e76a1a50
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/13/2020
ms.locfileid: "81243096"
---
# <a name="specifying-service-run-time-behavior"></a>Especificando comportamento de tempo de execução de serviço
Depois de ter projetado um contrato de serviço[(Projetando Contratos de Serviço)](designing-service-contracts.md)e implementado seu contrato de serviço[(Implementando Contratos de Serviços)](implementing-service-contracts.md)você pode configurar o comportamento de operação do tempo de execução do serviço. Este tópico discute comportamentos de serviço e operação fornecidos pelo sistema e descreve onde encontrar mais informações para criar novos comportamentos. Embora alguns comportamentos sejam aplicados como atributos, muitos são aplicados usando um arquivo de configuração de aplicativo ou programáticamente. Para obter mais informações sobre a configuração do aplicativo de serviço, consulte [Configuração de serviços](configuring-services.md).  
  
## <a name="overview"></a>Visão geral  
 O contrato define as entradas, saídas, tipos de dados e capacidades de um serviço desse tipo. A implementação de um contrato de prestação de serviços cria uma classe que, quando configurada com uma vinculação em um endereço, cumpre o contrato que implementa. As informações contratuais, vinculativas e de endereço são todas conhecidas pelo cliente; sem eles, o cliente não pode fazer uso do serviço.  
  
 No entanto, as especificidades da operação, como problemas de threading ou gerenciamento de instâncias, são opacas para os clientes. Depois de implementar seu contrato de serviço, você pode configurar um grande número de características de operação usando *comportamentos*. Comportamentos são objetos que modificam o tempo de execução da Windows Communication Foundation (WCF) definindo uma propriedade em tempo de execução ou inserindo um tipo de personalização no tempo de execução. Para obter mais informações sobre como modificar o tempo de execução, criando comportamentos definidos pelo usuário, consulte [Extending ServiceHost e a Camada de modelo de serviço](./extending/extending-servicehost-and-the-service-model-layer.md).  
  
 Os <xref:System.ServiceModel.ServiceBehaviorAttribute?displayProperty=nameWithType> <xref:System.ServiceModel.OperationBehaviorAttribute?displayProperty=nameWithType> e atributos são os comportamentos mais úteis e expõem os recursos de operação mais solicitados. Por serem atributos, você os aplica à implementação do serviço ou da operação. Outros comportamentos, como <xref:System.ServiceModel.Description.ServiceMetadataBehavior?displayProperty=nameWithType> o <xref:System.ServiceModel.Description.ServiceDebugBehavior?displayProperty=nameWithType>ou , são tipicamente aplicados usando um arquivo de configuração de aplicativo, embora você possa usá-los programáticamente.  
  
 Este tópico fornece uma <xref:System.ServiceModel.ServiceBehaviorAttribute> visão <xref:System.ServiceModel.OperationBehaviorAttribute> geral dos e atributos, descreve os vários escopos nos quais os comportamentos podem operar e fornece uma descrição rápida de muitos dos comportamentos fornecidos pelo sistema nos vários âmbitos que podem ser de interesse dos desenvolvedores do WCF.  
  
## <a name="servicebehaviorattribute-and-operationbehaviorattribute"></a>ServiceBehaviorAttribute e OperationBehaviorAttribute  
 Os comportamentos mais importantes <xref:System.ServiceModel.ServiceBehaviorAttribute> <xref:System.ServiceModel.OperationBehaviorAttribute> são os e atributos, que você pode usar para controlar:  
  
- Vidas de instâncias  
  
- Suporte a concorrência e sincronização  
  
- Comportamento de configuração  
  
- Comportamento de transação  
  
- Comportamento de serialização  
  
- Transformação de metadados  
  
- Vida útil da sessão  
  
- Filtragem de endereços e processamento de cabeçalho  
  
- Representação  
  
- Para usar esses atributos, marque a implementação do serviço ou da operação com o atributo apropriado a esse escopo e defina as propriedades. Por exemplo, o exemplo de código a <xref:System.ServiceModel.OperationBehaviorAttribute.Impersonation%2A?displayProperty=nameWithType> seguir mostra uma implementação de operação que usa a propriedade para exigir que os chamadores desta operação suportem a representação.  
  
 [!code-csharp[OperationBehaviorAttribute_Impersonation#1](../../../samples/snippets/csharp/VS_Snippets_CFX/operationbehaviorattribute_impersonation/cs/services.cs#1)]
 [!code-vb[OperationBehaviorAttribute_Impersonation#1](../../../samples/snippets/visualbasic/VS_Snippets_CFX/operationbehaviorattribute_impersonation/vb/services.vb#1)]  
  
 Muitas das propriedades requerem suporte adicional da vinculação. Por exemplo, uma operação que exija uma transação do cliente deve ser configurada para usar uma vinculação que suporte transações fluídas.  
  
### <a name="well-known-singleton-services"></a>Serviços bem conhecidos de Singleton  
 Você pode <xref:System.ServiceModel.ServiceBehaviorAttribute> usar <xref:System.ServiceModel.OperationBehaviorAttribute> e atributos para controlar <xref:System.ServiceModel.InstanceContext> certas vidas, tanto dos objetos de serviço que implementam as operações.  
  
 Por exemplo, <xref:System.ServiceModel.ServiceBehaviorAttribute.InstanceContextMode%2A?displayProperty=nameWithType> a propriedade controla a frequência com que o <xref:System.ServiceModel.InstanceContext> objeto é liberado e o <xref:System.ServiceModel.OperationBehaviorAttribute.ReleaseInstanceMode%2A?displayProperty=nameWithType> controle de propriedades <xref:System.ServiceModel.ServiceBehaviorAttribute.ReleaseServiceInstanceOnTransactionComplete%2A?displayProperty=nameWithType> quando o objeto de serviço é liberado.  
  
 No entanto, você também pode criar um objeto de serviço e criar o host de serviço usando esse objeto. Para isso, você também deve <xref:System.ServiceModel.ServiceBehaviorAttribute.InstanceContextMode%2A?displayProperty=nameWithType> definir <xref:System.ServiceModel.InstanceContextMode.Single> a propriedade para ou uma exceção é lançada quando o host de serviço é aberto.  
  
 Use <xref:System.ServiceModel.ServiceHost.%23ctor%28System.Object%2CSystem.Uri%5B%5D%29> o construtor para criar tal serviço. Ele fornece uma alternativa para <xref:System.ServiceModel.Dispatcher.IInstanceContextInitializer?displayProperty=nameWithType> implementar um personalizado quando você deseja fornecer uma instância específica de objeto para uso por um serviço singleton. Você pode usar essa sobrecarga quando seu tipo de implementação de serviço é difícil de construir (por exemplo, se ele não implementar um construtor público sem parâmetros).
  
 Observe que quando um objeto é fornecido a este construtor, alguns recursos relacionados ao Comportamento de Instancing da Windows Communication Foundation (WCF) funcionam de forma diferente. Por exemplo, <xref:System.ServiceModel.InstanceContext.ReleaseServiceInstance%2A?displayProperty=nameWithType> a chamada não tem efeito quando uma instância de objeto bem conhecida é fornecida. Da mesma forma, qualquer outro mecanismo de liberação de instâncias é ignorado. A <xref:System.ServiceModel.ServiceHost> classe sempre se comporta <xref:System.ServiceModel.OperationBehaviorAttribute.ReleaseInstanceMode%2A?displayProperty=nameWithType> como se <xref:System.ServiceModel.ReleaseInstanceMode.None?displayProperty=nameWithType> a propriedade estivesse definida para todas as operações.  
  
## <a name="other-service-endpoint-contract-and-operation-behaviors"></a>Outros Comportamentos de Serviço, Endpoint, Contrato e Operação  
 Comportamentos de serviço, <xref:System.ServiceModel.ServiceBehaviorAttribute> como o atributo, operam em todo um serviço. Por exemplo, se <xref:System.ServiceModel.ServiceBehaviorAttribute.ConcurrencyMode%2A?displayProperty=nameWithType> você <xref:System.ServiceModel.ConcurrencyMode.Multiple?displayProperty=nameWithType> definir a propriedade para você, você deve lidar com problemas de sincronização de segmento dentro de cada operação nesse serviço você mesmo. Os comportamentos de ponto final operam em um ponto final; muitos dos comportamentos de ponto final fornecidos pelo sistema são para a funcionalidade do cliente. Os comportamentos contratuais operam no nível do contrato, e os comportamentos de operação modificam a entrega da operação.  
  
 Muitos desses comportamentos são implementados em atributos, e você <xref:System.ServiceModel.ServiceBehaviorAttribute> <xref:System.ServiceModel.OperationBehaviorAttribute> faz uso deles como faz com os atributos — aplicando-os à classe de serviço apropriada ou à implementação da operação. Outros comportamentos, como <xref:System.ServiceModel.Description.ServiceMetadataBehavior> os <xref:System.ServiceModel.Description.ServiceDebugBehavior> objetos, são normalmente aplicados usando um arquivo de configuração de aplicativo, embora também possam ser usados de forma programática.  
  
 Por exemplo, a publicação de metadados <xref:System.ServiceModel.Description.ServiceMetadataBehavior> é configurada usando o objeto. O arquivo de configuração do aplicativo a seguir mostra o uso mais comum.  
  
 [!code-xml[ServiceMetadataBehavior#1](../../../samples/snippets/csharp/VS_Snippets_CFX/servicemetadatabehavior/cs/hostapplication.exe.config#1)]  
  
 As seções a seguir descrevem muitos dos comportamentos mais úteis fornecidos pelo sistema que você pode usar para modificar a entrega em tempo de execução do seu serviço ou cliente. Consulte o tópico de referência para determinar como usar cada um.  
  
### <a name="service-behaviors"></a>Comportamentos de serviço  
 Os seguintes comportamentos operam nos serviços.  
  
- <xref:System.ServiceModel.Activation.AspNetCompatibilityRequirementsAttribute>. Aplicado a um serviço WCF para indicar se esse serviço pode ser executado em ASP.NET modo de compatibilidade.  
  
- <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior>. Controla como o serviço autoriza as reivindicações dos clientes.  
  
- <xref:System.ServiceModel.Description.ServiceCredentials>. Configura uma credencial de serviço. Use esta classe para especificar a credencial para o serviço, como um certificado X.509.  
  
- <xref:System.ServiceModel.Description.ServiceDebugBehavior>. Habilita recursos de depuração e ajuda para um serviço WCF.  
  
- <xref:System.ServiceModel.Description.ServiceMetadataBehavior>. Controla a publicação de metadados de serviço e informações associadas.  
  
- <xref:System.ServiceModel.Description.ServiceSecurityAuditBehavior>. Especifica o comportamento de auditoria de eventos de segurança.  
  
- <xref:System.ServiceModel.Description.ServiceThrottlingBehavior>. Define as configurações de taxa de transferência de tempo de execução que permitem ajustar o desempenho do serviço.  
  
### <a name="endpoint-behaviors"></a>Comportamentos de ponto final  
 Os seguintes comportamentos operam em pontos finais. Muitos desses comportamentos são usados em aplicativos de clientes.  
  
- <xref:System.ServiceModel.CallbackBehaviorAttribute>. Configura uma implementação de serviço de retorno de chamada em um aplicativo cliente duplex.  
  
- <xref:System.ServiceModel.Description.CallbackDebugBehavior>. Habilita a depuração de serviço para um objeto de retorno de chamada WCF.  
  
- <xref:System.ServiceModel.Description.ClientCredentials>. Permite que o usuário configure credenciais de cliente e serviço, bem como as configurações de autenticação de credenciais de serviço para uso no cliente.  
  
- <xref:System.ServiceModel.Description.ClientViaBehavior>. Usado pelos clientes para especificar o Uri (Uniform Resource Identifier, identificador de recursos uniformes) para o qual o canal de transporte deve ser criado.  
  
- <xref:System.ServiceModel.Description.MustUnderstandBehavior>. Instrui o WCF `MustUnderstand` a desativar o processamento.  
  
- <xref:System.ServiceModel.Description.SynchronousReceiveBehavior>. Instrui o tempo de execução para usar um processo de recebimento síncrono para os canais.  
  
- <xref:System.ServiceModel.Description.TransactedBatchingBehavior>. Otimiza as operações de recebimento para transportes que suportam recebimentos transacionais.  
  
### <a name="contract-behaviors"></a>Comportamentos contratuais  
 <xref:System.ServiceModel.DeliveryRequirementsAttribute>. Especifica os requisitos de recurso que as associações devem fornecer para a implementação do serviço ou cliente.  
  
### <a name="operation-behaviors"></a>Comportamentos da Operação  
 Os seguintes comportamentos de operação especificam serialização e controles de transação para operações.  
  
- <xref:System.ServiceModel.Description.DataContractSerializerOperationBehavior>. Representa o comportamento de tempo de execução de <xref:System.Runtime.Serialization.DataContractSerializer?displayProperty=nameWithType>.  
  
- <xref:System.ServiceModel.Description.XmlSerializerOperationBehavior>. Controla o comportamento do `XmlSerializer` tempo de execução do e associa-o a uma operação.  
  
- <xref:System.ServiceModel.TransactionFlowAttribute>. Especifica o nível em que uma operação de serviço aceita um cabeçalho de transação.  
  
## <a name="see-also"></a>Confira também

- [Configurando serviços](configuring-services.md)
- [Como controlar instanciação de serviço](./feature-details/how-to-control-service-instancing.md)
