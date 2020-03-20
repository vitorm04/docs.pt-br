---
title: Configurando e estendendo o runtime com comportamentos
ms.date: 03/30/2017
helpviewer_keywords:
- attaching extensions using behaviors [WCF]
ms.assetid: 149b99b6-6eb6-4f45-be22-c967279677d9
ms.openlocfilehash: 67db06649d6059ff6b6e6fb8d84058621fcc7dab
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79185647"
---
# <a name="configuring-and-extending-the-runtime-with-behaviors"></a>Configurando e estendendo o runtime com comportamentos
Os comportamentos permitem modificar o comportamento padrão e adicionar extensões personalizadas que inspecionam e validam a configuração do serviço ou modificam o comportamento em tempo de execução nos aplicativos de serviço e cliente sustais da Windows Communication Foundation (Windows Communication Foundation). Este tópico descreve as interfaces de comportamento, como implementá-las e como adicioná-las à descrição do serviço (em um aplicativo de serviço) ou ponto final (em um aplicativo cliente) programáticamente ou em um arquivo de configuração. Para obter mais informações sobre o uso de comportamentos fornecidos pelo sistema, consulte [Especificar comportamento em tempo de execução do serviço](../specifying-service-run-time-behavior.md) [e especificar comportamento de tempo de execução do cliente](../specifying-client-run-time-behavior.md).  
  
## <a name="behaviors"></a>Comportamentos  
 Os tipos de comportamento são adicionados aos objetos de descrição de ponto final de serviço ou serviço (no serviço ou cliente, respectivamente) antes que esses objetos sejam usados pela Windows Communication Foundation (WCF) para criar um tempo de execução que execute um serviço WCF ou um cliente WCF. Quando esses comportamentos são chamados durante o processo de construção em tempo de execução, eles são capazes de acessar propriedades e métodos de tempo de execução que modificam o tempo de execução construído pelo contrato, vinculações e endereços.  
  
### <a name="behavior-methods"></a>Métodos de comportamento  
 Todos os comportamentos `AddBindingParameters` têm `ApplyDispatchBehavior` um método, um método, `Validate` um método e um `ApplyClientBehavior` método com uma exceção: Porque <xref:System.ServiceModel.Description.IServiceBehavior> não pode executar em um cliente, ele não implementa `ApplyClientBehavior`.  
  
- Use `AddBindingParameters` o método para modificar ou adicionar objetos personalizados a uma coleção que as vinculações personalizadas podem acessar para seu uso quando o tempo de execução for construído. Por exemplo, é assim que os requisitos de proteção são especificados que afetam a forma como o canal é construído, mas não são conhecidos pelo desenvolvedor do canal.  
  
- Use `Validate` o método para examinar a árvore de descrição e o objeto de tempo de execução correspondente para garantir que ele esteja em conformidade com algum conjunto de critérios.  
  
- Use `ApplyDispatchBehavior` os `ApplyClientBehavior` métodos e métodos para examinar a árvore de descrição e modificar o tempo de execução para um escopo específico no serviço ou no cliente. Você também pode inserir objetos de extensão.  
  
    > [!NOTE]
    > Embora uma árvore de descrição seja fornecida nestes métodos, é apenas para exame. Se uma árvore de descrição for modificada, o comportamento é indefinido.  
  
 As propriedades que você pode modificar e as interfaces de personalização que você pode implementar são acessadas através das classes de serviço e tempo de execução do cliente. Os tipos de <xref:System.ServiceModel.Dispatcher.DispatchRuntime> <xref:System.ServiceModel.Dispatcher.DispatchOperation> serviço são as aulas. Os tipos de <xref:System.ServiceModel.Dispatcher.ClientRuntime> <xref:System.ServiceModel.Dispatcher.ClientOperation> clientes são as classes. As <xref:System.ServiceModel.Dispatcher.ClientRuntime> <xref:System.ServiceModel.Dispatcher.DispatchRuntime> classes e as classes são os pontos de entrada de extensibilidade para acessar propriedades de tempo de execução e extensão em todo o cliente e em todo o serviço, respectivamente. Da mesma <xref:System.ServiceModel.Dispatcher.ClientOperation> forma, as classes expõem <xref:System.ServiceModel.Dispatcher.DispatchOperation> as propriedades de execução da operação e operação de serviço do cliente e coleções de extensão, respectivamente. No entanto, você pode acessar o objeto de tempo de execução com escopo mais amplo do objeto de tempo de execução da operação e vice-versa, se necessário.  
  
