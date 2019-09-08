---
title: Configuração e suporte de metadados
ms.date: 03/30/2017
ms.assetid: 27c240cb-8cab-472c-87f8-c864f4978758
ms.openlocfilehash: 16c386f8479778c7d2f17fbdfdb95dee558baf52
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70795842"
---
# <a name="configuration-and-metadata-support"></a>Configuração e suporte de metadados
Este tópico descreve como habilitar o suporte de configuração e metadados para associações e elementos de associação.  
  
## <a name="overview-of-configuration-and-metadata"></a>Visão geral da configuração e dos metadados  
 Este tópico discute as seguintes tarefas, que são itens opcionais 1, 2 e 4 na lista de tarefas [desenvolvimento de canais](developing-channels.md) .  
  
- Habilitando o suporte ao arquivo de configuração para um elemento de associação.  
  
- Habilitando o suporte ao arquivo de configuração para uma associação.  
  
- Exportando declarações WSDL e de política para um elemento de associação.  
  
- Identificação de declarações WSDL e de política para inserir e configurar seu elemento Binding ou Binding.  
  
 Para obter informações sobre como criar associações definidas pelo usuário e elementos de associação, consulte [Criando associações definidas pelo usuário](creating-user-defined-bindings.md) e [criando um BindingElement](creating-a-bindingelement.md), respectivamente.  
  
## <a name="adding-configuration-support"></a>Adicionando suporte à configuração  
 Para habilitar o suporte ao arquivo de configuração para um canal, você deve implementar duas <xref:System.ServiceModel.Configuration.BindingElementExtensionElement?displayProperty=nameWithType>seções de configuração,, que habilitam o suporte à <xref:System.ServiceModel.Configuration.StandardBindingElement?displayProperty=nameWithType> configuração <xref:System.ServiceModel.Configuration.StandardBindingCollectionElement%602?displayProperty=nameWithType>para elementos de associação e o e, que habilitam o suporte à configuração para associações.  
  
 Uma maneira mais fácil de fazer isso é usar a ferramenta de exemplo [ConfigurationCodeGenerator](../samples/configurationcodegenerator.md) para gerar o código de configuração para suas associações e elementos de associação.  
  
### <a name="extending-bindingelementextensionelement"></a>Estendendo BindingElementExtensionElement  
 O código de exemplo a seguir é obtido [do transporte: Exemplo](../samples/transport-udp.md) de UDP. O `UdpTransportElement` é um <xref:System.ServiceModel.Configuration.BindingElementExtensionElement> que expõe `UdpTransportBindingElement` para o sistema de configuração. Com algumas substituições básicas, o exemplo define o nome da seção de configuração, o tipo do elemento de associação e como criar o elemento de associação. Os usuários podem então registrar a seção de extensão em um arquivo de configuração da seguinte maneira.  
  
```xml  
<configuration>  
  <system.serviceModel>  
    <extensions>  
      <bindingElementExtensions>  
      <add name="udpTransport" type="Microsoft.ServiceModel.Samples.UdpTransportElement, UdpTransport />  
      </bindingElementExtensions>  
    </extensions>  
  </system.serviceModel>  
</configuration>  
```  
  
 A extensão pode ser referenciada de associações personalizadas para usar UDP como o transporte.  
  
```xml  
<configuration>  
  <system.serviceModel>  
    <bindings>  
      <customBinding>  
       <binding configurationName="UdpCustomBinding">  
         <udpTransport/>  
       </binding>  
      </customBinding>  
    </bindings>  
  </system.serviceModel>  
</configuration>  
```  
  
### <a name="adding-configuration-for-a-binding"></a>Adicionando configuração para uma associação  
 A seção `SampleProfileUdpBindingCollectionElement` é um <xref:System.ServiceModel.Configuration.StandardBindingCollectionElement%602> que expõe `SampleProfileUdpBinding` para o sistema de configuração. A maior parte da implementação é delegada para o `SampleProfileUdpBindingConfigurationElement`, que deriva de. <xref:System.ServiceModel.Configuration.StandardBindingElement> O `SampleProfileUdpBindingConfigurationElement` tem propriedades que correspondem às propriedades em `SampleProfileUdpBinding`e às `ConfigurationElement` funções a serem mapeadas da associação. Por fim, `OnApplyConfiguration` o método é substituído `SampleProfileUdpBinding`no, conforme mostrado no código de exemplo a seguir.  
  
