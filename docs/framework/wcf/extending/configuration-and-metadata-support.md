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
# <a name="configuration-and-metadata-support"></a><span data-ttu-id="d00d2-102">Configuração e suporte de metadados</span><span class="sxs-lookup"><span data-stu-id="d00d2-102">Configuration and Metadata Support</span></span>
<span data-ttu-id="d00d2-103">Este tópico descreve como habilitar o suporte de configuração e metadados para associações e elementos de associação.</span><span class="sxs-lookup"><span data-stu-id="d00d2-103">This topic describes how to enable configuration and metadata support for bindings and binding elements.</span></span>  
  
## <a name="overview-of-configuration-and-metadata"></a><span data-ttu-id="d00d2-104">Visão geral da configuração e dos metadados</span><span class="sxs-lookup"><span data-stu-id="d00d2-104">Overview of Configuration and Metadata</span></span>  
 <span data-ttu-id="d00d2-105">Este tópico discute as seguintes tarefas, que são itens opcionais 1, 2 e 4 na lista de tarefas [desenvolvimento de canais](developing-channels.md) .</span><span class="sxs-lookup"><span data-stu-id="d00d2-105">This topic discusses the following tasks, which are optional items 1, 2, and 4 in the [Developing Channels](developing-channels.md) task list.</span></span>  
  
- <span data-ttu-id="d00d2-106">Habilitando o suporte ao arquivo de configuração para um elemento de associação.</span><span class="sxs-lookup"><span data-stu-id="d00d2-106">Enabling configuration file support for a binding element.</span></span>  
  
- <span data-ttu-id="d00d2-107">Habilitando o suporte ao arquivo de configuração para uma associação.</span><span class="sxs-lookup"><span data-stu-id="d00d2-107">Enabling configuration file support for a binding.</span></span>  
  
- <span data-ttu-id="d00d2-108">Exportando declarações WSDL e de política para um elemento de associação.</span><span class="sxs-lookup"><span data-stu-id="d00d2-108">Exporting WSDL and policy assertions for a binding element.</span></span>  
  
- <span data-ttu-id="d00d2-109">Identificação de declarações WSDL e de política para inserir e configurar seu elemento Binding ou Binding.</span><span class="sxs-lookup"><span data-stu-id="d00d2-109">Identifying WSDL and policy assertions to insert and configure your binding or binding element.</span></span>  
  
 <span data-ttu-id="d00d2-110">Para obter informações sobre como criar associações definidas pelo usuário e elementos de associação, consulte [Criando associações definidas pelo usuário](creating-user-defined-bindings.md) e [criando um BindingElement](creating-a-bindingelement.md), respectivamente.</span><span class="sxs-lookup"><span data-stu-id="d00d2-110">For information about creating user-defined bindings and binding elements, see [Creating User-Defined Bindings](creating-user-defined-bindings.md) and [Creating a BindingElement](creating-a-bindingelement.md), respectively.</span></span>  
  
## <a name="adding-configuration-support"></a><span data-ttu-id="d00d2-111">Adicionando suporte à configuração</span><span class="sxs-lookup"><span data-stu-id="d00d2-111">Adding Configuration Support</span></span>  
 <span data-ttu-id="d00d2-112">Para habilitar o suporte ao arquivo de configuração para um canal, você deve implementar duas <xref:System.ServiceModel.Configuration.BindingElementExtensionElement?displayProperty=nameWithType>seções de configuração,, que habilitam o suporte à <xref:System.ServiceModel.Configuration.StandardBindingElement?displayProperty=nameWithType> configuração <xref:System.ServiceModel.Configuration.StandardBindingCollectionElement%602?displayProperty=nameWithType>para elementos de associação e o e, que habilitam o suporte à configuração para associações.</span><span class="sxs-lookup"><span data-stu-id="d00d2-112">To enable configuration file support for a channel, you must implement two configuration sections, <xref:System.ServiceModel.Configuration.BindingElementExtensionElement?displayProperty=nameWithType>, which enables configuration support for binding elements, and the <xref:System.ServiceModel.Configuration.StandardBindingElement?displayProperty=nameWithType> and <xref:System.ServiceModel.Configuration.StandardBindingCollectionElement%602?displayProperty=nameWithType>, which enable configuration support for bindings.</span></span>  
  
 <span data-ttu-id="d00d2-113">Uma maneira mais fácil de fazer isso é usar a ferramenta de exemplo [ConfigurationCodeGenerator](../samples/configurationcodegenerator.md) para gerar o código de configuração para suas associações e elementos de associação.</span><span class="sxs-lookup"><span data-stu-id="d00d2-113">An easier way to do this is to use the [ConfigurationCodeGenerator](../samples/configurationcodegenerator.md) sample tool to generate configuration code for your bindings and binding elements.</span></span>  
  
