---
title: Configurando associações para serviços do Windows Communication Foundation
ms.date: 03/30/2017
helpviewer_keywords:
- binding configuration [WCF]
ms.assetid: 99a85fd8-f7eb-4a84-a93e-7721b37d415c
ms.openlocfilehash: e7ee1a8ce358c77e46db39af67bd9dc20114fb3b
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79174817"
---
# <a name="configuring-bindings-for-windows-communication-foundation-services"></a><span data-ttu-id="c0e98-102">Configurando associações para serviços do Windows Communication Foundation</span><span class="sxs-lookup"><span data-stu-id="c0e98-102">Configuring Bindings for Windows Communication Foundation Services</span></span>
<span data-ttu-id="c0e98-103">Ao criar um aplicativo, muitas vezes você deseja adiar as decisões para o administrador após a implantação do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="c0e98-103">When creating an application, you often want to defer decisions to the administrator after the deployment of the application.</span></span> <span data-ttu-id="c0e98-104">Por exemplo, muitas vezes não há como saber com antecedência qual será um endereço de serviço, ou Uri (Uniform Resource Identifier), ou Identificador de Recursos Uniformes (URI).</span><span class="sxs-lookup"><span data-stu-id="c0e98-104">For example, there is often no way of knowing in advance what a service address, or Uniform Resource Identifier (URI), will be.</span></span> <span data-ttu-id="c0e98-105">Em vez de codificar um endereço, é preferível permitir que um administrador o faça depois de criar um serviço.</span><span class="sxs-lookup"><span data-stu-id="c0e98-105">Instead of hard-coding an address, it is preferable to allow an administrator to do so after creating a service.</span></span> <span data-ttu-id="c0e98-106">Essa flexibilidade é realizada através da configuração.</span><span class="sxs-lookup"><span data-stu-id="c0e98-106">This flexibility is accomplished through configuration.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="c0e98-107">Use a [ServiceModel Metadata Utility Tool (Svcutil.exe)](servicemodel-metadata-utility-tool-svcutil-exe.md) com o `/config` switch para criar rapidamente arquivos de configuração.</span><span class="sxs-lookup"><span data-stu-id="c0e98-107">Use the [ServiceModel Metadata Utility Tool (Svcutil.exe)](servicemodel-metadata-utility-tool-svcutil-exe.md) with the `/config` switch to quickly create configuration files.</span></span>  
  
## <a name="major-sections"></a><span data-ttu-id="c0e98-108">Principais Seções</span><span class="sxs-lookup"><span data-stu-id="c0e98-108">Major Sections</span></span>  
 <span data-ttu-id="c0e98-109">O esquema de configuração da Windows Communication Foundation (WCF) inclui as três principais seções (,`serviceModel` `bindings`e `services`):</span><span class="sxs-lookup"><span data-stu-id="c0e98-109">The Windows Communication Foundation (WCF) configuration scheme includes the following three major sections (`serviceModel`, `bindings`, and `services`):</span></span>  
  
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
  
