---
title: Configuração e suporte de metadados
ms.date: 03/30/2017
ms.assetid: 27c240cb-8cab-472c-87f8-c864f4978758
ms.openlocfilehash: 0ec8c3286037e7adbe6f5efb73e846a30b9d48d3
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79185659"
---
# <a name="configuration-and-metadata-support"></a><span data-ttu-id="c2145-102">Configuração e suporte de metadados</span><span class="sxs-lookup"><span data-stu-id="c2145-102">Configuration and Metadata Support</span></span>
<span data-ttu-id="c2145-103">Este tópico descreve como habilitar a configuração e o suporte a metadados para vinculações e elementos de vinculação.</span><span class="sxs-lookup"><span data-stu-id="c2145-103">This topic describes how to enable configuration and metadata support for bindings and binding elements.</span></span>  
  
## <a name="overview-of-configuration-and-metadata"></a><span data-ttu-id="c2145-104">Visão geral da configuração e metadados</span><span class="sxs-lookup"><span data-stu-id="c2145-104">Overview of Configuration and Metadata</span></span>  
 <span data-ttu-id="c2145-105">Este tópico discute as seguintes tarefas, que são itens opcionais 1, 2 e 4 na lista de [tarefas Canais em Desenvolvimento.](developing-channels.md)</span><span class="sxs-lookup"><span data-stu-id="c2145-105">This topic discusses the following tasks, which are optional items 1, 2, and 4 in the [Developing Channels](developing-channels.md) task list.</span></span>  
  
- <span data-ttu-id="c2145-106">Habilitando o suporte a arquivos de configuração para um elemento de vinculação.</span><span class="sxs-lookup"><span data-stu-id="c2145-106">Enabling configuration file support for a binding element.</span></span>  
  
- <span data-ttu-id="c2145-107">Habilitando o suporte a arquivos de configuração para uma vinculação.</span><span class="sxs-lookup"><span data-stu-id="c2145-107">Enabling configuration file support for a binding.</span></span>  
  
- <span data-ttu-id="c2145-108">Exportação de WSDL e afirmações de políticas para um elemento vinculante.</span><span class="sxs-lookup"><span data-stu-id="c2145-108">Exporting WSDL and policy assertions for a binding element.</span></span>  
  
- <span data-ttu-id="c2145-109">Identificar as afirmações de WSDL e de política para inserir e configurar seu elemento de vinculação ou vinculação.</span><span class="sxs-lookup"><span data-stu-id="c2145-109">Identifying WSDL and policy assertions to insert and configure your binding or binding element.</span></span>  
  
 <span data-ttu-id="c2145-110">Para obter informações sobre a criação de vinculações e elementos de vinculação definidos pelo usuário, consulte [Criando vinculações definidas pelo usuário](creating-user-defined-bindings.md) e criando um Elemento de [Vinculação,](creating-a-bindingelement.md)respectivamente.</span><span class="sxs-lookup"><span data-stu-id="c2145-110">For information about creating user-defined bindings and binding elements, see [Creating User-Defined Bindings](creating-user-defined-bindings.md) and [Creating a BindingElement](creating-a-bindingelement.md), respectively.</span></span>  
  