### <a name="extending-bindingelementextensionelement"></a><span data-ttu-id="d00d2-114">Estendendo BindingElementExtensionElement</span><span class="sxs-lookup"><span data-stu-id="d00d2-114">Extending BindingElementExtensionElement</span></span>  
 <span data-ttu-id="d00d2-115">O código de exemplo a seguir é obtido [do transporte: Exemplo](../samples/transport-udp.md) de UDP.</span><span class="sxs-lookup"><span data-stu-id="d00d2-115">The following example code is taken from the [Transport: UDP](../samples/transport-udp.md) sample.</span></span> <span data-ttu-id="d00d2-116">O `UdpTransportElement` é um <xref:System.ServiceModel.Configuration.BindingElementExtensionElement> que expõe `UdpTransportBindingElement` para o sistema de configuração.</span><span class="sxs-lookup"><span data-stu-id="d00d2-116">The `UdpTransportElement` is a <xref:System.ServiceModel.Configuration.BindingElementExtensionElement> that exposes `UdpTransportBindingElement` to the configuration system.</span></span> <span data-ttu-id="d00d2-117">Com algumas substituições básicas, o exemplo define o nome da seção de configuração, o tipo do elemento de associação e como criar o elemento de associação.</span><span class="sxs-lookup"><span data-stu-id="d00d2-117">With a few basic overrides, the sample defines the configuration section name, the type of the binding element and how to create the binding element.</span></span> <span data-ttu-id="d00d2-118">Os usuários podem então registrar a seção de extensão em um arquivo de configuração da seguinte maneira.</span><span class="sxs-lookup"><span data-stu-id="d00d2-118">Users can then register the extension section in a configuration file as follows.</span></span>  
  
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
  
 <span data-ttu-id="d00d2-119">A extensão pode ser referenciada de associações personalizadas para usar UDP como o transporte.</span><span class="sxs-lookup"><span data-stu-id="d00d2-119">The extension can be referenced from custom bindings to use UDP as the transport.</span></span>  
  
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
  