> [!NOTE]
> Para uma discussão sobre propriedades de tempo de execução e tipos de extensão que você pode usar para modificar o comportamento de execução de um cliente, consulte [Estendendo clientes](extending-clients.md). Para uma discussão sobre propriedades de tempo de execução e tipos de extensão que você pode usar para modificar o comportamento de execução de um despachante de serviço, consulte [Despachantes de extensão](extending-dispatchers.md).  
  
 A maioria dos usuários de WCF não interage diretamente com o tempo de execução; em vez disso, eles usam construções de modelo de programação principal, como pontos finais, contratos, vinculações, endereços e atributos de comportamento em classes ou comportamentos em arquivos de configuração. Esses construtos compõem a *árvore de descrição*, que é a especificação completa para a construção de um tempo de execução para suportar um serviço ou cliente descrito pela árvore de descrição.  
  
 Existem quatro tipos de comportamentos no WCF:  
  
- Os comportamentos<xref:System.ServiceModel.Description.IServiceBehavior> de serviço (tipos) permitem a personalização de todo o tempo de execução do serviço, incluindo <xref:System.ServiceModel.ServiceHostBase>.  
  
- Os comportamentos de<xref:System.ServiceModel.Description.IEndpointBehavior> ponto final (tipos) permitem a <xref:System.ServiceModel.Dispatcher.EndpointDispatcher> personalização dos pontos finais de serviço e seus objetos associados.  
  
- Os comportamentos<xref:System.ServiceModel.Description.IContractBehavior> contratuais (tipos) permitem <xref:System.ServiceModel.Dispatcher.ClientRuntime> a <xref:System.ServiceModel.Dispatcher.DispatchRuntime> personalização tanto das classes quanto nos aplicativos de clientes e serviços, respectivamente.  
  
- Comportamentos de<xref:System.ServiceModel.Description.IOperationBehavior> operação (tipos) permitem <xref:System.ServiceModel.Dispatcher.ClientOperation> a <xref:System.ServiceModel.Dispatcher.DispatchOperation> personalização das classes e classes, novamente, no cliente e no serviço.  
  
 Você pode adicionar esses comportamentos aos vários objetos de descrição implementando atributos personalizados, usando arquivos de configuração de aplicativos ou adicionando-os diretamente à coleção de comportamentos no objeto de descrição apropriado. O deve, no entanto, ser adicionado a uma descrição <xref:System.ServiceModel.ICommunicationObject.Open%2A?displayProperty=nameWithType> de <xref:System.ServiceModel.ServiceHost> serviço <xref:System.ServiceModel.ChannelFactory%601>ou objeto de descrição do ponto final do serviço antes de chamar o ou um .  
  
### <a name="behavior-scopes"></a>Escopos de comportamento  
 Existem quatro tipos de comportamento, cada um dos quais corresponde a um escopo específico de acesso em tempo de execução.  
  
#### <a name="service-behaviors"></a>Comportamentos de serviço  
 Os comportamentos de <xref:System.ServiceModel.Description.IServiceBehavior>serviço, que implementam, são o mecanismo principal pelo qual você modifica todo o tempo de execução do serviço. Existem três mecanismos para adicionar comportamentos de serviço a um serviço.  
  
1. Usando um atributo na classe de serviço.  Quando <xref:System.ServiceModel.ServiceHost> um é construído, a <xref:System.ServiceModel.ServiceHost> implementação usa a reflexão para descobrir o conjunto de atributos sobre o tipo de serviço. Se algum desses atributos <xref:System.ServiceModel.Description.IServiceBehavior>for em implementação de , <xref:System.ServiceModel.Description.ServiceDescription>eles são adicionados à coleta de comportamentos em . Isso permite que esses comportamentos participem da construção do tempo de execução do serviço.  
  
2. Programáticamente adicionando o comportamento à <xref:System.ServiceModel.Description.ServiceDescription>coleta de comportamentos em . Isso pode ser feito com as seguintes linhas de código:  
  
    ```csharp
    ServiceHost host = new ServiceHost(/* Parameters */);  
    host.Description.Behaviors.Add(/* Service Behavior */);  
    ```  
  
