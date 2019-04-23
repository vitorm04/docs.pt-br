---
title: <contractTypeNames>
ms.date: 03/30/2017
ms.assetid: 5ec5efc6-87f8-4160-9be0-dcd2e01df3df
ms.openlocfilehash: b1cec9272a1de029ab72ea4d5f36c74630e5b93a
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59089491"
---
# <a name="contracttypenames"></a><span data-ttu-id="b2f72-101">\<contractTypeNames></span><span class="sxs-lookup"><span data-stu-id="b2f72-101">\<contractTypeNames></span></span>
<span data-ttu-id="b2f72-102">Uma seção de configuração que especifica uma lista de nomes de tipo de contrato, que são os nomes de contrato de serviços que está sendo pesquisados, e os critérios normalmente usados durante a pesquisa para um serviço.</span><span class="sxs-lookup"><span data-stu-id="b2f72-102">A configuration section that specifies a list of contract type names, which are the contract names of the services being searched for, and the criteria typically used when searching for a service.</span></span> <span data-ttu-id="b2f72-103">Se mais de um nome de contrato for especificado, somente pontos de extremidade correspondentes a todos os contratos responderá.</span><span class="sxs-lookup"><span data-stu-id="b2f72-103">If more than one contract name is specified, only service endpoints matching ALL contracts will reply.</span></span> <span data-ttu-id="b2f72-104">Observe que no Windows Communication Foundation (WCF), um ponto de extremidade pode apenas suporta um contrato.</span><span class="sxs-lookup"><span data-stu-id="b2f72-104">Note that in Windows Communication Foundation (WCF), an endpoint can only support one contract.</span></span>  
  
 <span data-ttu-id="b2f72-105">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="b2f72-105">\<system.ServiceModel></span></span>  
<span data-ttu-id="b2f72-106">\<standardEndpoints></span><span class="sxs-lookup"><span data-stu-id="b2f72-106">\<standardEndpoints></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b2f72-107">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="b2f72-107">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="b2f72-108">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="b2f72-108">Attributes and Elements</span></span>  
 <span data-ttu-id="b2f72-109">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="b2f72-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="b2f72-110">Atributos</span><span class="sxs-lookup"><span data-stu-id="b2f72-110">Attributes</span></span>  
 <span data-ttu-id="b2f72-111">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="b2f72-111">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="b2f72-112">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="b2f72-112">Child Elements</span></span>  
  
|<span data-ttu-id="b2f72-113">Elemento</span><span class="sxs-lookup"><span data-stu-id="b2f72-113">Element</span></span>|<span data-ttu-id="b2f72-114">Descrição</span><span class="sxs-lookup"><span data-stu-id="b2f72-114">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="b2f72-115">\<add></span><span class="sxs-lookup"><span data-stu-id="b2f72-115">\<add></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/contracttypenames.md)|<span data-ttu-id="b2f72-116">Um nome de tipo de contrato é uma propriedade que se refere ao conjunto de critérios normalmente usados durante a pesquisa para um serviço.</span><span class="sxs-lookup"><span data-stu-id="b2f72-116">A contract type name is a property that refers to the set of criteria typically used when searching for a service.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="b2f72-117">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="b2f72-117">Parent Elements</span></span>  
  
|<span data-ttu-id="b2f72-118">Elemento</span><span class="sxs-lookup"><span data-stu-id="b2f72-118">Element</span></span>|<span data-ttu-id="b2f72-119">Descrição</span><span class="sxs-lookup"><span data-stu-id="b2f72-119">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="b2f72-120">\<findCriteria></span><span class="sxs-lookup"><span data-stu-id="b2f72-120">\<findCriteria></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/findcriteria.md)|<span data-ttu-id="b2f72-121">Um elemento de configuração que fornece um conjunto de critérios utilizados por um aplicativo cliente para pesquisar para um serviço de descoberta.</span><span class="sxs-lookup"><span data-stu-id="b2f72-121">A configuration element that supplies a set of criteria used by a client application to search for a discovery service.</span></span> <span data-ttu-id="b2f72-122">Critérios podem ser agrupados em critérios de pesquisa (especificando quais serviços você está procurando) e encontre os critérios de término (quanto tempo a pesquisa deve durar).</span><span class="sxs-lookup"><span data-stu-id="b2f72-122">Criteria can be grouped into search criteria (specifying what services you’re looking for) and find termination criteria (how long the search should last).</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="b2f72-123">Consulte também</span><span class="sxs-lookup"><span data-stu-id="b2f72-123">See also</span></span>

- <xref:System.ServiceModel.Discovery.FindCriteria>
- <xref:System.ServiceModel.Discovery.Configuration.FindCriteriaElement>
- <xref:System.ServiceModel.Discovery.Configuration.ContractTypeNameElementCollection>