```csharp 
protected override void OnApplyConfiguration(string configurationName)  
{  
            if (binding == null)  
                throw new ArgumentNullException("binding");  
  
            if (binding.GetType() != typeof(SampleProfileUdpBinding))  
            {  
                throw new ArgumentException(string.Format(CultureInfo.CurrentCulture,  
                    "Invalid type for binding. Expected type: {0}. Type passed in: {1}.",  
                    typeof(SampleProfileUdpBinding).AssemblyQualifiedName,  
                    binding.GetType().AssemblyQualifiedName));  
            }  
            SampleProfileUdpBinding udpBinding = (SampleProfileUdpBinding)binding;  
  
            udpBinding.OrderedSession = this.OrderedSession;  
            udpBinding.ReliableSessionEnabled = this.ReliableSessionEnabled;  
            udpBinding.SessionInactivityTimeout = this.SessionInactivityTimeout;  
            if (this.ClientBaseAddress != null)  
                   udpBinding.ClientBaseAddress = ClientBaseAddress;  
}  
```  
  
 Para registrar esse manipulador com o sistema de configuração, adicione a seção a seguir ao arquivo de configuração relevante.  
  
```xml  
<configuration>  
  <configSections>  
     <sectionGroup name="system.serviceModel">  
         <sectionGroup name="bindings">  
                 <section name="sampleProfileUdpBinding" type="Microsoft.ServiceModel.Samples.SampleProfileUdpBindingCollectionElement, UdpTransport />  
         </sectionGroup>  
     </sectionGroup>  
  </configSections>  
</configuration>  
```  
  
 Em seguida, ele pode ser referenciado na seção de [ \<configuração System. ServiceModel >](../../configure-apps/file-schema/wcf/system-servicemodel.md) .  
  
```xml  
<configuration>  
  <system.serviceModel>  
    <client>  
      <endpoint configurationName="calculator"  
                address="soap.udp://localhost:8001/"   
                bindingConfiguration="CalculatorServer"  
                binding="sampleProfileUdpBinding"   
                contract= "Microsoft.ServiceModel.Samples.ICalculatorContract">  
      </endpoint>  
    </client>  
  </system.serviceModel>  
</configuration>  
```  
  
## <a name="adding-metadata-support-for-a-binding-element"></a>Adicionando suporte de metadados para um elemento de associação  
 Para integrar um canal no sistema de metadados, ele deve dar suporte à importação e à exportação da política. Isso permite que ferramentas como a [ferramenta de utilitário de metadados ServiceModel (svcutil. exe)](../servicemodel-metadata-utility-tool-svcutil-exe.md) gerem clientes do elemento de associação.  
  
### <a name="adding-wsdl-support"></a>Adicionando suporte a WSDL  
 O elemento de associação de transporte em uma associação é responsável por exportar e importar informações de endereçamento nos metadados. Ao usar uma associação SOAP, o elemento de associação de transporte também deve exportar um URI de transporte correto nos metadados. O código de exemplo a seguir é obtido [do transporte: Exemplo](../samples/transport-udp.md) de UDP.  
  
#### <a name="wsdl-export"></a>Exportação de WSDL  
 Para exportar informações de endereçamento `UdpTransportBindingElement` , o <xref:System.ServiceModel.Description.IWsdlExportExtension?displayProperty=nameWithType> implementa a interface. O <xref:System.ServiceModel.Description.IWsdlExportExtension.ExportEndpoint%2A?displayProperty=nameWithType> método adiciona as informações de endereçamento corretas à porta WSDL.  
  