3. Implementando <xref:System.ServiceModel.Configuration.BehaviorExtensionElement> um costume que amplia a configuração. Isso permite o uso do comportamento do serviço a partir de arquivos de configuração de aplicativos.  
  
 Exemplos de comportamentos de serviço no <xref:System.ServiceModel.ServiceBehaviorAttribute> WCF <xref:System.ServiceModel.Description.ServiceThrottlingBehavior>incluem <xref:System.ServiceModel.Description.ServiceMetadataBehavior> o atributo, o e o comportamento.  
  
#### <a name="contract-behaviors"></a>Comportamentos contratuais  
 Os comportamentos contratuais, <xref:System.ServiceModel.Description.IContractBehavior> que implementam a interface, são usados para estender o tempo de execução do cliente e do serviço através de um contrato.  
  
 Existem dois mecanismos para adicionar comportamentos contratuais a um contrato.  O primeiro mecanismo é criar um atributo personalizado para ser usado na interface do contrato. Quando uma interface de contrato <xref:System.ServiceModel.ServiceHost> é <xref:System.ServiceModel.ChannelFactory%601>passada para a ou a, o WCF examina os atributos na interface. Se algum atributo for <xref:System.ServiceModel.Description.IContractBehavior>implementação de , esses são <xref:System.ServiceModel.Description.ContractDescription?displayProperty=nameWithType> adicionados à coleta de comportamentos na criação para essa interface.  
  
 Você também pode <xref:System.ServiceModel.Description.IContractBehaviorAttribute?displayProperty=nameWithType> implementar o atributo sobre o comportamento do contrato personalizado. Neste caso, o comportamento é o seguinte quando aplicado a:  
  
 • Uma interface de contrato. Neste caso, o comportamento é aplicado a todos os contratos desse tipo em qualquer <xref:System.ServiceModel.Description.IContractBehaviorAttribute.TargetContract%2A?displayProperty=nameWithType> ponto final e o WCF ignora o valor do imóvel.  
  
 • Uma classe de serviço. Nesse caso, o comportamento é aplicado apenas para endpoints o <xref:System.ServiceModel.Description.IContractBehaviorAttribute.TargetContract%2A> contrato do qual é o valor do imóvel.  
  
 •Uma aula de retorno de chamada. Neste caso, o comportamento é aplicado ao ponto final do cliente duplex e <xref:System.ServiceModel.Description.IContractBehaviorAttribute.TargetContract%2A> o WCF ignora o valor da propriedade.  
  
 O segundo mecanismo é adicionar o comportamento à <xref:System.ServiceModel.Description.ContractDescription>coleta de comportamentos em um .  
  
 Exemplos de comportamentos contratuais no <xref:System.ServiceModel.DeliveryRequirementsAttribute?displayProperty=nameWithType> WCF incluem o atributo. Para obter mais informações e um exemplo, consulte o tópico de referência.  
  
#### <a name="endpoint-behaviors"></a>Comportamentos de ponto final  
 Os comportamentos de ponto <xref:System.ServiceModel.Description.IEndpointBehavior>final, que implementam, são o mecanismo principal pelo qual você modifica todo o tempo de execução do serviço ou do cliente para um ponto final específico.  
  
 Existem dois mecanismos para adicionar comportamentos de ponto final a um serviço.  
  
1. Adicione o comportamento <xref:System.ServiceModel.Description.ServiceEndpoint.Behaviors%2A> à propriedade.  
  
2. Implemente <xref:System.ServiceModel.Configuration.BehaviorExtensionElement> um personalizado que prolongue a configuração.  
  
 Para obter mais informações e um exemplo, consulte o tópico de referência.  
  
#### <a name="operation-behaviors"></a>Comportamentos da Operação  
 Os comportamentos de operação, que implementam a <xref:System.ServiceModel.Description.IOperationBehavior> interface, são usados para estender o tempo de execução do cliente e do serviço para cada operação.  
  
 Há dois mecanismos para adicionar comportamentos de operação a uma operação. O primeiro mecanismo é criar um atributo personalizado para ser usado no método que modela a operação. Quando uma operação é <xref:System.ServiceModel.ServiceHost> adicionada <xref:System.ServiceModel.ChannelFactory>a a ou <xref:System.ServiceModel.Description.IOperationBehavior> a, o WCF <xref:System.ServiceModel.Description.OperationDescription> adiciona quaisquer atributos à coleta de comportamentos na criação para essa operação.  
  
 O segundo mecanismo é adicionando diretamente o comportamento à <xref:System.ServiceModel.Description.OperationDescription>coleta de comportamentos em um construído.  
  
 Exemplos de comportamentos de operação no <xref:System.ServiceModel.OperationBehaviorAttribute> WCF incluem o e o <xref:System.ServiceModel.TransactionFlowAttribute>.  
  
 Para obter mais informações e um exemplo, consulte o tópico de referência.  
  