### <a name="adding-configuration-for-a-binding"></a><span data-ttu-id="d00d2-120">Adicionando configuração para uma associação</span><span class="sxs-lookup"><span data-stu-id="d00d2-120">Adding Configuration for a Binding</span></span>  
 <span data-ttu-id="d00d2-121">A seção `SampleProfileUdpBindingCollectionElement` é um <xref:System.ServiceModel.Configuration.StandardBindingCollectionElement%602> que expõe `SampleProfileUdpBinding` para o sistema de configuração.</span><span class="sxs-lookup"><span data-stu-id="d00d2-121">The section `SampleProfileUdpBindingCollectionElement` is a <xref:System.ServiceModel.Configuration.StandardBindingCollectionElement%602> that exposes `SampleProfileUdpBinding` to the configuration system.</span></span> <span data-ttu-id="d00d2-122">A maior parte da implementação é delegada para o `SampleProfileUdpBindingConfigurationElement`, que deriva de. <xref:System.ServiceModel.Configuration.StandardBindingElement></span><span class="sxs-lookup"><span data-stu-id="d00d2-122">The bulk of the implementation is delegated to the `SampleProfileUdpBindingConfigurationElement`, which derives from <xref:System.ServiceModel.Configuration.StandardBindingElement>.</span></span> <span data-ttu-id="d00d2-123">O `SampleProfileUdpBindingConfigurationElement` tem propriedades que correspondem às propriedades em `SampleProfileUdpBinding`e às `ConfigurationElement` funções a serem mapeadas da associação.</span><span class="sxs-lookup"><span data-stu-id="d00d2-123">The `SampleProfileUdpBindingConfigurationElement` has properties that correspond to the properties on `SampleProfileUdpBinding`, and functions to map from the `ConfigurationElement` binding.</span></span> <span data-ttu-id="d00d2-124">Por fim, `OnApplyConfiguration` o método é substituído `SampleProfileUdpBinding`no, conforme mostrado no código de exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="d00d2-124">Finally, the `OnApplyConfiguration` method is overridden in the `SampleProfileUdpBinding`, as shown in the following sample code.</span></span>  
  
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
  
 <span data-ttu-id="d00d2-125">Para registrar esse manipulador com o sistema de configuração, adicione a seção a seguir ao arquivo de configuração relevante.</span><span class="sxs-lookup"><span data-stu-id="d00d2-125">To register this handler with the configuration system, add the following section to the relevant configuration file.</span></span>  
  
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
  
 <span data-ttu-id="d00d2-126">Em seguida, ele pode ser referenciado na seção de [ \<configuração System. ServiceModel >](../../configure-apps/file-schema/wcf/system-servicemodel.md) .</span><span class="sxs-lookup"><span data-stu-id="d00d2-126">It can then be referenced from the [\<system.serviceModel>](../../configure-apps/file-schema/wcf/system-servicemodel.md) configuration section.</span></span>  
  
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
  
## <a name="adding-metadata-support-for-a-binding-element"></a><span data-ttu-id="d00d2-127">Adicionando suporte de metadados para um elemento de associação</span><span class="sxs-lookup"><span data-stu-id="d00d2-127">Adding Metadata Support for a Binding Element</span></span>  
 <span data-ttu-id="d00d2-128">Para integrar um canal no sistema de metadados, ele deve dar suporte à importação e à exportação da política.</span><span class="sxs-lookup"><span data-stu-id="d00d2-128">To integrate a channel into the metadata system, it must support both the import and export of policy.</span></span> <span data-ttu-id="d00d2-129">Isso permite que ferramentas como a [ferramenta de utilitário de metadados ServiceModel (svcutil. exe)](../servicemodel-metadata-utility-tool-svcutil-exe.md) gerem clientes do elemento de associação.</span><span class="sxs-lookup"><span data-stu-id="d00d2-129">This allows tools such as [ServiceModel Metadata Utility Tool (Svcutil.exe)](../servicemodel-metadata-utility-tool-svcutil-exe.md) to generate clients of the binding element.</span></span>  
  
### <a name="adding-wsdl-support"></a><span data-ttu-id="d00d2-130">Adicionando suporte a WSDL</span><span class="sxs-lookup"><span data-stu-id="d00d2-130">Adding WSDL Support</span></span>  
 <span data-ttu-id="d00d2-131">O elemento de associação de transporte em uma associação é responsável por exportar e importar informações de endereçamento nos metadados.</span><span class="sxs-lookup"><span data-stu-id="d00d2-131">The transport binding element in a binding is responsible for exporting and importing addressing information in metadata.</span></span> <span data-ttu-id="d00d2-132">Ao usar uma associação SOAP, o elemento de associação de transporte também deve exportar um URI de transporte correto nos metadados.</span><span class="sxs-lookup"><span data-stu-id="d00d2-132">When using a SOAP binding, the transport binding element should also export a correct transport URI in metadata.</span></span> <span data-ttu-id="d00d2-133">O código de exemplo a seguir é obtido [do transporte: Exemplo](../samples/transport-udp.md) de UDP.</span><span class="sxs-lookup"><span data-stu-id="d00d2-133">The following example code is taken from the [Transport: UDP](../samples/transport-udp.md) sample.</span></span>  
  
