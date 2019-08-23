---
title: Configurando associações para serviços do Windows Communication Foundation
ms.date: 03/30/2017
helpviewer_keywords:
- binding configuration [WCF]
ms.assetid: 99a85fd8-f7eb-4a84-a93e-7721b37d415c
ms.openlocfilehash: bfcdcd172d96660c3351926a9c42d298ac3fa654
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69928559"
---
# <a name="configuring-bindings-for-windows-communication-foundation-services"></a><span data-ttu-id="3643a-102">Configurando associações para serviços do Windows Communication Foundation</span><span class="sxs-lookup"><span data-stu-id="3643a-102">Configuring Bindings for Windows Communication Foundation Services</span></span>
<span data-ttu-id="3643a-103">Ao criar um aplicativo, muitas vezes você desejará adiar decisões para o administrador após a implantação do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="3643a-103">When creating an application, you often want to defer decisions to the administrator after the deployment of the application.</span></span> <span data-ttu-id="3643a-104">Por exemplo, geralmente não há como saber com antecedência o que é um endereço de serviço, ou Uniform Resource Identifier (URI), será.</span><span class="sxs-lookup"><span data-stu-id="3643a-104">For example, there is often no way of knowing in advance what a service address, or Uniform Resource Identifier (URI), will be.</span></span> <span data-ttu-id="3643a-105">Em vez de embutir em código um endereço, é preferível permitir que um administrador faça isso depois de criar um serviço.</span><span class="sxs-lookup"><span data-stu-id="3643a-105">Instead of hard-coding an address, it is preferable to allow an administrator to do so after creating a service.</span></span> <span data-ttu-id="3643a-106">Essa flexibilidade é realizada por meio da configuração.</span><span class="sxs-lookup"><span data-stu-id="3643a-106">This flexibility is accomplished through configuration.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="3643a-107">Use a [ferramenta de utilitário de metadados ServiceModel (svcutil. exe)](../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) com a `/config` opção para criar rapidamente os arquivos de configuração.</span><span class="sxs-lookup"><span data-stu-id="3643a-107">Use the [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) with the `/config` switch to quickly create configuration files.</span></span>  
  
## <a name="major-sections"></a><span data-ttu-id="3643a-108">Seções principais</span><span class="sxs-lookup"><span data-stu-id="3643a-108">Major Sections</span></span>  
 <span data-ttu-id="3643a-109">O esquema de configuração do Windows Communication Foundation (WCF) inclui as três seções principais`serviceModel`a `bindings`seguir ( `services`, e):</span><span class="sxs-lookup"><span data-stu-id="3643a-109">The Windows Communication Foundation (WCF) configuration scheme includes the following three major sections (`serviceModel`, `bindings`, and `services`):</span></span>  
  
```xml  
<configuration>  
    <system.serviceModel>  
        <bindings>  
        </bindings>  
        <services>  
        </services>  
        <behaviors>  
        </behaviors>  
    </system.serviceModel>  
</configuration>  
```  
  
