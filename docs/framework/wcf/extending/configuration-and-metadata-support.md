---
title: Configuração e suporte de metadados
ms.date: 03/30/2017
ms.assetid: 27c240cb-8cab-472c-87f8-c864f4978758
ms.openlocfilehash: 3f6d506d719cbb1b2ecc8bae223dfe73e7e2d1a9
ms.sourcegitcommit: 14ad34f7c4564ee0f009acb8bfc0ea7af3bc9541
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/01/2019
ms.locfileid: "73425140"
---
# <a name="configuration-and-metadata-support"></a><span data-ttu-id="1444a-102">Configuração e suporte de metadados</span><span class="sxs-lookup"><span data-stu-id="1444a-102">Configuration and Metadata Support</span></span>
<span data-ttu-id="1444a-103">Este tópico descreve como habilitar o suporte de configuração e metadados para associações e elementos de associação.</span><span class="sxs-lookup"><span data-stu-id="1444a-103">This topic describes how to enable configuration and metadata support for bindings and binding elements.</span></span>  
  
## <a name="overview-of-configuration-and-metadata"></a><span data-ttu-id="1444a-104">Visão geral da configuração e dos metadados</span><span class="sxs-lookup"><span data-stu-id="1444a-104">Overview of Configuration and Metadata</span></span>  
 <span data-ttu-id="1444a-105">Este tópico discute as seguintes tarefas, que são itens opcionais 1, 2 e 4 na lista de tarefas [desenvolvimento de canais](developing-channels.md) .</span><span class="sxs-lookup"><span data-stu-id="1444a-105">This topic discusses the following tasks, which are optional items 1, 2, and 4 in the [Developing Channels](developing-channels.md) task list.</span></span>  
  
- <span data-ttu-id="1444a-106">Habilitando o suporte ao arquivo de configuração para um elemento de associação.</span><span class="sxs-lookup"><span data-stu-id="1444a-106">Enabling configuration file support for a binding element.</span></span>  
  
- <span data-ttu-id="1444a-107">Habilitando o suporte ao arquivo de configuração para uma associação.</span><span class="sxs-lookup"><span data-stu-id="1444a-107">Enabling configuration file support for a binding.</span></span>  
  
- <span data-ttu-id="1444a-108">Exportando declarações WSDL e de política para um elemento de associação.</span><span class="sxs-lookup"><span data-stu-id="1444a-108">Exporting WSDL and policy assertions for a binding element.</span></span>  
  
- <span data-ttu-id="1444a-109">Identificação de declarações WSDL e de política para inserir e configurar seu elemento Binding ou Binding.</span><span class="sxs-lookup"><span data-stu-id="1444a-109">Identifying WSDL and policy assertions to insert and configure your binding or binding element.</span></span>  
  
 <span data-ttu-id="1444a-110">Para obter informações sobre como criar associações definidas pelo usuário e elementos de associação, consulte [Criando associações definidas pelo usuário](creating-user-defined-bindings.md) e [criando um BindingElement](creating-a-bindingelement.md), respectivamente.</span><span class="sxs-lookup"><span data-stu-id="1444a-110">For information about creating user-defined bindings and binding elements, see [Creating User-Defined Bindings](creating-user-defined-bindings.md) and [Creating a BindingElement](creating-a-bindingelement.md), respectively.</span></span>  
  