#### <a name="wsdl-export"></a><span data-ttu-id="d00d2-134">Exportação de WSDL</span><span class="sxs-lookup"><span data-stu-id="d00d2-134">WSDL Export</span></span>  
 <span data-ttu-id="d00d2-135">Para exportar informações de endereçamento `UdpTransportBindingElement` , o <xref:System.ServiceModel.Description.IWsdlExportExtension?displayProperty=nameWithType> implementa a interface.</span><span class="sxs-lookup"><span data-stu-id="d00d2-135">To export addressing information, the `UdpTransportBindingElement` implements the <xref:System.ServiceModel.Description.IWsdlExportExtension?displayProperty=nameWithType> interface.</span></span> <span data-ttu-id="d00d2-136">O <xref:System.ServiceModel.Description.IWsdlExportExtension.ExportEndpoint%2A?displayProperty=nameWithType> método adiciona as informações de endereçamento corretas à porta WSDL.</span><span class="sxs-lookup"><span data-stu-id="d00d2-136">The <xref:System.ServiceModel.Description.IWsdlExportExtension.ExportEndpoint%2A?displayProperty=nameWithType> method adds the correct addressing information to the WSDL port.</span></span>  
  
```csharp  
if (context.WsdlPort != null)  
{  
    AddAddressToWsdlPort(context.WsdlPort, context.Endpoint.Address, encodingBindingElement.MessageVersion.Addressing);  
}  
```  
  
 <span data-ttu-id="d00d2-137">A `UdpTransportBindingElement` implementação<xref:System.ServiceModel.Description.IWsdlExportExtension.ExportEndpoint%2A> do método também exporta um URI de transporte quando o ponto de extremidade usa uma associação SOAP:</span><span class="sxs-lookup"><span data-stu-id="d00d2-137">The `UdpTransportBindingElement` implementation of the <xref:System.ServiceModel.Description.IWsdlExportExtension.ExportEndpoint%2A> method also exports a transport URI when the endpoint uses a SOAP binding:</span></span>  
  
```csharp  
WsdlNS.SoapBinding soapBinding = GetSoapBinding(context, exporter);  
if (soapBinding != null)  
{  
    soapBinding.Transport = UdpPolicyStrings.UdpNamespace;  
}  
```  
  
#### <a name="wsdl-import"></a><span data-ttu-id="d00d2-138">Importação de WSDL</span><span class="sxs-lookup"><span data-stu-id="d00d2-138">WSDL Import</span></span>  
 <span data-ttu-id="d00d2-139">Para estender o sistema de importação WSDL para lidar com a importação dos endereços, adicione a seguinte configuração ao arquivo de configuração para SvcUtil. exe, conforme mostrado no arquivo svcutil. exe. config:</span><span class="sxs-lookup"><span data-stu-id="d00d2-139">To extend the WSDL import system to handle importing the addresses, add the following configuration to the configuration file for Svcutil.exe as shown in the Svcutil.exe.config file:</span></span>  
  
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
  
 <span data-ttu-id="d00d2-140">Ao executar svcutil. exe, há duas opções para obter svcutil. exe para carregar as extensões de importação WSDL:</span><span class="sxs-lookup"><span data-stu-id="d00d2-140">When running Svcutil.exe, there are two options for getting Svcutil.exe to load the WSDL import extensions:</span></span>  
  
1. <span data-ttu-id="d00d2-141">Aponte para o SvcUtil. exe para o arquivo de configuração usando\<o arquivo/SvcutilConfig: File >.</span><span class="sxs-lookup"><span data-stu-id="d00d2-141">Point Svcutil.exe to the configuration file using the /SvcutilConfig:\<file>.</span></span>  
  
