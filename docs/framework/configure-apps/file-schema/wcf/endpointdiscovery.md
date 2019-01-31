---
title: <endpointDiscovery>
ms.date: 03/30/2017
ms.assetid: 70812717-888a-4748-9640-0df6715ff029
ms.openlocfilehash: effceee30abdaa1725b8c8718df22632961871e8
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/30/2019
ms.locfileid: "55266410"
---
# <a name="endpointdiscovery"></a><span data-ttu-id="f1343-101">\<endpointDiscovery></span><span class="sxs-lookup"><span data-stu-id="f1343-101">\<endpointDiscovery></span></span>
<span data-ttu-id="f1343-102">Especifica as várias configurações de descoberta para um ponto de extremidade, como sua capacidade de descoberta, escopos e quaisquer extensões personalizadas para seus metadados.</span><span class="sxs-lookup"><span data-stu-id="f1343-102">Specifies the various discovery settings for an endpoint, such as its discoverability, scopes, and any custom extensions to its metadata.</span></span>  
  
<span data-ttu-id="f1343-103">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="f1343-103">\<system.ServiceModel></span></span>  
<span data-ttu-id="f1343-104">\<comportamentos ></span><span class="sxs-lookup"><span data-stu-id="f1343-104">\<behaviors></span></span>  
<span data-ttu-id="f1343-105">\<endpointBehaviors></span><span class="sxs-lookup"><span data-stu-id="f1343-105">\<endpointBehaviors></span></span>  
<span data-ttu-id="f1343-106">\<behavior></span><span class="sxs-lookup"><span data-stu-id="f1343-106">\<behavior></span></span>  
<span data-ttu-id="f1343-107">\<endpointDiscovery></span><span class="sxs-lookup"><span data-stu-id="f1343-107">\<endpointDiscovery></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f1343-108">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="f1343-108">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="f1343-109">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="f1343-109">Attributes and Elements</span></span>  
 <span data-ttu-id="f1343-110">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="f1343-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="f1343-111">Atributos</span><span class="sxs-lookup"><span data-stu-id="f1343-111">Attributes</span></span>  
  
|<span data-ttu-id="f1343-112">Atributo</span><span class="sxs-lookup"><span data-stu-id="f1343-112">Attribute</span></span>|<span data-ttu-id="f1343-113">Descrição</span><span class="sxs-lookup"><span data-stu-id="f1343-113">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="f1343-114">habilitado</span><span class="sxs-lookup"><span data-stu-id="f1343-114">enabled</span></span>|<span data-ttu-id="f1343-115">Um valor booliano que especifica se descoberta está habilitada nesse ponto de extremidade.</span><span class="sxs-lookup"><span data-stu-id="f1343-115">A Boolean value that specifies whether discoverability is enabled on this endpoint.</span></span> <span data-ttu-id="f1343-116">O padrão é `false`.</span><span class="sxs-lookup"><span data-stu-id="f1343-116">The default is `false`.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="f1343-117">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="f1343-117">Child Elements</span></span>  
  
|<span data-ttu-id="f1343-118">Elemento</span><span class="sxs-lookup"><span data-stu-id="f1343-118">Element</span></span>|<span data-ttu-id="f1343-119">Descrição</span><span class="sxs-lookup"><span data-stu-id="f1343-119">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="f1343-120">\<scopes></span><span class="sxs-lookup"><span data-stu-id="f1343-120">\<scopes></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/scopes.md)|<span data-ttu-id="f1343-121">Uma coleção de URIs de escopo para o ponto de extremidade.</span><span class="sxs-lookup"><span data-stu-id="f1343-121">A collection of scope URIs for the endpoint.</span></span> <span data-ttu-id="f1343-122">Uris de mais de um escopo pode ser associado um ponto de extremidade.</span><span class="sxs-lookup"><span data-stu-id="f1343-122">More than one scope Uris can be associated with a single endpoint.</span></span>|  
|<span data-ttu-id="f1343-123">[\<Extensões >](../../../../../docs/framework/configure-apps/file-schema/wcf/extensions.md) [de \<endpointDiscovery >]</span><span class="sxs-lookup"><span data-stu-id="f1343-123">[\<extensions>](../../../../../docs/framework/configure-apps/file-schema/wcf/extensions.md) [of \<endpointDiscovery>]</span></span>|<span data-ttu-id="f1343-124">Uma coleção de elementos XML que permite que você especifique metadados personalizados para serem publicados para um ponto de extremidade.</span><span class="sxs-lookup"><span data-stu-id="f1343-124">A collection of XML elements that allows you to specify custom metadata to be published for an endpoint.</span></span>|  
|<span data-ttu-id="f1343-125">\<types></span><span class="sxs-lookup"><span data-stu-id="f1343-125">\<types></span></span>|<span data-ttu-id="f1343-126">Uma coleção de interfaces para pesquisar.</span><span class="sxs-lookup"><span data-stu-id="f1343-126">A collection of interfaces to search for.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="f1343-127">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="f1343-127">Parent Elements</span></span>  
  
