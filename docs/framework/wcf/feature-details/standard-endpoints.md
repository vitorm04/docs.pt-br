---
title: Pontos de extremidade padrão
ms.date: 03/30/2017
ms.assetid: 3fcb4225-addc-44f2-935d-30e4943a8812
ms.openlocfilehash: 48924e06457cf9f91ce4f900bb38de4d22bfc550
ms.sourcegitcommit: 927b7ea6b2ea5a440c8f23e3e66503152eb85591
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/16/2020
ms.locfileid: "81463783"
---
# <a name="standard-endpoints"></a>Pontos de extremidade padrão
Os pontos finais são definidos especificando um endereço, uma vinculação e um contrato. Outros parâmetros que podem ser definidos em um ponto final incluem configuração de comportamento, cabeçalhos e URIs de ouvir.  Para certos tipos de pontos finais, esses valores não mudam. Por exemplo, os pontos finais <xref:System.ServiceModel.Description.IMetadataExchange> de troca de metadados sempre usam o contrato. Outros pontos finais, <xref:System.ServiceModel.Description.WebHttpEndpoint> como sempre, exigem um comportamento de ponto final especificado. A usabilidade de um ponto final pode ser melhorada tendo pontos finais com valores padrão para propriedades de ponto final comumente usadas. Os pontos finais padrão permitem que um desenvolvedor defina um ponto final que tenha valores padrão ou onde as propriedades de um ou mais pontos finais não mudem.  Esses pontos finais permitem que você use esse ponto final sem ter que especificar informações de natureza estática. Os pontos finais padrão podem ser usados para pontos finais de infra-estrutura e aplicativos.  
  
## <a name="infrastructure-endpoints"></a>Pontos finais da infra-estrutura  
 Um serviço pode expor pontos finais com algumas das propriedades não explicitamente implementadas pelo autor do serviço. Por exemplo, o ponto final da <xref:System.ServiceModel.Description.IMetadataExchange> troca de metadados expõe o contrato, mas como um autor de serviço que você não implementa essa interface, ela é implementada pelo WCF. Esses pontos finais de infra-estrutura têm valores padrão para uma ou mais propriedades de ponto final, algumas das quais podem ser inalteráveis. A <xref:System.ServiceModel.Description.ServiceEndpoint.Contract%2A> propriedade do ponto final de <xref:System.ServiceModel.Description.IMetadataExchange>troca de metadados deve ser , enquanto outras propriedades como a vinculação podem ser fornecidas pelo desenvolvedor. Os pontos finais da <xref:System.ServiceModel.Description.ServiceEndpoint.IsSystemEndpoint%2A> infra-estrutura são identificados definindo a propriedade como `true`.  
  
## <a name="application-endpoints"></a>Pontos finais do aplicativo  
 Os desenvolvedores de aplicativos podem definir seus próprios pontos finais padrão que especificam valores padrão para o endereço, vinculação ou contrato. Você define um ponto final padrão, <xref:System.ServiceModel.Description.ServiceEndpoint> derivando uma classe e definindo as propriedades de ponto final apropriadas. Você pode fornecer valores padrão para propriedades que podem ser alteradas. Algumas outras propriedades terão valores estáticos que não podem ser alterados. O exemplo a seguir mostra como implementar um ponto final padrão.  
  
```csharp
public class CustomEndpoint : ServiceEndpoint
{
    public CustomEndpoint()
        : this(string.Empty)
    { }  

    public CustomEndpoint(string address)
        : this(address, ContractDescription.GetContract(typeof(ICalculator)))
    { }  

    // Create the custom endpoint with a fixed binding
    public CustomEndpoint(string address, ContractDescription contract)
        : base(contract)
    {
        this.Binding = new BasicHttpBinding();
        this.IsSystemEndpoint = false;
    }

    // Definition of the additional property of this endpoint
    public bool Property { get; set; }
}
```
  
 Para usar um ponto final personalizado definido pelo usuário em <xref:System.ServiceModel.Configuration.StandardEndpointElement>um arquivo <xref:System.ServiceModel.Configuration.StandardEndpointCollectionElement%602>de configuração, você deve derivar uma classe de , derivar uma classe e registrar o novo ponto final padrão na seção de extensões em app.config ou machine.config.  O <xref:System.ServiceModel.Configuration.StandardEndpointElement> fornece suporte de configuração para o ponto final padrão, como mostrado no exemplo a seguir.  
  
```csharp
public class CustomEndpointElement : StandardEndpointElement
{
    // Definition of the additional property for the standard endpoint element
    public bool Property
    {
        get { return (bool)base["property"]; }
        set { base["property"] = value; }
    }

    // The additional property needs to be added to the properties of the standard endpoint element
    protected override ConfigurationPropertyCollection Properties
    {
        get
        {
            ConfigurationPropertyCollection properties = base.Properties;
            properties.Add(new ConfigurationProperty("property", typeof(bool), false, ConfigurationPropertyOptions.None));
            return properties;
        }
    }

    // Return the type of this standard endpoint
    protected override Type EndpointType
    {
        get { return typeof(CustomEndpoint); }
    }

    // Create the custom service endpoint
    protected override ServiceEndpoint CreateServiceEndpoint(ContractDescription contract)
    {
        return new CustomEndpoint();
    }

    // Read the value given to the property in config and save it
    protected override void OnApplyConfiguration(ServiceEndpoint endpoint, ServiceEndpointElement serviceEndpointElement)
    {
        CustomEndpoint customEndpoint = (CustomEndpoint)endpoint;
        customEndpoint.Property = this.Property;
    }

    // Read the value given to the property in config and save it
    protected override void OnApplyConfiguration(ServiceEndpoint endpoint, ChannelEndpointElement channelEndpointElement)
    {
        CustomEndpoint customEndpoint = (CustomEndpoint)endpoint;
        customEndpoint.Property = this.Property;
    }

    // No validation in this sample
    protected override void OnInitializeAndValidate(ServiceEndpointElement serviceEndpointElement)
    {
    }

    // No validation in this sample
    protected override void OnInitializeAndValidate(ChannelEndpointElement channelEndpointElement)
    {
    }
}
```  
  
 O <xref:System.ServiceModel.Configuration.StandardEndpointCollectionElement%602> fornece o tipo de backup para `standardEndpoints` a coleção que aparece sob a seção <> na configuração para o ponto final padrão.  O exemplo a seguir mostra como implementar essa classe.  
  
