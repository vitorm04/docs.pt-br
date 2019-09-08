---
title: Configurando e estendendo o tempo de execução com comportamentos
ms.date: 03/30/2017
helpviewer_keywords:
- attaching extensions using behaviors [WCF]
ms.assetid: 149b99b6-6eb6-4f45-be22-c967279677d9
ms.openlocfilehash: 3a1e369fe52a2a529fb3511d9a65067b4a56ec1e
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70797258"
---
# <a name="configuring-and-extending-the-runtime-with-behaviors"></a>Configurando e estendendo o tempo de execução com comportamentos
Os comportamentos permitem modificar o comportamento padrão e adicionar extensões personalizadas que inspecionam e validam a configuração do serviço ou modificam o comportamento do tempo de execução em aplicativos de cliente e serviço Windows Communication Foundation (WCF). Este tópico descreve as interfaces de comportamento, como implementá-las e como adicioná-las à descrição do serviço (em um aplicativo de serviço) ou ponto de extremidade (em um aplicativo cliente) programaticamente ou em um arquivo de configuração. Para obter mais informações sobre como usar comportamentos fornecidos pelo sistema, consulte [especificando o comportamento de tempo de execução do serviço](../specifying-service-run-time-behavior.md) e [especificando o comportamento do tempo de execução do cliente](../specifying-client-run-time-behavior.md).  
  
## <a name="behaviors"></a>Comportamentos  
 Os tipos de comportamento são adicionados ao serviço ou objetos de descrição do ponto de extremidade de serviço (no serviço ou cliente, respectivamente) antes que esses objetos sejam usados pelo Windows Communication Foundation (WCF) para criar um tempo de execução que executa um serviço WCF ou um cliente WCF. Quando esses comportamentos são chamados durante o processo de construção de tempo de execução, eles são capazes de acessar propriedades e métodos de tempo de execução que modificam o tempo de execução construído pelo contrato, associações e endereços.  
  
### <a name="behavior-methods"></a>Métodos de comportamento  
 Todos os comportamentos têm `AddBindingParameters` um método `ApplyDispatchBehavior` , um método, `Validate` um método e um `ApplyClientBehavior` método com uma exceção: Como <xref:System.ServiceModel.Description.IServiceBehavior> o não pode ser executado em um cliente, ele `ApplyClientBehavior`não implementa.  
  
- Use o `AddBindingParameters` método para modificar ou adicionar objetos personalizados a uma coleção que as associações personalizadas podem acessar para seu uso quando o tempo de execução é construído. Por exemplo, como são especificados os requisitos de proteção que afetam a maneira como o canal é criado, mas não são conhecidos pelo desenvolvedor do canal.  
  
- Use o `Validate` método para examinar a árvore de descrição e o objeto de tempo de execução correspondente para garantir que ele esteja em conformidade com algum conjunto de critérios.  
  
- Use os `ApplyDispatchBehavior` métodos `ApplyClientBehavior` e para examinar a árvore de descrição e modificar o tempo de execução de um escopo específico no serviço ou no cliente. Você também pode inserir objetos de extensão também.  
  
    > [!NOTE]
    > Embora uma árvore de descrição seja fornecida nesses métodos, ela é apenas para exame. Se uma árvore de descrição for modificada, o comportamento será indefinido.  
  
 As propriedades que você pode modificar e as interfaces de personalização que podem ser implementadas são acessadas por meio das classes de tempo de execução do serviço e do cliente. Os tipos de serviço são <xref:System.ServiceModel.Dispatcher.DispatchRuntime> as <xref:System.ServiceModel.Dispatcher.DispatchOperation> classes e. Os tipos de cliente são <xref:System.ServiceModel.Dispatcher.ClientRuntime> as <xref:System.ServiceModel.Dispatcher.ClientOperation> classes e. As <xref:System.ServiceModel.Dispatcher.ClientRuntime> classes <xref:System.ServiceModel.Dispatcher.DispatchRuntime> e são os pontos de entrada de extensibilidade para acessar propriedades de tempo de execução de todo o cliente e de serviço e coleções de extensão, respectivamente. Da mesma forma <xref:System.ServiceModel.Dispatcher.ClientOperation> , <xref:System.ServiceModel.Dispatcher.DispatchOperation> as classes e expõem as propriedades de operação do cliente e tempo de execução de operação de serviço e coleções de extensão, respectivamente. No entanto, você pode acessar o objeto de tempo de execução com escopo maior do objeto de tempo de execução de operação e vice-versa, se necessário.  
  
