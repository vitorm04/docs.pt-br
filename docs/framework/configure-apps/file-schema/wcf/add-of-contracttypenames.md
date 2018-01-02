---
title: '&lt;adicionar&gt; &lt;contractTypeNames&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 03aff6be-5dfb-4a64-ada3-e36227cd43c7
caps.latest.revision: "2"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 191e3e221ae42e5c046f8df324989aae7ab0dc1c
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="ltaddgt-of-ltcontracttypenamesgt"></a><span data-ttu-id="7e5b5-102">&lt;adicionar&gt; &lt;contractTypeNames&gt;</span><span class="sxs-lookup"><span data-stu-id="7e5b5-102">&lt;add&gt; of &lt;contractTypeNames&gt;</span></span>
<span data-ttu-id="7e5b5-103">Um elemento de configuração que especifica o nome do contrato dos serviços que está sendo pesquisados e os critérios usados normalmente durante a pesquisa de um serviço.</span><span class="sxs-lookup"><span data-stu-id="7e5b5-103">A configuration element that specifies the contract name of the services being searched for, and the criteria typically used when searching for a service.</span></span> <span data-ttu-id="7e5b5-104">Se mais de um nome de contrato for especificado, somente pontos de extremidade correspondente a todos os contratos responderá.</span><span class="sxs-lookup"><span data-stu-id="7e5b5-104">If more than one contract name is specified, only service endpoints matching ALL contracts will reply.</span></span> <span data-ttu-id="7e5b5-105">Observe que em [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)], um ponto de extremidade só pode oferecer suporte a um contrato.</span><span class="sxs-lookup"><span data-stu-id="7e5b5-105">Note that in [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)], an endpoint can only support one contract.</span></span>  
  
 <span data-ttu-id="7e5b5-106">\<sistema. ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="7e5b5-106">\<system.ServiceModel></span></span>  
<span data-ttu-id="7e5b5-107">\<standardEndpoints ></span><span class="sxs-lookup"><span data-stu-id="7e5b5-107">\<standardEndpoints></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7e5b5-108">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="7e5b5-108">Syntax</span></span>  
  
```xml  
<system.serviceModel>  
    <standardEndpoints>       <dynamicEndpoint>           <standardEndpoint>             <discoveryClientSettings discoveryEndpoint="String" >               <findCriteria duration="TimeSpan"                  maxResults="Integer"                   scopeMatchBy="Uri" >                  <contractTypeNames>                     <add name="String" namespace="String" />                  <contractTypeNames>                  <extensions />                  <scopes>                    <add scope="URI"/>                  </scopes>               </findCriteria>             </discoveryClientSettings>          <standardEndpoint>       </dynamicEndpoint>            </standardEndpoints>  
</system.serviceModel>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="7e5b5-109">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="7e5b5-109">Attributes and Elements</span></span>  
 <span data-ttu-id="7e5b5-110">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="7e5b5-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="7e5b5-111">Atributos</span><span class="sxs-lookup"><span data-stu-id="7e5b5-111">Attributes</span></span>  
  
|<span data-ttu-id="7e5b5-112">Atributo</span><span class="sxs-lookup"><span data-stu-id="7e5b5-112">Attribute</span></span>|<span data-ttu-id="7e5b5-113">Descrição</span><span class="sxs-lookup"><span data-stu-id="7e5b5-113">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="7e5b5-114">name</span><span class="sxs-lookup"><span data-stu-id="7e5b5-114">name</span></span>|<span data-ttu-id="7e5b5-115">Uma cadeia de caracteres que especifica o nome do tipo de contrato.</span><span class="sxs-lookup"><span data-stu-id="7e5b5-115">A string that specifies the name of the contract type.</span></span>|  
|<span data-ttu-id="7e5b5-116">namespace</span><span class="sxs-lookup"><span data-stu-id="7e5b5-116">namespace</span></span>|<span data-ttu-id="7e5b5-117">Uma cadeia de caracteres que especifica o namespace do tipo de contrato.</span><span class="sxs-lookup"><span data-stu-id="7e5b5-117">A string that specifies the namespace of the contract type.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="7e5b5-118">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="7e5b5-118">Child Elements</span></span>  
 <span data-ttu-id="7e5b5-119">Nenhum</span><span class="sxs-lookup"><span data-stu-id="7e5b5-119">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="7e5b5-120">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="7e5b5-120">Parent Elements</span></span>  
  
|<span data-ttu-id="7e5b5-121">Elemento</span><span class="sxs-lookup"><span data-stu-id="7e5b5-121">Element</span></span>|<span data-ttu-id="7e5b5-122">Descrição</span><span class="sxs-lookup"><span data-stu-id="7e5b5-122">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="7e5b5-123">\<contractTypeNames ></span><span class="sxs-lookup"><span data-stu-id="7e5b5-123">\<contractTypeNames></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/contracttypenames.md)|<span data-ttu-id="7e5b5-124">Uma coleção de nomes de tipo de contrato.</span><span class="sxs-lookup"><span data-stu-id="7e5b5-124">A collection of contract type names.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="7e5b5-125">Consulte também</span><span class="sxs-lookup"><span data-stu-id="7e5b5-125">See Also</span></span>  
 <xref:System.ServiceModel.Discovery.FindCriteria>  
 <xref:System.ServiceModel.Discovery.Configuration.FindCriteriaElement>  
 <xref:System.ServiceModel.Discovery.Configuration.ContractTypeNameElement>
