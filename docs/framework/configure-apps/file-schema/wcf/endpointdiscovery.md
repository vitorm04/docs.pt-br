---
title: <endpointDiscovery>
ms.date: 03/30/2017
ms.assetid: 70812717-888a-4748-9640-0df6715ff029
ms.openlocfilehash: 98b1655f42b7b43604ed4ab9d66870ec204a9590
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/06/2019
ms.locfileid: "70398013"
---
# <a name="endpointdiscovery"></a><span data-ttu-id="ff925-101">\<> endpointDiscovery</span><span class="sxs-lookup"><span data-stu-id="ff925-101">\<endpointDiscovery></span></span>
<span data-ttu-id="ff925-102">Especifica as várias configurações de descoberta para um ponto de extremidade, como sua descoberta, escopos e quaisquer extensões personalizadas para seus metadados.</span><span class="sxs-lookup"><span data-stu-id="ff925-102">Specifies the various discovery settings for an endpoint, such as its discoverability, scopes, and any custom extensions to its metadata.</span></span>  
  
<span data-ttu-id="ff925-103">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="ff925-103">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="ff925-104">&nbsp;&nbsp;[ **\<> de System. serviceModel**](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="ff925-104">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="ff925-105">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<comportamentos >** ](behaviors.md)</span><span class="sxs-lookup"><span data-stu-id="ff925-105">&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)</span></span>\
<span data-ttu-id="ff925-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> endpointBehaviors**](endpointbehaviors.md)</span><span class="sxs-lookup"><span data-stu-id="ff925-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<endpointBehaviors>**](endpointbehaviors.md)</span></span>\
<span data-ttu-id="ff925-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> de comportamento**](behavior-of-endpointbehaviors.md)</span><span class="sxs-lookup"><span data-stu-id="ff925-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-endpointbehaviors.md)</span></span>\
<span data-ttu-id="ff925-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<> endpointDiscovery**</span><span class="sxs-lookup"><span data-stu-id="ff925-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<endpointDiscovery>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ff925-109">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="ff925-109">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="ff925-110">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="ff925-110">Attributes and Elements</span></span>  
 <span data-ttu-id="ff925-111">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="ff925-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="ff925-112">Atributos</span><span class="sxs-lookup"><span data-stu-id="ff925-112">Attributes</span></span>  
  
|<span data-ttu-id="ff925-113">Atributo</span><span class="sxs-lookup"><span data-stu-id="ff925-113">Attribute</span></span>|<span data-ttu-id="ff925-114">Descrição</span><span class="sxs-lookup"><span data-stu-id="ff925-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="ff925-115">enabled</span><span class="sxs-lookup"><span data-stu-id="ff925-115">enabled</span></span>|<span data-ttu-id="ff925-116">Um valor booliano que especifica se a descoberta está habilitada neste ponto de extremidade.</span><span class="sxs-lookup"><span data-stu-id="ff925-116">A Boolean value that specifies whether discoverability is enabled on this endpoint.</span></span> <span data-ttu-id="ff925-117">O padrão é `false`.</span><span class="sxs-lookup"><span data-stu-id="ff925-117">The default is `false`.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="ff925-118">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="ff925-118">Child Elements</span></span>  
  
|<span data-ttu-id="ff925-119">Elemento</span><span class="sxs-lookup"><span data-stu-id="ff925-119">Element</span></span>|<span data-ttu-id="ff925-120">Descrição</span><span class="sxs-lookup"><span data-stu-id="ff925-120">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="ff925-121">\<scopes></span><span class="sxs-lookup"><span data-stu-id="ff925-121">\<scopes></span></span>](scopes.md)|<span data-ttu-id="ff925-122">Uma coleção de URIs de escopo para o ponto de extremidade.</span><span class="sxs-lookup"><span data-stu-id="ff925-122">A collection of scope URIs for the endpoint.</span></span> <span data-ttu-id="ff925-123">Mais de um URI de escopo pode ser associado a um único ponto de extremidade.</span><span class="sxs-lookup"><span data-stu-id="ff925-123">More than one scope Uris can be associated with a single endpoint.</span></span>|  
|<span data-ttu-id="ff925-124">extensões > [of \<endpointDiscovery >] [ \<](extensions.md)</span><span class="sxs-lookup"><span data-stu-id="ff925-124">[\<extensions>](extensions.md) [of \<endpointDiscovery>]</span></span>|<span data-ttu-id="ff925-125">Uma coleção de elementos XML que permite que você especifique metadados personalizados a serem publicados para um ponto de extremidade.</span><span class="sxs-lookup"><span data-stu-id="ff925-125">A collection of XML elements that allows you to specify custom metadata to be published for an endpoint.</span></span>|  
|<span data-ttu-id="ff925-126">\<types></span><span class="sxs-lookup"><span data-stu-id="ff925-126">\<types></span></span>|<span data-ttu-id="ff925-127">Uma coleção de interfaces a serem pesquisadas.</span><span class="sxs-lookup"><span data-stu-id="ff925-127">A collection of interfaces to search for.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="ff925-128">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="ff925-128">Parent Elements</span></span>  
  