> [!NOTE]
> Para obter uma discussão sobre propriedades de tempo de execução e tipos de extensão que você pode usar para modificar o comportamento de execução de um cliente, consulte [estendendo clientes](extending-clients.md). Para obter uma discussão sobre as propriedades de tempo de execução e os tipos de extensão que você pode usar para modificar o comportamento de execução de um Dispatcher de serviço, consulte [estendendo expatchers](extending-dispatchers.md).  
  
 A maioria dos usuários do WCF não interage com o tempo de execução diretamente; em vez disso, eles usam construções de modelo de programação de núcleo como pontos de extremidade, contratos, associações, endereços e atributos de comportamento em classes ou comportamentos em arquivos de configuração. Essas construções compõem a *árvore de descrição*, que é a especificação completa para construir um tempo de execução para dar suporte a um serviço ou cliente descrito pela árvore de descrição.  
  
 Há quatro tipos de comportamentos no WCF:  
  
- Os comportamentos de<xref:System.ServiceModel.Description.IServiceBehavior> serviço (tipos) permitem a personalização de todo o tempo <xref:System.ServiceModel.ServiceHostBase>de execução do serviço, incluindo.  
  
- Os comportamentos de<xref:System.ServiceModel.Description.IEndpointBehavior> ponto de extremidade (tipos) permitem a personalização de pontos de extremidades <xref:System.ServiceModel.Dispatcher.EndpointDispatcher> de serviço e seus objetos associados.  
  
- Os comportamentos de<xref:System.ServiceModel.Description.IContractBehavior> contrato (tipos) permitem a personalização das <xref:System.ServiceModel.Dispatcher.ClientRuntime> classes <xref:System.ServiceModel.Dispatcher.DispatchRuntime> e dos aplicativos de cliente e serviço, respectivamente.  
  
- Comportamentos<xref:System.ServiceModel.Description.IOperationBehavior> deoperação<xref:System.ServiceModel.Dispatcher.DispatchOperation> (tipos) habilitam a personalização das classes enovamente,noclienteenoserviço.<xref:System.ServiceModel.Dispatcher.ClientOperation>  
  
 Você pode adicionar esses comportamentos aos vários objetos de descrição implementando atributos personalizados, usando arquivos de configuração de aplicativo ou diretamente adicionando-os à coleção de comportamentos no objeto de descrição apropriado. O deve, no entanto, ser adicionado a uma descrição de serviço ou objeto de descrição de <xref:System.ServiceModel.ICommunicationObject.Open%2A?displayProperty=nameWithType> ponto de <xref:System.ServiceModel.ServiceHost> extremidade de <xref:System.ServiceModel.ChannelFactory%601>serviço antes de chamar o ou um.  
  
### <a name="behavior-scopes"></a>Escopos de comportamento  
 Há quatro tipos de comportamento, cada um dos quais corresponde a um determinado escopo de acesso de tempo de execução.  
  
#### <a name="service-behaviors"></a>Comportamentos de serviço  
 Os comportamentos de serviço, <xref:System.ServiceModel.Description.IServiceBehavior>que implementam, são o mecanismo principal pelo qual você modifica o tempo de execução do serviço inteiro. Há três mecanismos para adicionar comportamentos de serviço a um serviço.  
  
