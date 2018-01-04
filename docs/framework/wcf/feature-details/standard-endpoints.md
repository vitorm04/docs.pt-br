---
title: "Pontos de extremidade padrão"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 3fcb4225-addc-44f2-935d-30e4943a8812
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: de5f1c858b9018071489354441cab197bf5db6e2
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="standard-endpoints"></a>Pontos de extremidade padrão
Pontos de extremidade são definidos pela especificação de um endereço, uma ligação e um contrato. Outros parâmetros que podem ser definidos em um ponto de extremidade incluem a configuração de comportamento, cabeçalhos e escutam URIs.  Para determinados tipos de pontos de extremidade que não altere esses valores. Por exemplo, pontos de extremidade de troca de metadados sempre usam o <xref:System.ServiceModel.Description.IMetadataExchange> contrato. Outros pontos de extremidade, como <xref:System.ServiceModel.Description.WebHttpEndpoint> sempre exigem um comportamento de ponto de extremidade especificado. O uso de um ponto de extremidade pode ser melhorado por ter pontos de extremidade com valores padrão para propriedades de ponto de extremidade de uso geral. Pontos de extremidade padrão permitem que um desenvolvedor definir um ponto de extremidade que tem valores padrão ou em que as propriedades de um ou mais do ponto de extremidade não é alterado.  Esses pontos de extremidade permitem que você use um ponto de extremidade sem precisar especificar informações de natureza estática. Pontos de extremidade padrão podem ser usados para pontos de extremidade de infraestrutura e aplicativo.  
  
## <a name="infrastructure-endpoints"></a>Pontos de extremidade de infraestrutura  
 Um serviço pode expor pontos de extremidade com algumas das propriedades não são explicitamente implementadas pelo autor do serviço. Por exemplo, o ponto de extremidade de troca de metadados expõe o <xref:System.ServiceModel.Description.IMetadataExchange> de contrato, mas como um serviço de autor implementa essa interface, ele é implementado pelo WCF. Esses pontos de extremidade de infraestrutura têm valores padrão para uma ou mais propriedades de ponto de extremidade, alguns dos quais podem ser inalterável. O <xref:System.ServiceModel.Description.ServiceEndpoint.Contract%2A> propriedade do ponto de extremidade de troca de metadados deve ser <xref:System.ServiceModel.Description.IMetadataExchange>, enquanto outras propriedades, como associação podem ser fornecidas pelo desenvolvedor. Pontos de extremidade de infraestrutura são identificados, definindo o <xref:System.ServiceModel.Description.ServiceEndpoint.IsSystemEndpoint%2A> propriedade `true`.  
  
## <a name="application-endpoints"></a>Pontos de extremidade do aplicativo  
 Os desenvolvedores de aplicativos podem definir seus próprios pontos de extremidade padrão que especificam valores padrão para o endereço, associação ou contrato. Definir um ponto de extremidade padrão derivando uma classe de <xref:System.ServiceModel.Description.ServiceEndpoint> e definindo as propriedades de ponto de extremidade apropriado. Você pode fornecer valores padrão para as propriedades que podem ser alteradas. Algumas outras propriedades terão valores estáticos que não é possível alterar. O exemplo a seguir mostra como implementar um ponto de extremidade padrão.  
  
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
  
 Para usar um ponto de extremidade de personalizado definido pelo usuário em um arquivo de configuração, você deve derivar uma classe de <xref:System.ServiceModel.Configuration.StandardEndpointElement>, derive uma classe de <xref:System.ServiceModel.Configuration.StandardEndpointCollectionElement%602>e registrar o novo ponto de extremidade padrão na seção de extensões em App. config ou Machine. config.  O <xref:System.ServiceModel.Configuration.StandardEndpointElement> fornece suporte à configuração para o ponto de extremidade padrão, conforme mostrado no exemplo a seguir.  
  
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
  
 O <xref:System.ServiceModel.Configuration.StandardEndpointCollectionElement%602> fornece o tipo de backup para a coleção que aparece sob o <`standardEndpoints`> seção na configuração para o ponto de extremidade padrão.  O exemplo a seguir mostra como implementar essa classe.  
  
```csharp
public class CustomEndpointCollectionElement : StandardEndpointCollectionElement<CustomEndpoint, CustomEndpointElement>
{
    // ...
}
```

O exemplo a seguir mostra como registrar um ponto de extremidade padrão na seção de extensões.

