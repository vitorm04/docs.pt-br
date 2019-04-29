---
title: Configurando associações para serviços do Windows Communication Foundation
ms.date: 03/30/2017
helpviewer_keywords:
- binding configuration [WCF]
ms.assetid: 99a85fd8-f7eb-4a84-a93e-7721b37d415c
ms.openlocfilehash: 009011100af86e315aa41beb822b1448e2f21b25
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61608736"
---
# <a name="configuring-bindings-for-windows-communication-foundation-services"></a><span data-ttu-id="3cfd3-102">Configurando associações para serviços do Windows Communication Foundation</span><span class="sxs-lookup"><span data-stu-id="3cfd3-102">Configuring Bindings for Windows Communication Foundation Services</span></span>
<span data-ttu-id="3cfd3-103">Ao criar um aplicativo, você geralmente deseja adiar as decisões para o administrador após a implantação do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="3cfd3-103">When creating an application, you often want to defer decisions to the administrator after the deployment of the application.</span></span> <span data-ttu-id="3cfd3-104">Por exemplo, geralmente não há nenhuma maneira de saber com antecedência qual um endereço de serviço ou o identificador de recurso uniforme (URI), será.</span><span class="sxs-lookup"><span data-stu-id="3cfd3-104">For example, there is often no way of knowing in advance what a service address, or Uniform Resource Identifier (URI), will be.</span></span> <span data-ttu-id="3cfd3-105">Em vez de embutir um endereço, é preferível para permitir que um administrador para fazer isso depois de criar um serviço.</span><span class="sxs-lookup"><span data-stu-id="3cfd3-105">Instead of hard-coding an address, it is preferable to allow an administrator to do so after creating a service.</span></span> <span data-ttu-id="3cfd3-106">Essa flexibilidade é realizada por meio da configuração.</span><span class="sxs-lookup"><span data-stu-id="3cfd3-106">This flexibility is accomplished through configuration.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="3cfd3-107">Use o [ferramenta de utilitário de metadados ServiceModel (Svcutil.exe)](../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) com o `/config` switch para criar rapidamente arquivos de configuração.</span><span class="sxs-lookup"><span data-stu-id="3cfd3-107">Use the [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) with the `/config` switch to quickly create configuration files.</span></span>  
  
## <a name="major-sections"></a><span data-ttu-id="3cfd3-108">Seções principais</span><span class="sxs-lookup"><span data-stu-id="3cfd3-108">Major Sections</span></span>  
 <span data-ttu-id="3cfd3-109">O esquema de configuração do Windows Communication Foundation (WCF) inclui as três seções principais (`serviceModel`, `bindings`, e `services`):</span><span class="sxs-lookup"><span data-stu-id="3cfd3-109">The Windows Communication Foundation (WCF) configuration scheme includes the following three major sections (`serviceModel`, `bindings`, and `services`):</span></span>  
  
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
  