## <a name="adding-configuration-support"></a><span data-ttu-id="1444a-111">Adicionando suporte à configuração</span><span class="sxs-lookup"><span data-stu-id="1444a-111">Adding Configuration Support</span></span>  
 <span data-ttu-id="1444a-112">Para habilitar o suporte ao arquivo de configuração para um canal, você deve implementar duas seções de configuração, <xref:System.ServiceModel.Configuration.BindingElementExtensionElement?displayProperty=nameWithType>, que habilita o suporte de configuração para elementos de associação e o <xref:System.ServiceModel.Configuration.StandardBindingElement?displayProperty=nameWithType> e <xref:System.ServiceModel.Configuration.StandardBindingCollectionElement%602?displayProperty=nameWithType>, que habilitam o suporte à configuração para associações.</span><span class="sxs-lookup"><span data-stu-id="1444a-112">To enable configuration file support for a channel, you must implement two configuration sections, <xref:System.ServiceModel.Configuration.BindingElementExtensionElement?displayProperty=nameWithType>, which enables configuration support for binding elements, and the <xref:System.ServiceModel.Configuration.StandardBindingElement?displayProperty=nameWithType> and <xref:System.ServiceModel.Configuration.StandardBindingCollectionElement%602?displayProperty=nameWithType>, which enable configuration support for bindings.</span></span>  
  
 <span data-ttu-id="1444a-113">Uma maneira mais fácil de fazer isso é usar a ferramenta de exemplo [ConfigurationCodeGenerator](../samples/configurationcodegenerator.md) para gerar o código de configuração para suas associações e elementos de associação.</span><span class="sxs-lookup"><span data-stu-id="1444a-113">An easier way to do this is to use the [ConfigurationCodeGenerator](../samples/configurationcodegenerator.md) sample tool to generate configuration code for your bindings and binding elements.</span></span>  
  
### <a name="extending-bindingelementextensionelement"></a><span data-ttu-id="1444a-114">Estendendo BindingElementExtensionElement</span><span class="sxs-lookup"><span data-stu-id="1444a-114">Extending BindingElementExtensionElement</span></span>  
 <span data-ttu-id="1444a-115">O código de exemplo a seguir é obtido da amostra [Transport: UDP](../samples/transport-udp.md) .</span><span class="sxs-lookup"><span data-stu-id="1444a-115">The following example code is taken from the [Transport: UDP](../samples/transport-udp.md) sample.</span></span> <span data-ttu-id="1444a-116">O `UdpTransportElement` é um <xref:System.ServiceModel.Configuration.BindingElementExtensionElement> que expõe `UdpTransportBindingElement` ao sistema de configuração.</span><span class="sxs-lookup"><span data-stu-id="1444a-116">The `UdpTransportElement` is a <xref:System.ServiceModel.Configuration.BindingElementExtensionElement> that exposes `UdpTransportBindingElement` to the configuration system.</span></span> <span data-ttu-id="1444a-117">Com algumas substituições básicas, o exemplo define o nome da seção de configuração, o tipo do elemento de associação e como criar o elemento de associação.</span><span class="sxs-lookup"><span data-stu-id="1444a-117">With a few basic overrides, the sample defines the configuration section name, the type of the binding element and how to create the binding element.</span></span> <span data-ttu-id="1444a-118">Os usuários podem então registrar a seção de extensão em um arquivo de configuração da seguinte maneira.</span><span class="sxs-lookup"><span data-stu-id="1444a-118">Users can then register the extension section in a configuration file as follows.</span></span>  
  
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
  
 <span data-ttu-id="1444a-119">A extensão pode ser referenciada de associações personalizadas para usar UDP como o transporte.</span><span class="sxs-lookup"><span data-stu-id="1444a-119">The extension can be referenced from custom bindings to use UDP as the transport.</span></span>  
  
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
  