## <a name="adding-configuration-support"></a><span data-ttu-id="c2145-111">Adicionando suporte à configuração</span><span class="sxs-lookup"><span data-stu-id="c2145-111">Adding Configuration Support</span></span>  
 <span data-ttu-id="c2145-112">Para habilitar o suporte a arquivos de configuração <xref:System.ServiceModel.Configuration.BindingElementExtensionElement?displayProperty=nameWithType>para um canal, você deve <xref:System.ServiceModel.Configuration.StandardBindingElement?displayProperty=nameWithType> <xref:System.ServiceModel.Configuration.StandardBindingCollectionElement%602?displayProperty=nameWithType>implementar duas seções de configuração, que permitem o suporte à configuração para elementos de vinculação e o e , que permitem o suporte à configuração para vinculações.</span><span class="sxs-lookup"><span data-stu-id="c2145-112">To enable configuration file support for a channel, you must implement two configuration sections, <xref:System.ServiceModel.Configuration.BindingElementExtensionElement?displayProperty=nameWithType>, which enables configuration support for binding elements, and the <xref:System.ServiceModel.Configuration.StandardBindingElement?displayProperty=nameWithType> and <xref:System.ServiceModel.Configuration.StandardBindingCollectionElement%602?displayProperty=nameWithType>, which enable configuration support for bindings.</span></span>  
  
 <span data-ttu-id="c2145-113">Uma maneira mais fácil de fazer isso é usar a ferramenta de amostra [ConfigurationCodeGenerator](../samples/configurationcodegenerator.md) para gerar código de configuração para suas vinculações e elementos de vinculação.</span><span class="sxs-lookup"><span data-stu-id="c2145-113">An easier way to do this is to use the [ConfigurationCodeGenerator](../samples/configurationcodegenerator.md) sample tool to generate configuration code for your bindings and binding elements.</span></span>  
  
### <a name="extending-bindingelementextensionelement"></a><span data-ttu-id="c2145-114">Estendendo bindingelementextensionelement</span><span class="sxs-lookup"><span data-stu-id="c2145-114">Extending BindingElementExtensionElement</span></span>  
 <span data-ttu-id="c2145-115">O seguinte código de exemplo é extraído da amostra [Transporte: UDP.](../samples/transport-udp.md)</span><span class="sxs-lookup"><span data-stu-id="c2145-115">The following example code is taken from the [Transport: UDP](../samples/transport-udp.md) sample.</span></span> <span data-ttu-id="c2145-116">O `UdpTransportElement` é <xref:System.ServiceModel.Configuration.BindingElementExtensionElement> um `UdpTransportBindingElement` que expõe ao sistema de configuração.</span><span class="sxs-lookup"><span data-stu-id="c2145-116">The `UdpTransportElement` is a <xref:System.ServiceModel.Configuration.BindingElementExtensionElement> that exposes `UdpTransportBindingElement` to the configuration system.</span></span> <span data-ttu-id="c2145-117">Com algumas substituições básicas, a amostra define o nome da seção de configuração, o tipo do elemento de ligação e como criar o elemento de ligação.</span><span class="sxs-lookup"><span data-stu-id="c2145-117">With a few basic overrides, the sample defines the configuration section name, the type of the binding element and how to create the binding element.</span></span> <span data-ttu-id="c2145-118">Os usuários podem então registrar a seção de extensão em um arquivo de configuração da seguinte forma.</span><span class="sxs-lookup"><span data-stu-id="c2145-118">Users can then register the extension section in a configuration file as follows.</span></span>  
  
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
  
 <span data-ttu-id="c2145-119">A extensão pode ser referenciada a partir de vinculações personalizadas para usar UDP como transporte.</span><span class="sxs-lookup"><span data-stu-id="c2145-119">The extension can be referenced from custom bindings to use UDP as the transport.</span></span>  
  
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
  