### <a name="servicemodel-elements"></a><span data-ttu-id="3cfd3-110">Elementos de ServiceModel</span><span class="sxs-lookup"><span data-stu-id="3cfd3-110">ServiceModel Elements</span></span>  
 <span data-ttu-id="3cfd3-111">Você pode usar a seção delimitada pelo `system.ServiceModel` elemento para configurar um tipo de serviço com um ou mais pontos de extremidade, bem como configurações de um serviço.</span><span class="sxs-lookup"><span data-stu-id="3cfd3-111">You can use the section bounded by the `system.ServiceModel` element to configure a service type with one or more endpoints, as well as settings for a service.</span></span> <span data-ttu-id="3cfd3-112">Cada ponto de extremidade, em seguida, pode ser configurado com um endereço, um contrato e uma associação.</span><span class="sxs-lookup"><span data-stu-id="3cfd3-112">Each endpoint can then be configured with an address, a contract, and a binding.</span></span> <span data-ttu-id="3cfd3-113">Para obter mais informações sobre pontos de extremidade, consulte [visão geral de criação de ponto de extremidade](../../../docs/framework/wcf/endpoint-creation-overview.md).</span><span class="sxs-lookup"><span data-stu-id="3cfd3-113">For more information about endpoints, see [Endpoint Creation Overview](../../../docs/framework/wcf/endpoint-creation-overview.md).</span></span> <span data-ttu-id="3cfd3-114">Se nenhum ponto de extremidade forem especificados, o tempo de execução adiciona pontos de extremidade padrão.</span><span class="sxs-lookup"><span data-stu-id="3cfd3-114">If no endpoints are specified, the runtime adds default endpoints.</span></span> <span data-ttu-id="3cfd3-115">Para obter mais informações sobre pontos de extremidade, associações e comportamentos padrão, confira [Configuração simplificada](../../../docs/framework/wcf/simplified-configuration.md) e [Configuração simplificada para serviços WCF](../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md).</span><span class="sxs-lookup"><span data-stu-id="3cfd3-115">For more information about default endpoints, bindings, and behaviors, see [Simplified Configuration](../../../docs/framework/wcf/simplified-configuration.md) and [Simplified Configuration for WCF Services](../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md).</span></span>  
  
 <span data-ttu-id="3cfd3-116">Uma associação Especifica (pipes HTTP, TCP, enfileiramento de mensagens) de transportes e protocolos (segurança, confiabilidade, os fluxos de transação) e consiste em elementos, cada um deles especifica um aspecto de como um ponto de extremidade se comunica com o mundo de associação.</span><span class="sxs-lookup"><span data-stu-id="3cfd3-116">A binding specifies transports (HTTP, TCP, pipes, Message Queuing) and protocols (Security, Reliability, Transaction flows) and consists of binding elements, each of which specifies an aspect of how an endpoint communicates with the world.</span></span>  
  
 <span data-ttu-id="3cfd3-117">Por exemplo, especificando o [ \<basicHttpBinding >](../../../docs/framework/configure-apps/file-schema/wcf/basichttpbinding.md) elemento indica para usar o HTTP como o transporte para um ponto de extremidade.</span><span class="sxs-lookup"><span data-stu-id="3cfd3-117">For example, specifying the [\<basicHttpBinding>](../../../docs/framework/configure-apps/file-schema/wcf/basichttpbinding.md) element indicates to use HTTP as the transport for an endpoint.</span></span> <span data-ttu-id="3cfd3-118">Isso é usado para conectar o ponto de extremidade no tempo de execução quando o serviço usando esse ponto de extremidade é aberto.</span><span class="sxs-lookup"><span data-stu-id="3cfd3-118">This is used to wire up the endpoint at run time when the service using this endpoint is opened.</span></span>  
  
 <span data-ttu-id="3cfd3-119">Há dois tipos de associações: predefinidos e personalizados.</span><span class="sxs-lookup"><span data-stu-id="3cfd3-119">There are two kinds of bindings: predefined and custom.</span></span> <span data-ttu-id="3cfd3-120">Associações predefinidas contêm útil combinações de elementos que são usados em cenários comuns.</span><span class="sxs-lookup"><span data-stu-id="3cfd3-120">Predefined bindings contain useful combinations of elements that are used in common scenarios.</span></span> <span data-ttu-id="3cfd3-121">Para obter uma lista de tipos de associação predefinida que o WCF fornece, consulte [System-Provided associações](../../../docs/framework/wcf/system-provided-bindings.md).</span><span class="sxs-lookup"><span data-stu-id="3cfd3-121">For a list of predefined binding types that WCF provides, see [System-Provided Bindings](../../../docs/framework/wcf/system-provided-bindings.md).</span></span> <span data-ttu-id="3cfd3-122">Se nenhuma coleção de associação predefinida tiver a combinação correta de recursos que precisa de um aplicativo de serviço, você pode construir ligações personalizadas para atender aos requisitos do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="3cfd3-122">If no predefined binding collection has the correct combination of features that a service application needs, you can construct custom bindings to meet the application's requirements.</span></span> <span data-ttu-id="3cfd3-123">Para obter mais informações sobre ligações personalizadas, consulte [ \<customBinding >](../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md).</span><span class="sxs-lookup"><span data-stu-id="3cfd3-123">For more information about custom bindings, see [\<customBinding>](../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md).</span></span>  
  
 <span data-ttu-id="3cfd3-124">Os quatro exemplos a seguir ilustram as configurações de associação mais comuns usadas para configurar um serviço WCF.</span><span class="sxs-lookup"><span data-stu-id="3cfd3-124">The following four examples illustrate the most common binding configurations used for setting up a WCF service.</span></span>  
  