### <a name="adding-configuration-for-a-binding"></a><span data-ttu-id="1444a-120">Adicionando configuração para uma associação</span><span class="sxs-lookup"><span data-stu-id="1444a-120">Adding Configuration for a Binding</span></span>  
 <span data-ttu-id="1444a-121">A seção `SampleProfileUdpBindingCollectionElement` é uma <xref:System.ServiceModel.Configuration.StandardBindingCollectionElement%602> que expõe `SampleProfileUdpBinding` ao sistema de configuração.</span><span class="sxs-lookup"><span data-stu-id="1444a-121">The section `SampleProfileUdpBindingCollectionElement` is a <xref:System.ServiceModel.Configuration.StandardBindingCollectionElement%602> that exposes `SampleProfileUdpBinding` to the configuration system.</span></span> <span data-ttu-id="1444a-122">A maior parte da implementação é delegada para o `SampleProfileUdpBindingConfigurationElement`, que deriva de <xref:System.ServiceModel.Configuration.StandardBindingElement>.</span><span class="sxs-lookup"><span data-stu-id="1444a-122">The bulk of the implementation is delegated to the `SampleProfileUdpBindingConfigurationElement`, which derives from <xref:System.ServiceModel.Configuration.StandardBindingElement>.</span></span> <span data-ttu-id="1444a-123">O `SampleProfileUdpBindingConfigurationElement` tem propriedades que correspondem às propriedades em `SampleProfileUdpBinding`e as funções a serem mapeadas da Associação `ConfigurationElement`.</span><span class="sxs-lookup"><span data-stu-id="1444a-123">The `SampleProfileUdpBindingConfigurationElement` has properties that correspond to the properties on `SampleProfileUdpBinding`, and functions to map from the `ConfigurationElement` binding.</span></span> <span data-ttu-id="1444a-124">Por fim, o método `OnApplyConfiguration` é substituído na `SampleProfileUdpBinding`, conforme mostrado no código de exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="1444a-124">Finally, the `OnApplyConfiguration` method is overridden in the `SampleProfileUdpBinding`, as shown in the following sample code.</span></span>  
  
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
  
 <span data-ttu-id="1444a-125">Para registrar esse manipulador com o sistema de configuração, adicione a seção a seguir ao arquivo de configuração relevante.</span><span class="sxs-lookup"><span data-stu-id="1444a-125">To register this handler with the configuration system, add the following section to the relevant configuration file.</span></span>  
  
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
  
 <span data-ttu-id="1444a-126">Em seguida, ele pode ser referenciado na seção de configuração do [\<System. serviceModel >](../../configure-apps/file-schema/wcf/system-servicemodel.md) .</span><span class="sxs-lookup"><span data-stu-id="1444a-126">It can then be referenced from the [\<system.serviceModel>](../../configure-apps/file-schema/wcf/system-servicemodel.md) configuration section.</span></span>  
  
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
  
## <a name="adding-metadata-support-for-a-binding-element"></a><span data-ttu-id="1444a-127">Adicionando suporte de metadados para um elemento de associação</span><span class="sxs-lookup"><span data-stu-id="1444a-127">Adding Metadata Support for a Binding Element</span></span>  
 <span data-ttu-id="1444a-128">Para integrar um canal no sistema de metadados, ele deve dar suporte à importação e à exportação da política.</span><span class="sxs-lookup"><span data-stu-id="1444a-128">To integrate a channel into the metadata system, it must support both the import and export of policy.</span></span> <span data-ttu-id="1444a-129">Isso permite que ferramentas como a [ferramenta de utilitário de metadados ServiceModel (svcutil. exe)](../servicemodel-metadata-utility-tool-svcutil-exe.md) gerem clientes do elemento de associação.</span><span class="sxs-lookup"><span data-stu-id="1444a-129">This allows tools such as [ServiceModel Metadata Utility Tool (Svcutil.exe)](../servicemodel-metadata-utility-tool-svcutil-exe.md) to generate clients of the binding element.</span></span>  
  
### <a name="adding-wsdl-support"></a><span data-ttu-id="1444a-130">Adicionando suporte a WSDL</span><span class="sxs-lookup"><span data-stu-id="1444a-130">Adding WSDL Support</span></span>  
 <span data-ttu-id="1444a-131">O elemento de associação de transporte em uma associação é responsável por exportar e importar informações de endereçamento nos metadados.</span><span class="sxs-lookup"><span data-stu-id="1444a-131">The transport binding element in a binding is responsible for exporting and importing addressing information in metadata.</span></span> <span data-ttu-id="1444a-132">Ao usar uma associação SOAP, o elemento de associação de transporte também deve exportar um URI de transporte correto nos metadados.</span><span class="sxs-lookup"><span data-stu-id="1444a-132">When using a SOAP binding, the transport binding element should also export a correct transport URI in metadata.</span></span> <span data-ttu-id="1444a-133">O código de exemplo a seguir é obtido da amostra [Transport: UDP](../samples/transport-udp.md) .</span><span class="sxs-lookup"><span data-stu-id="1444a-133">The following example code is taken from the [Transport: UDP](../samples/transport-udp.md) sample.</span></span>  
  