### <a name="servicemodel-elements"></a><span data-ttu-id="3643a-110">Elementos ServiceModel</span><span class="sxs-lookup"><span data-stu-id="3643a-110">ServiceModel Elements</span></span>  
 <span data-ttu-id="3643a-111">Você pode usar a seção vinculada pelo `system.ServiceModel` elemento para configurar um tipo de serviço com um ou mais pontos de extremidade, bem como configurações para um serviço.</span><span class="sxs-lookup"><span data-stu-id="3643a-111">You can use the section bounded by the `system.ServiceModel` element to configure a service type with one or more endpoints, as well as settings for a service.</span></span> <span data-ttu-id="3643a-112">Cada ponto de extremidade pode ser configurado com um endereço, um contrato e uma associação.</span><span class="sxs-lookup"><span data-stu-id="3643a-112">Each endpoint can then be configured with an address, a contract, and a binding.</span></span> <span data-ttu-id="3643a-113">Para obter mais informações sobre pontos de extremidade, consulte [visão geral da criação de ponto de extremidades](../../../docs/framework/wcf/endpoint-creation-overview.md).</span><span class="sxs-lookup"><span data-stu-id="3643a-113">For more information about endpoints, see [Endpoint Creation Overview](../../../docs/framework/wcf/endpoint-creation-overview.md).</span></span> <span data-ttu-id="3643a-114">Se nenhum ponto de extremidade for especificado, o tempo de execução adicionará pontos de extremidade padrão.</span><span class="sxs-lookup"><span data-stu-id="3643a-114">If no endpoints are specified, the runtime adds default endpoints.</span></span> <span data-ttu-id="3643a-115">Para obter mais informações sobre pontos de extremidade, associações e comportamentos padrão, confira [Configuração simplificada](../../../docs/framework/wcf/simplified-configuration.md) e [Configuração simplificada para serviços WCF](../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md).</span><span class="sxs-lookup"><span data-stu-id="3643a-115">For more information about default endpoints, bindings, and behaviors, see [Simplified Configuration](../../../docs/framework/wcf/simplified-configuration.md) and [Simplified Configuration for WCF Services](../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md).</span></span>  
  
 <span data-ttu-id="3643a-116">Uma associação especifica transportes (HTTP, TCP, Pipes, Enfileiramento de mensagens) e protocolos (segurança, confiabilidade, fluxos de transação) e consiste em elementos de associação, cada um deles especificando um aspecto de como um ponto de extremidade se comunica com o mundo.</span><span class="sxs-lookup"><span data-stu-id="3643a-116">A binding specifies transports (HTTP, TCP, pipes, Message Queuing) and protocols (Security, Reliability, Transaction flows) and consists of binding elements, each of which specifies an aspect of how an endpoint communicates with the world.</span></span>  
  
 <span data-ttu-id="3643a-117">Por exemplo, especificar o [ \<elemento BasicHttpBinding >](../../../docs/framework/configure-apps/file-schema/wcf/basichttpbinding.md) indica usar http como o transporte de um ponto de extremidade.</span><span class="sxs-lookup"><span data-stu-id="3643a-117">For example, specifying the [\<basicHttpBinding>](../../../docs/framework/configure-apps/file-schema/wcf/basichttpbinding.md) element indicates to use HTTP as the transport for an endpoint.</span></span> <span data-ttu-id="3643a-118">Isso é usado para conectar o ponto de extremidade em tempo de execução quando o serviço que usa esse ponto de extremidade é aberto.</span><span class="sxs-lookup"><span data-stu-id="3643a-118">This is used to wire up the endpoint at run time when the service using this endpoint is opened.</span></span>  
  
 <span data-ttu-id="3643a-119">Há dois tipos de associações: predefinidos e personalizados.</span><span class="sxs-lookup"><span data-stu-id="3643a-119">There are two kinds of bindings: predefined and custom.</span></span> <span data-ttu-id="3643a-120">As associações predefinidas contêm combinações úteis de elementos que são usadas em cenários comuns.</span><span class="sxs-lookup"><span data-stu-id="3643a-120">Predefined bindings contain useful combinations of elements that are used in common scenarios.</span></span> <span data-ttu-id="3643a-121">Para obter uma lista de tipos de associação predefinidos que o WCF fornece, consulte [associações fornecidas pelo sistema](../../../docs/framework/wcf/system-provided-bindings.md).</span><span class="sxs-lookup"><span data-stu-id="3643a-121">For a list of predefined binding types that WCF provides, see [System-Provided Bindings](../../../docs/framework/wcf/system-provided-bindings.md).</span></span> <span data-ttu-id="3643a-122">Se nenhuma coleção de associação predefinida tiver a combinação correta de recursos de que um aplicativo de serviço precisa, você poderá construir associações personalizadas para atender aos requisitos do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="3643a-122">If no predefined binding collection has the correct combination of features that a service application needs, you can construct custom bindings to meet the application's requirements.</span></span> <span data-ttu-id="3643a-123">Para obter mais informações sobre associações personalizadas, consulte [ \<CustomBinding >](../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md).</span><span class="sxs-lookup"><span data-stu-id="3643a-123">For more information about custom bindings, see [\<customBinding>](../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md).</span></span>  
  
 <span data-ttu-id="3643a-124">Os quatro exemplos a seguir ilustram as configurações de associação mais comuns usadas para configurar um serviço WCF.</span><span class="sxs-lookup"><span data-stu-id="3643a-124">The following four examples illustrate the most common binding configurations used for setting up a WCF service.</span></span>  
  
#### <a name="specifying-an-endpoint-to-use-a-binding-type"></a><span data-ttu-id="3643a-125">Especificando um ponto de extremidade para usar um tipo de associação</span><span class="sxs-lookup"><span data-stu-id="3643a-125">Specifying an Endpoint to Use a Binding Type</span></span>  
 <span data-ttu-id="3643a-126">O primeiro exemplo ilustra como especificar um ponto de extremidade configurado com um endereço, um contrato e uma associação.</span><span class="sxs-lookup"><span data-stu-id="3643a-126">The first example illustrates how to specify an endpoint configured with an address, a contract, and a binding.</span></span>  
  