### <a name="servicemodel-elements"></a><span data-ttu-id="c0e98-110">Elementos do ServiceModel</span><span class="sxs-lookup"><span data-stu-id="c0e98-110">ServiceModel Elements</span></span>  
 <span data-ttu-id="c0e98-111">Você pode usar a seção limitada pelo `system.ServiceModel` elemento para configurar um tipo de serviço com um ou mais pontos finais, bem como configurações para um serviço.</span><span class="sxs-lookup"><span data-stu-id="c0e98-111">You can use the section bounded by the `system.ServiceModel` element to configure a service type with one or more endpoints, as well as settings for a service.</span></span> <span data-ttu-id="c0e98-112">Cada ponto final pode então ser configurado com um endereço, um contrato e um vinculativo.</span><span class="sxs-lookup"><span data-stu-id="c0e98-112">Each endpoint can then be configured with an address, a contract, and a binding.</span></span> <span data-ttu-id="c0e98-113">Para obter mais informações sobre pontos finais, consulte [Visão geral da criação de endpoint](endpoint-creation-overview.md).</span><span class="sxs-lookup"><span data-stu-id="c0e98-113">For more information about endpoints, see [Endpoint Creation Overview](endpoint-creation-overview.md).</span></span> <span data-ttu-id="c0e98-114">Se nenhum ponto final for especificado, o tempo de execução adicionará pontos finais padrão.</span><span class="sxs-lookup"><span data-stu-id="c0e98-114">If no endpoints are specified, the runtime adds default endpoints.</span></span> <span data-ttu-id="c0e98-115">Para obter mais informações sobre pontos de extremidade, associações e comportamentos padrão, confira [Configuração simplificada](simplified-configuration.md) e [Configuração simplificada para serviços WCF](./samples/simplified-configuration-for-wcf-services.md).</span><span class="sxs-lookup"><span data-stu-id="c0e98-115">For more information about default endpoints, bindings, and behaviors, see [Simplified Configuration](simplified-configuration.md) and [Simplified Configuration for WCF Services](./samples/simplified-configuration-for-wcf-services.md).</span></span>  
  
 <span data-ttu-id="c0e98-116">Uma vinculação especifica transportes (HTTP, TCP, tubos, fila de mensagens) e protocolos (Segurança, Confiabilidade, Fluxos de Transação) e consiste em elementos de vinculação, cada um dos quais especifica um aspecto de como um ponto final se comunica com o mundo.</span><span class="sxs-lookup"><span data-stu-id="c0e98-116">A binding specifies transports (HTTP, TCP, pipes, Message Queuing) and protocols (Security, Reliability, Transaction flows) and consists of binding elements, each of which specifies an aspect of how an endpoint communicates with the world.</span></span>  
  
 <span data-ttu-id="c0e98-117">Por exemplo, especificar o [ \<elemento básicoHttpBinding>](../configure-apps/file-schema/wcf/basichttpbinding.md) indica usar HTTP como transporte para um ponto final.</span><span class="sxs-lookup"><span data-stu-id="c0e98-117">For example, specifying the [\<basicHttpBinding>](../configure-apps/file-schema/wcf/basichttpbinding.md) element indicates to use HTTP as the transport for an endpoint.</span></span> <span data-ttu-id="c0e98-118">Isso é usado para conectar o ponto final no tempo de execução quando o serviço usando este ponto final é aberto.</span><span class="sxs-lookup"><span data-stu-id="c0e98-118">This is used to wire up the endpoint at run time when the service using this endpoint is opened.</span></span>  
  
 <span data-ttu-id="c0e98-119">Existem dois tipos de ligações: predefinida e personalizada.</span><span class="sxs-lookup"><span data-stu-id="c0e98-119">There are two kinds of bindings: predefined and custom.</span></span> <span data-ttu-id="c0e98-120">As ligações predefinidas contêm combinações úteis de elementos que são usados em cenários comuns.</span><span class="sxs-lookup"><span data-stu-id="c0e98-120">Predefined bindings contain useful combinations of elements that are used in common scenarios.</span></span> <span data-ttu-id="c0e98-121">Para obter uma lista de tipos de vinculação predefinidos que o WCF fornece, consulte [Vinculações fornecidas pelo sistema](system-provided-bindings.md).</span><span class="sxs-lookup"><span data-stu-id="c0e98-121">For a list of predefined binding types that WCF provides, see [System-Provided Bindings](system-provided-bindings.md).</span></span> <span data-ttu-id="c0e98-122">Se nenhuma coleta de vinculação predefinida tiver a combinação correta de recursos que um aplicativo de serviço precisa, você pode construir vinculações personalizadas para atender aos requisitos do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="c0e98-122">If no predefined binding collection has the correct combination of features that a service application needs, you can construct custom bindings to meet the application's requirements.</span></span> <span data-ttu-id="c0e98-123">Para obter mais informações sobre vinculações personalizadas, consulte [ \<>de vinculação personalizada ](../configure-apps/file-schema/wcf/custombinding.md).</span><span class="sxs-lookup"><span data-stu-id="c0e98-123">For more information about custom bindings, see [\<customBinding>](../configure-apps/file-schema/wcf/custombinding.md).</span></span>  
  
 <span data-ttu-id="c0e98-124">Os quatro exemplos a seguir ilustram as configurações de vinculação mais comuns usadas para configurar um serviço WCF.</span><span class="sxs-lookup"><span data-stu-id="c0e98-124">The following four examples illustrate the most common binding configurations used for setting up a WCF service.</span></span>  
  