#### <a name="wsdl-export"></a><span data-ttu-id="1444a-134">Exportação de WSDL</span><span class="sxs-lookup"><span data-stu-id="1444a-134">WSDL Export</span></span>  
 <span data-ttu-id="1444a-135">Para exportar informações de endereçamento, o `UdpTransportBindingElement` implementa a interface <xref:System.ServiceModel.Description.IWsdlExportExtension?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="1444a-135">To export addressing information, the `UdpTransportBindingElement` implements the <xref:System.ServiceModel.Description.IWsdlExportExtension?displayProperty=nameWithType> interface.</span></span> <span data-ttu-id="1444a-136">O método <xref:System.ServiceModel.Description.IWsdlExportExtension.ExportEndpoint%2A?displayProperty=nameWithType> adiciona as informações de endereçamento corretas à porta WSDL.</span><span class="sxs-lookup"><span data-stu-id="1444a-136">The <xref:System.ServiceModel.Description.IWsdlExportExtension.ExportEndpoint%2A?displayProperty=nameWithType> method adds the correct addressing information to the WSDL port.</span></span>  
  
```csharp  
if (context.WsdlPort != null)  
{  
    AddAddressToWsdlPort(context.WsdlPort, context.Endpoint.Address, encodingBindingElement.MessageVersion.Addressing);  
}  
```  
  
 <span data-ttu-id="1444a-137">A implementação de `UdpTransportBindingElement` do método <xref:System.ServiceModel.Description.IWsdlExportExtension.ExportEndpoint%2A> também exporta um URI de transporte quando o ponto de extremidade usa uma associação SOAP:</span><span class="sxs-lookup"><span data-stu-id="1444a-137">The `UdpTransportBindingElement` implementation of the <xref:System.ServiceModel.Description.IWsdlExportExtension.ExportEndpoint%2A> method also exports a transport URI when the endpoint uses a SOAP binding:</span></span>  
  
```csharp  
WsdlNS.SoapBinding soapBinding = GetSoapBinding(context, exporter);  
if (soapBinding != null)  
{  
    soapBinding.Transport = UdpPolicyStrings.UdpNamespace;  
}  
```  
  
#### <a name="wsdl-import"></a><span data-ttu-id="1444a-138">Importação de WSDL</span><span class="sxs-lookup"><span data-stu-id="1444a-138">WSDL Import</span></span>  
 <span data-ttu-id="1444a-139">Para estender o sistema de importação WSDL para lidar com a importação dos endereços, adicione a seguinte configuração ao arquivo de configuração para SvcUtil. exe, conforme mostrado no arquivo svcutil. exe. config:</span><span class="sxs-lookup"><span data-stu-id="1444a-139">To extend the WSDL import system to handle importing the addresses, add the following configuration to the configuration file for Svcutil.exe as shown in the Svcutil.exe.config file:</span></span>  
  
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
  
 <span data-ttu-id="1444a-140">Ao executar svcutil. exe, há duas opções para obter svcutil. exe para carregar as extensões de importação WSDL:</span><span class="sxs-lookup"><span data-stu-id="1444a-140">When running Svcutil.exe, there are two options for getting Svcutil.exe to load the WSDL import extensions:</span></span>  
  
1. <span data-ttu-id="1444a-141">Aponte para o SvcUtil. exe para o arquivo de configuração usando o arquivo/SvcutilConfig:\<>.</span><span class="sxs-lookup"><span data-stu-id="1444a-141">Point Svcutil.exe to the configuration file using the /SvcutilConfig:\<file>.</span></span>  
  