```csharp  
if (context.WsdlPort != null)  
{  
    AddAddressToWsdlPort(context.WsdlPort, context.Endpoint.Address, encodingBindingElement.MessageVersion.Addressing);  
}  
```  
  
 A `UdpTransportBindingElement` implementação<xref:System.ServiceModel.Description.IWsdlExportExtension.ExportEndpoint%2A> do método também exporta um URI de transporte quando o ponto de extremidade usa uma associação SOAP:  
  
```csharp  
WsdlNS.SoapBinding soapBinding = GetSoapBinding(context, exporter);  
if (soapBinding != null)  
{  
    soapBinding.Transport = UdpPolicyStrings.UdpNamespace;  
}  
```  
  
#### <a name="wsdl-import"></a>Importação de WSDL  
 Para estender o sistema de importação WSDL para lidar com a importação dos endereços, adicione a seguinte configuração ao arquivo de configuração para SvcUtil. exe, conforme mostrado no arquivo svcutil. exe. config:  
  
```xml  
<configuration>  
  <system.serviceModel>  
    <client>  
      <metadata>  
        <wsdlImporters>  
          <extension type=" Microsoft.ServiceModel.Samples.UdpBindingElementImporter, UdpTransport" />  
        </policyImporters>  
      </metadata>  
    </client>  
  </system.serviceModel>  
</configuration>  
```  
  
 Ao executar svcutil. exe, há duas opções para obter svcutil. exe para carregar as extensões de importação WSDL:  
  
1. Aponte para o SvcUtil. exe para o arquivo de configuração usando\<o arquivo/SvcutilConfig: File >.  
  
2. Adicione a seção de configuração a svcutil. exe. config no mesmo diretório que svcutil. exe.  
  
 O `UdpBindingElementImporter` tipo implementa a <xref:System.ServiceModel.Description.IWsdlImportExtension?displayProperty=nameWithType> interface. O `ImportEndpoint` método importa o endereço da porta WSDL:  
  
```csharp  
BindingElementCollection bindingElements = context.Endpoint.Binding.CreateBindingElements();  
TransportBindingElement transportBindingElement = bindingElements.Find<TransportBindingElement>();  
if (transportBindingElement is UdpTransportBindingElement)  
{  
    ImportAddress(context);  
}  
```  
  
### <a name="adding-policy-support"></a>Adicionando suporte à política  
 O elemento de associação personalizado pode exportar declarações de política na associação WSDL para um ponto de extremidade de serviço para expressar os recursos desse elemento de associação. O código de exemplo a seguir é obtido [do transporte: Exemplo](../samples/transport-udp.md) de UDP.  
  
#### <a name="policy-export"></a>Exportação de política  
 O `UdpTransportBindingElement` tipo implementa <xref:System.ServiceModel.Description.IPolicyExportExtension?displayProperty=nameWithType> para adicionar suporte para exportar a política. Como resultado, <xref:System.ServiceModel.Description.MetadataExporter?displayProperty=nameWithType> o inclui `UdpTransportBindingElement` na geração de política para qualquer associação que a inclua.  
  
 No <xref:System.ServiceModel.Description.IPolicyExportExtension.ExportPolicy%2A?displayProperty=nameWithType>, adicione uma asserção para UDP e outra asserção se o canal estiver no modo multicast. Isso ocorre porque o modo multicast afeta a forma como a pilha de comunicação é construída e, portanto, deve ser coordenado entre ambos os lados.  
  
```csharp  
ICollection<XmlElement> bindingAssertions = context.GetBindingAssertions();  
XmlDocument xmlDocument = new XmlDocument();  
bindingAssertions.Add(xmlDocument.CreateElement(  
UdpPolicyStrings.Prefix, UdpPolicyStrings.TransportAssertion, UdpPolicyStrings.UdpNamespace));  
if (Multicast)  
{  
    bindingAssertions.Add(xmlDocument.CreateElement(  
UdpPolicyStrings.Prefix, UdpPolicyStrings.MulticastAssertion,     UdpPolicyStrings.UdpNamespace));  
}  
```  
  
 Como os elementos de associação de transporte personalizados são responsáveis pelo tratamento <xref:System.ServiceModel.Description.IPolicyExportExtension?displayProperty=nameWithType> de endereçamento `UdpTransportBindingElement` , a implementação no também deve lidar com a exportação das asserções de política apropriadas do WS-Addressing para indicar a versão do WS-Addressing sendo usado.  
  
