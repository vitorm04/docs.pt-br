---
title: <endpointDiscovery>
ms.date: 03/30/2017
ms.assetid: 70812717-888a-4748-9640-0df6715ff029
ms.openlocfilehash: 621c742e3bb06ce91fa5a6b8951351295f73df9e
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91185802"
---
# \<endpointDiscovery>

<span data-ttu-id="a094a-101">Especifica as várias configurações de descoberta para um ponto de extremidade, como sua descoberta, escopos e quaisquer extensões personalizadas para seus metadados.</span><span class="sxs-lookup"><span data-stu-id="a094a-101">Specifies the various discovery settings for an endpoint, such as its discoverability, scopes, and any custom extensions to its metadata.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<endpointBehaviors>**](endpointbehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-endpointbehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<endpointDiscovery>**  
  
## <a name="syntax"></a><span data-ttu-id="a094a-102">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="a094a-102">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="a094a-103">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="a094a-103">Attributes and Elements</span></span>  

 <span data-ttu-id="a094a-104">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="a094a-104">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="a094a-105">Atributos</span><span class="sxs-lookup"><span data-stu-id="a094a-105">Attributes</span></span>  
  
|<span data-ttu-id="a094a-106">Atributo</span><span class="sxs-lookup"><span data-stu-id="a094a-106">Attribute</span></span>|<span data-ttu-id="a094a-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="a094a-107">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="a094a-108">Habilitado</span><span class="sxs-lookup"><span data-stu-id="a094a-108">enabled</span></span>|<span data-ttu-id="a094a-109">Um valor booliano que especifica se a descoberta está habilitada neste ponto de extremidade.</span><span class="sxs-lookup"><span data-stu-id="a094a-109">A Boolean value that specifies whether discoverability is enabled on this endpoint.</span></span> <span data-ttu-id="a094a-110">O padrão é `false`.</span><span class="sxs-lookup"><span data-stu-id="a094a-110">The default is `false`.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="a094a-111">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="a094a-111">Child Elements</span></span>  
  
|<span data-ttu-id="a094a-112">Elemento</span><span class="sxs-lookup"><span data-stu-id="a094a-112">Element</span></span>|<span data-ttu-id="a094a-113">Descrição</span><span class="sxs-lookup"><span data-stu-id="a094a-113">Description</span></span>|  
|-------------|-----------------|  
|[\<scopes>](scopes.md)|<span data-ttu-id="a094a-114">Uma coleção de URIs de escopo para o ponto de extremidade.</span><span class="sxs-lookup"><span data-stu-id="a094a-114">A collection of scope URIs for the endpoint.</span></span> <span data-ttu-id="a094a-115">Mais de um URI de escopo pode ser associado a um único ponto de extremidade.</span><span class="sxs-lookup"><span data-stu-id="a094a-115">More than one scope Uris can be associated with a single endpoint.</span></span>|  
|<span data-ttu-id="a094a-116">[\<extensions>](extensions.md) [de \<endpointDiscovery> ]</span><span class="sxs-lookup"><span data-stu-id="a094a-116">[\<extensions>](extensions.md) [of \<endpointDiscovery>]</span></span>|<span data-ttu-id="a094a-117">Uma coleção de elementos XML que permite que você especifique metadados personalizados a serem publicados para um ponto de extremidade.</span><span class="sxs-lookup"><span data-stu-id="a094a-117">A collection of XML elements that allows you to specify custom metadata to be published for an endpoint.</span></span>|  
|\<types>|<span data-ttu-id="a094a-118">Uma coleção de interfaces a serem pesquisadas.</span><span class="sxs-lookup"><span data-stu-id="a094a-118">A collection of interfaces to search for.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="a094a-119">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="a094a-119">Parent Elements</span></span>  
  
|<span data-ttu-id="a094a-120">Elemento</span><span class="sxs-lookup"><span data-stu-id="a094a-120">Element</span></span>|<span data-ttu-id="a094a-121">Descrição</span><span class="sxs-lookup"><span data-stu-id="a094a-121">Description</span></span>|  
|-------------|-----------------|  
|[\<behavior>](behavior-of-endpointbehaviors.md)|<span data-ttu-id="a094a-122">Especifica um elemento de comportamento.</span><span class="sxs-lookup"><span data-stu-id="a094a-122">Specifies a behavior element.</span></span>|  
|||  
  
## <a name="remarks"></a><span data-ttu-id="a094a-123">Comentários</span><span class="sxs-lookup"><span data-stu-id="a094a-123">Remarks</span></span>  

 <span data-ttu-id="a094a-124">Quando adicionado à configuração de comportamento do ponto de extremidade e com o `enabled` atributo definido como `true` , esse elemento de configuração permite sua capacidade de descoberta.</span><span class="sxs-lookup"><span data-stu-id="a094a-124">When added to the endpoint’s behavior configuration and with the `enabled` attribute set to `true`, this configuration element enables its discoverability.</span></span> <span data-ttu-id="a094a-125">Além disso, você pode usar o [\<scopes>](scopes.md) elemento filho para especificar URIs de escopo personalizados que podem ser usados para filtrar pontos de extremidade de serviço durante a consulta, bem como o [\<extensions>](extensions.md) elemento filho para especificar metadados personalizados que devem ser publicados juntamente com os metadados detectáveis padrão (EPR, ContractTypeName, BindingName, Scope e ListenURI).</span><span class="sxs-lookup"><span data-stu-id="a094a-125">In addition, you can use the [\<scopes>](scopes.md)child element to specifying custom scope Uris that can be used to filter service endpoints during query, as well as the [\<extensions>](extensions.md) child element to specify custom metadata that should be published along with the standard discoverable metadata (EPR, ContractTypeName, BindingName, Scope and ListenURI).</span></span>  
  
 <span data-ttu-id="a094a-126">Esse elemento de configuração é dependente do [\<serviceDiscovery>](servicediscovery.md) elemento que fornece o controle de nível de serviço de descoberta.</span><span class="sxs-lookup"><span data-stu-id="a094a-126">This configuration element is dependent on the [\<serviceDiscovery>](servicediscovery.md) element that provides the service level control of discoverability.</span></span> <span data-ttu-id="a094a-127">Isso significa que as configurações desse elemento serão ignoradas se [\<serviceDiscovery>](servicediscovery.md) não estiver presente na configuração.</span><span class="sxs-lookup"><span data-stu-id="a094a-127">This means that this element’s settings are ignored if [\<serviceDiscovery>](servicediscovery.md) is not present in the configuration.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a094a-128">Exemplo</span><span class="sxs-lookup"><span data-stu-id="a094a-128">Example</span></span>  

 <span data-ttu-id="a094a-129">O exemplo de configuração a seguir especifica os escopos de filtragem e os metadados de extensão a serem publicados para um ponto de extremidade.</span><span class="sxs-lookup"><span data-stu-id="a094a-129">The following configuration example specifies filtering scopes and extension metadata to be published for an endpoint.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="a094a-130">Confira também</span><span class="sxs-lookup"><span data-stu-id="a094a-130">See also</span></span>

- <xref:System.ServiceModel.Discovery.EndpointDiscoveryBehavior>