### <a name="using-configuration-to-create-behaviors"></a>Usando configuração para criar comportamentos  
 Serviço e ponto final, e comportamentos contratuais podem ser projetados para serem especificados em código ou usando atributos; apenas comportamentos de serviço e ponto final podem ser configurados usando arquivos de configuração de aplicativos ou Web. Expor comportamentos usando atributos permite que os desenvolvedores especifiquem um comportamento em tempo de compilação que não pode ser adicionado, removido ou modificado em tempo de execução. Isso é muitas vezes adequado para comportamentos que são sempre necessários para o funcionamento <xref:System.ServiceModel.ServiceBehaviorAttribute?displayProperty=nameWithType> correto de um serviço (por exemplo, os parâmetros relacionados à transação ao atributo). Expor comportamentos usando a configuração permite que os desenvolvedores deixem a especificação e configuração desses comportamentos para aqueles que implantam o serviço. Isso é adequado para comportamentos que são componentes opcionais ou outra configuração específica de implantação, como se os metadados estão expostos para o serviço ou a configuração de autorização específica para um serviço.  
  
> [!NOTE]
> Você também pode usar comportamentos que suportam a configuração para impor políticas de aplicativos da empresa, inserindo-as no arquivo de configuração machine.config e bloqueando esses itens. Para obter uma descrição e um exemplo, consulte [Como: Bloquear pontos finais na Empresa](how-to-lock-down-endpoints-in-the-enterprise.md).  
  
 Para expor um comportamento usando a configuração, <xref:System.ServiceModel.Configuration.BehaviorExtensionElement> um desenvolvedor deve criar uma classe derivada e, em seguida, registrar essa extensão com configuração.  
  
 O exemplo de código <xref:System.ServiceModel.Description.IEndpointBehavior> a <xref:System.ServiceModel.Configuration.BehaviorExtensionElement>seguir mostra como um implementa:  
  
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
  
 Para que o sistema de <xref:System.ServiceModel.Configuration.BehaviorExtensionElement>configuração carregue um personalizado, ele deve ser registrado como uma extensão. O exemplo de código a seguir mostra o arquivo de configuração para o comportamento de ponto final anterior:  
  
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
  
 Onde `Microsoft.WCF.Documentation.EndpointBehaviorMessageInspector` está o tipo `HostApplication` de extensão de comportamento e é o nome da montagem em que essa classe foi compilada.  
  
### <a name="evaluation-order"></a>Ordem de Avaliação  
 Os <xref:System.ServiceModel.ChannelFactory%601?displayProperty=nameWithType> responsáveis <xref:System.ServiceModel.ServiceHost?displayProperty=nameWithType> pela construção do tempo de execução a partir do modelo de programação e descrição. Os comportamentos, como descrito anteriormente, contribuem para esse processo de construção no serviço, ponto final, contrato e operação.  
  
 Os <xref:System.ServiceModel.ServiceHost> comportamentos aplicados na seguinte ordem:  
  
1. Serviço  
  
2. Contrato  
  
3. Ponto de extremidade  
  
4. Operação  
  
 Dentro de qualquer coleção de comportamentos, nenhuma ordem é garantida.  
  
 Os <xref:System.ServiceModel.ChannelFactory%601> comportamentos aplicados na seguinte ordem:  
  
1. Contrato  
  
2. Ponto de extremidade  
  
3. Operação  
  
 Dentro de qualquer coleção de comportamentos, novamente, nenhuma ordem é garantida.  
  
