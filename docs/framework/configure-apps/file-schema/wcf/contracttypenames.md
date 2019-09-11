---
title: <contractTypeNames>
ms.date: 03/30/2017
ms.assetid: 5ec5efc6-87f8-4160-9be0-dcd2e01df3df
ms.openlocfilehash: c67e5b9e82b96e27ce73512680bd4236b26ef4dd
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/10/2019
ms.locfileid: "70855445"
---
# <a name="contracttypenames"></a><span data-ttu-id="602a9-101">\<contractTypeNames></span><span class="sxs-lookup"><span data-stu-id="602a9-101">\<contractTypeNames></span></span>
<span data-ttu-id="602a9-102">Uma seção de configuração que especifica uma lista de nomes de tipo de contrato, que são os nomes de contrato dos serviços que estão sendo pesquisados e os critérios normalmente usados ao pesquisar um serviço.</span><span class="sxs-lookup"><span data-stu-id="602a9-102">A configuration section that specifies a list of contract type names, which are the contract names of the services being searched for, and the criteria typically used when searching for a service.</span></span> <span data-ttu-id="602a9-103">Se mais de um nome de contrato for especificado, somente os pontos de extremidade de serviço correspondentes a todos os contratos serão respondidos.</span><span class="sxs-lookup"><span data-stu-id="602a9-103">If more than one contract name is specified, only service endpoints matching ALL contracts will reply.</span></span> <span data-ttu-id="602a9-104">Observe que no Windows Communication Foundation (WCF), um ponto de extremidade só pode dar suporte a um contrato.</span><span class="sxs-lookup"><span data-stu-id="602a9-104">Note that in Windows Communication Foundation (WCF), an endpoint can only support one contract.</span></span>  
  
<span data-ttu-id="602a9-105">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="602a9-105">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="602a9-106">&nbsp;&nbsp;[ **\<> de System. serviceModel**](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="602a9-106">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="602a9-107">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> standardEndpoints**](standardendpoints.md)</span><span class="sxs-lookup"><span data-stu-id="602a9-107">&nbsp;&nbsp;&nbsp;&nbsp;[**\<standardEndpoints>**](standardendpoints.md)</span></span>\
<span data-ttu-id="602a9-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> dynamicEndpoint**](dynamicendpoint.md)</span><span class="sxs-lookup"><span data-stu-id="602a9-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<dynamicEndpoint>**](dynamicendpoint.md)</span></span>\
<span data-ttu-id="602a9-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<> standardEndpoint**</span><span class="sxs-lookup"><span data-stu-id="602a9-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<standardEndpoint>**</span></span>\
<span data-ttu-id="602a9-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> discoveryClientSettings**](discoveryclientsettings.md)</span><span class="sxs-lookup"><span data-stu-id="602a9-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<discoveryClientSettings>**](discoveryclientsettings.md)</span></span>\
<span data-ttu-id="602a9-111">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> findCriteria**](findcriteria.md)</span><span class="sxs-lookup"><span data-stu-id="602a9-111">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<findCriteria>**](findcriteria.md)</span></span>\
<span data-ttu-id="602a9-112">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<> contractTypeNames**</span><span class="sxs-lookup"><span data-stu-id="602a9-112">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<contractTypeNames>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="602a9-113">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="602a9-113">Syntax</span></span>  
  
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
              <add name="String"
                   namespace="String" />
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="602a9-114">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="602a9-114">Attributes and Elements</span></span>  
 <span data-ttu-id="602a9-115">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="602a9-115">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="602a9-116">Atributos</span><span class="sxs-lookup"><span data-stu-id="602a9-116">Attributes</span></span>  
 <span data-ttu-id="602a9-117">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="602a9-117">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="602a9-118">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="602a9-118">Child Elements</span></span>  
  
|<span data-ttu-id="602a9-119">Elemento</span><span class="sxs-lookup"><span data-stu-id="602a9-119">Element</span></span>|<span data-ttu-id="602a9-120">Descrição</span><span class="sxs-lookup"><span data-stu-id="602a9-120">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="602a9-121">\<add></span><span class="sxs-lookup"><span data-stu-id="602a9-121">\<add></span></span>](contracttypenames.md)|<span data-ttu-id="602a9-122">Um nome de tipo de contrato é uma propriedade que se refere ao conjunto de critérios normalmente usado ao pesquisar um serviço.</span><span class="sxs-lookup"><span data-stu-id="602a9-122">A contract type name is a property that refers to the set of criteria typically used when searching for a service.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="602a9-123">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="602a9-123">Parent Elements</span></span>  
  
|<span data-ttu-id="602a9-124">Elemento</span><span class="sxs-lookup"><span data-stu-id="602a9-124">Element</span></span>|<span data-ttu-id="602a9-125">Descrição</span><span class="sxs-lookup"><span data-stu-id="602a9-125">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="602a9-126">\<findCriteria></span><span class="sxs-lookup"><span data-stu-id="602a9-126">\<findCriteria></span></span>](findcriteria.md)|<span data-ttu-id="602a9-127">Um elemento de configuração que fornece um conjunto de critérios usados por um aplicativo cliente para pesquisar um serviço de descoberta.</span><span class="sxs-lookup"><span data-stu-id="602a9-127">A configuration element that supplies a set of criteria used by a client application to search for a discovery service.</span></span> <span data-ttu-id="602a9-128">Os critérios podem ser agrupados em critérios de pesquisa (especificando quais serviços você está procurando) e localizar os critérios de encerramento (por quanto tempo a pesquisa deve durar).</span><span class="sxs-lookup"><span data-stu-id="602a9-128">Criteria can be grouped into search criteria (specifying what services you’re looking for) and find termination criteria (how long the search should last).</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="602a9-129">Consulte também</span><span class="sxs-lookup"><span data-stu-id="602a9-129">See also</span></span>

- <xref:System.ServiceModel.Discovery.FindCriteria>
- <xref:System.ServiceModel.Discovery.Configuration.FindCriteriaElement>
- <xref:System.ServiceModel.Discovery.Configuration.ContractTypeNameElementCollection>