|<span data-ttu-id="f1343-128">Elemento</span><span class="sxs-lookup"><span data-stu-id="f1343-128">Element</span></span>|<span data-ttu-id="f1343-129">Descrição</span><span class="sxs-lookup"><span data-stu-id="f1343-129">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="f1343-130">\<behavior></span><span class="sxs-lookup"><span data-stu-id="f1343-130">\<behavior></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md)|<span data-ttu-id="f1343-131">Especifica um elemento de comportamento.</span><span class="sxs-lookup"><span data-stu-id="f1343-131">Specifies a behavior element.</span></span>|  
|||  
  
## <a name="remarks"></a><span data-ttu-id="f1343-132">Comentários</span><span class="sxs-lookup"><span data-stu-id="f1343-132">Remarks</span></span>  
 <span data-ttu-id="f1343-133">Quando adicionado à configuração de comportamento do ponto de extremidade e com o `enabled` atributo definido como `true`, este elemento de configuração permite que a sua capacidade de descoberta.</span><span class="sxs-lookup"><span data-stu-id="f1343-133">When added to the endpoint’s behavior configuration and with the `enabled` attribute set to `true`, this configuration element enables its discoverability.</span></span> <span data-ttu-id="f1343-134">Além disso, você pode usar o [ \<escopos >](../../../../../docs/framework/configure-apps/file-schema/wcf/scopes.md)elemento filho a especificação de escopo personalizado Uris que podem ser usados para filtrar pontos de extremidade de serviço durante consulta, bem como o [ \<extensões >](../../../../../docs/framework/configure-apps/file-schema/wcf/extensions.md) elemento filho para especificar metadados personalizados que devem ser publicados junto com os metadados detectáveis padrão (EPR, ContractTypeName, BindingName, escopo e ListenURI).</span><span class="sxs-lookup"><span data-stu-id="f1343-134">In addition, you can use the [\<scopes>](../../../../../docs/framework/configure-apps/file-schema/wcf/scopes.md)child element to specifying custom scope Uris that can be used to filter service endpoints during query, as well as the [\<extensions>](../../../../../docs/framework/configure-apps/file-schema/wcf/extensions.md) child element to specify custom metadata that should be published along with the standard discoverable metadata (EPR, ContractTypeName, BindingName, Scope and ListenURI).</span></span>  
  
 <span data-ttu-id="f1343-135">Este elemento de configuração é dependente de [ \<serviceDiscovery >](../../../../../docs/framework/configure-apps/file-schema/wcf/servicediscovery.md) elemento que fornece o controle de nível de serviço de descoberta.</span><span class="sxs-lookup"><span data-stu-id="f1343-135">This configuration element is dependent on the [\<serviceDiscovery>](../../../../../docs/framework/configure-apps/file-schema/wcf/servicediscovery.md) element that provides the service level control of discoverability.</span></span> <span data-ttu-id="f1343-136">Isso significa que as configurações desse elemento são ignoradas se [ \<serviceDiscovery >](../../../../../docs/framework/configure-apps/file-schema/wcf/servicediscovery.md) não está presente na configuração.</span><span class="sxs-lookup"><span data-stu-id="f1343-136">This means that this element’s settings are ignored if [\<serviceDiscovery>](../../../../../docs/framework/configure-apps/file-schema/wcf/servicediscovery.md) is not present in the configuration.</span></span>  
  
## <a name="example"></a><span data-ttu-id="f1343-137">Exemplo</span><span class="sxs-lookup"><span data-stu-id="f1343-137">Example</span></span>  
 <span data-ttu-id="f1343-138">O exemplo de configuração a seguir especifica os escopos de filtragem e os metadados de extensão a ser publicado para um ponto de extremidade.</span><span class="sxs-lookup"><span data-stu-id="f1343-138">The following configuration example specifies filtering scopes and extension metadata to be published for an endpoint.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="f1343-139">Consulte também</span><span class="sxs-lookup"><span data-stu-id="f1343-139">See also</span></span>
- <xref:System.ServiceModel.Discovery.EndpointDiscoveryBehavior>