### <a name="adding-configuration-for-a-binding"></a><span data-ttu-id="c2145-120">Adicionando configuração para uma vinculação</span><span class="sxs-lookup"><span data-stu-id="c2145-120">Adding Configuration for a Binding</span></span>  
 <span data-ttu-id="c2145-121">A `SampleProfileUdpBindingCollectionElement` seção <xref:System.ServiceModel.Configuration.StandardBindingCollectionElement%602> é `SampleProfileUdpBinding` uma que se expõe ao sistema de configuração.</span><span class="sxs-lookup"><span data-stu-id="c2145-121">The section `SampleProfileUdpBindingCollectionElement` is a <xref:System.ServiceModel.Configuration.StandardBindingCollectionElement%602> that exposes `SampleProfileUdpBinding` to the configuration system.</span></span> <span data-ttu-id="c2145-122">A maior parte da implementação `SampleProfileUdpBindingConfigurationElement`é delegada <xref:System.ServiceModel.Configuration.StandardBindingElement>ao , que deriva de .</span><span class="sxs-lookup"><span data-stu-id="c2145-122">The bulk of the implementation is delegated to the `SampleProfileUdpBindingConfigurationElement`, which derives from <xref:System.ServiceModel.Configuration.StandardBindingElement>.</span></span> <span data-ttu-id="c2145-123">O `SampleProfileUdpBindingConfigurationElement` tem propriedades que correspondem às propriedades em `SampleProfileUdpBinding` `ConfigurationElement` , e funções para mapear a partir da vinculação.</span><span class="sxs-lookup"><span data-stu-id="c2145-123">The `SampleProfileUdpBindingConfigurationElement` has properties that correspond to the properties on `SampleProfileUdpBinding`, and functions to map from the `ConfigurationElement` binding.</span></span> <span data-ttu-id="c2145-124">Finalmente, `OnApplyConfiguration` o método é substituído `SampleProfileUdpBinding`no , como mostrado no código de amostra a seguir.</span><span class="sxs-lookup"><span data-stu-id="c2145-124">Finally, the `OnApplyConfiguration` method is overridden in the `SampleProfileUdpBinding`, as shown in the following sample code.</span></span>  
  
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
  
 <span data-ttu-id="c2145-125">Para registrar este manipulador com o sistema de configuração, adicione a seção a seguir ao arquivo de configuração relevante.</span><span class="sxs-lookup"><span data-stu-id="c2145-125">To register this handler with the configuration system, add the following section to the relevant configuration file.</span></span>  
  
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
  
 <span data-ttu-id="c2145-126">Em seguida, ele pode [ \<](../../configure-apps/file-schema/wcf/system-servicemodel.md) ser referenciado a partir da seção de configuração system.serviceModel>.</span><span class="sxs-lookup"><span data-stu-id="c2145-126">It can then be referenced from the [\<system.serviceModel>](../../configure-apps/file-schema/wcf/system-servicemodel.md) configuration section.</span></span>  
  
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
  
## <a name="adding-metadata-support-for-a-binding-element"></a><span data-ttu-id="c2145-127">Adicionando suporte a metadados para um elemento de vinculação</span><span class="sxs-lookup"><span data-stu-id="c2145-127">Adding Metadata Support for a Binding Element</span></span>  
 <span data-ttu-id="c2145-128">Para integrar um canal no sistema de metadados, ele deve apoiar tanto a importação quanto a exportação de políticas.</span><span class="sxs-lookup"><span data-stu-id="c2145-128">To integrate a channel into the metadata system, it must support both the import and export of policy.</span></span> <span data-ttu-id="c2145-129">Isso permite que ferramentas como [ServiceModel Metadata Utility Tool (Svcutil.exe)](../servicemodel-metadata-utility-tool-svcutil-exe.md) gerem clientes do elemento de vinculação.</span><span class="sxs-lookup"><span data-stu-id="c2145-129">This allows tools such as [ServiceModel Metadata Utility Tool (Svcutil.exe)](../servicemodel-metadata-utility-tool-svcutil-exe.md) to generate clients of the binding element.</span></span>  
  
### <a name="adding-wsdl-support"></a><span data-ttu-id="c2145-130">Adicionando suporte ao WSDL</span><span class="sxs-lookup"><span data-stu-id="c2145-130">Adding WSDL Support</span></span>  
 <span data-ttu-id="c2145-131">O elemento de vinculação de transporte em uma vinculação é responsável pela exportação e importação de informações de endereçamento em metadados.</span><span class="sxs-lookup"><span data-stu-id="c2145-131">The transport binding element in a binding is responsible for exporting and importing addressing information in metadata.</span></span> <span data-ttu-id="c2145-132">Ao usar uma vinculação SOAP, o elemento de ligação de transporte também deve exportar um URI de transporte correto em metadados.</span><span class="sxs-lookup"><span data-stu-id="c2145-132">When using a SOAP binding, the transport binding element should also export a correct transport URI in metadata.</span></span> <span data-ttu-id="c2145-133">O seguinte código de exemplo é extraído da amostra [Transporte: UDP.](../samples/transport-udp.md)</span><span class="sxs-lookup"><span data-stu-id="c2145-133">The following example code is taken from the [Transport: UDP](../samples/transport-udp.md) sample.</span></span>  
  