2. <span data-ttu-id="1444a-142">Adicione a seção de configuração a svcutil. exe. config no mesmo diretório que svcutil. exe.</span><span class="sxs-lookup"><span data-stu-id="1444a-142">Add the configuration section to Svcutil.exe.config in the same directory as Svcutil.exe.</span></span>  
  
 <span data-ttu-id="1444a-143">O tipo de `UdpBindingElementImporter` implementa a interface <xref:System.ServiceModel.Description.IWsdlImportExtension?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="1444a-143">The `UdpBindingElementImporter` type implements the <xref:System.ServiceModel.Description.IWsdlImportExtension?displayProperty=nameWithType> interface.</span></span> <span data-ttu-id="1444a-144">O método `ImportEndpoint` importa o endereço da porta WSDL:</span><span class="sxs-lookup"><span data-stu-id="1444a-144">The `ImportEndpoint` method imports the address from the WSDL port:</span></span>  
  
```csharp  
BindingElementCollection bindingElements = context.Endpoint.Binding.CreateBindingElements();  
TransportBindingElement transportBindingElement = bindingElements.Find<TransportBindingElement>();  
if (transportBindingElement is UdpTransportBindingElement)  
{  
    ImportAddress(context);  
}  
```  
  
### <a name="adding-policy-support"></a><span data-ttu-id="1444a-145">Adicionando suporte à política</span><span class="sxs-lookup"><span data-stu-id="1444a-145">Adding Policy Support</span></span>  
 <span data-ttu-id="1444a-146">O elemento de associação personalizado pode exportar declarações de política na associação WSDL para um ponto de extremidade de serviço para expressar os recursos desse elemento de associação.</span><span class="sxs-lookup"><span data-stu-id="1444a-146">The custom binding element can export policy assertions in the WSDL binding for a service endpoint to express the capabilities of that binding element.</span></span> <span data-ttu-id="1444a-147">O código de exemplo a seguir é obtido da amostra [Transport: UDP](../samples/transport-udp.md) .</span><span class="sxs-lookup"><span data-stu-id="1444a-147">The following example code is taken from the [Transport: UDP](../samples/transport-udp.md) sample.</span></span>  
  
#### <a name="policy-export"></a><span data-ttu-id="1444a-148">Exportação de política</span><span class="sxs-lookup"><span data-stu-id="1444a-148">Policy Export</span></span>  
 <span data-ttu-id="1444a-149">O tipo de `UdpTransportBindingElement` implementa <xref:System.ServiceModel.Description.IPolicyExportExtension?displayProperty=nameWithType> para adicionar suporte para exportar a política.</span><span class="sxs-lookup"><span data-stu-id="1444a-149">The `UdpTransportBindingElement` type implements <xref:System.ServiceModel.Description.IPolicyExportExtension?displayProperty=nameWithType> to add support for exporting policy.</span></span> <span data-ttu-id="1444a-150">Como resultado, o <xref:System.ServiceModel.Description.MetadataExporter?displayProperty=nameWithType> inclui `UdpTransportBindingElement` na geração de política para qualquer associação que o inclua.</span><span class="sxs-lookup"><span data-stu-id="1444a-150">As a result, <xref:System.ServiceModel.Description.MetadataExporter?displayProperty=nameWithType> includes `UdpTransportBindingElement` in the generation of policy for any binding that includes it.</span></span>  
  
 <span data-ttu-id="1444a-151">Em <xref:System.ServiceModel.Description.IPolicyExportExtension.ExportPolicy%2A?displayProperty=nameWithType>, adicione uma asserção para UDP e outra asserção se o canal estiver no modo multicast.</span><span class="sxs-lookup"><span data-stu-id="1444a-151">In <xref:System.ServiceModel.Description.IPolicyExportExtension.ExportPolicy%2A?displayProperty=nameWithType>, add an assertion for UDP and another assertion if the channel is in multicast mode.</span></span> <span data-ttu-id="1444a-152">Isso ocorre porque o modo multicast afeta a forma como a pilha de comunicação é construída e, portanto, deve ser coordenado entre ambos os lados.</span><span class="sxs-lookup"><span data-stu-id="1444a-152">This is because multicast mode affects how the communication stack is constructed, and thus must be coordinated between both sides.</span></span>  
  
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
  
 <span data-ttu-id="1444a-153">Como os elementos de associação de transporte personalizados são responsáveis pelo tratamento de endereçamento, a implementação de <xref:System.ServiceModel.Description.IPolicyExportExtension?displayProperty=nameWithType> no `UdpTransportBindingElement` também deve lidar com a exportação das declarações de política de WS-Addressing apropriadas para indicar a versão do WS-Addressing que está sendo usada.</span><span class="sxs-lookup"><span data-stu-id="1444a-153">Because custom transport binding elements are responsible for handling addressing, the <xref:System.ServiceModel.Description.IPolicyExportExtension?displayProperty=nameWithType> implementation on the `UdpTransportBindingElement` must also handle exporting the appropriate WS-Addressing policy assertions to indicate the version of WS-Addressing being used.</span></span>  
  