#### <a name="specifying-an-endpoint-to-use-a-binding-type"></a><span data-ttu-id="c0e98-125">Especificando um ponto final para usar um tipo de vinculação</span><span class="sxs-lookup"><span data-stu-id="c0e98-125">Specifying an Endpoint to Use a Binding Type</span></span>  
 <span data-ttu-id="c0e98-126">O primeiro exemplo ilustra como especificar um ponto final configurado com um endereço, um contrato e uma vinculação.</span><span class="sxs-lookup"><span data-stu-id="c0e98-126">The first example illustrates how to specify an endpoint configured with an address, a contract, and a binding.</span></span>  
  
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
  
 <span data-ttu-id="c0e98-127">Neste exemplo, `name` o atributo indica para qual tipo de serviço a configuração é.</span><span class="sxs-lookup"><span data-stu-id="c0e98-127">In this example, the `name` attribute indicates which service type the configuration is for.</span></span> <span data-ttu-id="c0e98-128">Quando você cria um serviço `HelloWorld` em seu código com o contrato, ele é inicializado com todos os pontos finais definidos na configuração do exemplo.</span><span class="sxs-lookup"><span data-stu-id="c0e98-128">When you create a service in your code with the `HelloWorld` contract, it is initialized with all of the endpoints defined in the example configuration.</span></span> <span data-ttu-id="c0e98-129">Se o conjunto implementar apenas um `name` contrato de serviço, o atributo pode ser omitido porque o serviço usa o único tipo disponível.</span><span class="sxs-lookup"><span data-stu-id="c0e98-129">If the assembly implements only one service contract, the `name` attribute can be omitted because the service uses the only available type.</span></span> <span data-ttu-id="c0e98-130">O atributo leva uma string, que deve estar no formato`Namespace.Class, AssemblyName, Version=0.0.0.0, Culture=neutral, PublicKeyToken=null`</span><span class="sxs-lookup"><span data-stu-id="c0e98-130">The attribute takes a string, which must be in the format `Namespace.Class, AssemblyName, Version=0.0.0.0, Culture=neutral, PublicKeyToken=null`</span></span>  
  
 <span data-ttu-id="c0e98-131">O `address` atributo especifica o URI que outros pontos finais usam para se comunicar com o serviço.</span><span class="sxs-lookup"><span data-stu-id="c0e98-131">The `address` attribute specifies the URI that other endpoints use to communicate to the service.</span></span> <span data-ttu-id="c0e98-132">O URI pode ser um caminho absoluto ou relativo.</span><span class="sxs-lookup"><span data-stu-id="c0e98-132">The URI can be either an absolute or relative path.</span></span> <span data-ttu-id="c0e98-133">Se um endereço relativo for fornecido, espera-se que o host forneça um endereço base apropriado para o esquema de transporte usado na vinculação.</span><span class="sxs-lookup"><span data-stu-id="c0e98-133">If a relative address is provided, the host is expected to provide a base address that is appropriate for the transport scheme used in the binding.</span></span> <span data-ttu-id="c0e98-134">Se um endereço não estiver configurado, o endereço base é assumido como o endereço para esse ponto final.</span><span class="sxs-lookup"><span data-stu-id="c0e98-134">If an address is not configured, the base address is assumed to be the address for that endpoint.</span></span>  
  
 <span data-ttu-id="c0e98-135">O `contract` atributo especifica o contrato que este ponto final está expondo.</span><span class="sxs-lookup"><span data-stu-id="c0e98-135">The `contract` attribute specifies the contract this endpoint is exposing.</span></span> <span data-ttu-id="c0e98-136">O tipo de implementação do serviço deve implementar o tipo de contrato.</span><span class="sxs-lookup"><span data-stu-id="c0e98-136">The service implementation type must implement the contract type.</span></span> <span data-ttu-id="c0e98-137">Se uma implementação de serviço implementar um único tipo de contrato, essa propriedade poderá ser omitida.</span><span class="sxs-lookup"><span data-stu-id="c0e98-137">If a service implementation implements a single contract type, then this property can be omitted.</span></span>  
  
 <span data-ttu-id="c0e98-138">O `binding` atributo seleciona uma vinculação predefinida ou personalizada para usar para este ponto final específico.</span><span class="sxs-lookup"><span data-stu-id="c0e98-138">The `binding` attribute selects a predefined or custom binding to use for this specific endpoint.</span></span> <span data-ttu-id="c0e98-139">Um ponto final que não seleciona explicitamente uma vinculação `BasicHttpBinding`usa a seleção de vinculação padrão, que é .</span><span class="sxs-lookup"><span data-stu-id="c0e98-139">An endpoint that does not explicitly select a binding uses the default binding selection, which is `BasicHttpBinding`.</span></span>  
  