```xml  
<service name="HelloWorld, IndigoConfig, Version=2.0.0.0, Culture=neutral, PublicKeyToken=null">  
  <!-- This section is optional with the default configuration introduced  
       in .NET Framework 4. -->  
  <endpoint   
      address="/HelloWorld2/"  
      contract="HelloWorld, IndigoConfig, Version=2.0.0.0, Culture=neutral, PublicKeyToken=null"  
      binding="basicHttpBinding" />
</service>  
```  
  
 <span data-ttu-id="3643a-127">Neste exemplo, o `name` atributo indica a qual tipo de serviço é a configuração.</span><span class="sxs-lookup"><span data-stu-id="3643a-127">In this example, the `name` attribute indicates which service type the configuration is for.</span></span> <span data-ttu-id="3643a-128">Quando você cria um serviço em seu código com o `HelloWorld` contrato, ele é inicializado com todos os pontos de extremidade definidos na configuração de exemplo.</span><span class="sxs-lookup"><span data-stu-id="3643a-128">When you create a service in your code with the `HelloWorld` contract, it is initialized with all of the endpoints defined in the example configuration.</span></span> <span data-ttu-id="3643a-129">Se o assembly implementar apenas um contrato de serviço, `name` o atributo poderá ser omitido porque o serviço usa o único tipo disponível.</span><span class="sxs-lookup"><span data-stu-id="3643a-129">If the assembly implements only one service contract, the `name` attribute can be omitted because the service uses the only available type.</span></span> <span data-ttu-id="3643a-130">O atributo usa uma cadeia de caracteres, que deve estar no formato`Namespace.Class, AssemblyName, Version=0.0.0.0, Culture=neutral, PublicKeyToken=null`</span><span class="sxs-lookup"><span data-stu-id="3643a-130">The attribute takes a string, which must be in the format `Namespace.Class, AssemblyName, Version=0.0.0.0, Culture=neutral, PublicKeyToken=null`</span></span>  
  
 <span data-ttu-id="3643a-131">O `address` atributo especifica o URI que outros pontos de extremidade usam para se comunicar com o serviço.</span><span class="sxs-lookup"><span data-stu-id="3643a-131">The `address` attribute specifies the URI that other endpoints use to communicate to the service.</span></span> <span data-ttu-id="3643a-132">O URI pode ser um caminho absoluto ou relativo.</span><span class="sxs-lookup"><span data-stu-id="3643a-132">The URI can be either an absolute or relative path.</span></span> <span data-ttu-id="3643a-133">Se um endereço relativo for fornecido, espera-se que o host forneça um endereço base apropriado para o esquema de transporte usado na associação.</span><span class="sxs-lookup"><span data-stu-id="3643a-133">If a relative address is provided, the host is expected to provide a base address that is appropriate for the transport scheme used in the binding.</span></span> <span data-ttu-id="3643a-134">Se um endereço não estiver configurado, presume-se que o endereço base seja o endereço para esse ponto de extremidade.</span><span class="sxs-lookup"><span data-stu-id="3643a-134">If an address is not configured, the base address is assumed to be the address for that endpoint.</span></span>  
  
 <span data-ttu-id="3643a-135">O `contract` atributo especifica o contrato que esse ponto de extremidade está expondo.</span><span class="sxs-lookup"><span data-stu-id="3643a-135">The `contract` attribute specifies the contract this endpoint is exposing.</span></span> <span data-ttu-id="3643a-136">O tipo de implementação do serviço deve implementar o tipo de contrato.</span><span class="sxs-lookup"><span data-stu-id="3643a-136">The service implementation type must implement the contract type.</span></span> <span data-ttu-id="3643a-137">Se uma implementação de serviço implementar um único tipo de contrato, essa propriedade poderá ser omitida.</span><span class="sxs-lookup"><span data-stu-id="3643a-137">If a service implementation implements a single contract type, then this property can be omitted.</span></span>  
  
 <span data-ttu-id="3643a-138">O `binding` atributo seleciona uma associação personalizada ou predefinida a ser usada para esse ponto de extremidade específico.</span><span class="sxs-lookup"><span data-stu-id="3643a-138">The `binding` attribute selects a predefined or custom binding to use for this specific endpoint.</span></span> <span data-ttu-id="3643a-139">Um ponto de extremidade que não seleciona explicitamente uma associação usa a seleção de associação padrão, `BasicHttpBinding`que é.</span><span class="sxs-lookup"><span data-stu-id="3643a-139">An endpoint that does not explicitly select a binding uses the default binding selection, which is `BasicHttpBinding`.</span></span>  
  
