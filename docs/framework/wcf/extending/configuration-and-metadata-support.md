---
title: Configuração e suporte de metadados
ms.date: 03/30/2017
ms.assetid: 27c240cb-8cab-472c-87f8-c864f4978758
ms.openlocfilehash: fb4e1cc51b827f083e580362f57df27ced770179
ms.sourcegitcommit: 59e36e65ac81cdd094a5a84617625b2a0ff3506e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/27/2020
ms.locfileid: "80345292"
---
# <a name="configuration-and-metadata-support"></a>Configuração e suporte de metadados
Este tópico descreve como habilitar a configuração e o suporte a metadados para vinculações e elementos de vinculação.  
  
## <a name="overview-of-configuration-and-metadata"></a>Visão geral da configuração e metadados  
 Este tópico discute as seguintes tarefas, que são itens opcionais 1, 2 e 4 na lista de [tarefas Canais em Desenvolvimento.](developing-channels.md)  
  
- Habilitando o suporte a arquivos de configuração para um elemento de vinculação.  
  
- Habilitando o suporte a arquivos de configuração para uma vinculação.  
  
- Exportação de WSDL e afirmações de políticas para um elemento vinculante.  
  
- Identificar as afirmações de WSDL e de política para inserir e configurar seu elemento de vinculação ou vinculação.  
  
 Para obter informações sobre a criação de vinculações e elementos de vinculação definidos pelo usuário, consulte [Criando vinculações definidas pelo usuário](creating-user-defined-bindings.md) e criando um Elemento de [Vinculação,](creating-a-bindingelement.md)respectivamente.  
  
## <a name="adding-configuration-support"></a>Adicionando suporte à configuração  
 Para habilitar o suporte a arquivos de configuração <xref:System.ServiceModel.Configuration.BindingElementExtensionElement?displayProperty=nameWithType>para um canal, você deve <xref:System.ServiceModel.Configuration.StandardBindingElement?displayProperty=nameWithType> <xref:System.ServiceModel.Configuration.StandardBindingCollectionElement%602?displayProperty=nameWithType>implementar duas seções de configuração, que permitem o suporte à configuração para elementos de vinculação e o e , que permitem o suporte à configuração para vinculações.  
  
 Uma maneira mais fácil de fazer isso é usar a ferramenta de amostra [ConfigurationCodeGenerator](../samples/configurationcodegenerator.md) para gerar código de configuração para suas vinculações e elementos de vinculação.  
  
### <a name="extending-bindingelementextensionelement"></a>Estendendo bindingelementextensionelement  
 O seguinte código de exemplo é extraído da amostra [Transporte: UDP.](../samples/transport-udp.md) O `UdpTransportElement` é <xref:System.ServiceModel.Configuration.BindingElementExtensionElement> um `UdpTransportBindingElement` que expõe ao sistema de configuração. Com algumas substituições básicas, a amostra define o nome da seção de configuração, o tipo do elemento de ligação e como criar o elemento de ligação. Os usuários podem então registrar a seção de extensão em um arquivo de configuração da seguinte forma.  
  
```xml  
<configuration>  
  <system.serviceModel>  
    <extensions>  
      <bindingElementExtensions>  
      <add name="udpTransport" type="Microsoft.ServiceModel.Samples.UdpTransportElement, UdpTransport" />  
      </bindingElementExtensions>  
    </extensions>  
  </system.serviceModel>  
</configuration>  
```  
  
 A extensão pode ser referenciada a partir de vinculações personalizadas para usar UDP como transporte.  
  
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
  
### <a name="adding-configuration-for-a-binding"></a>Adicionando configuração para uma vinculação  
 A `SampleProfileUdpBindingCollectionElement` seção <xref:System.ServiceModel.Configuration.StandardBindingCollectionElement%602> é `SampleProfileUdpBinding` uma que se expõe ao sistema de configuração. A maior parte da implementação `SampleProfileUdpBindingConfigurationElement`é delegada <xref:System.ServiceModel.Configuration.StandardBindingElement>ao , que deriva de . O `SampleProfileUdpBindingConfigurationElement` tem propriedades que correspondem às propriedades em `SampleProfileUdpBinding` `ConfigurationElement` , e funções para mapear a partir da vinculação. Finalmente, `OnApplyConfiguration` o método é substituído `SampleProfileUdpBinding`no , como mostrado no código de amostra a seguir.  
  