#### <a name="specifying-an-endpoint-to-use-a-binding-type"></a><span data-ttu-id="3cfd3-125">Especificando um ponto de extremidade para usar um tipo de associação</span><span class="sxs-lookup"><span data-stu-id="3cfd3-125">Specifying an Endpoint to Use a Binding Type</span></span>  
 <span data-ttu-id="3cfd3-126">O primeiro exemplo ilustra como especificar um ponto de extremidade configurado com um endereço, um contrato e uma associação.</span><span class="sxs-lookup"><span data-stu-id="3cfd3-126">The first example illustrates how to specify an endpoint configured with an address, a contract, and a binding.</span></span>  
  
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
  
 <span data-ttu-id="3cfd3-127">Neste exemplo, o `name` atributo indica que a configuração é do tipo de serviço.</span><span class="sxs-lookup"><span data-stu-id="3cfd3-127">In this example, the `name` attribute indicates which service type the configuration is for.</span></span> <span data-ttu-id="3cfd3-128">Quando você cria um serviço em seu código com o `HelloWorld` contrato, ele é inicializado com todos os pontos de extremidade definidos na configuração de exemplo.</span><span class="sxs-lookup"><span data-stu-id="3cfd3-128">When you create a service in your code with the `HelloWorld` contract, it is initialized with all of the endpoints defined in the example configuration.</span></span> <span data-ttu-id="3cfd3-129">Se o assembly implementa apenas um contrato de serviço, o `name` atributo pode ser omitido porque o serviço usa o tipo só está disponível.</span><span class="sxs-lookup"><span data-stu-id="3cfd3-129">If the assembly implements only one service contract, the `name` attribute can be omitted because the service uses the only available type.</span></span> <span data-ttu-id="3cfd3-130">O atributo utiliza uma cadeia de caracteres, deve estar no formato `Namespace.Class, AssemblyName, Version=0.0.0.0, Culture=neutral, PublicKeyToken=null`</span><span class="sxs-lookup"><span data-stu-id="3cfd3-130">The attribute takes a string, which must be in the format `Namespace.Class, AssemblyName, Version=0.0.0.0, Culture=neutral, PublicKeyToken=null`</span></span>  
  
 <span data-ttu-id="3cfd3-131">O `address` atributo especifica o URI usado por outros pontos de extremidade para se comunicar com o serviço.</span><span class="sxs-lookup"><span data-stu-id="3cfd3-131">The `address` attribute specifies the URI that other endpoints use to communicate to the service.</span></span> <span data-ttu-id="3cfd3-132">O URI pode ser um caminho absoluto ou relativo.</span><span class="sxs-lookup"><span data-stu-id="3cfd3-132">The URI can be either an absolute or relative path.</span></span> <span data-ttu-id="3cfd3-133">Se um endereço relativo for fornecido, o host deve fornecer um endereço base que é apropriado para o esquema de transporte usado na associação.</span><span class="sxs-lookup"><span data-stu-id="3cfd3-133">If a relative address is provided, the host is expected to provide a base address that is appropriate for the transport scheme used in the binding.</span></span> <span data-ttu-id="3cfd3-134">Se um endereço não estiver configurado, o endereço base é considerado o endereço do ponto de extremidade.</span><span class="sxs-lookup"><span data-stu-id="3cfd3-134">If an address is not configured, the base address is assumed to be the address for that endpoint.</span></span>  
  
 <span data-ttu-id="3cfd3-135">O `contract` atributo especifica o contrato que esse ponto de extremidade está expondo.</span><span class="sxs-lookup"><span data-stu-id="3cfd3-135">The `contract` attribute specifies the contract this endpoint is exposing.</span></span> <span data-ttu-id="3cfd3-136">O tipo de implementação de serviço deve implementar o tipo de contrato.</span><span class="sxs-lookup"><span data-stu-id="3cfd3-136">The service implementation type must implement the contract type.</span></span> <span data-ttu-id="3cfd3-137">Se uma implementação de serviço implementa um tipo de contrato único, em seguida, essa propriedade pode ser omitida.</span><span class="sxs-lookup"><span data-stu-id="3cfd3-137">If a service implementation implements a single contract type, then this property can be omitted.</span></span>  
  
 <span data-ttu-id="3cfd3-138">O `binding` atributo seleciona uma associação predefinida ou personalizada a ser usado para esse ponto de extremidade específico.</span><span class="sxs-lookup"><span data-stu-id="3cfd3-138">The `binding` attribute selects a predefined or custom binding to use for this specific endpoint.</span></span> <span data-ttu-id="3cfd3-139">Um ponto de extremidade não seleciona explicitamente uma associação usa a seleção de associação padrão, que é `BasicHttpBinding`.</span><span class="sxs-lookup"><span data-stu-id="3cfd3-139">An endpoint that does not explicitly select a binding uses the default binding selection, which is `BasicHttpBinding`.</span></span>  
  
