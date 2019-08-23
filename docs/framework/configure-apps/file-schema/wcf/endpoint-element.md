---
title: Elemento <endpoint>
ms.date: 03/30/2017
ms.assetid: 2fc8fedc-78d0-4e87-8142-fbfd26c15a4e
ms.openlocfilehash: 71ddb3b860870ee8feeeb36c3f64fa7bfebb0f10
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69925821"
---
# <a name="endpoint-element"></a><span data-ttu-id="44291-102">\<elemento de > do ponto de extremidade</span><span class="sxs-lookup"><span data-stu-id="44291-102">\<endpoint> element</span></span>
<span data-ttu-id="44291-103">Especifica a associação, o contrato e as propriedades de endereço para um ponto de extremidade de serviço, que é usado para expor serviços.</span><span class="sxs-lookup"><span data-stu-id="44291-103">Specifies binding, contract, and address properties for a service endpoint, which is used to expose services.</span></span>  
  
 <span data-ttu-id="44291-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="44291-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="44291-105">\<> de serviço</span><span class="sxs-lookup"><span data-stu-id="44291-105">\<service></span></span>  
<span data-ttu-id="44291-106">\<endpoint></span><span class="sxs-lookup"><span data-stu-id="44291-106">\<endpoint></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="44291-107">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="44291-107">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="44291-108">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="44291-108">Attributes and Elements</span></span>  
 <span data-ttu-id="44291-109">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="44291-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="44291-110">Atributos</span><span class="sxs-lookup"><span data-stu-id="44291-110">Attributes</span></span>  
  
