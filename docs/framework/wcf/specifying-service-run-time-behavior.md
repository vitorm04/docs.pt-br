---
title: Especificando comportamento de tempo de execução de serviço
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 5c5450ea-6af1-4b75-a267-613d0ac54707
ms.openlocfilehash: 61a81e342a16bd298cbebef2dc733b5ec631839c
ms.sourcegitcommit: 15109844229ade1c6449f48f3834db1b26907824
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/07/2018
ms.locfileid: "33807532"
---
# <a name="specifying-service-run-time-behavior"></a>Especificando comportamento de tempo de execução de serviço
Depois que você tiver criado um contrato de serviço ([Criando contratos de serviço](../../../docs/framework/wcf/designing-service-contracts.md)) e implementado o contrato de serviço ([implementando contratos de serviço](../../../docs/framework/wcf/implementing-service-contracts.md)) você pode configurar o comportamento da operação das tempo de execução do serviço. Este tópico discute o serviço fornecido pelo sistema e comportamentos de operação e descreve onde encontrar mais informações para criar novos comportamentos. Enquanto alguns comportamentos são aplicados como atributos, muitos são aplicados usando um arquivo de configuração do aplicativo ou programaticamente. Para obter mais informações sobre como configurar seu aplicativo de serviço, consulte [Configurando os serviços de](../../../docs/framework/wcf/configuring-services.md).  
  
## <a name="overview"></a>Visão geral  
 O contrato define as entradas, saídas, tipos de dados e recursos de um serviço desse tipo. Implementar um contrato de serviço cria uma classe que, quando configurado com uma associação em um endereço, preenche o contrato que ele implementa. Contratual, associação e informações de endereço são todos conhecidos pelo cliente; sem eles, o cliente não pode fazer uso do serviço.  
  
 No entanto, as especificações de operação, como problemas ou gerenciamento de instâncias de threading são opacas para clientes. Depois que você implementou o contrato de serviço, você pode configurar um grande número de características de operação usando *comportamentos*. Comportamentos são objetos que modificam o tempo de execução do Windows Communication Foundation (WCF), definindo uma propriedade de tempo de execução ou inserindo um tipo de personalização no tempo de execução. Para obter mais informações sobre como modificar o tempo de execução Criando comportamentos definidos pelo usuário, consulte [estendendo ServiceHost e a camada de modelo de serviço](../../../docs/framework/wcf/extending/extending-servicehost-and-the-service-model-layer.md).  
  
 O <xref:System.ServiceModel.ServiceBehaviorAttribute?displayProperty=nameWithType> e <xref:System.ServiceModel.OperationBehaviorAttribute?displayProperty=nameWithType> os atributos são os mais úteis comportamentos e expor solicitado o mais recursos de operação. Porque eles são atributos, você pode aplicá-los para a implementação de serviço ou operação. Outros comportamentos, como o <xref:System.ServiceModel.Description.ServiceMetadataBehavior?displayProperty=nameWithType> ou <xref:System.ServiceModel.Description.ServiceDebugBehavior?displayProperty=nameWithType>, normalmente são aplicadas usando um arquivo de configuração do aplicativo, embora você possa usá-los por meio de programação.  
  
 Este tópico fornece uma visão geral de <xref:System.ServiceModel.ServiceBehaviorAttribute> e <xref:System.ServiceModel.OperationBehaviorAttribute> atributos, descreve os vários escopos, em que os comportamentos podem operar e fornece uma breve descrição dos muitos dos comportamentos em vários escopos que podem ser fornecidos pelo sistema interesse para os desenvolvedores do WCF.  
  
## <a name="servicebehaviorattribute-and-operationbehaviorattribute"></a>ServiceBehaviorAttribute e OperationBehaviorAttribute  
 Os comportamentos mais importantes são o <xref:System.ServiceModel.ServiceBehaviorAttribute> e <xref:System.ServiceModel.OperationBehaviorAttribute> atributos, que você pode usar para controlar:  
  
-   Tempos de vida da instância  
  
-   Suporte a simultaneidade e sincronização  
  
-   Comportamento de configuração  
  
-   Comportamento de transação  
  
-   Comportamento de serialização  
  
-   Transformação de metadados  
  
-   Duração da sessão  
  
-   Filtragem de endereço e o processamento de cabeçalho  
  
-   Representação  
  