2. <span data-ttu-id="d00d2-142">Adicione a seção de configuração a svcutil. exe. config no mesmo diretório que svcutil. exe.</span><span class="sxs-lookup"><span data-stu-id="d00d2-142">Add the configuration section to Svcutil.exe.config in the same directory as Svcutil.exe.</span></span>  
  
 <span data-ttu-id="d00d2-143">O `UdpBindingElementImporter` tipo implementa a <xref:System.ServiceModel.Description.IWsdlImportExtension?displayProperty=nameWithType> interface.</span><span class="sxs-lookup"><span data-stu-id="d00d2-143">The `UdpBindingElementImporter` type implements the <xref:System.ServiceModel.Description.IWsdlImportExtension?displayProperty=nameWithType> interface.</span></span> <span data-ttu-id="d00d2-144">O `ImportEndpoint` método importa o endereço da porta WSDL:</span><span class="sxs-lookup"><span data-stu-id="d00d2-144">The `ImportEndpoint` method imports the address from the WSDL port:</span></span>  
  
```csharp  
BindingElementCollection bindingElements = context.Endpoint.Binding.CreateBindingElements();  
TransportBindingElement transportBindingElement = bindingElements.Find<TransportBindingElement>();  
if (transportBindingElement is UdpTransportBindingElement)  
{  
    ImportAddress(context);  
}  
```  
  
### <a name="adding-policy-support"></a><span data-ttu-id="d00d2-145">Adicionando suporte à política</span><span class="sxs-lookup"><span data-stu-id="d00d2-145">Adding Policy Support</span></span>  
 <span data-ttu-id="d00d2-146">O elemento de associação personalizado pode exportar declarações de política na associação WSDL para um ponto de extremidade de serviço para expressar os recursos desse elemento de associação.</span><span class="sxs-lookup"><span data-stu-id="d00d2-146">The custom binding element can export policy assertions in the WSDL binding for a service endpoint to express the capabilities of that binding element.</span></span> <span data-ttu-id="d00d2-147">O código de exemplo a seguir é obtido [do transporte: Exemplo](../samples/transport-udp.md) de UDP.</span><span class="sxs-lookup"><span data-stu-id="d00d2-147">The following example code is taken from the [Transport: UDP](../samples/transport-udp.md) sample.</span></span>  
  
#### <a name="policy-export"></a><span data-ttu-id="d00d2-148">Exportação de política</span><span class="sxs-lookup"><span data-stu-id="d00d2-148">Policy Export</span></span>  
 <span data-ttu-id="d00d2-149">O `UdpTransportBindingElement` tipo implementa <xref:System.ServiceModel.Description.IPolicyExportExtension?displayProperty=nameWithType> para adicionar suporte para exportar a política.</span><span class="sxs-lookup"><span data-stu-id="d00d2-149">The `UdpTransportBindingElement` type implements <xref:System.ServiceModel.Description.IPolicyExportExtension?displayProperty=nameWithType> to add support for exporting policy.</span></span> <span data-ttu-id="d00d2-150">Como resultado, <xref:System.ServiceModel.Description.MetadataExporter?displayProperty=nameWithType> o inclui `UdpTransportBindingElement` na geração de política para qualquer associação que a inclua.</span><span class="sxs-lookup"><span data-stu-id="d00d2-150">As a result, <xref:System.ServiceModel.Description.MetadataExporter?displayProperty=nameWithType> includes `UdpTransportBindingElement` in the generation of policy for any binding that includes it.</span></span>  
  
 <span data-ttu-id="d00d2-151">No <xref:System.ServiceModel.Description.IPolicyExportExtension.ExportPolicy%2A?displayProperty=nameWithType>, adicione uma asserção para UDP e outra asserção se o canal estiver no modo multicast.</span><span class="sxs-lookup"><span data-stu-id="d00d2-151">In <xref:System.ServiceModel.Description.IPolicyExportExtension.ExportPolicy%2A?displayProperty=nameWithType>, add an assertion for UDP and another assertion if the channel is in multicast mode.</span></span> <span data-ttu-id="d00d2-152">Isso ocorre porque o modo multicast afeta a forma como a pilha de comunicação é construída e, portanto, deve ser coordenado entre ambos os lados.</span><span class="sxs-lookup"><span data-stu-id="d00d2-152">This is because multicast mode affects how the communication stack is constructed, and thus must be coordinated between both sides.</span></span>  
  
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
  
 <span data-ttu-id="d00d2-153">Como os elementos de associação de transporte personalizados são responsáveis pelo tratamento <xref:System.ServiceModel.Description.IPolicyExportExtension?displayProperty=nameWithType> de endereçamento `UdpTransportBindingElement` , a implementação no também deve lidar com a exportação das asserções de política apropriadas do WS-Addressing para indicar a versão do WS-Addressing sendo usado.</span><span class="sxs-lookup"><span data-stu-id="d00d2-153">Because custom transport binding elements are responsible for handling addressing, the <xref:System.ServiceModel.Description.IPolicyExportExtension?displayProperty=nameWithType> implementation on the `UdpTransportBindingElement` must also handle exporting the appropriate WS-Addressing policy assertions to indicate the version of WS-Addressing being used.</span></span>  
  