|<span data-ttu-id="44291-111">Atributo</span><span class="sxs-lookup"><span data-stu-id="44291-111">Attribute</span></span>|<span data-ttu-id="44291-112">Descrição</span><span class="sxs-lookup"><span data-stu-id="44291-112">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="44291-113">endereço</span><span class="sxs-lookup"><span data-stu-id="44291-113">address</span></span>|<span data-ttu-id="44291-114">Uma cadeia de caracteres que contém o endereço do ponto de extremidade.</span><span class="sxs-lookup"><span data-stu-id="44291-114">A string that contains the address of the endpoint.</span></span> <span data-ttu-id="44291-115">O endereço pode ser especificado como um endereço absoluto ou relativo.</span><span class="sxs-lookup"><span data-stu-id="44291-115">The address can be specified as an absolute or relative address.</span></span> <span data-ttu-id="44291-116">Se um endereço relativo for fornecido, espera-se que o host forneça um endereço base apropriado para o esquema de transporte usado na associação.</span><span class="sxs-lookup"><span data-stu-id="44291-116">If a relative address is provided, the host is expected to provide a base address appropriate for the transport scheme used in the binding.</span></span> <span data-ttu-id="44291-117">Se um endereço não estiver configurado, presume-se que o endereço base seja o endereço para esse ponto de extremidade.</span><span class="sxs-lookup"><span data-stu-id="44291-117">If an address is not configured, the base address is assumed to be the address for that endpoint.</span></span><br /><br /> <span data-ttu-id="44291-118">O padrão é uma cadeia de caracteres vazia.</span><span class="sxs-lookup"><span data-stu-id="44291-118">The default is an empty string.</span></span>|  
|<span data-ttu-id="44291-119">behaviorConfiguration</span><span class="sxs-lookup"><span data-stu-id="44291-119">behaviorConfiguration</span></span>|<span data-ttu-id="44291-120">Uma cadeia de caracteres que contém o nome do comportamento a ser usado no ponto de extremidade.</span><span class="sxs-lookup"><span data-stu-id="44291-120">A string that contains the name of the behavior to be used in the endpoint.</span></span>|  
|<span data-ttu-id="44291-121">associação</span><span class="sxs-lookup"><span data-stu-id="44291-121">binding</span></span>|<span data-ttu-id="44291-122">Atributo de cadeia de caracteres necessário que especifica o tipo de associação a ser usado.</span><span class="sxs-lookup"><span data-stu-id="44291-122">Required string attribute that specifies the type of binding to use.</span></span> <span data-ttu-id="44291-123">O tipo deve ter uma seção de configuração registrada para ser referenciado.</span><span class="sxs-lookup"><span data-stu-id="44291-123">The type must have a registered configuration section in order to be referenced.</span></span> <span data-ttu-id="44291-124">O tipo é registrado pelo nome da seção, em vez de pelo nome do tipo da associação.</span><span class="sxs-lookup"><span data-stu-id="44291-124">The type is the registered by section name, rather than by the type name of the binding.</span></span>|  
|<span data-ttu-id="44291-125">bindingConfiguration</span><span class="sxs-lookup"><span data-stu-id="44291-125">bindingConfiguration</span></span>|<span data-ttu-id="44291-126">Uma cadeia de caracteres que especifica o nome de associação da associação a ser usada quando o ponto de extremidade é instanciado.</span><span class="sxs-lookup"><span data-stu-id="44291-126">A string that specifies the binding name of the binding to use when the endpoint is instantiated.</span></span> <span data-ttu-id="44291-127">O nome da associação deve estar no escopo no ponto em que o ponto de extremidade é definido.</span><span class="sxs-lookup"><span data-stu-id="44291-127">The binding name must be in scope at the point the endpoint is defined.</span></span> <span data-ttu-id="44291-128">O padrão é uma cadeia de caracteres vazia.</span><span class="sxs-lookup"><span data-stu-id="44291-128">The default is an empty string.</span></span><br /><br /> <span data-ttu-id="44291-129">Esse atributo é usado em conjunto com `binding` para fazer referência a uma configuração de associação específica no arquivo de configuração.</span><span class="sxs-lookup"><span data-stu-id="44291-129">This attribute is used in conjunction with `binding` to reference a specific binding configuration in the configuration file.</span></span> <span data-ttu-id="44291-130">Defina esse atributo se você estiver tentando usar uma associação personalizada.</span><span class="sxs-lookup"><span data-stu-id="44291-130">Set this attribute if you are attempting to use a custom binding.</span></span> <span data-ttu-id="44291-131">Caso contrário, uma exceção pode ser lançada.</span><span class="sxs-lookup"><span data-stu-id="44291-131">Otherwise, an exception may be thrown.</span></span>|  
|<span data-ttu-id="44291-132">bindingName</span><span class="sxs-lookup"><span data-stu-id="44291-132">bindingName</span></span>|<span data-ttu-id="44291-133">Uma cadeia de caracteres que especifica o nome qualificado exclusivo da Associação para exportação de definição por meio de WSDL.</span><span class="sxs-lookup"><span data-stu-id="44291-133">A string that specifies the unique qualified name of the binding for definition export through WSDL.</span></span> <span data-ttu-id="44291-134">O padrão é uma cadeia de caracteres vazia.</span><span class="sxs-lookup"><span data-stu-id="44291-134">The default is an empty string.</span></span>|  
|<span data-ttu-id="44291-135">bindingNamespace</span><span class="sxs-lookup"><span data-stu-id="44291-135">bindingNamespace</span></span>|<span data-ttu-id="44291-136">Uma cadeia de caracteres que especifica o nome qualificado do namespace da Associação para exportação de definição por meio de WSDL.</span><span class="sxs-lookup"><span data-stu-id="44291-136">A string that specifies the qualified name of the namespace of the binding for definition export through WSDL.</span></span> <span data-ttu-id="44291-137">O padrão é uma cadeia de caracteres vazia.</span><span class="sxs-lookup"><span data-stu-id="44291-137">The default is an empty string.</span></span>|  
|<span data-ttu-id="44291-138">contrato</span><span class="sxs-lookup"><span data-stu-id="44291-138">contract</span></span>|<span data-ttu-id="44291-139">Uma cadeia de caracteres que indica qual contrato este ponto de extremidade está expondo.</span><span class="sxs-lookup"><span data-stu-id="44291-139">A string that indicates which contract this endpoint is exposing.</span></span> <span data-ttu-id="44291-140">O assembly deve implementar o tipo de contrato.</span><span class="sxs-lookup"><span data-stu-id="44291-140">The assembly must implement the contract type.</span></span> <span data-ttu-id="44291-141">Se uma implementação de serviço implementar um único tipo de contrato, essa propriedade poderá ser omitida.</span><span class="sxs-lookup"><span data-stu-id="44291-141">If a service implementation implements a single contract type, then this property can be omitted.</span></span> <span data-ttu-id="44291-142">O padrão é uma cadeia de caracteres vazia.</span><span class="sxs-lookup"><span data-stu-id="44291-142">The default is an empty string.</span></span>|  
|<span data-ttu-id="44291-143">endpointConfiguration</span><span class="sxs-lookup"><span data-stu-id="44291-143">endpointConfiguration</span></span>|<span data-ttu-id="44291-144">Uma cadeia de caracteres que especifica o nome do ponto de extremidade padrão que é `kind` definido pelo atributo, que faz referência às informações de configuração adicionais desse ponto de extremidade padrão.</span><span class="sxs-lookup"><span data-stu-id="44291-144">A string that specifies the name of the standard endpoint that is set by the `kind` attribute, which references to the additional configuration information of this standard endpoint.</span></span> <span data-ttu-id="44291-145">O mesmo nome deve ser definido na `<standardEndpoints>` seção.</span><span class="sxs-lookup"><span data-stu-id="44291-145">The same name must be defined in the `<standardEndpoints>` section.</span></span>|  
|<span data-ttu-id="44291-146">isSystemEndpoint</span><span class="sxs-lookup"><span data-stu-id="44291-146">isSystemEndpoint</span></span>|<span data-ttu-id="44291-147">Um valor booliano que especifica se um ponto de extremidade é um ponto de extremidade de infraestrutura.</span><span class="sxs-lookup"><span data-stu-id="44291-147">A Boolean value that specifies whether an endpoint is an infrastructure endpoint.</span></span>|  
|<span data-ttu-id="44291-148">quase</span><span class="sxs-lookup"><span data-stu-id="44291-148">kind</span></span>|<span data-ttu-id="44291-149">Uma cadeia de caracteres que especifica o tipo de ponto de extremidade padrão aplicado.</span><span class="sxs-lookup"><span data-stu-id="44291-149">A string that specifies the type of standard endpoint applied.</span></span> <span data-ttu-id="44291-150">O tipo deve ser registrado na seção `<extensions>` ou em machine.config. Se nada for especificado, um ponto de extremidade de serviço comum será criado.</span><span class="sxs-lookup"><span data-stu-id="44291-150">The type must be registered in the `<extensions>` section or in machine.config. If nothing is specified, a common service endpoint is created.</span></span>|  
|<span data-ttu-id="44291-151">listenUriMode</span><span class="sxs-lookup"><span data-stu-id="44291-151">listenUriMode</span></span>|<span data-ttu-id="44291-152">Especifica como o transporte trata o `ListenUri` fornecido para o serviço escutar.</span><span class="sxs-lookup"><span data-stu-id="44291-152">Specifies how the transport treats the `ListenUri` provided for the service to listen on.</span></span> <span data-ttu-id="44291-153">Os valores válidos são</span><span class="sxs-lookup"><span data-stu-id="44291-153">Valid values are</span></span><br /><br /> <span data-ttu-id="44291-154">-Explícito</span><span class="sxs-lookup"><span data-stu-id="44291-154">-   Explicit</span></span><br /><span data-ttu-id="44291-155">-Exclusivo</span><span class="sxs-lookup"><span data-stu-id="44291-155">-   Unique</span></span><br /><br /> <span data-ttu-id="44291-156">O valor padrão é Explicit.</span><span class="sxs-lookup"><span data-stu-id="44291-156">The default value is Explicit.</span></span>|  
|<span data-ttu-id="44291-157">listenUri</span><span class="sxs-lookup"><span data-stu-id="44291-157">listenUri</span></span>|<span data-ttu-id="44291-158">Uma cadeia de caracteres que especifica o URI no qual o ponto de extremidade de serviço escuta.</span><span class="sxs-lookup"><span data-stu-id="44291-158">A string that specifies the URI at which the service endpoint listens.</span></span> <span data-ttu-id="44291-159">O padrão é uma cadeia de caracteres vazia.</span><span class="sxs-lookup"><span data-stu-id="44291-159">The default is an empty string.</span></span>|  
|<span data-ttu-id="44291-160">name</span><span class="sxs-lookup"><span data-stu-id="44291-160">name</span></span>|<span data-ttu-id="44291-161">Atributo opcional.</span><span class="sxs-lookup"><span data-stu-id="44291-161">Optional attribute.</span></span> <span data-ttu-id="44291-162">Uma cadeia de caracteres que especifica o nome do ponto de extremidade de serviço.</span><span class="sxs-lookup"><span data-stu-id="44291-162">A string that specifies the name the service endpoint.</span></span> <span data-ttu-id="44291-163">O valor padrão é a concatenação do nome da associação e o nome da descrição do contrato.</span><span class="sxs-lookup"><span data-stu-id="44291-163">The default value is the concatenation of the binding name and the contract description name.</span></span> <span data-ttu-id="44291-164">Os serviços podem ter vários pontos de extremidade e, portanto, `name` o atributo do Endpoint é diferente do nome do serviço.</span><span class="sxs-lookup"><span data-stu-id="44291-164">Services may have multiple endpoints, so the endpoint’s `name` attribute is distinct from the name of the service.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="44291-165">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="44291-165">Child Elements</span></span>  
  
