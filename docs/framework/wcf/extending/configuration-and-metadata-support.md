---
title: "Configuração e suporte de metadados"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 27c240cb-8cab-472c-87f8-c864f4978758
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: aa728f64b336cc13ae515838fb7ff5c98c742d10
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/02/2017
---
# <a name="configuration-and-metadata-support"></a><span data-ttu-id="77787-102">Configuração e suporte de metadados</span><span class="sxs-lookup"><span data-stu-id="77787-102">Configuration and Metadata Support</span></span>
<span data-ttu-id="77787-103">Este tópico descreve como habilitar o suporte de configuração e metadados para associações e elementos de associação.</span><span class="sxs-lookup"><span data-stu-id="77787-103">This topic describes how to enable configuration and metadata support for bindings and binding elements.</span></span>  
  
## <a name="overview-of-configuration-and-metadata"></a><span data-ttu-id="77787-104">Visão geral da configuração e metadados</span><span class="sxs-lookup"><span data-stu-id="77787-104">Overview of Configuration and Metadata</span></span>  
 <span data-ttu-id="77787-105">Este tópico aborda as seguintes tarefas, que são itens opcionais 1, 2 e 4 no [canais de desenvolvimento](../../../../docs/framework/wcf/extending/developing-channels.md) lista de tarefas.</span><span class="sxs-lookup"><span data-stu-id="77787-105">This topic discusses the following tasks, which are optional items 1, 2, and 4 in the [Developing Channels](../../../../docs/framework/wcf/extending/developing-channels.md) task list.</span></span>  
  
-   <span data-ttu-id="77787-106">Habilitando o suporte de arquivo de configuração para um elemento de associação.</span><span class="sxs-lookup"><span data-stu-id="77787-106">Enabling configuration file support for a binding element.</span></span>  
  
-   <span data-ttu-id="77787-107">Habilitando o suporte de arquivo de configuração para uma associação.</span><span class="sxs-lookup"><span data-stu-id="77787-107">Enabling configuration file support for a binding.</span></span>  
  
-   <span data-ttu-id="77787-108">Exportando asserções WSDL e política para um elemento de associação.</span><span class="sxs-lookup"><span data-stu-id="77787-108">Exporting WSDL and policy assertions for a binding element.</span></span>  
  
-   <span data-ttu-id="77787-109">Identifica as asserções WSDL e política para inserir e configurar a associação ou elemento de associação.</span><span class="sxs-lookup"><span data-stu-id="77787-109">Identifying WSDL and policy assertions to insert and configure your binding or binding element.</span></span>  
  
 <span data-ttu-id="77787-110">Para obter informações sobre como criar associações definidas pelo usuário e elementos de associação, consulte [Criando associações](../../../../docs/framework/wcf/extending/creating-user-defined-bindings.md) e [criando um BindingElement](../../../../docs/framework/wcf/extending/creating-a-bindingelement.md), respectivamente.</span><span class="sxs-lookup"><span data-stu-id="77787-110">For information about creating user-defined bindings and binding elements, see [Creating User-Defined Bindings](../../../../docs/framework/wcf/extending/creating-user-defined-bindings.md) and [Creating a BindingElement](../../../../docs/framework/wcf/extending/creating-a-bindingelement.md), respectively.</span></span>  
  
