---
title: <add> de <contractTypeNames>
ms.date: 03/30/2017
ms.assetid: 03aff6be-5dfb-4a64-ada3-e36227cd43c7
ms.openlocfilehash: 696752470aa39c2bcc66a1337f84119031742ae9
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/10/2019
ms.locfileid: "70850537"
---
# <a name="add-of-contracttypenames"></a><span data-ttu-id="60d5b-102">\<Adicionar > de \<contractTypeNames ></span><span class="sxs-lookup"><span data-stu-id="60d5b-102">\<add> of \<contractTypeNames></span></span>
<span data-ttu-id="60d5b-103">Um elemento de configuração que especifica o nome do contrato dos serviços que estão sendo pesquisados e os critérios normalmente usados durante a pesquisa de um serviço.</span><span class="sxs-lookup"><span data-stu-id="60d5b-103">A configuration element that specifies the contract name of the services being searched for, and the criteria typically used when searching for a service.</span></span> <span data-ttu-id="60d5b-104">Se mais de um nome de contrato for especificado, somente os pontos de extremidade de serviço correspondentes a todos os contratos serão respondidos.</span><span class="sxs-lookup"><span data-stu-id="60d5b-104">If more than one contract name is specified, only service endpoints matching ALL contracts will reply.</span></span> <span data-ttu-id="60d5b-105">Observe que no Windows Communication Foundation (WCF), um ponto de extremidade só pode dar suporte a um contrato.</span><span class="sxs-lookup"><span data-stu-id="60d5b-105">Note that in Windows Communication Foundation (WCF), an endpoint can only support one contract.</span></span>  
  
<span data-ttu-id="60d5b-106">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="60d5b-106">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="60d5b-107">&nbsp;&nbsp;[ **\<> de System. serviceModel**](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="60d5b-107">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="60d5b-108">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> standardEndpoints**](standardendpoints.md)</span><span class="sxs-lookup"><span data-stu-id="60d5b-108">&nbsp;&nbsp;&nbsp;&nbsp;[**\<standardEndpoints>**](standardendpoints.md)</span></span>\
<span data-ttu-id="60d5b-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> dynamicEndpoint**](dynamicendpoint.md)</span><span class="sxs-lookup"><span data-stu-id="60d5b-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<dynamicEndpoint>**](dynamicendpoint.md)</span></span>\
<span data-ttu-id="60d5b-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<> standardEndpoint**</span><span class="sxs-lookup"><span data-stu-id="60d5b-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<standardEndpoint>**</span></span>\
<span data-ttu-id="60d5b-111">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> discoveryClientSettings**](discoveryclientsettings.md)</span><span class="sxs-lookup"><span data-stu-id="60d5b-111">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<discoveryClientSettings>**](discoveryclientsettings.md)</span></span>\
<span data-ttu-id="60d5b-112">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> findCriteria**](findcriteria.md)</span><span class="sxs-lookup"><span data-stu-id="60d5b-112">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<findCriteria>**](findcriteria.md)</span></span>\
<span data-ttu-id="60d5b-113">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> contractTypeNames**](contracttypenames.md)</span><span class="sxs-lookup"><span data-stu-id="60d5b-113">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<contractTypeNames>**](contracttypenames.md)</span></span>\
<span data-ttu-id="60d5b-114">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<Adicionar >**</span><span class="sxs-lookup"><span data-stu-id="60d5b-114">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<add>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="60d5b-115">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="60d5b-115">Syntax</span></span>  
  
```xml  
<system.serviceModel>
  <standardEndpoints>
    <dynamicEndpoint>
      <standardEndpoint>
        <discoveryClientSettings discoveryEndpoint="String">
          <findCriteria duration="TimeSpan"
                        maxResults="Integer"
                        scopeMatchBy="Uri">
            <contractTypeNames>
              <add name="String" namespace="String" />
            <contractTypeNames>
            <extensions />
            <scopes>
              <add scope="URI"/>
            </scopes>
          </findCriteria>
        </discoveryClientSettings>
      <standardEndpoint>
    </dynamicEndpoint>
  </standardEndpoints>
</system.serviceModel>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="60d5b-116">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="60d5b-116">Attributes and Elements</span></span>  
 <span data-ttu-id="60d5b-117">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="60d5b-117">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="60d5b-118">Atributos</span><span class="sxs-lookup"><span data-stu-id="60d5b-118">Attributes</span></span>  
  
|<span data-ttu-id="60d5b-119">Atributo</span><span class="sxs-lookup"><span data-stu-id="60d5b-119">Attribute</span></span>|<span data-ttu-id="60d5b-120">Descrição</span><span class="sxs-lookup"><span data-stu-id="60d5b-120">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="60d5b-121">name</span><span class="sxs-lookup"><span data-stu-id="60d5b-121">name</span></span>|<span data-ttu-id="60d5b-122">Uma cadeia de caracteres que especifica o nome do tipo de contrato.</span><span class="sxs-lookup"><span data-stu-id="60d5b-122">A string that specifies the name of the contract type.</span></span>|  
|<span data-ttu-id="60d5b-123">namespace</span><span class="sxs-lookup"><span data-stu-id="60d5b-123">namespace</span></span>|<span data-ttu-id="60d5b-124">Uma cadeia de caracteres que especifica o namespace do tipo de contrato.</span><span class="sxs-lookup"><span data-stu-id="60d5b-124">A string that specifies the namespace of the contract type.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="60d5b-125">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="60d5b-125">Child Elements</span></span>  
 <span data-ttu-id="60d5b-126">Nenhum</span><span class="sxs-lookup"><span data-stu-id="60d5b-126">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="60d5b-127">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="60d5b-127">Parent Elements</span></span>  
  
|<span data-ttu-id="60d5b-128">Elemento</span><span class="sxs-lookup"><span data-stu-id="60d5b-128">Element</span></span>|<span data-ttu-id="60d5b-129">Descrição</span><span class="sxs-lookup"><span data-stu-id="60d5b-129">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="60d5b-130">\<contractTypeNames></span><span class="sxs-lookup"><span data-stu-id="60d5b-130">\<contractTypeNames></span></span>](contracttypenames.md)|<span data-ttu-id="60d5b-131">Uma coleção de nomes de tipo de contrato.</span><span class="sxs-lookup"><span data-stu-id="60d5b-131">A collection of contract type names.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="60d5b-132">Consulte também</span><span class="sxs-lookup"><span data-stu-id="60d5b-132">See also</span></span>

- <xref:System.ServiceModel.Discovery.FindCriteria>
- <xref:System.ServiceModel.Discovery.Configuration.FindCriteriaElement>
- <xref:System.ServiceModel.Discovery.Configuration.ContractTypeNameElement>
