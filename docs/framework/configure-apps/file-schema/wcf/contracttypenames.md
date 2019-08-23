---
title: <contractTypeNames>
ms.date: 03/30/2017
ms.assetid: 5ec5efc6-87f8-4160-9be0-dcd2e01df3df
ms.openlocfilehash: 12f9d4eca02ae3b306646826667c4eafef51a95c
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69919372"
---
# <a name="contracttypenames"></a><span data-ttu-id="a1c69-101">\<contractTypeNames></span><span class="sxs-lookup"><span data-stu-id="a1c69-101">\<contractTypeNames></span></span>
<span data-ttu-id="a1c69-102">Uma seção de configuração que especifica uma lista de nomes de tipo de contrato, que são os nomes de contrato dos serviços que estão sendo pesquisados e os critérios normalmente usados ao pesquisar um serviço.</span><span class="sxs-lookup"><span data-stu-id="a1c69-102">A configuration section that specifies a list of contract type names, which are the contract names of the services being searched for, and the criteria typically used when searching for a service.</span></span> <span data-ttu-id="a1c69-103">Se mais de um nome de contrato for especificado, somente os pontos de extremidade de serviço correspondentes a todos os contratos serão respondidos.</span><span class="sxs-lookup"><span data-stu-id="a1c69-103">If more than one contract name is specified, only service endpoints matching ALL contracts will reply.</span></span> <span data-ttu-id="a1c69-104">Observe que no Windows Communication Foundation (WCF), um ponto de extremidade só pode dar suporte a um contrato.</span><span class="sxs-lookup"><span data-stu-id="a1c69-104">Note that in Windows Communication Foundation (WCF), an endpoint can only support one contract.</span></span>  
  
 <span data-ttu-id="a1c69-105">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="a1c69-105">\<system.ServiceModel></span></span>  
<span data-ttu-id="a1c69-106">\<standardEndpoints></span><span class="sxs-lookup"><span data-stu-id="a1c69-106">\<standardEndpoints></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a1c69-107">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="a1c69-107">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="a1c69-108">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="a1c69-108">Attributes and Elements</span></span>  
 <span data-ttu-id="a1c69-109">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="a1c69-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="a1c69-110">Atributos</span><span class="sxs-lookup"><span data-stu-id="a1c69-110">Attributes</span></span>  
 <span data-ttu-id="a1c69-111">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="a1c69-111">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="a1c69-112">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="a1c69-112">Child Elements</span></span>  
  
|<span data-ttu-id="a1c69-113">Elemento</span><span class="sxs-lookup"><span data-stu-id="a1c69-113">Element</span></span>|<span data-ttu-id="a1c69-114">Descrição</span><span class="sxs-lookup"><span data-stu-id="a1c69-114">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="a1c69-115">\<add></span><span class="sxs-lookup"><span data-stu-id="a1c69-115">\<add></span></span>](contracttypenames.md)|<span data-ttu-id="a1c69-116">Um nome de tipo de contrato é uma propriedade que se refere ao conjunto de critérios normalmente usado ao pesquisar um serviço.</span><span class="sxs-lookup"><span data-stu-id="a1c69-116">A contract type name is a property that refers to the set of criteria typically used when searching for a service.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="a1c69-117">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="a1c69-117">Parent Elements</span></span>  
  
|<span data-ttu-id="a1c69-118">Elemento</span><span class="sxs-lookup"><span data-stu-id="a1c69-118">Element</span></span>|<span data-ttu-id="a1c69-119">Descrição</span><span class="sxs-lookup"><span data-stu-id="a1c69-119">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="a1c69-120">\<findCriteria></span><span class="sxs-lookup"><span data-stu-id="a1c69-120">\<findCriteria></span></span>](findcriteria.md)|<span data-ttu-id="a1c69-121">Um elemento de configuração que fornece um conjunto de critérios usados por um aplicativo cliente para pesquisar um serviço de descoberta.</span><span class="sxs-lookup"><span data-stu-id="a1c69-121">A configuration element that supplies a set of criteria used by a client application to search for a discovery service.</span></span> <span data-ttu-id="a1c69-122">Os critérios podem ser agrupados em critérios de pesquisa (especificando quais serviços você está procurando) e localizar os critérios de encerramento (por quanto tempo a pesquisa deve durar).</span><span class="sxs-lookup"><span data-stu-id="a1c69-122">Criteria can be grouped into search criteria (specifying what services you’re looking for) and find termination criteria (how long the search should last).</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="a1c69-123">Consulte também</span><span class="sxs-lookup"><span data-stu-id="a1c69-123">See also</span></span>

- <xref:System.ServiceModel.Discovery.FindCriteria>
- <xref:System.ServiceModel.Discovery.Configuration.FindCriteriaElement>
- <xref:System.ServiceModel.Discovery.Configuration.ContractTypeNameElementCollection>