```csharp  
AddWSAddressingAssertion(context, encodingBindingElement.MessageVersion.Addressing);  
```  
  
#### <a name="policy-import"></a><span data-ttu-id="1444a-154">Importação de política</span><span class="sxs-lookup"><span data-stu-id="1444a-154">Policy Import</span></span>  
 <span data-ttu-id="1444a-155">Para estender o sistema de importação de política, adicione a configuração a seguir ao arquivo de configuração para SvcUtil. exe, conforme mostrado no arquivo svcutil. exe. config:</span><span class="sxs-lookup"><span data-stu-id="1444a-155">To extend the policy import system, add the following configuration to the configuration file for Svcutil.exe as shown in the Svcutil.exe.config file:</span></span>  
  
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
  
 <span data-ttu-id="1444a-156">Em seguida, implementamos <xref:System.ServiceModel.Description.IPolicyImportExtension?displayProperty=nameWithType> de nossa classe registrada (`UdpBindingElementImporter`).</span><span class="sxs-lookup"><span data-stu-id="1444a-156">Then we implement <xref:System.ServiceModel.Description.IPolicyImportExtension?displayProperty=nameWithType> from our registered class (`UdpBindingElementImporter`).</span></span> <span data-ttu-id="1444a-157">Em <xref:System.ServiceModel.Description.IPolicyImportExtension.ImportPolicy%2A?displayProperty=nameWithType>, examine as asserções no namespace apropriado e processe aquelas para gerar o transporte e verificar se ele é multicast.</span><span class="sxs-lookup"><span data-stu-id="1444a-157">In <xref:System.ServiceModel.Description.IPolicyImportExtension.ImportPolicy%2A?displayProperty=nameWithType>, examine the assertions in the appropriate namespace and process the ones for generating the transport and checking if it is multicast.</span></span> <span data-ttu-id="1444a-158">Além disso, remova as asserções que o importador manipula da lista de asserções de associação.</span><span class="sxs-lookup"><span data-stu-id="1444a-158">In addition, remove the assertions that the importer handles from the list of binding assertions.</span></span> <span data-ttu-id="1444a-159">Novamente, ao executar svcutil. exe, há duas opções de integração:</span><span class="sxs-lookup"><span data-stu-id="1444a-159">Again, when running Svcutil.exe, there are two options for integration:</span></span>  
  
1. <span data-ttu-id="1444a-160">Aponte para o SvcUtil. exe para nosso arquivo de configuração usando o arquivo/SvcutilConfig:\<>.</span><span class="sxs-lookup"><span data-stu-id="1444a-160">Point Svcutil.exe to our configuration file using the /SvcutilConfig:\<file>.</span></span>  
  