|<span data-ttu-id="44291-166">Elemento</span><span class="sxs-lookup"><span data-stu-id="44291-166">Element</span></span>|<span data-ttu-id="44291-167">Descrição</span><span class="sxs-lookup"><span data-stu-id="44291-167">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="44291-168">\<headers></span><span class="sxs-lookup"><span data-stu-id="44291-168">\<headers></span></span>](headers.md)|<span data-ttu-id="44291-169">Uma coleção de cabeçalhos de endereço.</span><span class="sxs-lookup"><span data-stu-id="44291-169">A collection of address headers.</span></span>|  
|[<span data-ttu-id="44291-170">\<identity></span><span class="sxs-lookup"><span data-stu-id="44291-170">\<identity></span></span>](identity.md)|<span data-ttu-id="44291-171">Uma identidade que permite a autenticação de um ponto de extremidade por outros pontos de extremidades que trocam mensagens com ele.</span><span class="sxs-lookup"><span data-stu-id="44291-171">An identity that enables the authentication of an endpoint by other endpoints exchanging messages with it.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="44291-172">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="44291-172">Parent Elements</span></span>  
  
|<span data-ttu-id="44291-173">Elemento</span><span class="sxs-lookup"><span data-stu-id="44291-173">Element</span></span>|<span data-ttu-id="44291-174">Descrição</span><span class="sxs-lookup"><span data-stu-id="44291-174">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="44291-175">\<service></span><span class="sxs-lookup"><span data-stu-id="44291-175">\<service></span></span>](service.md)|<span data-ttu-id="44291-176">Uma seção de configuração que define uma lista de pontos de extremidade aos quais um cliente pode se conectar.</span><span class="sxs-lookup"><span data-stu-id="44291-176">A configuration section that defines a list of endpoints that a client can connect to.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="44291-177">Exemplo</span><span class="sxs-lookup"><span data-stu-id="44291-177">Example</span></span>  
 <span data-ttu-id="44291-178">Este é um exemplo de uma configuração de ponto de extremidade de serviço.</span><span class="sxs-lookup"><span data-stu-id="44291-178">This is an example of a service endpoint configuration.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="44291-179">Consulte também</span><span class="sxs-lookup"><span data-stu-id="44291-179">See also</span></span>

- <xref:System.ServiceModel.Configuration.ServiceEndpointElement>
- <xref:System.ServiceModel.EndpointAddress>
- <xref:System.ServiceModel.Description.ServiceEndpoint>
- [<span data-ttu-id="44291-180">Extremidade Endereços, associações e contratos</span><span class="sxs-lookup"><span data-stu-id="44291-180">Endpoints: Addresses, Bindings, and Contracts</span></span>](../../../wcf/feature-details/endpoints-addresses-bindings-and-contracts.md)
- [<span data-ttu-id="44291-181">Como: Criar um ponto de extremidade de serviço na configuração</span><span class="sxs-lookup"><span data-stu-id="44291-181">How to: Create a Service Endpoint in Configuration</span></span>](../../../wcf/feature-details/how-to-create-a-service-endpoint-in-configuration.md)
