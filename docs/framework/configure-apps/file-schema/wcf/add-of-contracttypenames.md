---
title: <add> de <contractTypeNames>
ms.date: 03/30/2017
ms.assetid: 03aff6be-5dfb-4a64-ada3-e36227cd43c7
ms.openlocfilehash: 856298cb0639cf19b941f326b5b9a25aa6663088
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59091311"
---
# <a name="add-of-contracttypenames"></a><span data-ttu-id="630d5-102">\<Adicionar > de \<contractTypeNames ></span><span class="sxs-lookup"><span data-stu-id="630d5-102">\<add> of \<contractTypeNames></span></span>
<span data-ttu-id="630d5-103">Um elemento de configuração que especifica o nome do contrato de serviços que está sendo pesquisados e os critérios normalmente usados durante a pesquisa para um serviço.</span><span class="sxs-lookup"><span data-stu-id="630d5-103">A configuration element that specifies the contract name of the services being searched for, and the criteria typically used when searching for a service.</span></span> <span data-ttu-id="630d5-104">Se mais de um nome de contrato for especificado, somente pontos de extremidade correspondentes a todos os contratos responderá.</span><span class="sxs-lookup"><span data-stu-id="630d5-104">If more than one contract name is specified, only service endpoints matching ALL contracts will reply.</span></span> <span data-ttu-id="630d5-105">Observe que no Windows Communication Foundation (WCF), um ponto de extremidade pode apenas suporta um contrato.</span><span class="sxs-lookup"><span data-stu-id="630d5-105">Note that in Windows Communication Foundation (WCF), an endpoint can only support one contract.</span></span>  
  
 <span data-ttu-id="630d5-106">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="630d5-106">\<system.ServiceModel></span></span>  
<span data-ttu-id="630d5-107">\<standardEndpoints></span><span class="sxs-lookup"><span data-stu-id="630d5-107">\<standardEndpoints></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="630d5-108">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="630d5-108">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="630d5-109">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="630d5-109">Attributes and Elements</span></span>  
 <span data-ttu-id="630d5-110">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="630d5-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="630d5-111">Atributos</span><span class="sxs-lookup"><span data-stu-id="630d5-111">Attributes</span></span>  
  
|<span data-ttu-id="630d5-112">Atributo</span><span class="sxs-lookup"><span data-stu-id="630d5-112">Attribute</span></span>|<span data-ttu-id="630d5-113">Descrição</span><span class="sxs-lookup"><span data-stu-id="630d5-113">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="630d5-114">name</span><span class="sxs-lookup"><span data-stu-id="630d5-114">name</span></span>|<span data-ttu-id="630d5-115">Uma cadeia de caracteres que especifica o nome do tipo de contrato.</span><span class="sxs-lookup"><span data-stu-id="630d5-115">A string that specifies the name of the contract type.</span></span>|  
|<span data-ttu-id="630d5-116">namespace</span><span class="sxs-lookup"><span data-stu-id="630d5-116">namespace</span></span>|<span data-ttu-id="630d5-117">Uma cadeia de caracteres que especifica o namespace do tipo de contrato.</span><span class="sxs-lookup"><span data-stu-id="630d5-117">A string that specifies the namespace of the contract type.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="630d5-118">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="630d5-118">Child Elements</span></span>  
 <span data-ttu-id="630d5-119">Nenhum</span><span class="sxs-lookup"><span data-stu-id="630d5-119">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="630d5-120">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="630d5-120">Parent Elements</span></span>  
  
|<span data-ttu-id="630d5-121">Elemento</span><span class="sxs-lookup"><span data-stu-id="630d5-121">Element</span></span>|<span data-ttu-id="630d5-122">Descrição</span><span class="sxs-lookup"><span data-stu-id="630d5-122">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="630d5-123">\<contractTypeNames></span><span class="sxs-lookup"><span data-stu-id="630d5-123">\<contractTypeNames></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/contracttypenames.md)|<span data-ttu-id="630d5-124">Uma coleção de nomes de tipo de contrato.</span><span class="sxs-lookup"><span data-stu-id="630d5-124">A collection of contract type names.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="630d5-125">Consulte também</span><span class="sxs-lookup"><span data-stu-id="630d5-125">See also</span></span>

- <xref:System.ServiceModel.Discovery.FindCriteria>
- <xref:System.ServiceModel.Discovery.Configuration.FindCriteriaElement>
- <xref:System.ServiceModel.Discovery.Configuration.ContractTypeNameElement>