## <a name="adding-configuration-support"></a><span data-ttu-id="77787-111">Adicionando suporte à configuração</span><span class="sxs-lookup"><span data-stu-id="77787-111">Adding Configuration Support</span></span>  
 <span data-ttu-id="77787-112">Para habilitar o suporte de arquivo de configuração para um canal, você deve implementar duas seções de configuração, <xref:System.ServiceModel.Configuration.BindingElementExtensionElement?displayProperty=nameWithType>, que habilita o suporte de configuração para associar elementos e o <xref:System.ServiceModel.Configuration.StandardBindingElement?displayProperty=nameWithType> e <xref:System.ServiceModel.Configuration.StandardBindingCollectionElement%602?displayProperty=nameWithType>, que permitem o suporte de configuração associações.</span><span class="sxs-lookup"><span data-stu-id="77787-112">To enable configuration file support for a channel, you must implement two configuration sections, <xref:System.ServiceModel.Configuration.BindingElementExtensionElement?displayProperty=nameWithType>, which enables configuration support for binding elements, and the <xref:System.ServiceModel.Configuration.StandardBindingElement?displayProperty=nameWithType> and <xref:System.ServiceModel.Configuration.StandardBindingCollectionElement%602?displayProperty=nameWithType>, which enable configuration support for bindings.</span></span>  
  
 <span data-ttu-id="77787-113">Uma maneira fácil de fazer isso é usar o [ConfigurationCodeGenerator](../../../../docs/framework/wcf/samples/configurationcodegenerator.md) ferramenta de exemplo para gerar código de configuração para suas associações e elementos de associação.</span><span class="sxs-lookup"><span data-stu-id="77787-113">An easier way to do this is to use the [ConfigurationCodeGenerator](../../../../docs/framework/wcf/samples/configurationcodegenerator.md) sample tool to generate configuration code for your bindings and binding elements.</span></span>  
  
### <a name="extending-bindingelementextensionelement"></a><span data-ttu-id="77787-114">Estendendo BindingElementExtensionElement</span><span class="sxs-lookup"><span data-stu-id="77787-114">Extending BindingElementExtensionElement</span></span>  
 <span data-ttu-id="77787-115">O exemplo de código a seguir é obtido a [transporte: UDP](../../../../docs/framework/wcf/samples/transport-udp.md) exemplo.</span><span class="sxs-lookup"><span data-stu-id="77787-115">The following example code is taken from the [Transport: UDP](../../../../docs/framework/wcf/samples/transport-udp.md) sample.</span></span> <span data-ttu-id="77787-116">O `UdpTransportElement` é um <xref:System.ServiceModel.Configuration.BindingElementExtensionElement> que expõe `UdpTransportBindingElement` para o sistema de configuração.</span><span class="sxs-lookup"><span data-stu-id="77787-116">The `UdpTransportElement` is a <xref:System.ServiceModel.Configuration.BindingElementExtensionElement> that exposes `UdpTransportBindingElement` to the configuration system.</span></span> <span data-ttu-id="77787-117">Com algumas substituições básicas, o exemplo define o nome da seção de configuração, o tipo de elemento de associação e como criar o elemento de associação.</span><span class="sxs-lookup"><span data-stu-id="77787-117">With a few basic overrides, the sample defines the configuration section name, the type of the binding element and how to create the binding element.</span></span> <span data-ttu-id="77787-118">Os usuários podem então registrar a seção de extensão em um arquivo de configuração da seguinte maneira.</span><span class="sxs-lookup"><span data-stu-id="77787-118">Users can then register the extension section in a configuration file as follows.</span></span>  
  
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
  
 <span data-ttu-id="77787-119">A extensão pode ser referenciada de associações personalizadas para usar UDP como o transporte.</span><span class="sxs-lookup"><span data-stu-id="77787-119">The extension can be referenced from custom bindings to use UDP as the transport.</span></span>  
  
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
  