#### <a name="wsdl-export"></a><span data-ttu-id="c2145-134">Exportação wsdl</span><span class="sxs-lookup"><span data-stu-id="c2145-134">WSDL Export</span></span>  
 <span data-ttu-id="c2145-135">Para exportar informações de `UdpTransportBindingElement` endereçamento, o implementa a <xref:System.ServiceModel.Description.IWsdlExportExtension?displayProperty=nameWithType> interface.</span><span class="sxs-lookup"><span data-stu-id="c2145-135">To export addressing information, the `UdpTransportBindingElement` implements the <xref:System.ServiceModel.Description.IWsdlExportExtension?displayProperty=nameWithType> interface.</span></span> <span data-ttu-id="c2145-136">O <xref:System.ServiceModel.Description.IWsdlExportExtension.ExportEndpoint%2A?displayProperty=nameWithType> método adiciona as informações corretas de endereçamento à porta WSDL.</span><span class="sxs-lookup"><span data-stu-id="c2145-136">The <xref:System.ServiceModel.Description.IWsdlExportExtension.ExportEndpoint%2A?displayProperty=nameWithType> method adds the correct addressing information to the WSDL port.</span></span>  
  
```csharp  
if (context.WsdlPort != null)  
{  
    AddAddressToWsdlPort(context.WsdlPort, context.Endpoint.Address, encodingBindingElement.MessageVersion.Addressing);  
}  
```  
  
 <span data-ttu-id="c2145-137">A `UdpTransportBindingElement` implementação <xref:System.ServiceModel.Description.IWsdlExportExtension.ExportEndpoint%2A> do método também exporta um URI de transporte quando o ponto final usa uma vinculação SOAP:</span><span class="sxs-lookup"><span data-stu-id="c2145-137">The `UdpTransportBindingElement` implementation of the <xref:System.ServiceModel.Description.IWsdlExportExtension.ExportEndpoint%2A> method also exports a transport URI when the endpoint uses a SOAP binding:</span></span>  
  
```csharp  
WsdlNS.SoapBinding soapBinding = GetSoapBinding(context, exporter);  
if (soapBinding != null)  
{  
    soapBinding.Transport = UdpPolicyStrings.UdpNamespace;  
}  
```  
  
#### <a name="wsdl-import"></a><span data-ttu-id="c2145-138">Importação de WSDL</span><span class="sxs-lookup"><span data-stu-id="c2145-138">WSDL Import</span></span>  
 <span data-ttu-id="c2145-139">Para estender o sistema de importação WSDL para lidar com a importação dos endereços, adicione a seguinte configuração ao arquivo de configuração para Svcutil.exe, conforme mostrado no arquivo Svcutil.exe.config:</span><span class="sxs-lookup"><span data-stu-id="c2145-139">To extend the WSDL import system to handle importing the addresses, add the following configuration to the configuration file for Svcutil.exe as shown in the Svcutil.exe.config file:</span></span>  
  
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
  
 <span data-ttu-id="c2145-140">Ao executar o Svcutil.exe, existem duas opções para obter Svcutil.exe para carregar as extensões de importação WSDL:</span><span class="sxs-lookup"><span data-stu-id="c2145-140">When running Svcutil.exe, there are two options for getting Svcutil.exe to load the WSDL import extensions:</span></span>  
  
1. <span data-ttu-id="c2145-141">Point Svcutil.exe para o arquivo de configuração usando\<o /SvcutilConfig: arquivo>.</span><span class="sxs-lookup"><span data-stu-id="c2145-141">Point Svcutil.exe to the configuration file using the /SvcutilConfig:\<file>.</span></span>  
  