```csharp
protected override void OnApplyConfiguration(string configurationName)  
{  
            if (binding == null)  
                throw new ArgumentNullException("binding");  
  
            if (binding.GetType() != typeof(SampleProfileUdpBinding))  
            {  
                var expectedType = typeof(SampleProfileUdpBinding).AssemblyQualifiedName;
                var typePassedIn = binding.GetType().AssemblyQualifiedName;
                throw new ArgumentException($"Invalid type for binding. Expected type: {expectedType}. Type passed in: {typePassedIn}.");  
            }  
            SampleProfileUdpBinding udpBinding = (SampleProfileUdpBinding)binding;  
  
            udpBinding.OrderedSession = this.OrderedSession;  
            udpBinding.ReliableSessionEnabled = this.ReliableSessionEnabled;  
            udpBinding.SessionInactivityTimeout = this.SessionInactivityTimeout;  
            if (this.ClientBaseAddress != null)  
                   udpBinding.ClientBaseAddress = ClientBaseAddress;  
}  
```  
  
 Para registrar este manipulador com o sistema de configuração, adicione a seção a seguir ao arquivo de configuração relevante.  
  
```xml  
<configuration>  
  <configSections>  
     <sectionGroup name="system.serviceModel">  
         <sectionGroup name="bindings">  
                 <section name="sampleProfileUdpBinding" type="Microsoft.ServiceModel.Samples.SampleProfileUdpBindingCollectionElement, UdpTransport" />  
         </sectionGroup>  
     </sectionGroup>  
  </configSections>  
</configuration>  
```  
  
 Em seguida, ele pode [ \<](../../configure-apps/file-schema/wcf/system-servicemodel.md) ser referenciado a partir da seção de configuração system.serviceModel>.  
  
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
  
## <a name="adding-metadata-support-for-a-binding-element"></a>Adicionando suporte a metadados para um elemento de vinculação  
 Para integrar um canal no sistema de metadados, ele deve apoiar tanto a importação quanto a exportação de políticas. Isso permite que ferramentas como [ServiceModel Metadata Utility Tool (Svcutil.exe)](../servicemodel-metadata-utility-tool-svcutil-exe.md) gerem clientes do elemento de vinculação.  
  
### <a name="adding-wsdl-support"></a>Adicionando suporte ao WSDL  
 O elemento de vinculação de transporte em uma vinculação é responsável pela exportação e importação de informações de endereçamento em metadados. Ao usar uma vinculação SOAP, o elemento de ligação de transporte também deve exportar um URI de transporte correto em metadados. O seguinte código de exemplo é extraído da amostra [Transporte: UDP.](../samples/transport-udp.md)  
  
#### <a name="wsdl-export"></a>Exportação wsdl  
 Para exportar informações de `UdpTransportBindingElement` endereçamento, o implementa a <xref:System.ServiceModel.Description.IWsdlExportExtension?displayProperty=nameWithType> interface. O <xref:System.ServiceModel.Description.IWsdlExportExtension.ExportEndpoint%2A?displayProperty=nameWithType> método adiciona as informações corretas de endereçamento à porta WSDL.  
  
```csharp  
if (context.WsdlPort != null)  
{  
    AddAddressToWsdlPort(context.WsdlPort, context.Endpoint.Address, encodingBindingElement.MessageVersion.Addressing);  
}  
```  
  
 A `UdpTransportBindingElement` implementação <xref:System.ServiceModel.Description.IWsdlExportExtension.ExportEndpoint%2A> do método também exporta um URI de transporte quando o ponto final usa uma vinculação SOAP:  
  
```csharp  
WsdlNS.SoapBinding soapBinding = GetSoapBinding(context, exporter);  
if (soapBinding != null)  
{  
    soapBinding.Transport = UdpPolicyStrings.UdpNamespace;  
}  
```  
  
#### <a name="wsdl-import"></a>Importação de WSDL  
 Para estender o sistema de importação WSDL para lidar com a importação dos endereços, adicione a seguinte configuração ao arquivo de configuração para Svcutil.exe, conforme mostrado no arquivo Svcutil.exe.config:  
  
```xml  
<configuration>  
  <system.serviceModel>  
    <client>  
      <metadata>  
        <wsdlImporters>  
          <extension type=" Microsoft.ServiceModel.Samples.UdpBindingElementImporter, UdpTransport" />  
        </wsdlImporters>  
      </metadata>  
    </client>  
  </system.serviceModel>  
</configuration>  
```  
  
 Ao executar o Svcutil.exe, existem duas opções para obter Svcutil.exe para carregar as extensões de importação WSDL:  
  
1. Point Svcutil.exe para o arquivo de configuração usando\<o /SvcutilConfig: arquivo>.  
  
2. Adicione a seção de configuração ao Svcutil.exe.config no mesmo diretório que Svcutil.exe.  
  
 O `UdpBindingElementImporter` tipo implementa a <xref:System.ServiceModel.Description.IWsdlImportExtension?displayProperty=nameWithType> interface. O `ImportEndpoint` método importa o endereço da porta WSDL:  
  
