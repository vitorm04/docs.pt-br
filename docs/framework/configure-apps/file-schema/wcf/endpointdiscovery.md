---
title: <endpointDiscovery>
ms.date: 03/30/2017
ms.assetid: 70812717-888a-4748-9640-0df6715ff029
ms.openlocfilehash: 5cb64c54067ba695f67d86c0026db77ebbe7d5ee
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69919044"
---
# <a name="endpointdiscovery"></a><span data-ttu-id="e3a65-101">\<> endpointDiscovery</span><span class="sxs-lookup"><span data-stu-id="e3a65-101">\<endpointDiscovery></span></span>
<span data-ttu-id="e3a65-102">Especifica as várias configurações de descoberta para um ponto de extremidade, como sua descoberta, escopos e quaisquer extensões personalizadas para seus metadados.</span><span class="sxs-lookup"><span data-stu-id="e3a65-102">Specifies the various discovery settings for an endpoint, such as its discoverability, scopes, and any custom extensions to its metadata.</span></span>  
  
<span data-ttu-id="e3a65-103">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="e3a65-103">\<system.ServiceModel></span></span>  
<span data-ttu-id="e3a65-104">\<comportamentos ></span><span class="sxs-lookup"><span data-stu-id="e3a65-104">\<behaviors></span></span>  
<span data-ttu-id="e3a65-105">\<endpointBehaviors></span><span class="sxs-lookup"><span data-stu-id="e3a65-105">\<endpointBehaviors></span></span>  
<span data-ttu-id="e3a65-106">\<> de comportamento</span><span class="sxs-lookup"><span data-stu-id="e3a65-106">\<behavior></span></span>  
<span data-ttu-id="e3a65-107">\<> endpointDiscovery</span><span class="sxs-lookup"><span data-stu-id="e3a65-107">\<endpointDiscovery></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e3a65-108">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="e3a65-108">Syntax</span></span>  
  