2. <span data-ttu-id="c2145-142">Adicione a seção de configuração ao Svcutil.exe.config no mesmo diretório que Svcutil.exe.</span><span class="sxs-lookup"><span data-stu-id="c2145-142">Add the configuration section to Svcutil.exe.config in the same directory as Svcutil.exe.</span></span>  
  
 <span data-ttu-id="c2145-143">O `UdpBindingElementImporter` tipo implementa a <xref:System.ServiceModel.Description.IWsdlImportExtension?displayProperty=nameWithType> interface.</span><span class="sxs-lookup"><span data-stu-id="c2145-143">The `UdpBindingElementImporter` type implements the <xref:System.ServiceModel.Description.IWsdlImportExtension?displayProperty=nameWithType> interface.</span></span> <span data-ttu-id="c2145-144">O `ImportEndpoint` método importa o endereço da porta WSDL:</span><span class="sxs-lookup"><span data-stu-id="c2145-144">The `ImportEndpoint` method imports the address from the WSDL port:</span></span>  
  
```csharp  
BindingElementCollection bindingElements = context.Endpoint.Binding.CreateBindingElements();  
TransportBindingElement transportBindingElement = bindingElements.Find<TransportBindingElement>();  
if (transportBindingElement is UdpTransportBindingElement)  
{  
    ImportAddress(context);  
}  
```  
  
### <a name="adding-policy-support"></a><span data-ttu-id="c2145-145">Adicionando suporte a políticas</span><span class="sxs-lookup"><span data-stu-id="c2145-145">Adding Policy Support</span></span>  
 <span data-ttu-id="c2145-146">O elemento de vinculação personalizado pode exportar afirmações de diretiva na vinculação WSDL para um ponto final de serviço para expressar as capacidades desse elemento de vinculação.</span><span class="sxs-lookup"><span data-stu-id="c2145-146">The custom binding element can export policy assertions in the WSDL binding for a service endpoint to express the capabilities of that binding element.</span></span> <span data-ttu-id="c2145-147">O seguinte código de exemplo é extraído da amostra [Transporte: UDP.](../samples/transport-udp.md)</span><span class="sxs-lookup"><span data-stu-id="c2145-147">The following example code is taken from the [Transport: UDP](../samples/transport-udp.md) sample.</span></span>  
  
#### <a name="policy-export"></a><span data-ttu-id="c2145-148">Exportação de políticas</span><span class="sxs-lookup"><span data-stu-id="c2145-148">Policy Export</span></span>  
 <span data-ttu-id="c2145-149">O `UdpTransportBindingElement` tipo <xref:System.ServiceModel.Description.IPolicyExportExtension?displayProperty=nameWithType> implementa para adicionar suporte à política de exportação.</span><span class="sxs-lookup"><span data-stu-id="c2145-149">The `UdpTransportBindingElement` type implements <xref:System.ServiceModel.Description.IPolicyExportExtension?displayProperty=nameWithType> to add support for exporting policy.</span></span> <span data-ttu-id="c2145-150">Como resultado, <xref:System.ServiceModel.Description.MetadataExporter?displayProperty=nameWithType> inclui `UdpTransportBindingElement` na geração de políticas para qualquer vinculação que a inclua.</span><span class="sxs-lookup"><span data-stu-id="c2145-150">As a result, <xref:System.ServiceModel.Description.MetadataExporter?displayProperty=nameWithType> includes `UdpTransportBindingElement` in the generation of policy for any binding that includes it.</span></span>  
  
 <span data-ttu-id="c2145-151">Em <xref:System.ServiceModel.Description.IPolicyExportExtension.ExportPolicy%2A?displayProperty=nameWithType>, adicione uma afirmação para UDP e outra afirmação se o canal estiver no modo multicast.</span><span class="sxs-lookup"><span data-stu-id="c2145-151">In <xref:System.ServiceModel.Description.IPolicyExportExtension.ExportPolicy%2A?displayProperty=nameWithType>, add an assertion for UDP and another assertion if the channel is in multicast mode.</span></span> <span data-ttu-id="c2145-152">Isso porque o modo multicast afeta a forma como a pilha de comunicação é construída e, portanto, deve ser coordenada entre ambos os lados.</span><span class="sxs-lookup"><span data-stu-id="c2145-152">This is because multicast mode affects how the communication stack is constructed, and thus must be coordinated between both sides.</span></span>  
  
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
  
 <span data-ttu-id="c2145-153">Como os elementos de vinculação de <xref:System.ServiceModel.Description.IPolicyExportExtension?displayProperty=nameWithType> transporte personalizados são responsáveis pelo manuseio da abordagem, a implementação no também `UdpTransportBindingElement` deve lidar com a exportação das afirmações apropriadas da política ws-addressing para indicar a versão do WS-Addressing a ser usado.</span><span class="sxs-lookup"><span data-stu-id="c2145-153">Because custom transport binding elements are responsible for handling addressing, the <xref:System.ServiceModel.Description.IPolicyExportExtension?displayProperty=nameWithType> implementation on the `UdpTransportBindingElement` must also handle exporting the appropriate WS-Addressing policy assertions to indicate the version of WS-Addressing being used.</span></span>  
  