```csharp  
AddWSAddressingAssertion(context, encodingBindingElement.MessageVersion.Addressing);  
```  
  
#### <a name="policy-import"></a><span data-ttu-id="d00d2-154">Importação de política</span><span class="sxs-lookup"><span data-stu-id="d00d2-154">Policy Import</span></span>  
 <span data-ttu-id="d00d2-155">Para estender o sistema de importação de política, adicione a configuração a seguir ao arquivo de configuração para SvcUtil. exe, conforme mostrado no arquivo svcutil. exe. config:</span><span class="sxs-lookup"><span data-stu-id="d00d2-155">To extend the policy import system, add the following configuration to the configuration file for Svcutil.exe as shown in the Svcutil.exe.config file:</span></span>  
  
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
  
 <span data-ttu-id="d00d2-156">Em seguida, <xref:System.ServiceModel.Description.IPolicyImportExtension?displayProperty=nameWithType> implementamos a partir de`UdpBindingElementImporter`nossa classe registrada ().</span><span class="sxs-lookup"><span data-stu-id="d00d2-156">Then we implement <xref:System.ServiceModel.Description.IPolicyImportExtension?displayProperty=nameWithType> from our registered class (`UdpBindingElementImporter`).</span></span> <span data-ttu-id="d00d2-157">No <xref:System.ServiceModel.Description.IPolicyImportExtension.ImportPolicy%2A?displayProperty=nameWithType>, examine as asserções no namespace apropriado e processe aquelas para gerar o transporte e verificar se ele é multicast.</span><span class="sxs-lookup"><span data-stu-id="d00d2-157">In <xref:System.ServiceModel.Description.IPolicyImportExtension.ImportPolicy%2A?displayProperty=nameWithType>, examine the assertions in the appropriate namespace and process the ones for generating the transport and checking if it is multicast.</span></span> <span data-ttu-id="d00d2-158">Além disso, remova as asserções que o importador manipula da lista de asserções de associação.</span><span class="sxs-lookup"><span data-stu-id="d00d2-158">In addition, remove the assertions that the importer handles from the list of binding assertions.</span></span> <span data-ttu-id="d00d2-159">Novamente, ao executar svcutil. exe, há duas opções de integração:</span><span class="sxs-lookup"><span data-stu-id="d00d2-159">Again, when running Svcutil.exe, there are two options for integration:</span></span>  
  
1. <span data-ttu-id="d00d2-160">Aponte para o SvcUtil. exe para nosso arquivo de configuração usando\<o arquivo/SvcutilConfig: File >.</span><span class="sxs-lookup"><span data-stu-id="d00d2-160">Point Svcutil.exe to our configuration file using the /SvcutilConfig:\<file>.</span></span>  
  
