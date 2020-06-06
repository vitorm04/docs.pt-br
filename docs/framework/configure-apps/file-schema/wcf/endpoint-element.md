---
title: Elemento <endpoint>
ms.date: 03/30/2017
ms.assetid: 2fc8fedc-78d0-4e87-8142-fbfd26c15a4e
ms.openlocfilehash: fb9d3bf9b5f1a742abcc70d78af026c179ec4c4d
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/06/2020
ms.locfileid: "70855385"
---
# <a name="endpoint-element"></a><span data-ttu-id="a16fb-102">Elemento \<endpoint></span><span class="sxs-lookup"><span data-stu-id="a16fb-102">\<endpoint> element</span></span>
<span data-ttu-id="a16fb-103">Especifica a associação, o contrato e as propriedades de endereço para um ponto de extremidade de serviço, que é usado para expor serviços.</span><span class="sxs-lookup"><span data-stu-id="a16fb-103">Specifies binding, contract, and address properties for a service endpoint, which is used to expose services.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<services>**](services.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<service>**](service.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<endpoint>**  
  
## <a name="syntax"></a><span data-ttu-id="a16fb-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="a16fb-104">Syntax</span></span>  
  
```xml  
<endpoint address="String"
          behaviorConfiguration="String"
          binding="String"
          bindingConfiguration="String"
          bindingName="String"
          bindingNamespace="String"
          contract="String"
          endpointConfiguration="String"
          isSystemEndpoint="Boolean"
          kind="String"
          listenUriMode="Explicit/Unique"
          listenUri="Uri">
</endpoint>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="a16fb-105">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="a16fb-105">Attributes and Elements</span></span>  
 <span data-ttu-id="a16fb-106">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="a16fb-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="a16fb-107">Atributos</span><span class="sxs-lookup"><span data-stu-id="a16fb-107">Attributes</span></span>  
  
|<span data-ttu-id="a16fb-108">Atributo</span><span class="sxs-lookup"><span data-stu-id="a16fb-108">Attribute</span></span>|<span data-ttu-id="a16fb-109">Descrição</span><span class="sxs-lookup"><span data-stu-id="a16fb-109">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="a16fb-110">address</span><span class="sxs-lookup"><span data-stu-id="a16fb-110">address</span></span>|<span data-ttu-id="a16fb-111">Uma cadeia de caracteres que contém o endereço do ponto de extremidade.</span><span class="sxs-lookup"><span data-stu-id="a16fb-111">A string that contains the address of the endpoint.</span></span> <span data-ttu-id="a16fb-112">O endereço pode ser especificado como um endereço absoluto ou relativo.</span><span class="sxs-lookup"><span data-stu-id="a16fb-112">The address can be specified as an absolute or relative address.</span></span> <span data-ttu-id="a16fb-113">Se um endereço relativo for fornecido, espera-se que o host forneça um endereço base apropriado para o esquema de transporte usado na associação.</span><span class="sxs-lookup"><span data-stu-id="a16fb-113">If a relative address is provided, the host is expected to provide a base address appropriate for the transport scheme used in the binding.</span></span> <span data-ttu-id="a16fb-114">Se um endereço não estiver configurado, presume-se que o endereço base seja o endereço para esse ponto de extremidade.</span><span class="sxs-lookup"><span data-stu-id="a16fb-114">If an address is not configured, the base address is assumed to be the address for that endpoint.</span></span><br /><br /> <span data-ttu-id="a16fb-115">O padrão é uma cadeia de caracteres vazia.</span><span class="sxs-lookup"><span data-stu-id="a16fb-115">The default is an empty string.</span></span>|  
|<span data-ttu-id="a16fb-116">behaviorConfiguration</span><span class="sxs-lookup"><span data-stu-id="a16fb-116">behaviorConfiguration</span></span>|<span data-ttu-id="a16fb-117">Uma cadeia de caracteres que contém o nome do comportamento a ser usado no ponto de extremidade.</span><span class="sxs-lookup"><span data-stu-id="a16fb-117">A string that contains the name of the behavior to be used in the endpoint.</span></span>|  
|<span data-ttu-id="a16fb-118">associação</span><span class="sxs-lookup"><span data-stu-id="a16fb-118">binding</span></span>|<span data-ttu-id="a16fb-119">Atributo de cadeia de caracteres necessário que especifica o tipo de associação a ser usado.</span><span class="sxs-lookup"><span data-stu-id="a16fb-119">Required string attribute that specifies the type of binding to use.</span></span> <span data-ttu-id="a16fb-120">O tipo deve ter uma seção de configuração registrada para ser referenciado.</span><span class="sxs-lookup"><span data-stu-id="a16fb-120">The type must have a registered configuration section in order to be referenced.</span></span> <span data-ttu-id="a16fb-121">O tipo é registrado pelo nome da seção, em vez de pelo nome do tipo da associação.</span><span class="sxs-lookup"><span data-stu-id="a16fb-121">The type is the registered by section name, rather than by the type name of the binding.</span></span>|  
|<span data-ttu-id="a16fb-122">bindingConfiguration</span><span class="sxs-lookup"><span data-stu-id="a16fb-122">bindingConfiguration</span></span>|<span data-ttu-id="a16fb-123">Uma cadeia de caracteres que especifica o nome de associação da associação a ser usada quando o ponto de extremidade é instanciado.</span><span class="sxs-lookup"><span data-stu-id="a16fb-123">A string that specifies the binding name of the binding to use when the endpoint is instantiated.</span></span> <span data-ttu-id="a16fb-124">O nome da associação deve estar no escopo no ponto em que o ponto de extremidade é definido.</span><span class="sxs-lookup"><span data-stu-id="a16fb-124">The binding name must be in scope at the point the endpoint is defined.</span></span> <span data-ttu-id="a16fb-125">O padrão é uma cadeia de caracteres vazia.</span><span class="sxs-lookup"><span data-stu-id="a16fb-125">The default is an empty string.</span></span><br /><br /> <span data-ttu-id="a16fb-126">Esse atributo é usado em conjunto com `binding` para fazer referência a uma configuração de associação específica no arquivo de configuração.</span><span class="sxs-lookup"><span data-stu-id="a16fb-126">This attribute is used in conjunction with `binding` to reference a specific binding configuration in the configuration file.</span></span> <span data-ttu-id="a16fb-127">Defina esse atributo se você estiver tentando usar uma associação personalizada.</span><span class="sxs-lookup"><span data-stu-id="a16fb-127">Set this attribute if you are attempting to use a custom binding.</span></span> <span data-ttu-id="a16fb-128">Caso contrário, uma exceção pode ser lançada.</span><span class="sxs-lookup"><span data-stu-id="a16fb-128">Otherwise, an exception may be thrown.</span></span>|  
|<span data-ttu-id="a16fb-129">BindingName</span><span class="sxs-lookup"><span data-stu-id="a16fb-129">bindingName</span></span>|<span data-ttu-id="a16fb-130">Uma cadeia de caracteres que especifica o nome qualificado exclusivo da Associação para exportação de definição por meio de WSDL.</span><span class="sxs-lookup"><span data-stu-id="a16fb-130">A string that specifies the unique qualified name of the binding for definition export through WSDL.</span></span> <span data-ttu-id="a16fb-131">O padrão é uma cadeia de caracteres vazia.</span><span class="sxs-lookup"><span data-stu-id="a16fb-131">The default is an empty string.</span></span>|  
|<span data-ttu-id="a16fb-132">bindingNamespace</span><span class="sxs-lookup"><span data-stu-id="a16fb-132">bindingNamespace</span></span>|<span data-ttu-id="a16fb-133">Uma cadeia de caracteres que especifica o nome qualificado do namespace da Associação para exportação de definição por meio de WSDL.</span><span class="sxs-lookup"><span data-stu-id="a16fb-133">A string that specifies the qualified name of the namespace of the binding for definition export through WSDL.</span></span> <span data-ttu-id="a16fb-134">O padrão é uma cadeia de caracteres vazia.</span><span class="sxs-lookup"><span data-stu-id="a16fb-134">The default is an empty string.</span></span>|  
|<span data-ttu-id="a16fb-135">contrato</span><span class="sxs-lookup"><span data-stu-id="a16fb-135">contract</span></span>|<span data-ttu-id="a16fb-136">Uma cadeia de caracteres que indica qual contrato este ponto de extremidade está expondo.</span><span class="sxs-lookup"><span data-stu-id="a16fb-136">A string that indicates which contract this endpoint is exposing.</span></span> <span data-ttu-id="a16fb-137">O assembly deve implementar o tipo de contrato.</span><span class="sxs-lookup"><span data-stu-id="a16fb-137">The assembly must implement the contract type.</span></span> <span data-ttu-id="a16fb-138">Se uma implementação de serviço implementar um único tipo de contrato, essa propriedade poderá ser omitida.</span><span class="sxs-lookup"><span data-stu-id="a16fb-138">If a service implementation implements a single contract type, then this property can be omitted.</span></span> <span data-ttu-id="a16fb-139">O padrão é uma cadeia de caracteres vazia.</span><span class="sxs-lookup"><span data-stu-id="a16fb-139">The default is an empty string.</span></span>|  
|<span data-ttu-id="a16fb-140">endpointConfiguration</span><span class="sxs-lookup"><span data-stu-id="a16fb-140">endpointConfiguration</span></span>|<span data-ttu-id="a16fb-141">Uma cadeia de caracteres que especifica o nome do ponto de extremidade padrão que é definido pelo `kind` atributo, que faz referência às informações de configuração adicionais desse ponto de extremidade padrão.</span><span class="sxs-lookup"><span data-stu-id="a16fb-141">A string that specifies the name of the standard endpoint that is set by the `kind` attribute, which references to the additional configuration information of this standard endpoint.</span></span> <span data-ttu-id="a16fb-142">O mesmo nome deve ser definido na `<standardEndpoints>` seção.</span><span class="sxs-lookup"><span data-stu-id="a16fb-142">The same name must be defined in the `<standardEndpoints>` section.</span></span>|  
|<span data-ttu-id="a16fb-143">isSystemEndpoint</span><span class="sxs-lookup"><span data-stu-id="a16fb-143">isSystemEndpoint</span></span>|<span data-ttu-id="a16fb-144">Um valor booliano que especifica se um ponto de extremidade é um ponto de extremidade de infraestrutura.</span><span class="sxs-lookup"><span data-stu-id="a16fb-144">A Boolean value that specifies whether an endpoint is an infrastructure endpoint.</span></span>|  
|<span data-ttu-id="a16fb-145">kind</span><span class="sxs-lookup"><span data-stu-id="a16fb-145">kind</span></span>|<span data-ttu-id="a16fb-146">Uma cadeia de caracteres que especifica o tipo de ponto de extremidade padrão aplicado.</span><span class="sxs-lookup"><span data-stu-id="a16fb-146">A string that specifies the type of standard endpoint applied.</span></span> <span data-ttu-id="a16fb-147">O tipo deve ser registrado na `<extensions>` seção ou em Machine. config. Se nada for especificado, um ponto de extremidade de serviço comum será criado.</span><span class="sxs-lookup"><span data-stu-id="a16fb-147">The type must be registered in the `<extensions>` section or in machine.config. If nothing is specified, a common service endpoint is created.</span></span>|  
|<span data-ttu-id="a16fb-148">listenUriMode</span><span class="sxs-lookup"><span data-stu-id="a16fb-148">listenUriMode</span></span>|<span data-ttu-id="a16fb-149">Especifica como o transporte trata o `ListenUri` fornecido para o serviço escutar.</span><span class="sxs-lookup"><span data-stu-id="a16fb-149">Specifies how the transport treats the `ListenUri` provided for the service to listen on.</span></span> <span data-ttu-id="a16fb-150">Os valores válidos são</span><span class="sxs-lookup"><span data-stu-id="a16fb-150">Valid values are</span></span><br /><br /> <span data-ttu-id="a16fb-151">-Explícito</span><span class="sxs-lookup"><span data-stu-id="a16fb-151">-   Explicit</span></span><br /><span data-ttu-id="a16fb-152">-Exclusivo</span><span class="sxs-lookup"><span data-stu-id="a16fb-152">-   Unique</span></span><br /><br /> <span data-ttu-id="a16fb-153">O valor padrão é Explicit.</span><span class="sxs-lookup"><span data-stu-id="a16fb-153">The default value is Explicit.</span></span>|  
|<span data-ttu-id="a16fb-154">listenUri</span><span class="sxs-lookup"><span data-stu-id="a16fb-154">listenUri</span></span>|<span data-ttu-id="a16fb-155">Uma cadeia de caracteres que especifica o URI no qual o ponto de extremidade de serviço escuta.</span><span class="sxs-lookup"><span data-stu-id="a16fb-155">A string that specifies the URI at which the service endpoint listens.</span></span> <span data-ttu-id="a16fb-156">O padrão é uma cadeia de caracteres vazia.</span><span class="sxs-lookup"><span data-stu-id="a16fb-156">The default is an empty string.</span></span>|  
|<span data-ttu-id="a16fb-157">name</span><span class="sxs-lookup"><span data-stu-id="a16fb-157">name</span></span>|<span data-ttu-id="a16fb-158">Atributo opcional.</span><span class="sxs-lookup"><span data-stu-id="a16fb-158">Optional attribute.</span></span> <span data-ttu-id="a16fb-159">Uma cadeia de caracteres que especifica o nome do ponto de extremidade de serviço.</span><span class="sxs-lookup"><span data-stu-id="a16fb-159">A string that specifies the name the service endpoint.</span></span> <span data-ttu-id="a16fb-160">O valor padrão é a concatenação do nome da associação e o nome da descrição do contrato.</span><span class="sxs-lookup"><span data-stu-id="a16fb-160">The default value is the concatenation of the binding name and the contract description name.</span></span> <span data-ttu-id="a16fb-161">Os serviços podem ter vários pontos de extremidade e, portanto, o atributo do Endpoint `name` é diferente do nome do serviço.</span><span class="sxs-lookup"><span data-stu-id="a16fb-161">Services may have multiple endpoints, so the endpoint’s `name` attribute is distinct from the name of the service.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="a16fb-162">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="a16fb-162">Child Elements</span></span>  
  
|<span data-ttu-id="a16fb-163">Elemento</span><span class="sxs-lookup"><span data-stu-id="a16fb-163">Element</span></span>|<span data-ttu-id="a16fb-164">Descrição</span><span class="sxs-lookup"><span data-stu-id="a16fb-164">Description</span></span>|  
|-------------|-----------------|  
|[\<headers>](headers.md)|<span data-ttu-id="a16fb-165">Uma coleção de cabeçalhos de endereço.</span><span class="sxs-lookup"><span data-stu-id="a16fb-165">A collection of address headers.</span></span>|  
|[\<identity>](identity.md)|<span data-ttu-id="a16fb-166">Uma identidade que permite a autenticação de um ponto de extremidade por outros pontos de extremidades que trocam mensagens com ele.</span><span class="sxs-lookup"><span data-stu-id="a16fb-166">An identity that enables the authentication of an endpoint by other endpoints exchanging messages with it.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="a16fb-167">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="a16fb-167">Parent Elements</span></span>  
  
|<span data-ttu-id="a16fb-168">Elemento</span><span class="sxs-lookup"><span data-stu-id="a16fb-168">Element</span></span>|<span data-ttu-id="a16fb-169">Descrição</span><span class="sxs-lookup"><span data-stu-id="a16fb-169">Description</span></span>|  
|-------------|-----------------|  
|[\<service>](service.md)|<span data-ttu-id="a16fb-170">Uma seção de configuração que define uma lista de pontos de extremidade aos quais um cliente pode se conectar.</span><span class="sxs-lookup"><span data-stu-id="a16fb-170">A configuration section that defines a list of endpoints that a client can connect to.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="a16fb-171">Exemplo</span><span class="sxs-lookup"><span data-stu-id="a16fb-171">Example</span></span>  
 <span data-ttu-id="a16fb-172">Este é um exemplo de uma configuração de ponto de extremidade de serviço.</span><span class="sxs-lookup"><span data-stu-id="a16fb-172">This is an example of a service endpoint configuration.</span></span>  
  
```xml  
<endpoint address="/HelloWorld/"
          bindingConfiguration="usingDefaults"
          bindingName="MyBinding"
          binding="customBinding"
          contract="HelloWorld">
  <headers>
    <region xmlns="http://tempuri.org/">EastCoast</region>
    <member xmlns="http://tempuri.org/">Gold</member>
  </headers>
</endpoint>
```  
  
## <a name="see-also"></a><span data-ttu-id="a16fb-173">Confira também</span><span class="sxs-lookup"><span data-stu-id="a16fb-173">See also</span></span>

- <xref:System.ServiceModel.Configuration.ServiceEndpointElement>
- <xref:System.ServiceModel.EndpointAddress>
- <xref:System.ServiceModel.Description.ServiceEndpoint>
- [<span data-ttu-id="a16fb-174">Pontos de extremidade: endereços, associações e contratos</span><span class="sxs-lookup"><span data-stu-id="a16fb-174">Endpoints: Addresses, Bindings, and Contracts</span></span>](../../../wcf/feature-details/endpoints-addresses-bindings-and-contracts.md)
- [<span data-ttu-id="a16fb-175">Como criar um ponto de extremidade de serviço em configuração</span><span class="sxs-lookup"><span data-stu-id="a16fb-175">How to: Create a Service Endpoint in Configuration</span></span>](../../../wcf/feature-details/how-to-create-a-service-endpoint-in-configuration.md)
