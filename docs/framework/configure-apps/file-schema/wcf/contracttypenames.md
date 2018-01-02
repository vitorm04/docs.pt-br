---
title: '&lt;contractTypeNames&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 5ec5efc6-87f8-4160-9be0-dcd2e01df3df
caps.latest.revision: "2"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: e5ac3a4af54d9f470a1cbd50096731b23d28b0c5
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="ltcontracttypenamesgt"></a><span data-ttu-id="eb703-102">&lt;contractTypeNames&gt;</span><span class="sxs-lookup"><span data-stu-id="eb703-102">&lt;contractTypeNames&gt;</span></span>
<span data-ttu-id="eb703-103">Uma seção de configuração que especifica uma lista de nomes de tipo de contrato, que são os nomes de contrato de serviços que está sendo pesquisados, e os critérios usados normalmente durante a pesquisa de um serviço.</span><span class="sxs-lookup"><span data-stu-id="eb703-103">A configuration section that specifies a list of contract type names, which are the contract names of the services being searched for, and the criteria typically used when searching for a service.</span></span> <span data-ttu-id="eb703-104">Se mais de um nome de contrato for especificado, somente pontos de extremidade correspondente a todos os contratos responderá.</span><span class="sxs-lookup"><span data-stu-id="eb703-104">If more than one contract name is specified, only service endpoints matching ALL contracts will reply.</span></span> <span data-ttu-id="eb703-105">Observe que em [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)], um ponto de extremidade só pode oferecer suporte a um contrato.</span><span class="sxs-lookup"><span data-stu-id="eb703-105">Note that in [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)], an endpoint can only support one contract.</span></span>  
  
 <span data-ttu-id="eb703-106">\<sistema. ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="eb703-106">\<system.ServiceModel></span></span>  
<span data-ttu-id="eb703-107">\<standardEndpoints ></span><span class="sxs-lookup"><span data-stu-id="eb703-107">\<standardEndpoints></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="eb703-108">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="eb703-108">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="eb703-109">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="eb703-109">Attributes and Elements</span></span>  
 <span data-ttu-id="eb703-110">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="eb703-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="eb703-111">Atributos</span><span class="sxs-lookup"><span data-stu-id="eb703-111">Attributes</span></span>  
 <span data-ttu-id="eb703-112">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="eb703-112">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="eb703-113">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="eb703-113">Child Elements</span></span>  
  
|<span data-ttu-id="eb703-114">Elemento</span><span class="sxs-lookup"><span data-stu-id="eb703-114">Element</span></span>|<span data-ttu-id="eb703-115">Descrição</span><span class="sxs-lookup"><span data-stu-id="eb703-115">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="eb703-116">\<add></span><span class="sxs-lookup"><span data-stu-id="eb703-116">\<add></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/contracttypenames.md)|<span data-ttu-id="eb703-117">Um nome de tipo de contrato é uma propriedade que faz referência ao conjunto de critérios usados normalmente durante a pesquisa de um serviço.</span><span class="sxs-lookup"><span data-stu-id="eb703-117">A contract type name is a property that refers to the set of criteria typically used when searching for a service.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="eb703-118">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="eb703-118">Parent Elements</span></span>  
  
|<span data-ttu-id="eb703-119">Elemento</span><span class="sxs-lookup"><span data-stu-id="eb703-119">Element</span></span>|<span data-ttu-id="eb703-120">Descrição</span><span class="sxs-lookup"><span data-stu-id="eb703-120">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="eb703-121">\<findCriteria ></span><span class="sxs-lookup"><span data-stu-id="eb703-121">\<findCriteria></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/findcriteria.md)|<span data-ttu-id="eb703-122">Um elemento de configuração que fornece um conjunto de critérios usados por um aplicativo cliente para pesquisar para um serviço de descoberta.</span><span class="sxs-lookup"><span data-stu-id="eb703-122">A configuration element that supplies a set of criteria used by a client application to search for a discovery service.</span></span> <span data-ttu-id="eb703-123">Critérios podem ser agrupados em critérios de pesquisa (especificando quais serviços você está procurando) e localizar os critérios de encerramento (quanto tempo a pesquisa deve durar).</span><span class="sxs-lookup"><span data-stu-id="eb703-123">Criteria can be grouped into search criteria (specifying what services you’re looking for) and find termination criteria (how long the search should last).</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="eb703-124">Consulte também</span><span class="sxs-lookup"><span data-stu-id="eb703-124">See Also</span></span>  
 <xref:System.ServiceModel.Discovery.FindCriteria>  
 <xref:System.ServiceModel.Discovery.Configuration.FindCriteriaElement>  
 <xref:System.ServiceModel.Discovery.Configuration.ContractTypeNameElementCollection>