2. <span data-ttu-id="d00d2-161">Adicione a seção de configuração a svcutil. exe. config no mesmo diretório que svcutil. exe.</span><span class="sxs-lookup"><span data-stu-id="d00d2-161">Add the configuration section to Svcutil.exe.config in the same directory as Svcutil.exe.</span></span>  
  
### <a name="adding-a-custom-standard-binding-importer"></a><span data-ttu-id="d00d2-162">Adicionando um importador de associação padrão personalizado</span><span class="sxs-lookup"><span data-stu-id="d00d2-162">Adding a Custom Standard Binding Importer</span></span>  
 <span data-ttu-id="d00d2-163">Svcutil. exe e o <xref:System.ServiceModel.Description.WsdlImporter?displayProperty=nameWithType> tipo, por padrão, reconhecem e importam associações fornecidas pelo sistema.</span><span class="sxs-lookup"><span data-stu-id="d00d2-163">Svcutil.exe and the <xref:System.ServiceModel.Description.WsdlImporter?displayProperty=nameWithType> type, by default, recognize and import system-provided bindings.</span></span> <span data-ttu-id="d00d2-164">Caso contrário, a associação será importada como uma <xref:System.ServiceModel.Channels.CustomBinding?displayProperty=nameWithType> instância.</span><span class="sxs-lookup"><span data-stu-id="d00d2-164">Otherwise, the binding gets imported as a <xref:System.ServiceModel.Channels.CustomBinding?displayProperty=nameWithType> instance.</span></span> <span data-ttu-id="d00d2-165">Para habilitar svcutil. exe e o <xref:System.ServiceModel.Description.WsdlImporter> para importar `UdpBindingElementImporter` o `SampleProfileUdpBinding` também atua como um importador de associação padrão personalizado.</span><span class="sxs-lookup"><span data-stu-id="d00d2-165">To enable Svcutil.exe and the <xref:System.ServiceModel.Description.WsdlImporter> to import the `SampleProfileUdpBinding` the `UdpBindingElementImporter` also acts as a custom standard binding importer.</span></span>  
  
 <span data-ttu-id="d00d2-166">Um importador de associação padrão personalizado implementa `ImportEndpoint` o método <xref:System.ServiceModel.Description.IWsdlImportExtension?displayProperty=nameWithType> na interface para examinar a <xref:System.ServiceModel.Channels.CustomBinding?displayProperty=nameWithType> instância importada de metadados para ver se ela pode ter sido gerada por uma associação padrão específica.</span><span class="sxs-lookup"><span data-stu-id="d00d2-166">A custom standard binding importer implements the `ImportEndpoint` method on the <xref:System.ServiceModel.Description.IWsdlImportExtension?displayProperty=nameWithType> interface to examine the <xref:System.ServiceModel.Channels.CustomBinding?displayProperty=nameWithType> instance imported from metadata to see if it could have been generated by specific standard binding.</span></span>  
  
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
  
 <span data-ttu-id="d00d2-167">Em geral, a implementação de um importador de associação padrão personalizado envolve a verificação das propriedades dos elementos de associação importados para verificar se apenas as propriedades que poderiam ter sido definidas pela associação padrão foram alteradas e todas as outras propriedades são seus padrões.</span><span class="sxs-lookup"><span data-stu-id="d00d2-167">Generally, implementing a custom standard binding importer involves checking the properties of the imported binding elements to verify that only properties that could have been set by the standard binding have changed and all other properties are their defaults.</span></span> <span data-ttu-id="d00d2-168">Uma estratégia básica para implementar um importador de associação padrão é criar uma instância da associação padrão, propagar as propriedades dos elementos de associação para a instância de associação padrão à qual a associação padrão dá suporte e comparar a associação elementos da associação padrão com os elementos de associação importados.</span><span class="sxs-lookup"><span data-stu-id="d00d2-168">A basic strategy for implementing a standard binding importer is to create an instance of the standard binding, propagate the properties from the binding elements to the standard binding instance that the standard binding supports, and the compare the binding elements from the standard binding with the imported binding elements.</span></span>
