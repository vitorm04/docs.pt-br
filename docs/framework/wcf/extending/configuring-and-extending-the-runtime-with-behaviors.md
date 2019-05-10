---
title: Configurando e estendendo o tempo de execução com comportamentos
ms.date: 03/30/2017
helpviewer_keywords:
- attaching extensions using behaviors [WCF]
ms.assetid: 149b99b6-6eb6-4f45-be22-c967279677d9
ms.openlocfilehash: 297a951e4678e05da73193133bd6050360b041ff
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64587344"
---
# <a name="configuring-and-extending-the-runtime-with-behaviors"></a>Configurando e estendendo o tempo de execução com comportamentos
Comportamentos que você possa modificar o comportamento padrão e adicionar extensões personalizadas que inspecionem e validar a configuração de serviço ou modificam o comportamento de tempo de execução em aplicativos de cliente e o serviço do Windows Communication Foundation (WCF). Este tópico descreve as interfaces de comportamento, como implementá-los e como adicioná-los para a descrição do serviço (em um aplicativo de serviço) ou o ponto de extremidade (em um aplicativo de cliente) por meio de programação ou em um arquivo de configuração. Para obter mais informações sobre como usar os comportamentos fornecidos pelo sistema, consulte [especificando comportamento de tempo de execução do serviço](../../../../docs/framework/wcf/specifying-service-run-time-behavior.md) e [especificando comportamento de tempo de execução do cliente](../../../../docs/framework/wcf/specifying-client-run-time-behavior.md).  
  
## <a name="behaviors"></a>Comportamentos  
 Tipos de comportamento são adicionados ao serviço ou objetos de descrição do ponto de extremidade de serviço (no serviço ou cliente, respectivamente) antes que esses objetos são usados pelo Windows Communication Foundation (WCF) para criar um tempo de execução que executa um serviço WCF ou um cliente do WCF. Quando esses comportamentos são chamados durante o processo de construção de tempo de execução, em seguida, eles são capazes de acessar propriedades de tempo de execução e os métodos que modificam o tempo de execução construído o contrato, associações e endereços.  
  
### <a name="behavior-methods"></a>Métodos de comportamento  
 Todos os comportamentos têm uma `AddBindingParameters` método, uma `ApplyDispatchBehavior` método, um `Validate` método e um `ApplyClientBehavior` método com uma exceção: Porque <xref:System.ServiceModel.Description.IServiceBehavior> não é possível executar em um cliente, ele não implementa `ApplyClientBehavior`.  
  
- Use o `AddBindingParameters` método para modificar ou adicionar objetos personalizados a uma coleção de ligações personalizadas podem acessar para uso quando o tempo de execução é construído. Por exemplo, isso como os requisitos de proteção são especificados, que afetam a maneira que o canal é criado, mas não são conhecidos pelo desenvolvedor do canal.  
  
- Use o `Validate` método para examinar a árvore de descrição e o objeto correspondente do tempo de execução para verificar se ele está em conformidade com um conjunto de critérios.  
  
- Use o `ApplyDispatchBehavior` e `ApplyClientBehavior` métodos para examinar a descrição de árvore e modificar o tempo de execução para um escopo específico no serviço ou no cliente. Você também pode inserir objetos de extensão também.  
  
    > [!NOTE]
    >  Embora uma árvore de descrição é fornecida nesses métodos, é apenas para exame. Se uma árvore de descrição for modificada, o comportamento será indefinido.  
  
 As propriedades que você pode modificar e você pode implementar as interfaces de personalização são acessadas por meio das classes de tempo de execução do serviço e cliente. Os tipos de serviço são as <xref:System.ServiceModel.Dispatcher.DispatchRuntime> e <xref:System.ServiceModel.Dispatcher.DispatchOperation> classes. Os tipos de cliente são as <xref:System.ServiceModel.Dispatcher.ClientRuntime> e <xref:System.ServiceModel.Dispatcher.ClientOperation> classes. O <xref:System.ServiceModel.Dispatcher.ClientRuntime> e <xref:System.ServiceModel.Dispatcher.DispatchRuntime> classes são os pontos de entrada de extensibilidade para acessar propriedades de tempo de execução do cliente e de serviço e coleções de extensão, respectivamente. Da mesma forma, o <xref:System.ServiceModel.Dispatcher.ClientOperation> e <xref:System.ServiceModel.Dispatcher.DispatchOperation> classes exponham a operação de cliente e propriedades de tempo de execução da operação de serviço e coleções de extensão, respectivamente. Você pode, no entanto, o acesso, o runtime com escopo mais amplo de objeto a objeto e vice-versa de tempo de execução do operação se precisa ser.  
  
