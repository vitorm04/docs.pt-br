---
title: Configuração e suporte de metadados
ms.date: 03/30/2017
ms.assetid: 27c240cb-8cab-472c-87f8-c864f4978758
ms.openlocfilehash: abc9177fcc7b338a365d61721b63041ddcd68ab9
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/09/2019
ms.locfileid: "59298299"
---
# <a name="configuration-and-metadata-support"></a>Configuração e suporte de metadados
Este tópico descreve como habilitar o suporte de configuração e metadados para associações e elementos de associação.  
  
## <a name="overview-of-configuration-and-metadata"></a>Visão geral da configuração e metadados  
 Este tópico aborda as seguintes tarefas são itens opcionais, 1, 2 e 4 na [canais de desenvolvimento](../../../../docs/framework/wcf/extending/developing-channels.md) lista de tarefas.  
  
-   Habilitando o suporte de arquivo de configuração para um elemento de associação.  
  
-   Habilitando o suporte de arquivo de configuração para uma associação.  
  
-   Exportando asserções WSDL e política para um elemento de associação.  
  
-   Identificando declarações WSDL e política para inserir e configurar o elemento de associação ou a associação.  
  
 Para obter informações sobre como criar associações definidas pelo usuário e elementos de associação, consulte [criando ligações](../../../../docs/framework/wcf/extending/creating-user-defined-bindings.md) e [criando um BindingElement](../../../../docs/framework/wcf/extending/creating-a-bindingelement.md), respectivamente.  
  
## <a name="adding-configuration-support"></a>Adicionando suporte à configuração  
 Para habilitar o suporte de arquivo de configuração para um canal, você deve implementar duas seções de configuração, <xref:System.ServiceModel.Configuration.BindingElementExtensionElement?displayProperty=nameWithType>, que habilita o suporte de configuração para elementos de associação e o <xref:System.ServiceModel.Configuration.StandardBindingElement?displayProperty=nameWithType> e <xref:System.ServiceModel.Configuration.StandardBindingCollectionElement%602?displayProperty=nameWithType>, que permitem que o suporte de configuração associações.  
  
 Uma maneira fácil de fazer isso é usar o [ConfigurationCodeGenerator](../../../../docs/framework/wcf/samples/configurationcodegenerator.md) ferramenta de exemplo para gerar o código de configuração para suas associações e elementos de associação.  
  
### <a name="extending-bindingelementextensionelement"></a>Estendendo BindingElementExtensionElement  
 O exemplo de código a seguir é retirado de [transporte: UDP](../../../../docs/framework/wcf/samples/transport-udp.md) exemplo. O `UdpTransportElement` é um <xref:System.ServiceModel.Configuration.BindingElementExtensionElement> que expõe `UdpTransportBindingElement` ao sistema de configuração. Com algumas substituições básicas, o exemplo define o nome da seção de configuração, o tipo do elemento de associação e como criar o elemento de associação. Os usuários podem, em seguida, registrar a seção de extensão em um arquivo de configuração da seguinte maneira.  
  
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
  
 A extensão pode ser referenciada de ligações personalizadas para usar UDP como o transporte.  
  
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
  
### <a name="adding-configuration-for-a-binding"></a>Adicionar configuração de uma associação  
 A seção `SampleProfileUdpBindingCollectionElement` é um <xref:System.ServiceModel.Configuration.StandardBindingCollectionElement%602> que expõe `SampleProfileUdpBinding` ao sistema de configuração. A maior parte da implementação é delegada para o `SampleProfileUdpBindingConfigurationElement`, que é derivada de <xref:System.ServiceModel.Configuration.StandardBindingElement>. O `SampleProfileUdpBindingConfigurationElement` tem propriedades que correspondem às propriedades nos `SampleProfileUdpBinding`e funções para mapear o `ConfigurationElement` associação. Por fim, o `OnApplyConfiguration` método for substituído no `SampleProfileUdpBinding`, conforme mostrado no código de exemplo a seguir.  
  
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
  
 Para registrar esse manipulador com o sistema de configuração, adicione a seguinte seção ao arquivo de configuração relevantes.  
  
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
  
 Em seguida, pode ser referenciada do [ \<System. ServiceModel >](../../../../docs/framework/configure-apps/file-schema/wcf/system-servicemodel.md) seção de configuração.  
  
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
  