#### <a name="modifying-a-predefined-binding"></a><span data-ttu-id="3643a-140">Modificando uma associação predefinida</span><span class="sxs-lookup"><span data-stu-id="3643a-140">Modifying a Predefined Binding</span></span>  
 <span data-ttu-id="3643a-141">No exemplo a seguir, uma associação predefinida é modificada.</span><span class="sxs-lookup"><span data-stu-id="3643a-141">In the following example, a predefined binding is modified.</span></span> <span data-ttu-id="3643a-142">Em seguida, ele pode ser usado para configurar qualquer ponto de extremidade no serviço.</span><span class="sxs-lookup"><span data-stu-id="3643a-142">It can then be used to configure any endpoint in the service.</span></span> <span data-ttu-id="3643a-143">A associação é modificada definindo o <xref:System.ServiceModel.Configuration.IBindingConfigurationElement.ReceiveTimeout%2A> valor como 1 segundo.</span><span class="sxs-lookup"><span data-stu-id="3643a-143">The binding is modified by setting the <xref:System.ServiceModel.Configuration.IBindingConfigurationElement.ReceiveTimeout%2A> value to 1 second.</span></span> <span data-ttu-id="3643a-144">Observe que a propriedade retorna um <xref:System.TimeSpan> objeto.</span><span class="sxs-lookup"><span data-stu-id="3643a-144">Note that the property returns a <xref:System.TimeSpan> object.</span></span>  
  
 <span data-ttu-id="3643a-145">Essa associação alterada é encontrada na seção associações.</span><span class="sxs-lookup"><span data-stu-id="3643a-145">That altered binding is found in the bindings section.</span></span> <span data-ttu-id="3643a-146">Essa associação alterada agora pode ser usada ao criar qualquer ponto de extremidade, `binding` definindo o atributo `endpoint` no elemento.</span><span class="sxs-lookup"><span data-stu-id="3643a-146">This altered binding can now be used when creating any endpoint by setting the `binding` attribute in the `endpoint` element.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="3643a-147">Se você fornecer um nome específico para a associação, o `bindingConfiguration` especificado no ponto de extremidade de serviço deverá corresponder a ele.</span><span class="sxs-lookup"><span data-stu-id="3643a-147">If you give a particular name to the binding, the `bindingConfiguration` specified in the service endpoint must match with it.</span></span>  
  
```xml  
<service name="HelloWorld, IndigoConfig, Version=2.0.0.0, Culture=neutral, PublicKeyToken=null">  
  <endpoint   
      address="/HelloWorld2/"  
      contract="HelloWorld, IndigoConfig, Version=2.0.0.0, Culture=neutral, PublicKeyToken=null"  
      binding="basicHttpBinding" />
</service>  
<bindings>  
    <basicHttpBinding   
        receiveTimeout="00:00:01"  
    />  
</bindings>  
```  
  
## <a name="configuring-a-behavior-to-apply-to-a-service"></a><span data-ttu-id="3643a-148">Configurando um comportamento para aplicar a um serviço</span><span class="sxs-lookup"><span data-stu-id="3643a-148">Configuring a Behavior to Apply to a Service</span></span>  
 <span data-ttu-id="3643a-149">No exemplo a seguir, um comportamento específico é configurado para o tipo de serviço.</span><span class="sxs-lookup"><span data-stu-id="3643a-149">In the following example, a specific behavior is configured for the service type.</span></span> <span data-ttu-id="3643a-150">O `ServiceMetadataBehavior` elemento é usado para habilitar a [ferramenta de utilitário de metadados ServiceModel (svcutil. exe)](../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) para consultar o serviço e gerar documentos WSDL (Web Services Description Language) a partir dos metadados.</span><span class="sxs-lookup"><span data-stu-id="3643a-150">The `ServiceMetadataBehavior` element is used to enable the [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) to query the service and generate Web Services Description Language (WSDL) documents from the metadata.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="3643a-151">Se você fornecer um nome específico para o comportamento, o `behaviorConfiguration` especificado na seção serviço ou ponto de extremidade deverá corresponder a ele.</span><span class="sxs-lookup"><span data-stu-id="3643a-151">If you give a particular name to the behavior, the `behaviorConfiguration` specified in the service or endpoint section must match it.</span></span>  
  