> [!NOTE]
>  Para uma discussão sobre as propriedades de tempo de execução e tipos de extensão que você pode usar para modificar o comportamento de execução de um cliente, consulte [estendendo clientes](../../../../docs/framework/wcf/extending/extending-clients.md). Para uma discussão sobre as propriedades de tempo de execução e os tipos de extensão que você pode usar para modificar o comportamento de execução de um dispatcher de serviço, consulte [estendendo Dispatchers](../../../../docs/framework/wcf/extending/extending-dispatchers.md).  
  
 A maioria dos usuários do WCF não interagem com o tempo de execução diretamente; em vez disso, eles usam construções de modelo, como pontos de extremidade, contratos, associações, endereços e atributos em classes ou comportamentos em arquivos de configuração de comportamento de programação do core. Essas construções compõem o *árvore descrição*, que é a especificação completa para a criação de um tempo de execução para dar suporte a um serviço ou cliente descrita pela árvore de descrição.  
  
 Há quatro tipos de comportamentos do WCF:  
  
- Comportamentos de serviço (<xref:System.ServiceModel.Description.IServiceBehavior> tipos) permitem a personalização do tempo de execução de todo o serviço, incluindo <xref:System.ServiceModel.ServiceHostBase>.  
  
- Comportamentos de ponto de extremidade (<xref:System.ServiceModel.Description.IEndpointBehavior> tipos) permitem a personalização de pontos de extremidade de serviço e seus respectivos <xref:System.ServiceModel.Dispatcher.EndpointDispatcher> objetos.  
  
- Comportamentos de contrato (<xref:System.ServiceModel.Description.IContractBehavior> tipos) permitem a personalização de ambos os <xref:System.ServiceModel.Dispatcher.ClientRuntime> e <xref:System.ServiceModel.Dispatcher.DispatchRuntime> classes no cliente e aplicativos de serviço, respectivamente.  
  
- Comportamentos de operação (<xref:System.ServiceModel.Description.IOperationBehavior> tipos) permitem a personalização do <xref:System.ServiceModel.Dispatcher.ClientOperation> e <xref:System.ServiceModel.Dispatcher.DispatchOperation> classes, novamente, no cliente e o serviço.  
  
 Você pode adicionar esses comportamentos para os vários objetos de descrição com a implementação de atributos personalizados, usando arquivos de configuração de aplicativo, ou diretamente ao adicioná-los à coleção de comportamentos no objeto de descrição apropriada. Deve, no entanto, ser adicionado a uma descrição do serviço ou objeto de descrição do ponto de extremidade de serviço antes de chamar <xref:System.ServiceModel.ICommunicationObject.Open%2A?displayProperty=nameWithType> sobre o <xref:System.ServiceModel.ServiceHost> ou um <xref:System.ServiceModel.ChannelFactory%601>.  
  
### <a name="behavior-scopes"></a>Escopos de comportamento  
 Há quatro tipos de comportamento, cada um correspondendo a um determinado escopo de acesso de tempo de execução.  
  
#### <a name="service-behaviors"></a>Comportamentos de serviço  
 Comportamentos de serviço, que implementam <xref:System.ServiceModel.Description.IServiceBehavior>, são o principal mecanismo pelo qual você modificar o tempo de execução de todo o serviço. Existem três mecanismos para adicionar comportamentos de serviço a um serviço.  
  
1. Usando um atributo na classe de serviço.  Quando um <xref:System.ServiceModel.ServiceHost> é construído, o <xref:System.ServiceModel.ServiceHost> implementação usa a reflexão para descobrir o conjunto de atributos no tipo de serviço. Se qualquer um desses atributos são implementações de <xref:System.ServiceModel.Description.IServiceBehavior>, eles são adicionados à coleção de comportamentos em <xref:System.ServiceModel.Description.ServiceDescription>. Isso permite que esses comportamentos participar na construção do serviço de tempo de execução.  
  
2. Adicionando programaticamente o comportamento à coleção de comportamentos em <xref:System.ServiceModel.Description.ServiceDescription>. Isso pode ser feito com as seguintes linhas de código:  
  
    ```csharp
    ServiceHost host = new ServiceHost(/* Parameters */);  
    host.Description.Behaviors.Add(/* Service Behavior */);  
    ```  
  