2. <span data-ttu-id="1444a-161">Adicione a seção de configuração a svcutil. exe. config no mesmo diretório que svcutil. exe.</span><span class="sxs-lookup"><span data-stu-id="1444a-161">Add the configuration section to Svcutil.exe.config in the same directory as Svcutil.exe.</span></span>  
  
### <a name="adding-a-custom-standard-binding-importer"></a><span data-ttu-id="1444a-162">Adicionando um importador de associação padrão personalizado</span><span class="sxs-lookup"><span data-stu-id="1444a-162">Adding a Custom Standard Binding Importer</span></span>  
 <span data-ttu-id="1444a-163">Svcutil. exe e o tipo de <xref:System.ServiceModel.Description.WsdlImporter?displayProperty=nameWithType>, por padrão, reconhecem e importam associações fornecidas pelo sistema.</span><span class="sxs-lookup"><span data-stu-id="1444a-163">Svcutil.exe and the <xref:System.ServiceModel.Description.WsdlImporter?displayProperty=nameWithType> type, by default, recognize and import system-provided bindings.</span></span> <span data-ttu-id="1444a-164">Caso contrário, a associação será importada como uma instância de <xref:System.ServiceModel.Channels.CustomBinding?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="1444a-164">Otherwise, the binding gets imported as a <xref:System.ServiceModel.Channels.CustomBinding?displayProperty=nameWithType> instance.</span></span> <span data-ttu-id="1444a-165">Para habilitar svcutil. exe e a <xref:System.ServiceModel.Description.WsdlImporter> importar o `SampleProfileUdpBinding` o `UdpBindingElementImporter` também atua como um importador de associação padrão personalizado.</span><span class="sxs-lookup"><span data-stu-id="1444a-165">To enable Svcutil.exe and the <xref:System.ServiceModel.Description.WsdlImporter> to import the `SampleProfileUdpBinding` the `UdpBindingElementImporter` also acts as a custom standard binding importer.</span></span>  
  
 <span data-ttu-id="1444a-166">Um importador de associação padrão personalizado implementa o método `ImportEndpoint` na interface <xref:System.ServiceModel.Description.IWsdlImportExtension?displayProperty=nameWithType> para examinar a instância de <xref:System.ServiceModel.Channels.CustomBinding?displayProperty=nameWithType> importada de metadados para ver se ela pode ter sido gerada por uma associação padrão específica.</span><span class="sxs-lookup"><span data-stu-id="1444a-166">A custom standard binding importer implements the `ImportEndpoint` method on the <xref:System.ServiceModel.Description.IWsdlImportExtension?displayProperty=nameWithType> interface to examine the <xref:System.ServiceModel.Channels.CustomBinding?displayProperty=nameWithType> instance imported from metadata to see if it could have been generated by specific standard binding.</span></span>  
  
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
  
 <span data-ttu-id="1444a-167">Em geral, a implementação de um importador de associação padrão personalizado envolve a verificação das propriedades dos elementos de associação importados para verificar se apenas as propriedades que poderiam ter sido definidas pela associação padrão foram alteradas e todas as outras propriedades são seus padrões.</span><span class="sxs-lookup"><span data-stu-id="1444a-167">Generally, implementing a custom standard binding importer involves checking the properties of the imported binding elements to verify that only properties that could have been set by the standard binding have changed and all other properties are their defaults.</span></span> <span data-ttu-id="1444a-168">Uma estratégia básica para implementar um importador de associação padrão é criar uma instância da associação padrão, propagar as propriedades dos elementos de associação para a instância de associação padrão à qual a associação padrão dá suporte e comparar a associação elementos da associação padrão com os elementos de associação importados.</span><span class="sxs-lookup"><span data-stu-id="1444a-168">A basic strategy for implementing a standard binding importer is to create an instance of the standard binding, propagate the properties from the binding elements to the standard binding instance that the standard binding supports, and the compare the binding elements from the standard binding with the imported binding elements.</span></span>