```xml  
<behaviors>  
    <behavior>  
        <ServiceMetadata httpGetEnabled="true" />   
    </behavior>  
</behaviors>  
<services>  
    <service   
       name="HelloWorld, IndigoConfig, Version=2.0.0.0, Culture=neutral, PublicKeyToken=null">
       <endpoint   
          address="http://computer:8080/Hello"  
          contract="HelloWorld, IndigoConfig, Version=2.0.0.0, Culture=neutral, PublicKeyToken=null"  
          binding="basicHttpBinding" />
    </service>  
</services>  
```  
  
 <span data-ttu-id="3643a-152">A configuração anterior permite que um cliente chame e obtenha os metadados do serviço digitado "HelloWorld".</span><span class="sxs-lookup"><span data-stu-id="3643a-152">The preceding configuration enables a client to call and get the metadata of the "HelloWorld" typed service.</span></span>  
  
 `svcutil /config:Client.exe.config http://computer:8080/Hello?wsdl`  
  
## <a name="specifying-a-service-with-two-endpoints-using-different-binding-values"></a><span data-ttu-id="3643a-153">Especificando um serviço com dois pontos de extremidade usando valores de associação diferentes</span><span class="sxs-lookup"><span data-stu-id="3643a-153">Specifying a Service with Two Endpoints Using Different Binding Values</span></span>  
 <span data-ttu-id="3643a-154">Neste último exemplo, dois pontos de extremidade são configurados para `HelloWorld` o tipo de serviço.</span><span class="sxs-lookup"><span data-stu-id="3643a-154">In this last example, two endpoints are configured for the `HelloWorld` service type.</span></span> <span data-ttu-id="3643a-155">Cada ponto de extremidade usa um `bindingConfiguration` atributo personalizado diferente do mesmo tipo de associação (cada um `basicHttpBinding`modifica o).</span><span class="sxs-lookup"><span data-stu-id="3643a-155">Each endpoint uses a different customized  `bindingConfiguration` attribute of the same binding type (each modifies the `basicHttpBinding`).</span></span>  
  
```xml  
<service name="HelloWorld, IndigoConfig, Version=2.0.0.0, Culture=neutral, PublicKeyToken=null">  
    <endpoint  
        address="http://computer:8080/Hello1"  
        contract="HelloWorld, IndigoConfig, Version=2.0.0.0, Culture=neutral, PublicKeyToken=null"  
        binding="basicHttpBinding"  
        bindingConfiguration="shortTimeout" />
    <endpoint  
        address="http://computer:8080/Hello2"  
        contract="HelloWorld, IndigoConfig, Version=2.0.0.0, Culture=neutral, PublicKeyToken=null"  
        binding="basicHttpBinding"  
        bindingConfiguration="Secure" />
</service>  
<bindings>  
    <basicHttpBinding   
        name="shortTimeout"  
        timeout="00:00:00:01"   
     />  
     <basicHttpBinding   
        name="Secure">  
        <Security mode="Transport" />  
     </basicHttpBinding>
</bindings>  
```  
  
 <span data-ttu-id="3643a-156">Você pode obter o mesmo comportamento usando a configuração padrão adicionando uma `protocolMapping` seção e configurando as associações, conforme demonstrado no exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="3643a-156">You can get the same behavior using the default configuration by adding a `protocolMapping` section and configuring the bindings as demonstrated in the following example.</span></span>  
  
```xml  
<protocolMapping>  
    <add scheme="http" binding="basicHttpBinding" bindingConfiguration="shortTimeout" />  
    <add scheme="https" binding="basicHttpBinding" bindingConfiguration="Secure" />  
</protocolMapping>  
<bindings>  
    <basicHttpBinding   
        name="shortTimeout"  
        timeout="00:00:00:01"   
     />  
     <basicHttpBinding   
        name="Secure" />  
        <Security mode="Transport" />  
</bindings>  
```  
  
## <a name="see-also"></a><span data-ttu-id="3643a-157">Consulte também</span><span class="sxs-lookup"><span data-stu-id="3643a-157">See also</span></span>

- [<span data-ttu-id="3643a-158">Configuração simplificada</span><span class="sxs-lookup"><span data-stu-id="3643a-158">Simplified Configuration</span></span>](../../../docs/framework/wcf/simplified-configuration.md)
- [<span data-ttu-id="3643a-159">Associações fornecidas pelo sistema</span><span class="sxs-lookup"><span data-stu-id="3643a-159">System-Provided Bindings</span></span>](../../../docs/framework/wcf/system-provided-bindings.md)
- [<span data-ttu-id="3643a-160">Visão geral de criação de ponto de extremidade</span><span class="sxs-lookup"><span data-stu-id="3643a-160">Endpoint Creation Overview</span></span>](../../../docs/framework/wcf/endpoint-creation-overview.md)
- [<span data-ttu-id="3643a-161">Usando associações para configurar serviços e clientes</span><span class="sxs-lookup"><span data-stu-id="3643a-161">Using Bindings to Configure Services and Clients</span></span>](../../../docs/framework/wcf/using-bindings-to-configure-services-and-clients.md)