3. Implementação de uma <xref:System.ServiceModel.Configuration.BehaviorExtensionElement> que se estende a configuração. Isso permite que o uso do comportamento do serviço de arquivos de configuração do aplicativo.  
  
 Exemplos de comportamentos de serviço do WCF a <xref:System.ServiceModel.ServiceBehaviorAttribute> atributo, o <xref:System.ServiceModel.Description.ServiceThrottlingBehavior>e o <xref:System.ServiceModel.Description.ServiceMetadataBehavior> comportamento.  
  
#### <a name="contract-behaviors"></a>Comportamentos de contrato  
 Contrato de comportamentos, que implementam o <xref:System.ServiceModel.Description.IContractBehavior> interface, são usados para estender o cliente e o serviço de tempo de execução em um contrato.  
  
 Há dois mecanismos para adicionar comportamentos de contrato a um contrato.  O primeiro mecanismo é criar um atributo personalizado a ser usado na interface de contrato. Quando uma interface de contrato seja passada para um <xref:System.ServiceModel.ServiceHost> ou um <xref:System.ServiceModel.ChannelFactory%601>, WCF examina os atributos na interface. Se todos os atributos são implementações de <xref:System.ServiceModel.Description.IContractBehavior>, aquelas são adicionadas à coleção de comportamentos a <xref:System.ServiceModel.Description.ContractDescription?displayProperty=nameWithType> criado para essa interface.  
  
 Você também pode implementar o <xref:System.ServiceModel.Description.IContractBehaviorAttribute?displayProperty=nameWithType> do atributo de comportamento de contrato personalizado. Nesse caso, o comportamento é da seguinte maneira quando aplicado a:  
  
 Interface de contrato •A. Nesse caso, o comportamento é aplicado a todos os contratos desse tipo em qualquer ponto de extremidade e WCF ignora o valor da <xref:System.ServiceModel.Description.IContractBehaviorAttribute.TargetContract%2A?displayProperty=nameWithType> propriedade.  
  
 Classe de serviço •A. Nesse caso, o comportamento é aplicado somente aos pontos de extremidade que o contrato que é o valor da <xref:System.ServiceModel.Description.IContractBehaviorAttribute.TargetContract%2A> propriedade.  
  
 Classe de retorno de chamada •A. Nesse caso, o comportamento é aplicado ao ponto de extremidade do cliente duplex e WCF ignora o valor da <xref:System.ServiceModel.Description.IContractBehaviorAttribute.TargetContract%2A> propriedade.  
  
 O segundo mecanismo é adicionar o comportamento à coleção de comportamentos em um <xref:System.ServiceModel.Description.ContractDescription>.  
  
 Exemplos de comportamentos de contrato no WCF a <xref:System.ServiceModel.DeliveryRequirementsAttribute?displayProperty=nameWithType> atributo. Para obter mais informações e um exemplo, consulte o tópico de referência.  
  
#### <a name="endpoint-behaviors"></a>Comportamentos de ponto de extremidade  
 Comportamentos de ponto de extremidade, que implementam <xref:System.ServiceModel.Description.IEndpointBehavior>, são o principal mecanismo pelo qual você modificar o tempo de execução para um ponto de extremidade específico de cliente ou de todo o serviço.  
  
 Há dois mecanismos para adicionar comportamentos de ponto de extremidade a um serviço.  
  
1. Adicionar o comportamento para o <xref:System.ServiceModel.Description.ServiceEndpoint.Behaviors%2A> propriedade.  
  
2. Implementar um personalizado <xref:System.ServiceModel.Configuration.BehaviorExtensionElement> que se estende a configuração.  
  
 Para obter mais informações e um exemplo, consulte o tópico de referência.  
  
#### <a name="operation-behaviors"></a>Comportamentos de operação  
 Comportamentos de operação, que implementam o <xref:System.ServiceModel.Description.IOperationBehavior> interface, são usados para estender o cliente e o serviço de tempo de execução para cada operação.  
  
 Há dois mecanismos para adicionar comportamentos de operação para uma operação. O primeiro mecanismo é criar um atributo personalizado a ser usado no método que modela a operação. Quando uma operação é adicionada como um <xref:System.ServiceModel.ServiceHost> ou um <xref:System.ServiceModel.ChannelFactory>, WCF adiciona quaisquer <xref:System.ServiceModel.Description.IOperationBehavior> atributos para a coleção de comportamentos no <xref:System.ServiceModel.Description.OperationDescription> criado para essa operação.  
  
 O segundo mecanismo é adicionando diretamente o comportamento à coleção behaviors em um construído <xref:System.ServiceModel.Description.OperationDescription>.  
  
 Exemplos de comportamentos de operação do WCF a <xref:System.ServiceModel.OperationBehaviorAttribute> e o <xref:System.ServiceModel.TransactionFlowAttribute>.  
  
 Para obter mais informações e um exemplo, consulte o tópico de referência.  
  