```xml  
<extensions>  
      <standardEndpointExtensions>  
        <add  
          name="customStandardEndpoint"  
          type="CustomEndpointCollectionElement, Example.dll,  
                Version=1.0.0.0, Culture=neutral, PublicKeyToken=ffffffffffffffff"/>  
```  
  
## <a name="configuring-a-standard-endpoint"></a>Configurando um ponto de extremidade padrão  
 Pontos de extremidade padrão podem ser adicionados no código ou na configuração.  Para adicionar um ponto de extremidade padrão no código simplesmente instanciar o tipo de ponto de extremidade padrão apropriado e adicioná-lo para o host de serviço, conforme mostrado no exemplo a seguir:  
  
```csharp  
serviceHost.AddServiceEndpoint(new CustomEndpoint());  
```  
  
 Para adicionar um ponto de extremidade padrão na configuração, adicione um <`endpoint`> elemento para o <`service`> elemento e quaisquer definições de configuração no é necessário o <`standardEndpoints`> elemento. O exemplo a seguir mostra como adicionar um <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint>, um dos pontos de extremidade padrão que é fornecido com [!INCLUDE[netfx_current_long](../../../../includes/netfx-current-long-md.md)].  
  
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
  
 O tipo de ponto de extremidade padrão é especificado usando o atributo de tipo no <`endpoint`> elemento. O ponto de extremidade é configurado dentro de <`standardEndpoints`> elemento. No exemplo acima, uma <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint> ponto de extremidade é adicionado e configurado. O <`udpDiscoveryEndpoint`> elemento contém um <`standardEndpoint`> que define o <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint.MulticastAddress%2A> propriedade o <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint>.  
  
## <a name="standard-endpoints-shipped-with-the-net-framework"></a>Pontos de extremidade padrão fornecidos com o .NET Framework  
 A tabela a seguir lista os pontos de extremidade padrão que acompanham o [!INCLUDE[netfx_current_long](../../../../includes/netfx-current-long-md.md)].  
  
 `Mex Endpoint`  
 Um ponto de extremidade padrão que é usado para expor metadados de serviço.  
  
 <xref:System.ServiceModel.Discovery.AnnouncementEndpoint>  
 Um ponto de extremidade padrão usado pelos serviços para enviar mensagens de comunicado.  
  
 <xref:System.ServiceModel.Discovery.DiscoveryEndpoint>  
 Um ponto de extremidade padrão que é usado pelos serviços para enviar mensagens de descoberta.  
  
 <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint>  
 Associação de um ponto de extremidade padrão que é pré-configurado para operações de descoberta através de um UDP multicast.  
  
 <xref:System.ServiceModel.Discovery.UdpAnnouncementEndpoint>  
 Um ponto de extremidade padrão que é usado pelos serviços para enviar mensagens de aviso sobre uma associação de UDP.  
  
 <xref:System.ServiceModel.Discovery.DynamicEndpoint>  
 Um ponto de extremidade padrão que usa o WS-Discovery para localizar o endereço de ponto de extremidade dinamicamente em tempo de execução.  
  
 <xref:System.ServiceModel.Description.ServiceMetadataEndpoint>  
 Um ponto de extremidade padrão de troca de metadados.  
  
 <xref:System.ServiceModel.Description.WebHttpEndpoint>  
 Um ponto de extremidade padrão com um <xref:System.ServiceModel.WebHttpBinding> associação que automaticamente adiciona o <xref:System.ServiceModel.Description.WebHttpBehavior> comportamento  
  
 <xref:System.ServiceModel.Description.WebScriptEndpoint>  
 Um ponto de extremidade padrão com um <xref:System.ServiceModel.WebHttpBinding> associação que automaticamente adiciona o <xref:System.ServiceModel.Description.WebScriptEnablingBehavior> comportamento.  
  
 <xref:System.ServiceModel.Description.WebServiceEndpoint>  
 Um ponto de extremidade padrão com um <xref:System.ServiceModel.WebHttpBinding> associação.  
  
 <xref:System.ServiceModel.Activities.WorkflowControlEndpoint>  
 Um ponto de extremidade padrão que permite que você possa chamar operações de controle em instâncias de fluxo de trabalho.  
  
 <xref:System.ServiceModel.Activities.WorkflowHostingEndpoint>  
 Um ponto de extremidade padrão que dá suporte a retomada da criação e o indicador de fluxo de trabalho.