### <a name="adding-behaviors-programmatically"></a>Adicionando comportamentos programáticamente  
 As propriedades <xref:System.ServiceModel.Description.ServiceDescription?displayProperty=nameWithType> do aplicativo de serviço não <xref:System.ServiceModel.Channels.CommunicationObject.OnOpening%2A?displayProperty=nameWithType> devem <xref:System.ServiceModel.ServiceHostBase?displayProperty=nameWithType>ser modificadas posteriormente ao método em . Alguns membros, <xref:System.ServiceModel.ServiceHostBase.Credentials%2A?displayProperty=nameWithType> como `AddServiceEndpoint` a propriedade <xref:System.ServiceModel.ServiceHostBase> <xref:System.ServiceModel.ServiceHost?displayProperty=nameWithType>e os métodos e , lançam uma exceção se modificados após esse ponto. Outros permitem modificá-los, mas o resultado é indefinido.  
  
 Da mesma forma, <xref:System.ServiceModel.Description.ServiceEndpoint?displayProperty=nameWithType> no cliente os valores <xref:System.ServiceModel.Channels.CommunicationObject.OnOpening%2A> não <xref:System.ServiceModel.ChannelFactory?displayProperty=nameWithType>devem ser modificados após a chamada para o . A <xref:System.ServiceModel.ChannelFactory.Credentials%2A?displayProperty=nameWithType> propriedade lança uma exceção se modificada após esse ponto, mas os outros valores de descrição do cliente podem ser modificados sem erro. O resultado, no entanto, é indefinido.  
  
 Seja para o serviço ou cliente, recomenda-se que <xref:System.ServiceModel.Channels.CommunicationObject.Open%2A?displayProperty=nameWithType>você modifique a descrição antes de ligar .  
  
### <a name="inheritance-rules-for-behavior-attributes"></a>Regras de herança para atributos de comportamento  
 Todos os quatro tipos de comportamentos podem ser preenchidos usando atributos – comportamentos de serviço e comportamentos contratuais. Como os atributos são definidos em objetos e membros gerenciados, e objetos gerenciados e membros apoiam a herança, é necessário definir como os atributos de comportamento funcionam no contexto da herança.  
  
 Em alto nível, a regra é que para um escopo específico (por exemplo, serviço, contrato ou operação), todos os atributos de comportamento na hierarquia de herança para esse escopo são aplicados. Se houver dois atributos de comportamento do mesmo tipo, apenas o tipo mais derivado é usado.  
  
#### <a name="service-behaviors"></a>Comportamentos de serviço  
 Para uma determinada classe de serviço, todos os atributos de comportamento de serviço nessa classe, e sobre os pais dessa classe, são aplicados. Se o mesmo tipo de atributo for aplicado em vários lugares da hierarquia de herança, o tipo mais derivado é usado.  
  
```csharp  
[ServiceBehavior(ConcurrencyMode = ConcurrencyMode.Multiple)]  
[AspNetCompatibilityRequirementsAttribute(  
    AspNetCompatibilityRequirementsMode = AspNetCompatibilityRequirementsMode.Allowed)]  
public class A { /* … */ }  
  
[ServiceBehavior(InstanceContextMode = InstanceContextMode.Single)]  
public class B : A { /* … */}  
```  
  
 Por exemplo, no caso anterior, o serviço <xref:System.ServiceModel.InstanceContextMode> <xref:System.ServiceModel.InstanceContextMode.Single>B <xref:System.ServiceModel.Activation.AspNetCompatibilityRequirementsMode> acaba <xref:System.ServiceModel.Activation.AspNetCompatibilityRequirementsMode.Allowed>com um <xref:System.ServiceModel.ConcurrencyMode> <xref:System.ServiceModel.ConcurrencyMode.Single>de , um modo de , e a de . O <xref:System.ServiceModel.ConcurrencyMode> <xref:System.ServiceModel.ConcurrencyMode.Single>é <xref:System.ServiceModel.ServiceBehaviorAttribute> , porque o atributo no serviço B está em "mais derivado" do que no serviço A.  
  
#### <a name="contract-behaviors"></a>Comportamentos contratuais  
 Para um determinado contrato, todos os atributos de comportamento contratual nessa interface e sobre os pais dessa interface, são aplicados. Se o mesmo tipo de atributo for aplicado em vários lugares da hierarquia de herança, o tipo mais derivado é usado.  
  
#### <a name="operation-behaviors"></a>Comportamentos da Operação  
 Se uma determinada operação não substituir uma operação abstrata ou virtual existente, nenhuma regra de herança se aplica.  
  
 Se uma operação anular uma operação existente, então todos os atributos de comportamento de operação nessa operação e sobre os pais dessa operação, são aplicados.  Se o mesmo tipo de atributo for aplicado em vários lugares da hierarquia de herança, o tipo mais derivado é usado.