```csharp  
AddWSAddressingAssertion(context, encodingBindingElement.MessageVersion.Addressing);  
```  
  
#### <a name="policy-import"></a><span data-ttu-id="c2145-154">Importação de políticas</span><span class="sxs-lookup"><span data-stu-id="c2145-154">Policy Import</span></span>  
 <span data-ttu-id="c2145-155">Para estender o sistema de importação de políticas, adicione a seguinte configuração ao arquivo de configuração de Svcutil.exe, conforme mostrado no arquivo Svcutil.exe.config:</span><span class="sxs-lookup"><span data-stu-id="c2145-155">To extend the policy import system, add the following configuration to the configuration file for Svcutil.exe as shown in the Svcutil.exe.config file:</span></span>  
  
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
  
 <span data-ttu-id="c2145-156">Então implementamos <xref:System.ServiceModel.Description.IPolicyImportExtension?displayProperty=nameWithType> a partir`UdpBindingElementImporter`de nossa classe registrada ( ).</span><span class="sxs-lookup"><span data-stu-id="c2145-156">Then we implement <xref:System.ServiceModel.Description.IPolicyImportExtension?displayProperty=nameWithType> from our registered class (`UdpBindingElementImporter`).</span></span> <span data-ttu-id="c2145-157">Em <xref:System.ServiceModel.Description.IPolicyImportExtension.ImportPolicy%2A?displayProperty=nameWithType>, examine as afirmações no namespace apropriado e processe as para gerar o transporte e verificar se ele é multicast.</span><span class="sxs-lookup"><span data-stu-id="c2145-157">In <xref:System.ServiceModel.Description.IPolicyImportExtension.ImportPolicy%2A?displayProperty=nameWithType>, examine the assertions in the appropriate namespace and process the ones for generating the transport and checking if it is multicast.</span></span> <span data-ttu-id="c2145-158">Além disso, remova as afirmações que o importador lida da lista de afirmações vinculantes.</span><span class="sxs-lookup"><span data-stu-id="c2145-158">In addition, remove the assertions that the importer handles from the list of binding assertions.</span></span> <span data-ttu-id="c2145-159">Novamente, ao executar o Svcutil.exe, há duas opções de integração:</span><span class="sxs-lookup"><span data-stu-id="c2145-159">Again, when running Svcutil.exe, there are two options for integration:</span></span>  
  
1. <span data-ttu-id="c2145-160">Point Svcutil.exe para o nosso arquivo de configuração\<usando o /SvcutilConfig: arquivo>.</span><span class="sxs-lookup"><span data-stu-id="c2145-160">Point Svcutil.exe to our configuration file using the /SvcutilConfig:\<file>.</span></span>  
  