### <a name="using-configuration-to-create-behaviors"></a>Usando a configuração para criar comportamentos  
 Serviço e o ponto de extremidade e pode de comportamentos de contrato por projetado para ser especificado no código ou usando os atributos; somente os comportamentos de serviço e o ponto de extremidade podem ser configurados usando o aplicativo ou arquivos de configuração Web. Expondo comportamentos usando atributos permite que os desenvolvedores especifiquem um comportamento em tempo de compilação que não pode ser adicionado, removido ou modificado em tempo de execução. Isso geralmente é adequado para comportamentos que sempre são necessários para a operação correta de um serviço (por exemplo, os parâmetros relacionados de transação para o <xref:System.ServiceModel.ServiceBehaviorAttribute?displayProperty=nameWithType> atributo). Expondo comportamentos usando a configuração permite aos desenvolvedores deixar a especificação e a configuração desses comportamentos para aqueles que implantar o serviço. Isso é adequado para comportamentos que são componentes opcionais ou outra configuração de implantação específicas, como se os metadados são expostos para o serviço ou a configuração de autorização específico para um serviço.  
  
> [!NOTE]
>  Você também pode usar comportamentos que dão suporte à configuração para impor as políticas de aplicativo da empresa, inserindo-os no arquivo de configuração Machine. config e bloquear esses itens. Para obter uma descrição e um exemplo, consulte [como: Bloquear pontos de extremidade na empresa](../../../../docs/framework/wcf/extending/how-to-lock-down-endpoints-in-the-enterprise.md).  
  
 Para expor um comportamento usando a configuração, um desenvolvedor deve criar uma classe derivada de <xref:System.ServiceModel.Configuration.BehaviorExtensionElement> e, em seguida, registre essa extensão com a configuração.  
  
 O seguinte exemplo de código mostra como um <xref:System.ServiceModel.Description.IEndpointBehavior> implementa <xref:System.ServiceModel.Configuration.BehaviorExtensionElement>:  
  
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
  
 Para que o sistema de configuração carregar um personalizado <xref:System.ServiceModel.Configuration.BehaviorExtensionElement>, ele deve ser registrado como uma extensão. O exemplo de código a seguir mostra o arquivo de configuração para o comportamento anterior do ponto de extremidade:  
  
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
  
 Em que `Microsoft.WCF.Documentation.EndpointBehaviorMessageInspector` é o tipo de extensão de comportamento e `HostApplication` é o nome do assembly no qual essa classe foi compilada.  
  
### <a name="evaluation-order"></a>Ordem de avaliação  
 O <xref:System.ServiceModel.ChannelFactory%601?displayProperty=nameWithType> e o <xref:System.ServiceModel.ServiceHost?displayProperty=nameWithType> são responsáveis por compilar o tempo de execução do modelo de programação e a descrição. Comportamentos, conforme descritos anteriormente, contribuem para que o processo no serviço, ponto de extremidade, contrato e operação de compilação.  
  
 O <xref:System.ServiceModel.ServiceHost> aplica comportamentos na seguinte ordem:  
  
1. Serviço  
  
2. Contrato  
  
3. Ponto de extremidade  
  
4. Operação  
  
 Dentro de qualquer coleção de comportamentos, nenhuma ordem é garantida.  
  
 O <xref:System.ServiceModel.ChannelFactory%601> aplica comportamentos na seguinte ordem:  
  
1. Contrato  
  
2. Ponto de extremidade  
  
3. Operação  
  
 Dentro de qualquer coleção de comportamentos, novamente, sem nenhuma ordem é garantida.  
  