-   Para usar esses atributos, marque a implementação de serviço ou a operação com o atributo apropriado para esse escopo e definir as propriedades. Por exemplo, o exemplo de código a seguir mostra uma implementação de operação que usa o <xref:System.ServiceModel.OperationBehaviorAttribute.Impersonation%2A?displayProperty=nameWithType> propriedade para exigir que os chamadores dessa operação suporte à representação.  
  
 [!code-csharp[OperationBehaviorAttribute_Impersonation#1](../../../samples/snippets/csharp/VS_Snippets_CFX/operationbehaviorattribute_impersonation/cs/services.cs#1)]
 [!code-vb[OperationBehaviorAttribute_Impersonation#1](../../../samples/snippets/visualbasic/VS_Snippets_CFX/operationbehaviorattribute_impersonation/vb/services.vb#1)]  
  
 Muitas das propriedades requerem suporte adicional da associação. Por exemplo, uma operação que requer uma transação do cliente deve ser configurada para usar uma associação que dá suporte a transações de fluxo.  
  
### <a name="well-known-singleton-services"></a>Serviços de Singleton conhecido  
 Você pode usar o <xref:System.ServiceModel.ServiceBehaviorAttribute> e <xref:System.ServiceModel.OperationBehaviorAttribute> atributos para controlar determinados tempos de vida, ambos os <xref:System.ServiceModel.InstanceContext> e dos objetos de serviço que implementam as operações.  
  
 Por exemplo, o <xref:System.ServiceModel.ServiceBehaviorAttribute.InstanceContextMode%2A?displayProperty=nameWithType> propriedade controla com que frequência o <xref:System.ServiceModel.InstanceContext> é liberado e o <xref:System.ServiceModel.OperationBehaviorAttribute.ReleaseInstanceMode%2A?displayProperty=nameWithType> e <xref:System.ServiceModel.ServiceBehaviorAttribute.ReleaseServiceInstanceOnTransactionComplete%2A?displayProperty=nameWithType> propriedades que controlam quando o objeto de serviço é liberado.  
  
 No entanto, também pode criar um objeto de serviço por conta própria e crie o host de serviço usando o objeto. Para fazer isso, você também deve definir o <xref:System.ServiceModel.ServiceBehaviorAttribute.InstanceContextMode%2A?displayProperty=nameWithType> propriedade <xref:System.ServiceModel.InstanceContextMode.Single> ou uma exceção é lançada quando o host de serviço é aberto.  
  
 Use o <xref:System.ServiceModel.ServiceHost.%23ctor%28System.Object%2CSystem.Uri%5B%5D%29?displayProperty=nameWithType> construtor para criar um serviço. Ele fornece uma alternativa à implementação de uma <xref:System.ServiceModel.Dispatcher.IInstanceContextInitializer?displayProperty=nameWithType> quando você deseja fornecer uma instância de objeto específico para uso por um serviço de singleton. Você pode usar essa sobrecarga ao seu tipo de implementação de serviço é difícil construir (por exemplo, se ele não implementa um construtor público padrão que não tem parâmetros).  
  
 Observe que quando um objeto é fornecido para esse construtor, alguns recursos relacionados para o Windows Communication Foundation (WCF) comportamento de instâncias funcionam de forma diferente. Por exemplo, chamar <xref:System.ServiceModel.InstanceContext.ReleaseServiceInstance%2A?displayProperty=nameWithType> não tem nenhum efeito quando uma instância de objeto conhecido é fornecida. Da mesma forma, qualquer outro mecanismo de versão da instância é ignorado. O <xref:System.ServiceModel.ServiceHost> classe sempre se comporta como se o <xref:System.ServiceModel.OperationBehaviorAttribute.ReleaseInstanceMode%2A?displayProperty=nameWithType> está definida como <xref:System.ServiceModel.ReleaseInstanceMode.None?displayProperty=nameWithType> para todas as operações.  
  
## <a name="other-service-endpoint-contract-and-operation-behaviors"></a>Outro serviço, ponto de extremidade, contrato e comportamentos de operação  
 Comportamentos de serviço, como o <xref:System.ServiceModel.ServiceBehaviorAttribute> atributo, operar em todo o serviço. Por exemplo, se você definir o <xref:System.ServiceModel.ServiceBehaviorAttribute.ConcurrencyMode%2A?displayProperty=nameWithType> propriedade <xref:System.ServiceModel.ConcurrencyMode.Multiple?displayProperty=nameWithType> você deve tratar problemas de sincronização de thread dentro de cada operação nesse serviço. Comportamentos de ponto de extremidade operam em um ponto de extremidade; muitos dos comportamentos de ponto de extremidade fornecido pelo sistema são para a funcionalidade de cliente. Comportamentos de contrato operam no nível do contrato e comportamentos de operação modificar a entrega de operação.  
  
 Muitos desses comportamentos são implementados em atributos e fazer utilizá-las como faz o <xref:System.ServiceModel.ServiceBehaviorAttribute> e <xref:System.ServiceModel.OperationBehaviorAttribute> atributos — por aplicá-las para a implementação de classe ou operação de serviço apropriado. Outros comportamentos, como o <xref:System.ServiceModel.Description.ServiceMetadataBehavior> ou <xref:System.ServiceModel.Description.ServiceDebugBehavior> objetos, são normalmente aplicadas usando um arquivo de configuração do aplicativo, embora também possa ser usados por meio de programação.  
  
 Por exemplo, a publicação de metadados é configurada usando o <xref:System.ServiceModel.Description.ServiceMetadataBehavior> objeto. O seguinte arquivo de configuração do aplicativo mostra o uso mais comum.  
  
 [!code-csharp[ServiceMetadataBehavior#1](../../../samples/snippets/csharp/VS_Snippets_CFX/servicemetadatabehavior/cs/hostapplication.cs#1)]  
  
 As seções a seguir descrevem a muitos dos comportamentos fornecido pelo sistema mais úteis que você pode usar para modificar a entrega de tempo de execução do serviço ou cliente. Consulte o tópico de referência para determinar como usar cada uma delas.  
  
### <a name="service-behaviors"></a>Comportamentos de serviço  
 Os seguintes comportamentos operam nos serviços.  
  
-   <xref:System.ServiceModel.Activation.AspNetCompatibilityRequirementsAttribute>. Aplicado a um serviço WCF para indicar se esse serviço pode ser executado [!INCLUDE[vstecasp](../../../includes/vstecasp-md.md)] modo de compatibilidade.  
  
-   <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior>. Controla como o serviço autoriza declarações de cliente.  
  
-   <xref:System.ServiceModel.Description.ServiceCredentials>. Configura uma credencial de serviço. Use esta classe para especificar a credencial para o serviço, como um certificado x. 509.  
  
-   <xref:System.ServiceModel.Description.ServiceDebugBehavior>. Habilita a depuração e os recursos de informações para um serviço WCF da Ajuda.  
  
-   <xref:System.ServiceModel.Description.ServiceMetadataBehavior>. Controla a publicação de metadados de serviço e informações associadas.  
  
-   <xref:System.ServiceModel.Description.ServiceSecurityAuditBehavior>. Especifica o comportamento de auditoria de eventos de segurança.  
  
-   <xref:System.ServiceModel.Description.ServiceThrottlingBehavior>. Define as configurações de taxa de transferência de tempo de execução que permitem ajustar o desempenho do serviço.  
  
### <a name="endpoint-behaviors"></a>Comportamentos de ponto de extremidade  
 Os seguintes comportamentos operam nos pontos de extremidade. Muitos desses comportamentos são usados em aplicativos cliente.  
  
-   <xref:System.ServiceModel.CallbackBehaviorAttribute>. Configura uma implementação de serviço de retorno de chamada em um aplicativo cliente duplex.  
  
-   <xref:System.ServiceModel.Description.CallbackDebugBehavior>. Habilita a depuração de serviço para um objeto de retorno de chamada do WCF.  
  
-   <xref:System.ServiceModel.Description.ClientCredentials>. Permite ao usuário configurar as credenciais de cliente e de serviço, bem como configurações de autenticação de credenciais para uso no cliente de serviço.  
  
-   <xref:System.ServiceModel.Description.ClientViaBehavior>. Usado por clientes para especificar o identificador de URI (Uniform Resource) para o qual o canal de transporte deve ser criado.  
  
-   <xref:System.ServiceModel.Description.MustUnderstandBehavior>. Instrui o WCF para desabilitar o `MustUnderstand` de processamento.  
  
-   <xref:System.ServiceModel.Description.SynchronousReceiveBehavior>. Instrui o tempo de execução para usar um síncrono receber o processo de canais.  
  
-   <xref:System.ServiceModel.Description.TransactedBatchingBehavior>. Otimiza as operações de recebimento para os transportes que recebe suporte transacional.  
  
### <a name="contract-behaviors"></a>Comportamentos de contrato  
 <xref:System.ServiceModel.DeliveryRequirementsAttribute>. Especifica os requisitos de recurso que as associações devem fornecer para a implementação do serviço ou cliente.  
  
### <a name="operation-behaviors"></a>Comportamentos de operação  
 Os seguintes comportamentos de operação especificar controles de serialização e a transação para operações.  
  
-   <xref:System.ServiceModel.Description.DataContractSerializerOperationBehavior>. Representa o comportamento de tempo de execução de <xref:System.Runtime.Serialization.DataContractSerializer?displayProperty=nameWithType>.  
  
-   <xref:System.ServiceModel.Description.XmlSerializerOperationBehavior>. Controla o comportamento de tempo de execução de `XmlSerializer` e o associa a uma operação.  
  
-   <xref:System.ServiceModel.TransactionFlowAttribute>. Especifica o nível no qual uma operação de serviço aceita um cabeçalho de transação.  
  
## <a name="see-also"></a>Consulte também  
 [Configurando serviços](../../../docs/framework/wcf/configuring-services.md)  
 [Como controlar instanciação de serviço](../../../docs/framework/wcf/feature-details/how-to-control-service-instancing.md)