2. <span data-ttu-id="c2145-161">Adicione a seção de configuração ao Svcutil.exe.config no mesmo diretório que Svcutil.exe.</span><span class="sxs-lookup"><span data-stu-id="c2145-161">Add the configuration section to Svcutil.exe.config in the same directory as Svcutil.exe.</span></span>  
  
### <a name="adding-a-custom-standard-binding-importer"></a><span data-ttu-id="c2145-162">Adicionando um importador de vinculação padrão personalizado</span><span class="sxs-lookup"><span data-stu-id="c2145-162">Adding a Custom Standard Binding Importer</span></span>  
 <span data-ttu-id="c2145-163">Svcutil.exe e <xref:System.ServiceModel.Description.WsdlImporter?displayProperty=nameWithType> o tipo, por padrão, reconhecem e importam vinculações fornecidas pelo sistema.</span><span class="sxs-lookup"><span data-stu-id="c2145-163">Svcutil.exe and the <xref:System.ServiceModel.Description.WsdlImporter?displayProperty=nameWithType> type, by default, recognize and import system-provided bindings.</span></span> <span data-ttu-id="c2145-164">Caso contrário, a vinculação <xref:System.ServiceModel.Channels.CustomBinding?displayProperty=nameWithType> é importada como instância.</span><span class="sxs-lookup"><span data-stu-id="c2145-164">Otherwise, the binding gets imported as a <xref:System.ServiceModel.Channels.CustomBinding?displayProperty=nameWithType> instance.</span></span> <span data-ttu-id="c2145-165">Para habilitar svcutil.exe e `SampleProfileUdpBinding` `UdpBindingElementImporter` <xref:System.ServiceModel.Description.WsdlImporter> importar o também atua como um importador de vinculação padrão personalizado.</span><span class="sxs-lookup"><span data-stu-id="c2145-165">To enable Svcutil.exe and the <xref:System.ServiceModel.Description.WsdlImporter> to import the `SampleProfileUdpBinding` the `UdpBindingElementImporter` also acts as a custom standard binding importer.</span></span>  
  
 <span data-ttu-id="c2145-166">Um importador de vinculação `ImportEndpoint` padrão <xref:System.ServiceModel.Description.IWsdlImportExtension?displayProperty=nameWithType> personalizado implementa <xref:System.ServiceModel.Channels.CustomBinding?displayProperty=nameWithType> o método na interface para examinar a instância importada de metadados para ver se ele poderia ter sido gerado por uma vinculação padrão específica.</span><span class="sxs-lookup"><span data-stu-id="c2145-166">A custom standard binding importer implements the `ImportEndpoint` method on the <xref:System.ServiceModel.Description.IWsdlImportExtension?displayProperty=nameWithType> interface to examine the <xref:System.ServiceModel.Channels.CustomBinding?displayProperty=nameWithType> instance imported from metadata to see if it could have been generated by specific standard binding.</span></span>  
  
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
  
 <span data-ttu-id="c2145-167">Geralmente, a implementação de um importador de vinculação padrão personalizado envolve verificar as propriedades dos elementos de ligação importados para verificar se apenas as propriedades que poderiam ter sido definidas pela vinculação padrão foram alteradas e todas as outras propriedades são seus padrões.</span><span class="sxs-lookup"><span data-stu-id="c2145-167">Generally, implementing a custom standard binding importer involves checking the properties of the imported binding elements to verify that only properties that could have been set by the standard binding have changed and all other properties are their defaults.</span></span> <span data-ttu-id="c2145-168">Uma estratégia básica para implementar um importador de vinculação padrão é criar uma instância da vinculação padrão, propagar as propriedades dos elementos vinculantes à instância de vinculação padrão que a vinculação padrão suporta, e comparar a vinculação elementos da vinculação padrão com os elementos de ligação importados.</span><span class="sxs-lookup"><span data-stu-id="c2145-168">A basic strategy for implementing a standard binding importer is to create an instance of the standard binding, propagate the properties from the binding elements to the standard binding instance that the standard binding supports, and the compare the binding elements from the standard binding with the imported binding elements.</span></span>