### <a name="adding-configuration-for-a-binding"></a><span data-ttu-id="77787-120">Adicionando configuração de uma associação</span><span class="sxs-lookup"><span data-stu-id="77787-120">Adding Configuration for a Binding</span></span>  
 <span data-ttu-id="77787-121">A seção `SampleProfileUdpBindingCollectionElement` é um <xref:System.ServiceModel.Configuration.StandardBindingCollectionElement%602> que expõe `SampleProfileUdpBinding` para o sistema de configuração.</span><span class="sxs-lookup"><span data-stu-id="77787-121">The section `SampleProfileUdpBindingCollectionElement` is a <xref:System.ServiceModel.Configuration.StandardBindingCollectionElement%602> that exposes `SampleProfileUdpBinding` to the configuration system.</span></span> <span data-ttu-id="77787-122">A maior parte da implementação é delegada ao `SampleProfileUdpBindingConfigurationElement`, que é derivado de <xref:System.ServiceModel.Configuration.StandardBindingElement>.</span><span class="sxs-lookup"><span data-stu-id="77787-122">The bulk of the implementation is delegated to the `SampleProfileUdpBindingConfigurationElement`, which derives from <xref:System.ServiceModel.Configuration.StandardBindingElement>.</span></span> <span data-ttu-id="77787-123">O `SampleProfileUdpBindingConfigurationElement` tem propriedades que correspondem às propriedades em `SampleProfileUdpBinding`, funções e para mapear o `ConfigurationElement` associação.</span><span class="sxs-lookup"><span data-stu-id="77787-123">The `SampleProfileUdpBindingConfigurationElement` has properties that correspond to the properties on `SampleProfileUdpBinding`, and functions to map from the `ConfigurationElement` binding.</span></span> <span data-ttu-id="77787-124">Por fim, o `OnApplyConfiguration` método é substituído o `SampleProfileUdpBinding`, conforme mostrado no código de exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="77787-124">Finally, the `OnApplyConfiguration` method is overridden in the `SampleProfileUdpBinding`, as shown in the following sample code.</span></span>  
  