1. Usando um atributo na classe de serviço.  Quando um <xref:System.ServiceModel.ServiceHost> é construído, a <xref:System.ServiceModel.ServiceHost> implementação usa a reflexão para descobrir o conjunto de atributos no tipo do serviço. Se qualquer um desses atributos for implementações <xref:System.ServiceModel.Description.IServiceBehavior>do, eles serão adicionados à coleção de comportamentos <xref:System.ServiceModel.Description.ServiceDescription>no. Isso permite que esses comportamentos participem da construção do tempo de execução do serviço.  
  
2. Adicionando programaticamente o comportamento à coleção de <xref:System.ServiceModel.Description.ServiceDescription>comportamentos no. Isso pode ser feito com as seguintes linhas de código:  
  
    ```csharp
    ServiceHost host = new ServiceHost(/* Parameters */);  
    host.Description.Behaviors.Add(/* Service Behavior */);  
    ```  
  
3. Implementação de um <xref:System.ServiceModel.Configuration.BehaviorExtensionElement> personalizado que estende a configuração. Isso permite o uso do comportamento do serviço dos arquivos de configuração do aplicativo.  
  
 Exemplos de comportamentos de serviço no WCF incluem <xref:System.ServiceModel.ServiceBehaviorAttribute> o atributo, <xref:System.ServiceModel.Description.ServiceThrottlingBehavior>o e o <xref:System.ServiceModel.Description.ServiceMetadataBehavior> comportamento.  
  
#### <a name="contract-behaviors"></a>Comportamentos de contrato  
 Os comportamentos de contrato, que <xref:System.ServiceModel.Description.IContractBehavior> implementam a interface, são usados para estender o tempo de execução do cliente e do serviço em um contrato.  
  
 Há dois mecanismos para adicionar comportamentos de contrato a um contrato.  O primeiro mecanismo é criar um atributo personalizado a ser usado na interface do contrato. Quando uma interface de contrato é passada para um <xref:System.ServiceModel.ServiceHost> ou um <xref:System.ServiceModel.ChannelFactory%601>, o WCF examina os atributos na interface. Se qualquer atributo for implementações <xref:System.ServiceModel.Description.IContractBehavior>do, eles serão adicionados à coleção de comportamentos <xref:System.ServiceModel.Description.ContractDescription?displayProperty=nameWithType> no criado para essa interface.  
  
 Você também pode implementar o <xref:System.ServiceModel.Description.IContractBehaviorAttribute?displayProperty=nameWithType> no atributo de comportamento de contrato personalizado. Nesse caso, o comportamento é o seguinte quando aplicado a:  
  
 • Uma interface de contrato. Nesse caso, o comportamento é aplicado a todos os contratos desse tipo em qualquer ponto de extremidade e o WCF ignora o valor da <xref:System.ServiceModel.Description.IContractBehaviorAttribute.TargetContract%2A?displayProperty=nameWithType> propriedade.  
  
 • Uma classe de serviço. Nesse caso, o comportamento é aplicado somente a pontos de extremidade do contrato que é o valor da <xref:System.ServiceModel.Description.IContractBehaviorAttribute.TargetContract%2A> propriedade.  
  
 • Uma classe de retorno de chamada. Nesse caso, o comportamento é aplicado ao ponto de extremidade do cliente duplex e o WCF ignora o valor da <xref:System.ServiceModel.Description.IContractBehaviorAttribute.TargetContract%2A> propriedade.  
  
 O segundo mecanismo é adicionar o comportamento à coleção de comportamentos em um <xref:System.ServiceModel.Description.ContractDescription>.  
  
 Exemplos de comportamentos de contrato no WCF incluem <xref:System.ServiceModel.DeliveryRequirementsAttribute?displayProperty=nameWithType> o atributo. Para obter mais informações e um exemplo, consulte o tópico de referência.  
  
#### <a name="endpoint-behaviors"></a>Comportamentos de ponto de extremidade  
 Os comportamentos de ponto de <xref:System.ServiceModel.Description.IEndpointBehavior>extremidade, que implementam, são o mecanismo principal pelo qual você modifica o serviço inteiro ou o tempo de execução do cliente para um ponto de extremidade específico.  
  
 Há dois mecanismos para adicionar comportamentos de ponto de extremidade a um serviço.  
  
