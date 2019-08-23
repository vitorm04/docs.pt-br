---
title: <add> de <contractTypeNames>
ms.date: 03/30/2017
ms.assetid: 03aff6be-5dfb-4a64-ada3-e36227cd43c7
ms.openlocfilehash: 24f1478b99aef909ae93f87a70be257e9ba10d7a
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69926744"
---
# <a name="add-of-contracttypenames"></a><span data-ttu-id="1a21a-102">\<Adicionar > de \<contractTypeNames ></span><span class="sxs-lookup"><span data-stu-id="1a21a-102">\<add> of \<contractTypeNames></span></span>
<span data-ttu-id="1a21a-103">Um elemento de configuração que especifica o nome do contrato dos serviços que estão sendo pesquisados e os critérios normalmente usados durante a pesquisa de um serviço.</span><span class="sxs-lookup"><span data-stu-id="1a21a-103">A configuration element that specifies the contract name of the services being searched for, and the criteria typically used when searching for a service.</span></span> <span data-ttu-id="1a21a-104">Se mais de um nome de contrato for especificado, somente os pontos de extremidade de serviço correspondentes a todos os contratos serão respondidos.</span><span class="sxs-lookup"><span data-stu-id="1a21a-104">If more than one contract name is specified, only service endpoints matching ALL contracts will reply.</span></span> <span data-ttu-id="1a21a-105">Observe que no Windows Communication Foundation (WCF), um ponto de extremidade só pode dar suporte a um contrato.</span><span class="sxs-lookup"><span data-stu-id="1a21a-105">Note that in Windows Communication Foundation (WCF), an endpoint can only support one contract.</span></span>  
  
 <span data-ttu-id="1a21a-106">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="1a21a-106">\<system.ServiceModel></span></span>  
<span data-ttu-id="1a21a-107">\<standardEndpoints></span><span class="sxs-lookup"><span data-stu-id="1a21a-107">\<standardEndpoints></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1a21a-108">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="1a21a-108">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="1a21a-109">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="1a21a-109">Attributes and Elements</span></span>  
 <span data-ttu-id="1a21a-110">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="1a21a-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="1a21a-111">Atributos</span><span class="sxs-lookup"><span data-stu-id="1a21a-111">Attributes</span></span>  
  
|<span data-ttu-id="1a21a-112">Atributo</span><span class="sxs-lookup"><span data-stu-id="1a21a-112">Attribute</span></span>|<span data-ttu-id="1a21a-113">Descrição</span><span class="sxs-lookup"><span data-stu-id="1a21a-113">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="1a21a-114">name</span><span class="sxs-lookup"><span data-stu-id="1a21a-114">name</span></span>|<span data-ttu-id="1a21a-115">Uma cadeia de caracteres que especifica o nome do tipo de contrato.</span><span class="sxs-lookup"><span data-stu-id="1a21a-115">A string that specifies the name of the contract type.</span></span>|  
|<span data-ttu-id="1a21a-116">namespace</span><span class="sxs-lookup"><span data-stu-id="1a21a-116">namespace</span></span>|<span data-ttu-id="1a21a-117">Uma cadeia de caracteres que especifica o namespace do tipo de contrato.</span><span class="sxs-lookup"><span data-stu-id="1a21a-117">A string that specifies the namespace of the contract type.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="1a21a-118">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="1a21a-118">Child Elements</span></span>  
 <span data-ttu-id="1a21a-119">Nenhum</span><span class="sxs-lookup"><span data-stu-id="1a21a-119">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="1a21a-120">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="1a21a-120">Parent Elements</span></span>  
  
|<span data-ttu-id="1a21a-121">Elemento</span><span class="sxs-lookup"><span data-stu-id="1a21a-121">Element</span></span>|<span data-ttu-id="1a21a-122">Descrição</span><span class="sxs-lookup"><span data-stu-id="1a21a-122">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="1a21a-123">\<contractTypeNames></span><span class="sxs-lookup"><span data-stu-id="1a21a-123">\<contractTypeNames></span></span>](contracttypenames.md)|<span data-ttu-id="1a21a-124">Uma coleção de nomes de tipo de contrato.</span><span class="sxs-lookup"><span data-stu-id="1a21a-124">A collection of contract type names.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="1a21a-125">Consulte também</span><span class="sxs-lookup"><span data-stu-id="1a21a-125">See also</span></span>

- <xref:System.ServiceModel.Discovery.FindCriteria>
- <xref:System.ServiceModel.Discovery.Configuration.FindCriteriaElement>
- <xref:System.ServiceModel.Discovery.Configuration.ContractTypeNameElement>