```  
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
  
 <span data-ttu-id="77787-125">Para registrar esse manipulador com o sistema de configuração, adicione a seção a seguir ao arquivo de configuração relevantes.</span><span class="sxs-lookup"><span data-stu-id="77787-125">To register this handler with the configuration system, add the following section to the relevant configuration file.</span></span>  
  
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
  
 <span data-ttu-id="77787-126">Em seguida, pode ser referenciada do [ \<System. ServiceModel >](../../../../docs/framework/configure-apps/file-schema/wcf/system-servicemodel.md) seção de configuração.</span><span class="sxs-lookup"><span data-stu-id="77787-126">It can then be referenced from the [\<system.serviceModel>](../../../../docs/framework/configure-apps/file-schema/wcf/system-servicemodel.md) configuration section.</span></span>  
  
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
  
## <a name="adding-metadata-support-for-a-binding-element"></a><span data-ttu-id="77787-127">Adicionando suporte a metadados para um elemento de associação</span><span class="sxs-lookup"><span data-stu-id="77787-127">Adding Metadata Support for a Binding Element</span></span>  
 <span data-ttu-id="77787-128">Para integrar um canal para o sistema de metadados, deverá dar suporte a importação e exportação de política.</span><span class="sxs-lookup"><span data-stu-id="77787-128">To integrate a channel into the metadata system, it must support both the import and export of policy.</span></span> <span data-ttu-id="77787-129">Isso permite que ferramentas como [Ferramenta Utilitária de metadados ServiceModel (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) para gerar os clientes do elemento de associação.</span><span class="sxs-lookup"><span data-stu-id="77787-129">This allows tools such as [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) to generate clients of the binding element.</span></span>  
  
### <a name="adding-wsdl-support"></a><span data-ttu-id="77787-130">Adicionando suporte a WSDL</span><span class="sxs-lookup"><span data-stu-id="77787-130">Adding WSDL Support</span></span>  
 <span data-ttu-id="77787-131">O elemento de associação de transporte em uma associação é responsável para exportar e importar informações de endereçamento nos metadados.</span><span class="sxs-lookup"><span data-stu-id="77787-131">The transport binding element in a binding is responsible for exporting and importing addressing information in metadata.</span></span> <span data-ttu-id="77787-132">Ao usar uma associação SOAP, o elemento de associação de transporte também deve exportar uma URI de transporte correta nos metadados.</span><span class="sxs-lookup"><span data-stu-id="77787-132">When using a SOAP binding, the transport binding element should also export a correct transport URI in metadata.</span></span> <span data-ttu-id="77787-133">O exemplo de código a seguir é obtido a [transporte: UDP](../../../../docs/framework/wcf/samples/transport-udp.md) exemplo.</span><span class="sxs-lookup"><span data-stu-id="77787-133">The following example code is taken from the [Transport: UDP](../../../../docs/framework/wcf/samples/transport-udp.md) sample.</span></span>  
  
#### <a name="wsdl-export"></a><span data-ttu-id="77787-134">Exportação WSDL</span><span class="sxs-lookup"><span data-stu-id="77787-134">WSDL Export</span></span>  
 <span data-ttu-id="77787-135">Para exportar informações de endereçamento, o `UdpTransportBindingElement` implementa o <xref:System.ServiceModel.Description.IWsdlExportExtension?displayProperty=nameWithType> interface.</span><span class="sxs-lookup"><span data-stu-id="77787-135">To export addressing information, the `UdpTransportBindingElement` implements the <xref:System.ServiceModel.Description.IWsdlExportExtension?displayProperty=nameWithType> interface.</span></span> <span data-ttu-id="77787-136">O <xref:System.ServiceModel.Description.IWsdlExportExtension.ExportEndpoint%2A?displayProperty=nameWithType> método adiciona as informações de endereçamento corretas para a porta WSDL.</span><span class="sxs-lookup"><span data-stu-id="77787-136">The <xref:System.ServiceModel.Description.IWsdlExportExtension.ExportEndpoint%2A?displayProperty=nameWithType> method adds the correct addressing information to the WSDL port.</span></span>  
  
```  
if (context.WsdlPort != null)  
{  
    AddAddressToWsdlPort(context.WsdlPort, context.Endpoint.Address, encodingBindingElement.MessageVersion.Addressing);  
}  
```  
  
 <span data-ttu-id="77787-137">O `UdpTransportBindingElement` implementação o <xref:System.ServiceModel.Description.IWsdlExportExtension.ExportEndpoint%2A> método também exporta um transporte URI quando o ponto de extremidade usa uma associação SOAP:</span><span class="sxs-lookup"><span data-stu-id="77787-137">The `UdpTransportBindingElement` implementation of the <xref:System.ServiceModel.Description.IWsdlExportExtension.ExportEndpoint%2A> method also exports a transport URI when the endpoint uses a SOAP binding:</span></span>  
  
```  
WsdlNS.SoapBinding soapBinding = GetSoapBinding(context, exporter);  
if (soapBinding != null)  
{  
    soapBinding.Transport = UdpPolicyStrings.UdpNamespace;  
}  
```  
  
#### <a name="wsdl-import"></a><span data-ttu-id="77787-138">Importação WSDL</span><span class="sxs-lookup"><span data-stu-id="77787-138">WSDL Import</span></span>  
 <span data-ttu-id="77787-139">Para estender o sistema de importação WSDL para lidar com a importação de endereços, adicione a seguinte configuração para o arquivo de configuração para Svcutil.exe conforme mostrado no arquivo Svcutil.exe.config:</span><span class="sxs-lookup"><span data-stu-id="77787-139">To extend the WSDL import system to handle importing the addresses, add the following configuration to the configuration file for Svcutil.exe as shown in the Svcutil.exe.config file:</span></span>  
  
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
  
 <span data-ttu-id="77787-140">Ao executar o Svcutil.exe, há duas opções para obter o Svcutil.exe para carregar as extensões de importação WSDL:</span><span class="sxs-lookup"><span data-stu-id="77787-140">When running Svcutil.exe, there are two options for getting Svcutil.exe to load the WSDL import extensions:</span></span>  
  
1.  <span data-ttu-id="77787-141">Ponto Svcutil.exe para o arquivo de configuração usando o /SvcutilConfig:\<arquivo >.</span><span class="sxs-lookup"><span data-stu-id="77787-141">Point Svcutil.exe to the configuration file using the /SvcutilConfig:\<file>.</span></span>  
  
2.  <span data-ttu-id="77787-142">Adicione a seção de configuração para Svcutil.exe.config no mesmo diretório que o Svcutil.exe.</span><span class="sxs-lookup"><span data-stu-id="77787-142">Add the configuration section to Svcutil.exe.config in the same directory as Svcutil.exe.</span></span>  
  
 <span data-ttu-id="77787-143">O `UdpBindingElementImporter` tipo implementa o <xref:System.ServiceModel.Description.IWsdlImportExtension?displayProperty=nameWithType> interface.</span><span class="sxs-lookup"><span data-stu-id="77787-143">The `UdpBindingElementImporter` type implements the <xref:System.ServiceModel.Description.IWsdlImportExtension?displayProperty=nameWithType> interface.</span></span> <span data-ttu-id="77787-144">O `ImportEndpoint` método importa o endereço da porta WSDL:</span><span class="sxs-lookup"><span data-stu-id="77787-144">The `ImportEndpoint` method imports the address from the WSDL port:</span></span>  
  
```  
BindingElementCollection bindingElements = context.Endpoint.Binding.CreateBindingElements();  
TransportBindingElement transportBindingElement = bindingElements.Find<TransportBindingElement>();  
if (transportBindingElement is UdpTransportBindingElement)  
{  
    ImportAddress(context);  
}  
```  
  
### <a name="adding-policy-support"></a><span data-ttu-id="77787-145">Adicionando suporte a política</span><span class="sxs-lookup"><span data-stu-id="77787-145">Adding Policy Support</span></span>  
 <span data-ttu-id="77787-146">O elemento de associação personalizada pode exportar declarações de política na associação WSDL para um ponto de extremidade de serviço para expressar os recursos desse elemento de associação.</span><span class="sxs-lookup"><span data-stu-id="77787-146">The custom binding element can export policy assertions in the WSDL binding for a service endpoint to express the capabilities of that binding element.</span></span> <span data-ttu-id="77787-147">O exemplo de código a seguir é obtido a [transporte: UDP](../../../../docs/framework/wcf/samples/transport-udp.md) exemplo.</span><span class="sxs-lookup"><span data-stu-id="77787-147">The following example code is taken from the [Transport: UDP](../../../../docs/framework/wcf/samples/transport-udp.md) sample.</span></span>  
  
#### <a name="policy-export"></a><span data-ttu-id="77787-148">Exportação de diretivas</span><span class="sxs-lookup"><span data-stu-id="77787-148">Policy Export</span></span>  
 <span data-ttu-id="77787-149">O `UdpTransportBindingElement` tipo implementa '<xref:System.ServiceModel.Description.IPolicyExportExtension?displayProperty=nameWithType> para adicionar suporte para exportação de política.</span><span class="sxs-lookup"><span data-stu-id="77787-149">The `UdpTransportBindingElement` type implements``<xref:System.ServiceModel.Description.IPolicyExportExtension?displayProperty=nameWithType> to add support for exporting policy.</span></span> <span data-ttu-id="77787-150">Como resultado, <xref:System.ServiceModel.Description.MetadataExporter?displayProperty=nameWithType> inclui `UdpTransportBindingElement` na geração de política para qualquer associação que o inclua.</span><span class="sxs-lookup"><span data-stu-id="77787-150">As a result, <xref:System.ServiceModel.Description.MetadataExporter?displayProperty=nameWithType> includes `UdpTransportBindingElement` in the generation of policy for any binding that includes it.</span></span>  
  
 <span data-ttu-id="77787-151">Em <xref:System.ServiceModel.Description.IPolicyExportExtension.ExportPolicy%2A?displayProperty=nameWithType>, adicionar uma asserção para UDP e outra asserção se o canal estiver no modo de multicast.</span><span class="sxs-lookup"><span data-stu-id="77787-151">In <xref:System.ServiceModel.Description.IPolicyExportExtension.ExportPolicy%2A?displayProperty=nameWithType>, add an assertion for UDP and another assertion if the channel is in multicast mode.</span></span> <span data-ttu-id="77787-152">Isso ocorre porque o modo multicast afeta como a pilha de comunicação é construída e, portanto, deve ser coordenada entre os dois lados.</span><span class="sxs-lookup"><span data-stu-id="77787-152">This is because multicast mode affects how the communication stack is constructed, and thus must be coordinated between both sides.</span></span>  
  
```  
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
  
 <span data-ttu-id="77787-153">Como os elementos de associação de transporte personalizado serão responsáveis pela manipulação de endereçamento, o <xref:System.ServiceModel.Description.IPolicyExportExtension?displayProperty=nameWithType> implementação no `UdpTransportBindingElement` também deve tratar exportando as apropriado declarações de política WS-Addressing para indicar a versão do WS-Addressing está sendo usado.</span><span class="sxs-lookup"><span data-stu-id="77787-153">Because custom transport binding elements are responsible for handling addressing, the <xref:System.ServiceModel.Description.IPolicyExportExtension?displayProperty=nameWithType> implementation on the `UdpTransportBindingElement` must also handle exporting the appropriate WS-Addressing policy assertions to indicate the version of WS-Addressing being used.</span></span>  
  