#### <a name="modifying-a-predefined-binding"></a><span data-ttu-id="c0e98-140">Modificando uma vinculação predefinida</span><span class="sxs-lookup"><span data-stu-id="c0e98-140">Modifying a Predefined Binding</span></span>  
 <span data-ttu-id="c0e98-141">No exemplo a seguir, uma vinculação predefinida é modificada.</span><span class="sxs-lookup"><span data-stu-id="c0e98-141">In the following example, a predefined binding is modified.</span></span> <span data-ttu-id="c0e98-142">Em seguida, ele pode ser usado para configurar qualquer ponto final no serviço.</span><span class="sxs-lookup"><span data-stu-id="c0e98-142">It can then be used to configure any endpoint in the service.</span></span> <span data-ttu-id="c0e98-143">A vinculação é <xref:System.ServiceModel.Configuration.IBindingConfigurationElement.ReceiveTimeout%2A> modificada definindo o valor para 1 segundo.</span><span class="sxs-lookup"><span data-stu-id="c0e98-143">The binding is modified by setting the <xref:System.ServiceModel.Configuration.IBindingConfigurationElement.ReceiveTimeout%2A> value to 1 second.</span></span> <span data-ttu-id="c0e98-144">Observe que a <xref:System.TimeSpan> propriedade retorna um objeto.</span><span class="sxs-lookup"><span data-stu-id="c0e98-144">Note that the property returns a <xref:System.TimeSpan> object.</span></span>  
  
 <span data-ttu-id="c0e98-145">Essa vinculação alterada é encontrada na seção de vinculações.</span><span class="sxs-lookup"><span data-stu-id="c0e98-145">That altered binding is found in the bindings section.</span></span> <span data-ttu-id="c0e98-146">Esta vinculação alterada agora pode ser usada `binding` ao criar `endpoint` qualquer ponto final, definindo o atributo no elemento.</span><span class="sxs-lookup"><span data-stu-id="c0e98-146">This altered binding can now be used when creating any endpoint by setting the `binding` attribute in the `endpoint` element.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="c0e98-147">Se você der um nome `bindingConfiguration` específico à vinculação, o ponto final de serviço especificado deve coincidir com ele.</span><span class="sxs-lookup"><span data-stu-id="c0e98-147">If you give a particular name to the binding, the `bindingConfiguration` specified in the service endpoint must match with it.</span></span>  
  
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
  
