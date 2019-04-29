---
title: <add> de <contractTypeNames>
ms.date: 03/30/2017
ms.assetid: 03aff6be-5dfb-4a64-ada3-e36227cd43c7
ms.openlocfilehash: 856298cb0639cf19b941f326b5b9a25aa6663088
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61701184"
---
# <a name="add-of-contracttypenames"></a><span data-ttu-id="7003c-102">\<Adicionar > de \<contractTypeNames ></span><span class="sxs-lookup"><span data-stu-id="7003c-102">\<add> of \<contractTypeNames></span></span>
<span data-ttu-id="7003c-103">Um elemento de configuração que especifica o nome do contrato de serviços que está sendo pesquisados e os critérios normalmente usados durante a pesquisa para um serviço.</span><span class="sxs-lookup"><span data-stu-id="7003c-103">A configuration element that specifies the contract name of the services being searched for, and the criteria typically used when searching for a service.</span></span> <span data-ttu-id="7003c-104">Se mais de um nome de contrato for especificado, somente pontos de extremidade correspondentes a todos os contratos responderá.</span><span class="sxs-lookup"><span data-stu-id="7003c-104">If more than one contract name is specified, only service endpoints matching ALL contracts will reply.</span></span> <span data-ttu-id="7003c-105">Observe que no Windows Communication Foundation (WCF), um ponto de extremidade pode apenas suporta um contrato.</span><span class="sxs-lookup"><span data-stu-id="7003c-105">Note that in Windows Communication Foundation (WCF), an endpoint can only support one contract.</span></span>  
  
 <span data-ttu-id="7003c-106">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="7003c-106">\<system.ServiceModel></span></span>  
<span data-ttu-id="7003c-107">\<standardEndpoints></span><span class="sxs-lookup"><span data-stu-id="7003c-107">\<standardEndpoints></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7003c-108">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="7003c-108">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="7003c-109">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="7003c-109">Attributes and Elements</span></span>  
 <span data-ttu-id="7003c-110">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="7003c-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="7003c-111">Atributos</span><span class="sxs-lookup"><span data-stu-id="7003c-111">Attributes</span></span>  
  
|<span data-ttu-id="7003c-112">Atributo</span><span class="sxs-lookup"><span data-stu-id="7003c-112">Attribute</span></span>|<span data-ttu-id="7003c-113">Descrição</span><span class="sxs-lookup"><span data-stu-id="7003c-113">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="7003c-114">name</span><span class="sxs-lookup"><span data-stu-id="7003c-114">name</span></span>|<span data-ttu-id="7003c-115">Uma cadeia de caracteres que especifica o nome do tipo de contrato.</span><span class="sxs-lookup"><span data-stu-id="7003c-115">A string that specifies the name of the contract type.</span></span>|  
|<span data-ttu-id="7003c-116">namespace</span><span class="sxs-lookup"><span data-stu-id="7003c-116">namespace</span></span>|<span data-ttu-id="7003c-117">Uma cadeia de caracteres que especifica o namespace do tipo de contrato.</span><span class="sxs-lookup"><span data-stu-id="7003c-117">A string that specifies the namespace of the contract type.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="7003c-118">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="7003c-118">Child Elements</span></span>  
 <span data-ttu-id="7003c-119">Nenhum</span><span class="sxs-lookup"><span data-stu-id="7003c-119">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="7003c-120">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="7003c-120">Parent Elements</span></span>  
  
|<span data-ttu-id="7003c-121">Elemento</span><span class="sxs-lookup"><span data-stu-id="7003c-121">Element</span></span>|<span data-ttu-id="7003c-122">Descrição</span><span class="sxs-lookup"><span data-stu-id="7003c-122">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="7003c-123">\<contractTypeNames></span><span class="sxs-lookup"><span data-stu-id="7003c-123">\<contractTypeNames></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/contracttypenames.md)|<span data-ttu-id="7003c-124">Uma coleção de nomes de tipo de contrato.</span><span class="sxs-lookup"><span data-stu-id="7003c-124">A collection of contract type names.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="7003c-125">Consulte também</span><span class="sxs-lookup"><span data-stu-id="7003c-125">See also</span></span>

- <xref:System.ServiceModel.Discovery.FindCriteria>
- <xref:System.ServiceModel.Discovery.Configuration.FindCriteriaElement>
- <xref:System.ServiceModel.Discovery.Configuration.ContractTypeNameElement>