```  
AddWSAddressingAssertion(context, encodingBindingElement.MessageVersion.Addressing);  
```  
  
#### <a name="policy-import"></a><span data-ttu-id="77787-154">Importação da política</span><span class="sxs-lookup"><span data-stu-id="77787-154">Policy Import</span></span>  
 <span data-ttu-id="77787-155">Para estender o sistema de importação de política, adicione a seguinte configuração para o arquivo de configuração para Svcutil.exe conforme mostrado no arquivo Svcutil.exe.config:</span><span class="sxs-lookup"><span data-stu-id="77787-155">To extend the policy import system, add the following configuration to the configuration file for Svcutil.exe as shown in the Svcutil.exe.config file:</span></span>  
  
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
  
 <span data-ttu-id="77787-156">Em seguida, implementamos <xref:System.ServiceModel.Description.IPolicyImportExtension?displayProperty=nameWithType> de nossa classe registrada (`UdpBindingElementImporter`).</span><span class="sxs-lookup"><span data-stu-id="77787-156">Then we implement <xref:System.ServiceModel.Description.IPolicyImportExtension?displayProperty=nameWithType> from our registered class (`UdpBindingElementImporter`).</span></span> <span data-ttu-id="77787-157">Em <xref:System.ServiceModel.Description.IPolicyImportExtension.ImportPolicy%2A?displayProperty=nameWithType>, examine as declarações de namespace apropriado e processar os para o transporte de gerar e verificar se ele é multicast.</span><span class="sxs-lookup"><span data-stu-id="77787-157">In <xref:System.ServiceModel.Description.IPolicyImportExtension.ImportPolicy%2A?displayProperty=nameWithType>, examine the assertions in the appropriate namespace and process the ones for generating the transport and checking if it is multicast.</span></span> <span data-ttu-id="77787-158">Além disso, remova as declarações que manipula o importador da lista de declarações de associação.</span><span class="sxs-lookup"><span data-stu-id="77787-158">In addition, remove the assertions that the importer handles from the list of binding assertions.</span></span> <span data-ttu-id="77787-159">Novamente, ao executar o Svcutil.exe, há duas opções para integração:</span><span class="sxs-lookup"><span data-stu-id="77787-159">Again, when running Svcutil.exe, there are two options for integration:</span></span>  
  