1. Adicione o comportamento à <xref:System.ServiceModel.Description.ServiceEndpoint.Behaviors%2A> propriedade.  
  
2. Implemente um <xref:System.ServiceModel.Configuration.BehaviorExtensionElement> personalizado que estenda a configuração.  
  
 Para obter mais informações e um exemplo, consulte o tópico de referência.  
  
#### <a name="operation-behaviors"></a>Comportamentos de operação  
 Os comportamentos de operação, que <xref:System.ServiceModel.Description.IOperationBehavior> implementam a interface, são usados para estender o tempo de execução do cliente e do serviço para cada operação.  
  
 Há dois mecanismos para adicionar comportamentos de operação a uma operação. O primeiro mecanismo é criar um atributo personalizado a ser usado no método que modela a operação. Quando uma <xref:System.ServiceModel.ServiceHost> operação é adicionada a <xref:System.ServiceModel.ChannelFactory>ou a, o WCF adiciona quaisquer <xref:System.ServiceModel.Description.IOperationBehavior> atributos à coleção de comportamentos no <xref:System.ServiceModel.Description.OperationDescription> criado para essa operação.  
  
 O segundo mecanismo é adicionar diretamente o comportamento à coleção de comportamentos em um construído <xref:System.ServiceModel.Description.OperationDescription>.  
  
 Exemplos de comportamentos de operação no WCF incluem <xref:System.ServiceModel.OperationBehaviorAttribute> o e <xref:System.ServiceModel.TransactionFlowAttribute>o.  
  
 Para obter mais informações e um exemplo, consulte o tópico de referência.  
  
### <a name="using-configuration-to-create-behaviors"></a>Usando a configuração para criar comportamentos  
 Os comportamentos de serviço e ponto de extremidade e contrato podem ser projetados para serem especificados no código ou usando atributos; somente comportamentos de serviço e ponto de extremidade podem ser configurados usando arquivos de configuração de aplicativo ou da Web. Expor comportamentos usando atributos permite que os desenvolvedores especifiquem um comportamento em tempo de compilação que não pode ser adicionado, removido ou modificado em tempo de execução. Isso é geralmente adequado para comportamentos que são sempre necessários para a operação correta de um serviço (por exemplo, os parâmetros relacionados à transação para o <xref:System.ServiceModel.ServiceBehaviorAttribute?displayProperty=nameWithType> atributo). Expor comportamentos usando a configuração permite que os desenvolvedores deixem a especificação e a configuração desses comportamentos para aqueles que implantam o serviço. Isso é adequado para comportamentos que são componentes opcionais ou outra configuração específica da implantação, como se os metadados são expostos para o serviço ou a configuração de autorização específica para um serviço.  
  
> [!NOTE]
> Você também pode usar comportamentos que dão suporte à configuração para impor políticas de aplicativo da empresa inserindo-as no arquivo de configuração Machine. config e bloqueando esses itens. Para obter uma descrição e um exemplo, [consulte Como: Bloquear pontos de extremidade na empresa](how-to-lock-down-endpoints-in-the-enterprise.md).  
  
 Para expor um comportamento usando a configuração, um desenvolvedor deve criar uma classe derivada <xref:System.ServiceModel.Configuration.BehaviorExtensionElement> de e, em seguida, registrar essa extensão com a configuração.  
  
 O exemplo de código a seguir mostra <xref:System.ServiceModel.Description.IEndpointBehavior> como <xref:System.ServiceModel.Configuration.BehaviorExtensionElement>um implementa:  
  
```csharp
// BehaviorExtensionElement members  
public override Type BehaviorType  
{  
  get { return typeof(EndpointBehaviorMessageInspector); }  
}  
  
protected override object CreateBehavior()  
{  
  return new EndpointBehaviorMessageInspector();  
}  
```  
  
 Para que o sistema de configuração carregue um personalizado <xref:System.ServiceModel.Configuration.BehaviorExtensionElement>, ele deve ser registrado como uma extensão. O exemplo de código a seguir mostra o arquivo de configuração para o comportamento do ponto de extremidade anterior:  
  