```csharp  
AddWSAddressingAssertion(context, encodingBindingElement.MessageVersion.Addressing);  
```  
  
#### <a name="policy-import"></a>Importação de política  
 Para estender o sistema de importação de política, adicione a configuração a seguir ao arquivo de configuração para SvcUtil. exe, conforme mostrado no arquivo svcutil. exe. config:  
  
```xml  
<configuration>  
  <system.serviceModel>  
    <client>  
      <metadata>  
        <policyImporters>  
          <extension type=" Microsoft.ServiceModel.Samples.UdpBindingElementImporter, UdpTransport" />  
        </policyImporters>  
      </metadata>  
    </client>  
  </system.serviceModel>  
</configuration>  
```  
  
 Em seguida, <xref:System.ServiceModel.Description.IPolicyImportExtension?displayProperty=nameWithType> implementamos a partir de`UdpBindingElementImporter`nossa classe registrada (). No <xref:System.ServiceModel.Description.IPolicyImportExtension.ImportPolicy%2A?displayProperty=nameWithType>, examine as asserções no namespace apropriado e processe aquelas para gerar o transporte e verificar se ele é multicast. Além disso, remova as asserções que o importador manipula da lista de asserções de associação. Novamente, ao executar svcutil. exe, há duas opções de integração:  
  
1. Aponte para o SvcUtil. exe para nosso arquivo de configuração usando\<o arquivo/SvcutilConfig: File >.  
  
2. Adicione a seção de configuração a svcutil. exe. config no mesmo diretório que svcutil. exe.  
  
### <a name="adding-a-custom-standard-binding-importer"></a>Adicionando um importador de associação padrão personalizado  
 Svcutil. exe e o <xref:System.ServiceModel.Description.WsdlImporter?displayProperty=nameWithType> tipo, por padrão, reconhecem e importam associações fornecidas pelo sistema. Caso contrário, a associação será importada como uma <xref:System.ServiceModel.Channels.CustomBinding?displayProperty=nameWithType> instância. Para habilitar svcutil. exe e o <xref:System.ServiceModel.Description.WsdlImporter> para importar `UdpBindingElementImporter` o `SampleProfileUdpBinding` também atua como um importador de associação padrão personalizado.  
  
 Um importador de associação padrão personalizado implementa `ImportEndpoint` o método <xref:System.ServiceModel.Description.IWsdlImportExtension?displayProperty=nameWithType> na interface para examinar a <xref:System.ServiceModel.Channels.CustomBinding?displayProperty=nameWithType> instância importada de metadados para ver se ela pode ter sido gerada por uma associação padrão específica.  
  
```csharp  
if (context.Endpoint.Binding is CustomBinding)  
{  
    Binding binding;  
    if (transportBindingElement is UdpTransportBindingElement)  
    {  
        //if TryCreate is true, the CustomBinding will be replace by a SampleProfileUdpBinding in the  
        //generated config file for better typed generation.  
        if (SampleProfileUdpBinding.TryCreate(bindingElements, out binding))  
        {  
            binding.Name = context.Endpoint.Binding.Name;  
            binding.Namespace = context.Endpoint.Binding.Namespace;  
            context.Endpoint.Binding = binding;  
        }  
    }  
}  
```  
  
 Em geral, a implementação de um importador de associação padrão personalizado envolve a verificação das propriedades dos elementos de associação importados para verificar se apenas as propriedades que poderiam ter sido definidas pela associação padrão foram alteradas e todas as outras propriedades são seus padrões. Uma estratégia básica para implementar um importador de associação padrão é criar uma instância da associação padrão, propagar as propriedades dos elementos de associação para a instância de associação padrão à qual a associação padrão dá suporte e comparar a associação elementos da associação padrão com os elementos de associação importados.
