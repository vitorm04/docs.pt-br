---
title: '&lt;endpointDiscovery&gt;'
ms.date: 03/30/2017
ms.assetid: 70812717-888a-4748-9640-0df6715ff029
ms.openlocfilehash: c5971ce79ac2f03fbdc91653d5d282804e98cf8a
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32754243"
---
# <a name="ltendpointdiscoverygt"></a><span data-ttu-id="d04d6-102">&lt;endpointDiscovery&gt;</span><span class="sxs-lookup"><span data-stu-id="d04d6-102">&lt;endpointDiscovery&gt;</span></span>
<span data-ttu-id="d04d6-103">Especifica as várias configurações de descoberta para um ponto de extremidade, como sua capacidade de descoberta, escopos e quaisquer extensões personalizadas para seus metadados.</span><span class="sxs-lookup"><span data-stu-id="d04d6-103">Specifies the various discovery settings for an endpoint, such as its discoverability, scopes, and any custom extensions to its metadata.</span></span>  
  
<span data-ttu-id="d04d6-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="d04d6-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="d04d6-105">\<comportamentos ></span><span class="sxs-lookup"><span data-stu-id="d04d6-105">\<behaviors></span></span>  
<span data-ttu-id="d04d6-106">\<endpointBehaviors></span><span class="sxs-lookup"><span data-stu-id="d04d6-106">\<endpointBehaviors></span></span>  
<span data-ttu-id="d04d6-107">\<comportamento ></span><span class="sxs-lookup"><span data-stu-id="d04d6-107">\<behavior></span></span>  
<span data-ttu-id="d04d6-108">\<endpointDiscovery ></span><span class="sxs-lookup"><span data-stu-id="d04d6-108">\<endpointDiscovery></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d04d6-109">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="d04d6-109">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="d04d6-110">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="d04d6-110">Attributes and Elements</span></span>  
 <span data-ttu-id="d04d6-111">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="d04d6-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="d04d6-112">Atributos</span><span class="sxs-lookup"><span data-stu-id="d04d6-112">Attributes</span></span>  
  
|<span data-ttu-id="d04d6-113">Atributo</span><span class="sxs-lookup"><span data-stu-id="d04d6-113">Attribute</span></span>|<span data-ttu-id="d04d6-114">Descrição</span><span class="sxs-lookup"><span data-stu-id="d04d6-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="d04d6-115">habilitado</span><span class="sxs-lookup"><span data-stu-id="d04d6-115">enabled</span></span>|<span data-ttu-id="d04d6-116">Um valor booliano que especifica se a descoberta está habilitada neste ponto de extremidade.</span><span class="sxs-lookup"><span data-stu-id="d04d6-116">A Boolean value that that specifies whether discoverability is enabled on this endpoint.</span></span> <span data-ttu-id="d04d6-117">O padrão é `false`.</span><span class="sxs-lookup"><span data-stu-id="d04d6-117">The default is `false`.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="d04d6-118">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="d04d6-118">Child Elements</span></span>  
  
|<span data-ttu-id="d04d6-119">Elemento</span><span class="sxs-lookup"><span data-stu-id="d04d6-119">Element</span></span>|<span data-ttu-id="d04d6-120">Descrição</span><span class="sxs-lookup"><span data-stu-id="d04d6-120">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="d04d6-121">\<escopos ></span><span class="sxs-lookup"><span data-stu-id="d04d6-121">\<scopes></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/scopes.md)|<span data-ttu-id="d04d6-122">Uma coleção de URIs de escopo para o ponto de extremidade.</span><span class="sxs-lookup"><span data-stu-id="d04d6-122">A collection of scope URIs for the endpoint.</span></span> <span data-ttu-id="d04d6-123">Uris de mais de um escopo pode ser associado um ponto de extremidade.</span><span class="sxs-lookup"><span data-stu-id="d04d6-123">More than one scope Uris can be associated with a single endpoint.</span></span>|  
|<span data-ttu-id="d04d6-124">[\<Extensões >](../../../../../docs/framework/configure-apps/file-schema/wcf/extensions.md) [de \<endpointDiscovery >]</span><span class="sxs-lookup"><span data-stu-id="d04d6-124">[\<extensions>](../../../../../docs/framework/configure-apps/file-schema/wcf/extensions.md) [of \<endpointDiscovery>]</span></span>|<span data-ttu-id="d04d6-125">Uma coleção de elementos XML que permite que você especifique metadados personalizados a serem publicados para um ponto de extremidade.</span><span class="sxs-lookup"><span data-stu-id="d04d6-125">A collection of XML elements that allows you to specify custom metadata to be published for an endpoint.</span></span>|  
|<span data-ttu-id="d04d6-126">\<tipos ></span><span class="sxs-lookup"><span data-stu-id="d04d6-126">\<types></span></span>|<span data-ttu-id="d04d6-127">Uma coleção de interfaces para pesquisar.</span><span class="sxs-lookup"><span data-stu-id="d04d6-127">A collection of interfaces to search for.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="d04d6-128">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="d04d6-128">Parent Elements</span></span>  
  