```xml  
<configuration>  
  <system.serviceModel>  
    <services>  
      <service   
        name="Microsoft.WCF.Documentation.SampleService"  
        behaviorConfiguration="metadataSupport"  
      >  
        <host>  
          <baseAddresses>  
            <add baseAddress="http://localhost:8080/ServiceMetadata" />  
          </baseAddresses>  
        </host>  
        <endpoint  
          address="/SampleService"  
          binding="wsHttpBinding"  
          behaviorConfiguration="withMessageInspector"   
          contract="Microsoft.WCF.Documentation.ISampleService"  
        />  
        <endpoint  
           address="mex"  
           binding="mexHttpBinding"  
           contract="IMetadataExchange"  
        />  
      </service>  
    </services>  
    <behaviors>  
      <serviceBehaviors>  
      <behavior name="metadataSupport">  
        <serviceMetadata httpGetEnabled="true" httpGetUrl=""/>  
      </behavior>  
      </serviceBehaviors>  
      <endpointBehaviors>  
        <behavior name="withMessageInspector">  
          <endpointMessageInspector />  
        </behavior>  
      </endpointBehaviors>  
    </behaviors>  
    <extensions>  
      <behaviorExtensions>  
        <add   
          name="endpointMessageInspector"  
          type="Microsoft.WCF.Documentation.EndpointBehaviorMessageInspector, HostApplication, Version=0.0.0.0, Culture=neutral, PublicKeyToken=null"  
        />  
      </behaviorExtensions>  
    </extensions>  
  </system.serviceModel>  
</configuration>  
```  
  
 Em `Microsoft.WCF.Documentation.EndpointBehaviorMessageInspector` que é o tipo de extensão `HostApplication` de comportamento e é o nome do assembly no qual essa classe foi compilada.  
  
### <a name="evaluation-order"></a>Ordem de avaliação  
 O <xref:System.ServiceModel.ChannelFactory%601?displayProperty=nameWithType> e o <xref:System.ServiceModel.ServiceHost?displayProperty=nameWithType> são responsáveis por criar o tempo de execução do modelo de programação e descrição. Os comportamentos, conforme descrito anteriormente, contribuem para esse processo de compilação no serviço, no ponto de extremidade, no contrato e na operação.  
  
 O <xref:System.ServiceModel.ServiceHost> aplica comportamentos na seguinte ordem:  
  
1. Serviço  
  
2. Contrato  
  
3. Ponto de extremidade  
  
4. Operação  
  
 Em qualquer coleção de comportamentos, nenhum pedido é garantido.  
  
 O <xref:System.ServiceModel.ChannelFactory%601> aplica comportamentos na seguinte ordem:  
  
1. Contrato  
  
2. Ponto de extremidade  
  
3. Operação  
  
 Em qualquer coleção de comportamentos, novamente, nenhum pedido é garantido.  
  