1.  <span data-ttu-id="77787-160">Ponto Svcutil.exe para nosso arquivo de configuração usando o /SvcutilConfig:\<arquivo >.</span><span class="sxs-lookup"><span data-stu-id="77787-160">Point Svcutil.exe to our configuration file using the /SvcutilConfig:\<file>.</span></span>  
  
2.  <span data-ttu-id="77787-161">Adicione a seção de configuração para Svcutil.exe.config no mesmo diretório que o Svcutil.exe.</span><span class="sxs-lookup"><span data-stu-id="77787-161">Add the configuration section to Svcutil.exe.config in the same directory as Svcutil.exe.</span></span>  
  
### <a name="adding-a-custom-standard-binding-importer"></a><span data-ttu-id="77787-162">Adicionando um padrão personalizado importador de associação</span><span class="sxs-lookup"><span data-stu-id="77787-162">Adding a Custom Standard Binding Importer</span></span>  
 <span data-ttu-id="77787-163">Svcutil.exe e <xref:System.ServiceModel.Description.WsdlImporter?displayProperty=nameWithType> tipo, por padrão, reconhecer e importar associações fornecidas pelo sistema.</span><span class="sxs-lookup"><span data-stu-id="77787-163">Svcutil.exe and the <xref:System.ServiceModel.Description.WsdlImporter?displayProperty=nameWithType> type, by default, recognize and import system-provided bindings.</span></span> <span data-ttu-id="77787-164">Caso contrário, a associação é importada como um <xref:System.ServiceModel.Channels.CustomBinding?displayProperty=nameWithType> instância.</span><span class="sxs-lookup"><span data-stu-id="77787-164">Otherwise, the binding gets imported as a <xref:System.ServiceModel.Channels.CustomBinding?displayProperty=nameWithType> instance.</span></span> <span data-ttu-id="77787-165">Para habilitar o Svcutil.exe e o <xref:System.ServiceModel.Description.WsdlImporter> para importar o `SampleProfileUdpBinding` o `UdpBindingElementImporter` também atua como um importador de associação padrão personalizada.</span><span class="sxs-lookup"><span data-stu-id="77787-165">To enable Svcutil.exe and the <xref:System.ServiceModel.Description.WsdlImporter> to import the `SampleProfileUdpBinding` the `UdpBindingElementImporter` also acts as a custom standard binding importer.</span></span>  
  
 <span data-ttu-id="77787-166">Implementa um importador de associação padrão personalizada a `ImportEndpoint` método o <xref:System.ServiceModel.Description.IWsdlImportExtension?displayProperty=nameWithType> interface para examinar o <xref:System.ServiceModel.Channels.CustomBinding?displayProperty=nameWithType> instância importada de metadados para ver se ele pode ter sido gerado por associação padrão específica.</span><span class="sxs-lookup"><span data-stu-id="77787-166">A custom standard binding importer implements the `ImportEndpoint` method on the <xref:System.ServiceModel.Description.IWsdlImportExtension?displayProperty=nameWithType> interface to examine the <xref:System.ServiceModel.Channels.CustomBinding?displayProperty=nameWithType> instance imported from metadata to see if it could have been generated by specific standard binding.</span></span>  
  
```  
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
  
 <span data-ttu-id="77787-167">Em geral, implementar um importador de associação padrão personalizado envolve verificando as propriedades dos elementos de associação importados para verificar que somente as propriedades que podem ser definidas por meio da associação padrão foram alterados e todas as outras propriedades são seus padrões.</span><span class="sxs-lookup"><span data-stu-id="77787-167">Generally, implementing a custom standard binding importer involves checking the properties of the imported binding elements to verify that only properties that could have been set by the standard binding have changed and all other properties are their defaults.</span></span> <span data-ttu-id="77787-168">Uma estratégia básica para implementar um importador de associação padrão é criar uma instância da associação padrão, para propagar as propriedades de elementos de associação para a instância de associação padrão que oferece suporte a associação padrão e comparar a associação elementos de associação padrão com os elementos de associação importados.</span><span class="sxs-lookup"><span data-stu-id="77787-168">A basic strategy for implementing a standard binding importer is to create an instance of the standard binding, propagate the properties from the binding elements to the standard binding instance that the standard binding supports, and the compare the binding elements from the standard binding with the imported binding elements.</span></span>