#### <a name="modifying-a-predefined-binding"></a><span data-ttu-id="3cfd3-140">Modificando uma associação predefinida</span><span class="sxs-lookup"><span data-stu-id="3cfd3-140">Modifying a Predefined Binding</span></span>  
 <span data-ttu-id="3cfd3-141">No exemplo a seguir, uma associação predefinida é modificada.</span><span class="sxs-lookup"><span data-stu-id="3cfd3-141">In the following example, a predefined binding is modified.</span></span> <span data-ttu-id="3cfd3-142">Ele pode ser usado para configurar qualquer ponto de extremidade no serviço.</span><span class="sxs-lookup"><span data-stu-id="3cfd3-142">It can then be used to configure any endpoint in the service.</span></span> <span data-ttu-id="3cfd3-143">A associação é modificada, definindo o <xref:System.ServiceModel.Configuration.IBindingConfigurationElement.ReceiveTimeout%2A> valor como 1 segundo.</span><span class="sxs-lookup"><span data-stu-id="3cfd3-143">The binding is modified by setting the <xref:System.ServiceModel.Configuration.IBindingConfigurationElement.ReceiveTimeout%2A> value to 1 second.</span></span> <span data-ttu-id="3cfd3-144">Observe que a propriedade retorna um <xref:System.TimeSpan> objeto.</span><span class="sxs-lookup"><span data-stu-id="3cfd3-144">Note that the property returns a <xref:System.TimeSpan> object.</span></span>  
  
 <span data-ttu-id="3cfd3-145">Alterado de associação for encontrado na seção de associações.</span><span class="sxs-lookup"><span data-stu-id="3cfd3-145">That altered binding is found in the bindings section.</span></span> <span data-ttu-id="3cfd3-146">Isso alterado associação agora pode ser usado durante a criação de qualquer ponto de extremidade, definindo o `binding` de atributo no `endpoint` elemento.</span><span class="sxs-lookup"><span data-stu-id="3cfd3-146">This altered binding can now be used when creating any endpoint by setting the `binding` attribute in the `endpoint` element.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="3cfd3-147">Se você fornecer um nome específico à associação, o `bindingConfiguration` especificado no serviço de ponto de extremidade deve corresponder com ele.</span><span class="sxs-lookup"><span data-stu-id="3cfd3-147">If you give a particular name to the binding, the `bindingConfiguration` specified in the service endpoint must match with it.</span></span>  
  
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
  