```csharp
public class CustomEndpointCollectionElement : StandardEndpointCollectionElement<CustomEndpoint, CustomEndpointElement>
{
    // ...
}
```

O exemplo a seguir mostra como registrar um ponto final padrão na seção extensões.

```xml  
<extensions>  
      <standardEndpointExtensions>  
        <add  
          name="customStandardEndpoint"  
          type="CustomEndpointCollectionElement, Example.dll,  
                Version=1.0.0.0, Culture=neutral, PublicKeyToken=ffffffffffffffff"/>  
      </standardEndpointExtensions>
</extensions>  
```  
  
## <a name="configuring-a-standard-endpoint"></a>Configurando um ponto final padrão  
 Os pontos finais padrão podem ser adicionados em código ou na configuração.  Para adicionar um ponto final padrão no código, basta instanciar o tipo de ponto final padrão apropriado e adicioná-lo ao host de serviço, conforme mostrado no exemplo a seguir:  
  
```csharp  
serviceHost.AddServiceEndpoint(new CustomEndpoint());  
```  
  
 Para adicionar um ponto final padrão `endpoint` na configuração, `service` adicione um elemento> <`standardEndpoints` ao elemento <> e quaisquer configurações necessárias no elemento de> <. O exemplo a seguir <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint>mostra como adicionar a , [!INCLUDE[netfx_current_long](../../../../includes/netfx-current-long-md.md)]um dos pontos finais padrão com os quais é enviado .  
  
```xml  
<services>  
  <service>  
    <endpoint isSystemEndpoint="true" kind="udpDiscoveryEndpoint" />  
  </service>  
</services>  
<standardEndpoints>
  <udpDiscoveryEndpoint>  
     <standardEndpoint multicastAddress="soap.udp://239.255.255.250:3702" />
  </udpDiscoveryEndpoint>
</standardEndpoints>
```  
  
 O tipo de ponto final padrão é especificado `endpoint` usando o atributo tipo no elemento <>. O ponto final é configurado dentro do elemento> <. `standardEndpoints` No exemplo acima, <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint> um ponto final é adicionado e configurado. O `udpDiscoveryEndpoint` elemento> <`standardEndpoint` contém uma <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint.MulticastAddress%2A>> <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint><que define a propriedade do .  
  
## <a name="standard-endpoints-shipped-with-the-net-framework"></a>Pontos finais padrão enviados com o Framework .NET  
 A tabela a seguir lista os [!INCLUDE[netfx_current_long](../../../../includes/netfx-current-long-md.md)]pontos finais padrão enviados com .  
  
 `Mex Endpoint`  
 Um ponto final padrão que é usado para expor metadados de serviço.  
  
 <xref:System.ServiceModel.Discovery.AnnouncementEndpoint>  
 Um ponto de extremidade padrão usado pelos serviços para enviar mensagens de comunicado.  
  
 <xref:System.ServiceModel.Discovery.DiscoveryEndpoint>  
 Um ponto final padrão que é usado pelos serviços para enviar mensagens de descoberta.  
  
 <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint>  
 Um ponto de extremidade padrão pré-configurado para operações de descoberta por meio de uma associação multicast UDP.  
  
 <xref:System.ServiceModel.Discovery.UdpAnnouncementEndpoint>  
 Um ponto de extremidade padrão usado pelos serviços para enviar mensagens de comunicado por meio de uma associação UDP.  
  
 <xref:System.ServiceModel.Discovery.DynamicEndpoint>  
 Um ponto final padrão que usa o WS-Discovery para encontrar o endereço de ponto final dinamicamente em tempo de execução.  
  
 <xref:System.ServiceModel.Description.ServiceMetadataEndpoint>  
 Um ponto final padrão para troca de metadados.  
  
 <xref:System.ServiceModel.Description.WebHttpEndpoint>  
 Um ponto final <xref:System.ServiceModel.WebHttpBinding> padrão com uma <xref:System.ServiceModel.Description.WebHttpBehavior> vinculação que adiciona automaticamente o comportamento  
  
 <xref:System.ServiceModel.Description.WebScriptEndpoint>  
 Um ponto final <xref:System.ServiceModel.WebHttpBinding> padrão com uma <xref:System.ServiceModel.Description.WebScriptEnablingBehavior> ligação que adiciona automaticamente o comportamento.  
  
 <xref:System.ServiceModel.Description.WebServiceEndpoint>  
 Um ponto final <xref:System.ServiceModel.WebHttpBinding> padrão com uma ligação.  
  
 <xref:System.ServiceModel.Activities.WorkflowControlEndpoint>  
 Um ponto de extremidade padrão que permite chamar operações de controle em instâncias de fluxo de trabalho.  
  
 <xref:System.ServiceModel.Activities.WorkflowHostingEndpoint>  
 Um ponto final padrão que suporta a criação do fluxo de trabalho e a retomada de marcadores.