### <a name="adding-behaviors-programmatically"></a>Adicionando comportamentos programaticamente  
 As propriedades do <xref:System.ServiceModel.Description.ServiceDescription?displayProperty=nameWithType> no aplicativo de serviço não devem ser modificadas subsequentemente <xref:System.ServiceModel.Channels.CommunicationObject.OnOpening%2A?displayProperty=nameWithType> para o <xref:System.ServiceModel.ServiceHostBase?displayProperty=nameWithType>método em. Alguns membros, como a <xref:System.ServiceModel.ServiceHostBase.Credentials%2A?displayProperty=nameWithType> Propriedade e os `AddServiceEndpoint` métodos em <xref:System.ServiceModel.ServiceHostBase> e <xref:System.ServiceModel.ServiceHost?displayProperty=nameWithType>, geram uma exceção, se modificado após esse ponto. Outros permitem que você os modifique, mas o resultado é indefinido.  
  
 Da mesma forma, no cliente <xref:System.ServiceModel.Description.ServiceEndpoint?displayProperty=nameWithType> , os valores não devem ser modificados após <xref:System.ServiceModel.Channels.CommunicationObject.OnOpening%2A> a chamada <xref:System.ServiceModel.ChannelFactory?displayProperty=nameWithType>para no. A <xref:System.ServiceModel.ChannelFactory.Credentials%2A?displayProperty=nameWithType> propriedade gera uma exceção se modificada após esse ponto, mas os outros valores de descrição do cliente podem ser modificados sem erros. O resultado, no entanto, é indefinido.  
  
 Seja para o serviço ou cliente, é recomendável que você modifique a descrição antes de chamar <xref:System.ServiceModel.Channels.CommunicationObject.Open%2A?displayProperty=nameWithType>.  
  
### <a name="inheritance-rules-for-behavior-attributes"></a>Regras de herança para atributos de comportamento  
 Todos os quatro tipos de comportamentos podem ser populados usando atributos – comportamentos de serviço e comportamentos de contrato. Como os atributos são definidos em objetos e membros gerenciados, e os membros e objetos gerenciados dão suporte à herança, é necessário definir como os atributos de comportamento funcionam no contexto de herança.  
  
 Em um alto nível, a regra é que para um escopo específico (por exemplo, serviço, contrato ou operação), todos os atributos de comportamento na hierarquia de herança desse escopo são aplicados. Se houver dois atributos de comportamento do mesmo tipo, somente o tipo mais derivado será usado.  
  
#### <a name="service-behaviors"></a>Comportamentos de serviço  
 Para uma determinada classe de serviço, todos os atributos de comportamento de serviço nessa classe e nos pais dessa classe são aplicados. Se o mesmo tipo de atributo for aplicado em vários locais na hierarquia de herança, o tipo mais derivado será usado.  
  
```csharp  
[ServiceBehavior(ConcurrencyMode = ConcurrencyMode.Multiple)]  
[AspNetCompatibilityRequirementsAttribute(  
    AspNetCompatibilityRequirementsMode = AspNetCompatibilityRequirementsMode.Allowed)]  
public class A { /* … */ }  
  
[ServiceBehavior(InstanceContextMode = InstanceContextMode.Single)]  
public class B : A { /* … */}  
```  
  
 Por exemplo, no caso anterior, o serviço B acaba com um <xref:System.ServiceModel.InstanceContextMode> de <xref:System.ServiceModel.InstanceContextMode.Single>, um <xref:System.ServiceModel.Activation.AspNetCompatibilityRequirementsMode> modo de <xref:System.ServiceModel.Activation.AspNetCompatibilityRequirementsMode.Allowed>e um <xref:System.ServiceModel.ConcurrencyMode> de <xref:System.ServiceModel.ConcurrencyMode.Single>. O <xref:System.ServiceModel.ConcurrencyMode> é <xref:System.ServiceModel.ConcurrencyMode.Single>, porque<xref:System.ServiceModel.ServiceBehaviorAttribute> o atributo no serviço B está em "mais derivado" do que no serviço A.  
  
#### <a name="contract-behaviors"></a>Comportamentos de contrato  
 Para um determinado contrato, todos os atributos de comportamento de contrato nessa interface e nos pais dessa interface são aplicados. Se o mesmo tipo de atributo for aplicado em vários locais na hierarquia de herança, o tipo mais derivado será usado.  
  
#### <a name="operation-behaviors"></a>Comportamentos de operação  
 Se uma determinada operação não substituir uma operação abstrata ou virtual existente, nenhuma regra de herança será aplicada.  
  
 Se uma operação substituir uma operação existente, todos os atributos de comportamento da operação nessa operação e nos pais dessa operação serão aplicados.  Se o mesmo tipo de atributo for aplicado em vários locais na hierarquia de herança, o tipo mais derivado será usado.