```csharp  
BindingElementCollection bindingElements = context.Endpoint.Binding.CreateBindingElements();  
TransportBindingElement transportBindingElement = bindingElements.Find<TransportBindingElement>();  
if (transportBindingElement is UdpTransportBindingElement)  
{  
    ImportAddress(context);  
}  
```  
  
### <a name="adding-policy-support"></a>Adicionando suporte a políticas  
 O elemento de vinculação personalizado pode exportar afirmações de diretiva na vinculação WSDL para um ponto final de serviço para expressar as capacidades desse elemento de vinculação. O seguinte código de exemplo é extraído da amostra [Transporte: UDP.](../samples/transport-udp.md)  
  
#### <a name="policy-export"></a>Exportação de políticas  
 O `UdpTransportBindingElement` tipo <xref:System.ServiceModel.Description.IPolicyExportExtension?displayProperty=nameWithType> implementa para adicionar suporte à política de exportação. Como resultado, <xref:System.ServiceModel.Description.MetadataExporter?displayProperty=nameWithType> inclui `UdpTransportBindingElement` na geração de políticas para qualquer vinculação que a inclua.  
  
 Em <xref:System.ServiceModel.Description.IPolicyExportExtension.ExportPolicy%2A?displayProperty=nameWithType>, adicione uma afirmação para UDP e outra afirmação se o canal estiver no modo multicast. Isso porque o modo multicast afeta a forma como a pilha de comunicação é construída e, portanto, deve ser coordenada entre ambos os lados.  
  
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
  
 Como os elementos de vinculação de <xref:System.ServiceModel.Description.IPolicyExportExtension?displayProperty=nameWithType> transporte personalizados são responsáveis pelo manuseio da abordagem, a implementação no também `UdpTransportBindingElement` deve lidar com a exportação das afirmações apropriadas da política ws-addressing para indicar a versão do WS-Addressing a ser usado.  
  
```csharp  
AddWSAddressingAssertion(context, encodingBindingElement.MessageVersion.Addressing);  
```  
  
#### <a name="policy-import"></a>Importação de políticas  
 Para estender o sistema de importação de políticas, adicione a seguinte configuração ao arquivo de configuração de Svcutil.exe, conforme mostrado no arquivo Svcutil.exe.config:  
  
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
  
 Então implementamos <xref:System.ServiceModel.Description.IPolicyImportExtension?displayProperty=nameWithType> a partir`UdpBindingElementImporter`de nossa classe registrada ( ). Em <xref:System.ServiceModel.Description.IPolicyImportExtension.ImportPolicy%2A?displayProperty=nameWithType>, examine as afirmações no namespace apropriado e processe as para gerar o transporte e verificar se ele é multicast. Além disso, remova as afirmações que o importador lida da lista de afirmações vinculantes. Novamente, ao executar o Svcutil.exe, há duas opções de integração:  
  
1. Point Svcutil.exe para o nosso arquivo de configuração\<usando o /SvcutilConfig: arquivo>.  
  
2. Adicione a seção de configuração ao Svcutil.exe.config no mesmo diretório que Svcutil.exe.  
  
### <a name="adding-a-custom-standard-binding-importer"></a>Adicionando um importador de vinculação padrão personalizado  
 Svcutil.exe e <xref:System.ServiceModel.Description.WsdlImporter?displayProperty=nameWithType> o tipo, por padrão, reconhecem e importam vinculações fornecidas pelo sistema. Caso contrário, a vinculação <xref:System.ServiceModel.Channels.CustomBinding?displayProperty=nameWithType> é importada como instância. Para habilitar svcutil.exe e `SampleProfileUdpBinding` `UdpBindingElementImporter` <xref:System.ServiceModel.Description.WsdlImporter> importar o também atua como um importador de vinculação padrão personalizado.  
  
 Um importador de vinculação `ImportEndpoint` padrão <xref:System.ServiceModel.Description.IWsdlImportExtension?displayProperty=nameWithType> personalizado implementa <xref:System.ServiceModel.Channels.CustomBinding?displayProperty=nameWithType> o método na interface para examinar a instância importada de metadados para ver se ele poderia ter sido gerado por uma vinculação padrão específica.  
  
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
  
 Geralmente, a implementação de um importador de vinculação padrão personalizado envolve verificar as propriedades dos elementos de ligação importados para verificar se apenas as propriedades que poderiam ter sido definidas pela vinculação padrão foram alteradas e todas as outras propriedades são seus padrões. Uma estratégia básica para implementar um importador de vinculação padrão é criar uma instância da vinculação padrão, propagar as propriedades dos elementos vinculantes à instância de vinculação padrão que a vinculação padrão suporta, e comparar a vinculação elementos da vinculação padrão com os elementos de ligação importados.