## <a name="configuring-a-behavior-to-apply-to-a-service"></a><span data-ttu-id="3cfd3-148">Configurando um comportamento a ser aplicado a um serviço</span><span class="sxs-lookup"><span data-stu-id="3cfd3-148">Configuring a Behavior to Apply to a Service</span></span>  
 <span data-ttu-id="3cfd3-149">No exemplo a seguir, um comportamento específico é configurado para o tipo de serviço.</span><span class="sxs-lookup"><span data-stu-id="3cfd3-149">In the following example, a specific behavior is configured for the service type.</span></span> <span data-ttu-id="3cfd3-150">O `ServiceMetadataBehavior` elemento é usado para habilitar o [ferramenta Utilitário de metadados ServiceModel (Svcutil.exe)](../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) para consultar o serviço e gerar documentos de descrição linguagem WSDL (Web Services) dos metadados.</span><span class="sxs-lookup"><span data-stu-id="3cfd3-150">The `ServiceMetadataBehavior` element is used to enable the [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) to query the service and generate Web Services Description Language (WSDL) documents from the metadata.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="3cfd3-151">Se você fornecer um nome específico para o comportamento, o `behaviorConfiguration` especificado no serviço ou ponto de extremidade de seção deve corresponder a ele.</span><span class="sxs-lookup"><span data-stu-id="3cfd3-151">If you give a particular name to the behavior, the `behaviorConfiguration` specified in the service or endpoint section must match it.</span></span>  
  
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
  
 <span data-ttu-id="3cfd3-152">O habilita a configuração anterior um cliente chamar e obter os metadados de "HelloWorld" digitado o serviço.</span><span class="sxs-lookup"><span data-stu-id="3cfd3-152">The preceding configuration enables a client to call and get the metadata of the "HelloWorld" typed service.</span></span>  
  
 `svcutil /config:Client.exe.config http://computer:8080/Hello?wsdl`  
  
## <a name="specifying-a-service-with-two-endpoints-using-different-binding-values"></a><span data-ttu-id="3cfd3-153">Especificando um serviço com dois pontos de extremidade usando valores diferentes de associação</span><span class="sxs-lookup"><span data-stu-id="3cfd3-153">Specifying a Service with Two Endpoints Using Different Binding Values</span></span>  
 <span data-ttu-id="3cfd3-154">Neste último exemplo, dois pontos de extremidade são configurados para o `HelloWorld` tipo de serviço.</span><span class="sxs-lookup"><span data-stu-id="3cfd3-154">In this last example, two endpoints are configured for the `HelloWorld` service type.</span></span> <span data-ttu-id="3cfd3-155">Cada ponto de extremidade usa diferentes personalizado `bindingConfiguration` atributo do mesmo tipo de associação (cada modifica o `basicHttpBinding`).</span><span class="sxs-lookup"><span data-stu-id="3cfd3-155">Each endpoint uses a different customized  `bindingConfiguration` attribute of the same binding type (each modifies the `basicHttpBinding`).</span></span>  
  
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
  
 <span data-ttu-id="3cfd3-156">Você pode obter o mesmo comportamento usando a configuração padrão, adicionando um `protocolMapping` seção e configurar as associações, conforme demonstrado no exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="3cfd3-156">You can get the same behavior using the default configuration by adding a `protocolMapping` section and configuring the bindings as demonstrated in the following example.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="3cfd3-157">Consulte também</span><span class="sxs-lookup"><span data-stu-id="3cfd3-157">See also</span></span>

- [<span data-ttu-id="3cfd3-158">Configuração simplificada</span><span class="sxs-lookup"><span data-stu-id="3cfd3-158">Simplified Configuration</span></span>](../../../docs/framework/wcf/simplified-configuration.md)
- [<span data-ttu-id="3cfd3-159">Associações fornecidas pelo sistema</span><span class="sxs-lookup"><span data-stu-id="3cfd3-159">System-Provided Bindings</span></span>](../../../docs/framework/wcf/system-provided-bindings.md)
- [<span data-ttu-id="3cfd3-160">Visão geral de criação de ponto de extremidade</span><span class="sxs-lookup"><span data-stu-id="3cfd3-160">Endpoint Creation Overview</span></span>](../../../docs/framework/wcf/endpoint-creation-overview.md)
- [<span data-ttu-id="3cfd3-161">Usando associações para configurar serviços e clientes</span><span class="sxs-lookup"><span data-stu-id="3cfd3-161">Using Bindings to Configure Services and Clients</span></span>](../../../docs/framework/wcf/using-bindings-to-configure-services-and-clients.md)