## <a name="configuring-a-behavior-to-apply-to-a-service"></a><span data-ttu-id="c0e98-148">Configurando um comportamento para aplicar a um serviço</span><span class="sxs-lookup"><span data-stu-id="c0e98-148">Configuring a Behavior to Apply to a Service</span></span>  
 <span data-ttu-id="c0e98-149">No exemplo a seguir, um comportamento específico é configurado para o tipo de serviço.</span><span class="sxs-lookup"><span data-stu-id="c0e98-149">In the following example, a specific behavior is configured for the service type.</span></span> <span data-ttu-id="c0e98-150">O `ServiceMetadataBehavior` elemento é usado para permitir que a [ServiceModel Metadata Utility Tool (Svcutil.exe)](servicemodel-metadata-utility-tool-svcutil-exe.md) consulte o serviço e gere documentos WSDL (Web Services Description Language, linguagem de descrição de serviços da Web) a partir dos metadados.</span><span class="sxs-lookup"><span data-stu-id="c0e98-150">The `ServiceMetadataBehavior` element is used to enable the [ServiceModel Metadata Utility Tool (Svcutil.exe)](servicemodel-metadata-utility-tool-svcutil-exe.md) to query the service and generate Web Services Description Language (WSDL) documents from the metadata.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="c0e98-151">Se você der um nome `behaviorConfiguration` específico ao comportamento, o especificado na seção serviço ou ponto final deve corresponder a ele.</span><span class="sxs-lookup"><span data-stu-id="c0e98-151">If you give a particular name to the behavior, the `behaviorConfiguration` specified in the service or endpoint section must match it.</span></span>  
  
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
  
 <span data-ttu-id="c0e98-152">A configuração anterior permite que um cliente ligue e obtenha os metadados do serviço digitado "HelloWorld".</span><span class="sxs-lookup"><span data-stu-id="c0e98-152">The preceding configuration enables a client to call and get the metadata of the "HelloWorld" typed service.</span></span>  
  
 `svcutil /config:Client.exe.config http://computer:8080/Hello?wsdl`  
  
## <a name="specifying-a-service-with-two-endpoints-using-different-binding-values"></a><span data-ttu-id="c0e98-153">Especificando um serviço com dois pontos finais usando diferentes valores de vinculação</span><span class="sxs-lookup"><span data-stu-id="c0e98-153">Specifying a Service with Two Endpoints Using Different Binding Values</span></span>  
 <span data-ttu-id="c0e98-154">Neste último exemplo, dois pontos finais `HelloWorld` são configurados para o tipo de serviço.</span><span class="sxs-lookup"><span data-stu-id="c0e98-154">In this last example, two endpoints are configured for the `HelloWorld` service type.</span></span> <span data-ttu-id="c0e98-155">Cada ponto final usa `bindingConfiguration` um atributo personalizado diferente do `basicHttpBinding`mesmo tipo de vinculação (cada um modifica o ).</span><span class="sxs-lookup"><span data-stu-id="c0e98-155">Each endpoint uses a different customized  `bindingConfiguration` attribute of the same binding type (each modifies the `basicHttpBinding`).</span></span>  
  
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
  
 <span data-ttu-id="c0e98-156">Você pode obter o mesmo comportamento usando `protocolMapping` a configuração padrão adicionando uma seção e configurando as vinculações como demonstrado no exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="c0e98-156">You can get the same behavior using the default configuration by adding a `protocolMapping` section and configuring the bindings as demonstrated in the following example.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="c0e98-157">Confira também</span><span class="sxs-lookup"><span data-stu-id="c0e98-157">See also</span></span>

- [<span data-ttu-id="c0e98-158">Configuração simplificada</span><span class="sxs-lookup"><span data-stu-id="c0e98-158">Simplified Configuration</span></span>](simplified-configuration.md)
- [<span data-ttu-id="c0e98-159">Associações fornecidas pelo sistema</span><span class="sxs-lookup"><span data-stu-id="c0e98-159">System-Provided Bindings</span></span>](system-provided-bindings.md)
- [<span data-ttu-id="c0e98-160">Visão geral de criação de ponto de extremidade</span><span class="sxs-lookup"><span data-stu-id="c0e98-160">Endpoint Creation Overview</span></span>](endpoint-creation-overview.md)
- [<span data-ttu-id="c0e98-161">Usando associações para configurar serviços e clientes</span><span class="sxs-lookup"><span data-stu-id="c0e98-161">Using Bindings to Configure Services and Clients</span></span>](using-bindings-to-configure-services-and-clients.md)