### <a name="adding-behaviors-programmatically"></a>Adicionando comportamentos de forma programática  
 Propriedades do <xref:System.ServiceModel.Description.ServiceDescription?displayProperty=nameWithType> no serviço de aplicativo não deve ser modificado subsequente para o <xref:System.ServiceModel.Channels.CommunicationObject.OnOpening%2A?displayProperty=nameWithType> método em <xref:System.ServiceModel.ServiceHostBase?displayProperty=nameWithType>. Alguns membros, como o <xref:System.ServiceModel.ServiceHostBase.Credentials%2A?displayProperty=nameWithType> propriedade e o `AddServiceEndpoint` métodos <xref:System.ServiceModel.ServiceHostBase> e <xref:System.ServiceModel.ServiceHost?displayProperty=nameWithType>, lançar uma exceção se modificado após esse ponto. Outros permitem que você modificá-los, mas o resultado será indefinido.  
  
 Da mesma forma, no cliente a <xref:System.ServiceModel.Description.ServiceEndpoint?displayProperty=nameWithType> valores não devem ser modificados após a chamada para <xref:System.ServiceModel.Channels.CommunicationObject.OnOpening%2A> sobre o <xref:System.ServiceModel.ChannelFactory?displayProperty=nameWithType>. O <xref:System.ServiceModel.ChannelFactory.Credentials%2A?displayProperty=nameWithType> propriedade gera uma exceção se modificado após esse ponto, mas os outros valores de descrição de cliente podem ser modificados sem erro. No entanto, o resultado será indefinido.  
  
 Se para o serviço ou cliente, é recomendável que você modifique a descrição antes de chamar <xref:System.ServiceModel.Channels.CommunicationObject.Open%2A?displayProperty=nameWithType>.  
  
### <a name="inheritance-rules-for-behavior-attributes"></a>Regras de herança para atributos de comportamento  
 Todos os quatro tipos de comportamentos podem ser preenchidos usando atributos – comportamentos de serviço e comportamentos de contrato. Como os atributos são definidos em objetos gerenciados e os membros e objetos gerenciados e os membros dão suporte à herança, é necessário definir como os atributos de comportamento funcionam no contexto de herança.  
  
 Em um alto nível, a regra é que, para um escopo específico (por exemplo, serviço, contrato ou operação), todos os atributos de comportamento na hierarquia de herança para esse escopo são aplicados. Se houver dois atributos de comportamento do mesmo tipo, somente o tipo mais derivado é usado.  
  
#### <a name="service-behaviors"></a>Comportamentos de serviço  
 Para uma classe de serviço fornecido, todos os atributos de comportamento de serviço nessa classe e nos pais da classe, são aplicados. Se o mesmo tipo de atributo é aplicado em vários lugares na hierarquia de herança, o tipo mais derivado é usado.  
  
```csharp  
[ServiceBehavior(ConcurrencyMode = ConcurrencyMode.Multiple)]  
[AspNetCompatibilityRequirementsAttribute(  
    AspNetCompatibilityRequirementsMode = AspNetCompatibilityRequirementsMode.Allowed)]  
public class A { /* … */ }  
  
[ServiceBehavior(InstanceContextMode = InstanceContextMode.Single)]  
public class B : A { /* … */}  
```  
  
 Por exemplo, no caso anterior, o serviço B acaba com uma <xref:System.ServiceModel.InstanceContextMode> dos <xref:System.ServiceModel.InstanceContextMode.Single>, um <xref:System.ServiceModel.Activation.AspNetCompatibilityRequirementsMode> modo de <xref:System.ServiceModel.Activation.AspNetCompatibilityRequirementsMode.Allowed>e um <xref:System.ServiceModel.ConcurrencyMode> de <xref:System.ServiceModel.ConcurrencyMode.Single>. O <xref:System.ServiceModel.ConcurrencyMode> está <xref:System.ServiceModel.ConcurrencyMode.Single>, pois <xref:System.ServiceModel.ServiceBehaviorAttribute> atributo no serviço B estiver em "mais derivada" do que o do serviço A.  
  
#### <a name="contract-behaviors"></a>Comportamentos de contrato  
 Para um determinado contrato, todos os de contrato de atributos de comportamento em que a interface e nos pais dessa interface, são aplicadas. Se o mesmo tipo de atributo é aplicado em vários lugares na hierarquia de herança, o tipo mais derivado é usado.  
  
#### <a name="operation-behaviors"></a>Comportamentos de operação  
 Se uma determinada operação não substitui um resumo da existente ou uma operação virtual, não há regras de herança se aplicam.  
  
 Se uma operação Substituir uma operação existente e, em seguida, todos os atributos de comportamento de operação em que a operação e nos pais dessa operação, são aplicadas.  Se o mesmo tipo de atributo é aplicado em vários lugares na hierarquia de herança, o tipo mais derivado é usado.