|<span data-ttu-id="ff925-129">Elemento</span><span class="sxs-lookup"><span data-stu-id="ff925-129">Element</span></span>|<span data-ttu-id="ff925-130">Descrição</span><span class="sxs-lookup"><span data-stu-id="ff925-130">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="ff925-131">\<> de comportamento</span><span class="sxs-lookup"><span data-stu-id="ff925-131">\<behavior></span></span>](behavior-of-endpointbehaviors.md)|<span data-ttu-id="ff925-132">Especifica um elemento de comportamento.</span><span class="sxs-lookup"><span data-stu-id="ff925-132">Specifies a behavior element.</span></span>|  
|||  
  
## <a name="remarks"></a><span data-ttu-id="ff925-133">Comentários</span><span class="sxs-lookup"><span data-stu-id="ff925-133">Remarks</span></span>  
 <span data-ttu-id="ff925-134">Quando adicionado à configuração de comportamento do ponto de extremidade e `enabled` com o atributo `true`definido como, esse elemento de configuração permite sua capacidade de descoberta.</span><span class="sxs-lookup"><span data-stu-id="ff925-134">When added to the endpoint’s behavior configuration and with the `enabled` attribute set to `true`, this configuration element enables its discoverability.</span></span> <span data-ttu-id="ff925-135">Além disso, você pode usar os [ \<escopos >](scopes.md)elemento filho para especificar URIs de escopo personalizado que podem ser usados para filtrar pontos de extremidade de serviço durante a consulta, bem como as [ \<extensões >](extensions.md) elemento filho para especificar personalizado metadados que devem ser publicados juntamente com os metadados detectáveis padrão (EPR, ContractTypeName, BindingName, Scope e ListenURI).</span><span class="sxs-lookup"><span data-stu-id="ff925-135">In addition, you can use the [\<scopes>](scopes.md)child element to specifying custom scope Uris that can be used to filter service endpoints during query, as well as the [\<extensions>](extensions.md) child element to specify custom metadata that should be published along with the standard discoverable metadata (EPR, ContractTypeName, BindingName, Scope and ListenURI).</span></span>  
  
 <span data-ttu-id="ff925-136">Esse elemento de configuração é dependente do elemento de [ \<>](servicediscovery.md) do Service Discovery que fornece o controle de nível de serviço de descoberta.</span><span class="sxs-lookup"><span data-stu-id="ff925-136">This configuration element is dependent on the [\<serviceDiscovery>](servicediscovery.md) element that provides the service level control of discoverability.</span></span> <span data-ttu-id="ff925-137">Isso significa que as configurações desse elemento serão ignoradas se [ \<o > do indiscovery](servicediscovery.md) não estiver presente na configuração.</span><span class="sxs-lookup"><span data-stu-id="ff925-137">This means that this element’s settings are ignored if [\<serviceDiscovery>](servicediscovery.md) is not present in the configuration.</span></span>  
  
## <a name="example"></a><span data-ttu-id="ff925-138">Exemplo</span><span class="sxs-lookup"><span data-stu-id="ff925-138">Example</span></span>  
 <span data-ttu-id="ff925-139">O exemplo de configuração a seguir especifica os escopos de filtragem e os metadados de extensão a serem publicados para um ponto de extremidade.</span><span class="sxs-lookup"><span data-stu-id="ff925-139">The following configuration example specifies filtering scopes and extension metadata to be published for an endpoint.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="ff925-140">Consulte também</span><span class="sxs-lookup"><span data-stu-id="ff925-140">See also</span></span>

- <xref:System.ServiceModel.Discovery.EndpointDiscoveryBehavior>