## <a name="adding-metadata-support-for-a-binding-element"></a>Adicionar suporte de metadados para um elemento de associação  
 Para integrar um canal para o sistema de metadados, ele deve oferecer suporte a importação e a exportação da política. Isso permite que ferramentas como [ferramenta de utilitário de metadados ServiceModel (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) para gerar os clientes do elemento de associação.  
  
### <a name="adding-wsdl-support"></a>Adicionando suporte a WSDL  
 O elemento de associação de transporte em uma associação é responsável por exportação e importação de informações de endereçamento nos metadados. Ao usar uma associação SOAP, o elemento de associação de transporte também deve exportar um URI de transporte correto nos metadados. O exemplo de código a seguir é retirado de [transporte: UDP](../../../../docs/framework/wcf/samples/transport-udp.md) exemplo.  
  
#### <a name="wsdl-export"></a>Exportação WSDL  
 Para exportar informações de endereçamento, o `UdpTransportBindingElement` implementa o <xref:System.ServiceModel.Description.IWsdlExportExtension?displayProperty=nameWithType> interface. O <xref:System.ServiceModel.Description.IWsdlExportExtension.ExportEndpoint%2A?displayProperty=nameWithType> método adiciona as informações de endereçamento corretas para a porta WSDL.  
  
```csharp  
if (context.WsdlPort != null)  
{  
    AddAddressToWsdlPort(context.WsdlPort, context.Endpoint.Address, encodingBindingElement.MessageVersion.Addressing);  
}  
```  
  
 O `UdpTransportBindingElement` implementação do <xref:System.ServiceModel.Description.IWsdlExportExtension.ExportEndpoint%2A> método também exporta um transporte URI quando o ponto de extremidade usa uma associação SOAP:  
  
```csharp  
WsdlNS.SoapBinding soapBinding = GetSoapBinding(context, exporter);  
if (soapBinding != null)  
{  
    soapBinding.Transport = UdpPolicyStrings.UdpNamespace;  
}  
```  
  
#### <a name="wsdl-import"></a>Importação WSDL  
 Para estender o sistema de importação WSDL para lidar com os endereços a importação, adicione a seguinte configuração ao arquivo de configuração para Svcutil.exe conforme mostrado no arquivo de svcutil:  
  
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
  
 Ao executar Svcutil.exe, há duas opções para obtenção de Svcutil.exe para carregar as extensões de importação WSDL:  
  
1. Svcutil.exe ponto para o arquivo de configuração usando o /SvcutilConfig:\<arquivo >.  
  
2. Adicione a seção de configuração para svcutil no mesmo diretório que Svcutil.exe.  
  
 O `UdpBindingElementImporter` tipo implementa o <xref:System.ServiceModel.Description.IWsdlImportExtension?displayProperty=nameWithType> interface. O `ImportEndpoint` método importa o endereço da porta WSDL:  
  
```csharp  
BindingElementCollection bindingElements = context.Endpoint.Binding.CreateBindingElements();  
TransportBindingElement transportBindingElement = bindingElements.Find<TransportBindingElement>();  
if (transportBindingElement is UdpTransportBindingElement)  
{  
    ImportAddress(context);  
}  
```  
  
### <a name="adding-policy-support"></a>Adicionando suporte à política  
 O elemento de associação personalizada pode exportar declarações de política na associação WSDL para um ponto de extremidade de serviço para expressar os recursos desse elemento de associação. O exemplo de código a seguir é retirado de [transporte: UDP](../../../../docs/framework/wcf/samples/transport-udp.md) exemplo.  
  
#### <a name="policy-export"></a>Exportação de política  
 O `UdpTransportBindingElement` tipo implementa <xref:System.ServiceModel.Description.IPolicyExportExtension?displayProperty=nameWithType> para adicionar suporte para exportação de política. Como resultado, <xref:System.ServiceModel.Description.MetadataExporter?displayProperty=nameWithType> inclui `UdpTransportBindingElement` na geração de política para qualquer ligação que inclui-lo.  
  
 No <xref:System.ServiceModel.Description.IPolicyExportExtension.ExportPolicy%2A?displayProperty=nameWithType>, adicionar uma asserção para UDP e outra asserção se o canal estiver no modo de multicast. Isso ocorre porque afeta o modo de multicast, como a pilha de comunicação é construída e, portanto, deve ser coordenada entre os dois lados.  
  
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
  
 Porque os elementos de associação de transporte personalizado serão responsáveis por lidar endereçamento, o <xref:System.ServiceModel.Description.IPolicyExportExtension?displayProperty=nameWithType> implementação no `UdpTransportBindingElement` também deve tratar exportando as declarações de política WS-Addressing, com apropriada para indicar a versão do WS-Addressing que está sendo usado.  
  
```csharp  
AddWSAddressingAssertion(context, encodingBindingElement.MessageVersion.Addressing);  
```  
  
#### <a name="policy-import"></a>Importação da política  
 Para estender o sistema de importação de política, adicione a seguinte configuração ao arquivo de configuração para Svcutil.exe conforme mostrado no arquivo de svcutil:  
  
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
  
 Em seguida, implementamos <xref:System.ServiceModel.Description.IPolicyImportExtension?displayProperty=nameWithType> de nossa classe registrada (`UdpBindingElementImporter`). No <xref:System.ServiceModel.Description.IPolicyImportExtension.ImportPolicy%2A?displayProperty=nameWithType>, examine as declarações no namespace apropriado e processar os para o transporte de gerar e verificar se ele é multicast. Além disso, remova as declarações que manipula o importador da lista de asserções de associação. Novamente, ao executar Svcutil.exe, há duas opções para a integração:  
  
1. Ponto Svcutil.exe ao nosso arquivo de configuração usando o /SvcutilConfig:\<arquivo >.  
  
2. Adicione a seção de configuração para svcutil no mesmo diretório que Svcutil.exe.  
  
### <a name="adding-a-custom-standard-binding-importer"></a>Adicionando uma ligação importador de padrão personalizado  
 Svcutil.exe e o <xref:System.ServiceModel.Description.WsdlImporter?displayProperty=nameWithType> tipo, por padrão, reconhecer e importar associações fornecidas pelo sistema. Caso contrário, a associação obtém importada como um <xref:System.ServiceModel.Channels.CustomBinding?displayProperty=nameWithType> instância. Para habilitar o Svcutil.exe e o <xref:System.ServiceModel.Description.WsdlImporter> para importar o `SampleProfileUdpBinding` o `UdpBindingElementImporter` também atua como um importador de associação padrão personalizada.  
  
 Um importador de associação padrão personalizada implementa o `ImportEndpoint` método na <xref:System.ServiceModel.Description.IWsdlImportExtension?displayProperty=nameWithType> interface para examinar o <xref:System.ServiceModel.Channels.CustomBinding?displayProperty=nameWithType> importada dos metadados para ver se ele pode ter sido gerado por associação padrão específica de instância.  
  
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
  
 Em geral, implementar um importador de associação padrão personalizado envolve verificar as propriedades dos elementos de associação importados para verificar que somente as propriedades que poderiam ter sido definidas por associação padrão foram alterados e todas as outras propriedades são seus valores padrão. Uma estratégia básica para implementar um importador de associação padrão é criar uma instância de associação padrão, propagar as propriedades de elementos de associação para a instância de associação padrão que dá suporte à associação padrão e comparar a associação elementos de associação padrão com os elementos de associação importados.