|<span data-ttu-id="d04d6-129">Elemento</span><span class="sxs-lookup"><span data-stu-id="d04d6-129">Element</span></span>|<span data-ttu-id="d04d6-130">Descrição</span><span class="sxs-lookup"><span data-stu-id="d04d6-130">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="d04d6-131">\<comportamento ></span><span class="sxs-lookup"><span data-stu-id="d04d6-131">\<behavior></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md)|<span data-ttu-id="d04d6-132">Especifica um elemento de comportamento.</span><span class="sxs-lookup"><span data-stu-id="d04d6-132">Specifies a behavior element.</span></span>|  
|||  
  
## <a name="remarks"></a><span data-ttu-id="d04d6-133">Comentários</span><span class="sxs-lookup"><span data-stu-id="d04d6-133">Remarks</span></span>  
 <span data-ttu-id="d04d6-134">Quando adicionado à configuração de comportamento do ponto de extremidade e com o `enabled` atributo definido como `true`, este elemento de configuração permite que a sua capacidade de descoberta.</span><span class="sxs-lookup"><span data-stu-id="d04d6-134">When added to the endpoint’s behavior configuration and with the `enabled` attribute set to `true`, this configuration element enables its discoverability.</span></span> <span data-ttu-id="d04d6-135">Além disso, você pode usar o [ \<escopos >](../../../../../docs/framework/configure-apps/file-schema/wcf/scopes.md)elemento filho à especificação de escopo personalizado Uris que podem ser usados para filtrar pontos de extremidade de serviço durante a consulta, bem como o [ \<extensões >](../../../../../docs/framework/configure-apps/file-schema/wcf/extensions.md) elemento filho para especificar metadados personalizados que devem ser publicados junto com os metadados detectável padrão (EPR, ContractTypeName, BindingName, escopo e ListenURI).</span><span class="sxs-lookup"><span data-stu-id="d04d6-135">In addition, you can use the [\<scopes>](../../../../../docs/framework/configure-apps/file-schema/wcf/scopes.md)child element to specifying custom scope Uris that can be used to filter service endpoints during query, as well as the [\<extensions>](../../../../../docs/framework/configure-apps/file-schema/wcf/extensions.md) child element to specify custom metadata that should be published along with the standard discoverable metadata (EPR, ContractTypeName, BindingName, Scope and ListenURI).</span></span>  
  
 <span data-ttu-id="d04d6-136">Este elemento de configuração é dependente de [ \<serviceDiscovery >](../../../../../docs/framework/configure-apps/file-schema/wcf/servicediscovery.md) elemento que fornece o controle de nível de serviço de descoberta.</span><span class="sxs-lookup"><span data-stu-id="d04d6-136">This configuration element is dependent on the [\<serviceDiscovery>](../../../../../docs/framework/configure-apps/file-schema/wcf/servicediscovery.md) element that provides the service level control of discoverability.</span></span> <span data-ttu-id="d04d6-137">Isso significa que as configurações do elemento são ignoradas se [ \<serviceDiscovery >](../../../../../docs/framework/configure-apps/file-schema/wcf/servicediscovery.md) não está presente na configuração.</span><span class="sxs-lookup"><span data-stu-id="d04d6-137">This means that this element’s settings are ignored if [\<serviceDiscovery>](../../../../../docs/framework/configure-apps/file-schema/wcf/servicediscovery.md) is not present in the configuration.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d04d6-138">Exemplo</span><span class="sxs-lookup"><span data-stu-id="d04d6-138">Example</span></span>  
 <span data-ttu-id="d04d6-139">O exemplo de configuração a seguir especifica os escopos de filtragem e metadados de extensão a ser publicado para um ponto de extremidade.</span><span class="sxs-lookup"><span data-stu-id="d04d6-139">The following configuration example specifies filtering scopes and extension metadata to be published for an endpoint.</span></span>  
  
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
          <add scope="http://contoso/test1"/>  
          <add scope="http://contoso/test2"/>  
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
  
## <a name="see-also"></a><span data-ttu-id="d04d6-140">Consulte também</span><span class="sxs-lookup"><span data-stu-id="d04d6-140">See Also</span></span>  
 <xref:System.ServiceModel.Discovery.EndpointDiscoveryBehavior>