```xml  
<behaviors>
  <endpointBehaviors>
    <behavior name="String">
      <endpointDiscovery enabled="Boolean">
        <scopes>
          <add scope="URI"/>
        </scopes>
        <extensions />
      </endpointDiscovery>
    </behavior>
  </endpointBehaviors>
</behaviors>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="e3a65-109">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="e3a65-109">Attributes and Elements</span></span>  
 <span data-ttu-id="e3a65-110">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="e3a65-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="e3a65-111">Atributos</span><span class="sxs-lookup"><span data-stu-id="e3a65-111">Attributes</span></span>  
  
|<span data-ttu-id="e3a65-112">Atributo</span><span class="sxs-lookup"><span data-stu-id="e3a65-112">Attribute</span></span>|<span data-ttu-id="e3a65-113">Descrição</span><span class="sxs-lookup"><span data-stu-id="e3a65-113">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="e3a65-114">habilitado</span><span class="sxs-lookup"><span data-stu-id="e3a65-114">enabled</span></span>|<span data-ttu-id="e3a65-115">Um valor booliano que especifica se a descoberta está habilitada neste ponto de extremidade.</span><span class="sxs-lookup"><span data-stu-id="e3a65-115">A Boolean value that specifies whether discoverability is enabled on this endpoint.</span></span> <span data-ttu-id="e3a65-116">O padrão é `false`.</span><span class="sxs-lookup"><span data-stu-id="e3a65-116">The default is `false`.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="e3a65-117">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="e3a65-117">Child Elements</span></span>  
  
|<span data-ttu-id="e3a65-118">Elemento</span><span class="sxs-lookup"><span data-stu-id="e3a65-118">Element</span></span>|<span data-ttu-id="e3a65-119">Descrição</span><span class="sxs-lookup"><span data-stu-id="e3a65-119">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="e3a65-120">\<scopes></span><span class="sxs-lookup"><span data-stu-id="e3a65-120">\<scopes></span></span>](scopes.md)|<span data-ttu-id="e3a65-121">Uma coleção de URIs de escopo para o ponto de extremidade.</span><span class="sxs-lookup"><span data-stu-id="e3a65-121">A collection of scope URIs for the endpoint.</span></span> <span data-ttu-id="e3a65-122">Mais de um URI de escopo pode ser associado a um único ponto de extremidade.</span><span class="sxs-lookup"><span data-stu-id="e3a65-122">More than one scope Uris can be associated with a single endpoint.</span></span>|  
|<span data-ttu-id="e3a65-123">extensões > [of \<endpointDiscovery >] [ \<](extensions.md)</span><span class="sxs-lookup"><span data-stu-id="e3a65-123">[\<extensions>](extensions.md) [of \<endpointDiscovery>]</span></span>|<span data-ttu-id="e3a65-124">Uma coleção de elementos XML que permite que você especifique metadados personalizados a serem publicados para um ponto de extremidade.</span><span class="sxs-lookup"><span data-stu-id="e3a65-124">A collection of XML elements that allows you to specify custom metadata to be published for an endpoint.</span></span>|  
|<span data-ttu-id="e3a65-125">\<types></span><span class="sxs-lookup"><span data-stu-id="e3a65-125">\<types></span></span>|<span data-ttu-id="e3a65-126">Uma coleção de interfaces a serem pesquisadas.</span><span class="sxs-lookup"><span data-stu-id="e3a65-126">A collection of interfaces to search for.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="e3a65-127">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="e3a65-127">Parent Elements</span></span>  
  
|<span data-ttu-id="e3a65-128">Elemento</span><span class="sxs-lookup"><span data-stu-id="e3a65-128">Element</span></span>|<span data-ttu-id="e3a65-129">Descrição</span><span class="sxs-lookup"><span data-stu-id="e3a65-129">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="e3a65-130">\<> de comportamento</span><span class="sxs-lookup"><span data-stu-id="e3a65-130">\<behavior></span></span>](behavior-of-endpointbehaviors.md)|<span data-ttu-id="e3a65-131">Especifica um elemento de comportamento.</span><span class="sxs-lookup"><span data-stu-id="e3a65-131">Specifies a behavior element.</span></span>|  
|||  
  
## <a name="remarks"></a><span data-ttu-id="e3a65-132">Comentários</span><span class="sxs-lookup"><span data-stu-id="e3a65-132">Remarks</span></span>  
 <span data-ttu-id="e3a65-133">Quando adicionado à configuração de comportamento do ponto de extremidade e `enabled` com o atributo `true`definido como, esse elemento de configuração permite sua capacidade de descoberta.</span><span class="sxs-lookup"><span data-stu-id="e3a65-133">When added to the endpoint’s behavior configuration and with the `enabled` attribute set to `true`, this configuration element enables its discoverability.</span></span> <span data-ttu-id="e3a65-134">Além disso, você pode usar os [ \<escopos >](scopes.md)elemento filho para especificar URIs de escopo personalizado que podem ser usados para filtrar pontos de extremidade de serviço durante a consulta, bem como as [ \<extensões >](extensions.md) elemento filho para especificar personalizado metadados que devem ser publicados juntamente com os metadados detectáveis padrão (EPR, ContractTypeName, BindingName, Scope e ListenURI).</span><span class="sxs-lookup"><span data-stu-id="e3a65-134">In addition, you can use the [\<scopes>](scopes.md)child element to specifying custom scope Uris that can be used to filter service endpoints during query, as well as the [\<extensions>](extensions.md) child element to specify custom metadata that should be published along with the standard discoverable metadata (EPR, ContractTypeName, BindingName, Scope and ListenURI).</span></span>  
  
 <span data-ttu-id="e3a65-135">Esse elemento de configuração é dependente do elemento de [ \<>](servicediscovery.md) do Service Discovery que fornece o controle de nível de serviço de descoberta.</span><span class="sxs-lookup"><span data-stu-id="e3a65-135">This configuration element is dependent on the [\<serviceDiscovery>](servicediscovery.md) element that provides the service level control of discoverability.</span></span> <span data-ttu-id="e3a65-136">Isso significa que as configurações desse elemento serão ignoradas [ \<](servicediscovery.md) se o > do indiscovery não estiver presente na configuração.</span><span class="sxs-lookup"><span data-stu-id="e3a65-136">This means that this element’s settings are ignored if [\<serviceDiscovery>](servicediscovery.md) is not present in the configuration.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e3a65-137">Exemplo</span><span class="sxs-lookup"><span data-stu-id="e3a65-137">Example</span></span>  
 <span data-ttu-id="e3a65-138">O exemplo de configuração a seguir especifica os escopos de filtragem e os metadados de extensão a serem publicados para um ponto de extremidade.</span><span class="sxs-lookup"><span data-stu-id="e3a65-138">The following configuration example specifies filtering scopes and extension metadata to be published for an endpoint.</span></span>  
  
```xml  
<services>
  <service name="CalculatorService"
           behaviorConfiguration="CalculatorServiceBehavior">
    <endpoint binding="basicHttpBinding"
              address="calculator"
              contract="ICalculatorService"
              behaviorConfiguration="calculatorEndpointBehavior" />
  </service>
</services>
<behaviors>
  <serviceBehaviors>
    <behavior name="CalculatorServiceBehavior">
      <serviceDiscovery />
    </behavior>
  </serviceBehaviors>
  <endpointBehaviors>
    <behavior name="calculatorEndpointBehavior">
      <endpointDiscovery enabled="true">
        <scopes>
          <add scope="http://contoso/test1" />
          <add scope="http://contoso/test2" />
        </scopes>
        <extensions>
          <e:Publisher xmlns:e="http://example.org">
            <e:Name>The Example Organization</e:Name>
            <e:Address>One Example Way, ExampleTown, EX 12345</e:Address>
            <e:Contact>support@example.org</e:Contact>
          </e:Publisher>
          <AnotherCustomMetadata>Custom Metadata</AnotherCustomMetadata>
        </extensions>
      </endpointDiscovery>
    </behavior>
  </endpointBehaviors>
</behaviors>
```  
  
## <a name="see-also"></a><span data-ttu-id="e3a65-139">Consulte também</span><span class="sxs-lookup"><span data-stu-id="e3a65-139">See also</span></span>

- <xref:System.ServiceModel.Discovery.EndpointDiscoveryBehavior>
