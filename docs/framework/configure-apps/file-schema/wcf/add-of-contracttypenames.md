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
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: bebea15e6d1f24c95905355dbced33aa9c5150f2
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="ltaddgt-of-ltcontracttypenamesgt"></a><span data-ttu-id="56f32-102">&lt;adicionar&gt; &lt;contractTypeNames&gt;</span><span class="sxs-lookup"><span data-stu-id="56f32-102">&lt;add&gt; of &lt;contractTypeNames&gt;</span></span>
<span data-ttu-id="56f32-103">Um elemento de configuração que especifica o nome do contrato dos serviços que está sendo pesquisados e os critérios usados normalmente durante a pesquisa de um serviço.</span><span class="sxs-lookup"><span data-stu-id="56f32-103">A configuration element that specifies the contract name of the services being searched for, and the criteria typically used when searching for a service.</span></span> <span data-ttu-id="56f32-104">Se mais de um nome de contrato for especificado, somente pontos de extremidade correspondente a todos os contratos responderá.</span><span class="sxs-lookup"><span data-stu-id="56f32-104">If more than one contract name is specified, only service endpoints matching ALL contracts will reply.</span></span> <span data-ttu-id="56f32-105">Observe que em [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)], um ponto de extremidade só pode oferecer suporte a um contrato.</span><span class="sxs-lookup"><span data-stu-id="56f32-105">Note that in [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)], an endpoint can only support one contract.</span></span>  
  
 <span data-ttu-id="56f32-106">\<sistema. ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="56f32-106">\<system.ServiceModel></span></span>  
<span data-ttu-id="56f32-107">\<standardEndpoints ></span><span class="sxs-lookup"><span data-stu-id="56f32-107">\<standardEndpoints></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="56f32-108">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="56f32-108">Syntax</span></span>  
  
```xml  
<system.serviceModel>  
    <standardEndpoints>       <dynamicEndpoint>           <standardEndpoint>             <discoveryClientSettings discoveryEndpoint="String" >               <findCriteria duration="TimeSpan"                  maxResults="Integer"                   scopeMatchBy="Uri" >                  <contractTypeNames>                     <add name="String" namespace="String" />                  <contractTypeNames>                  <extensions />                  <scopes>                    <add scope="URI"/>                  </scopes>               </findCriteria>             </discoveryClientSettings>          <standardEndpoint>       </dynamicEndpoint>            </standardEndpoints>  
</system.serviceModel>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="56f32-109">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="56f32-109">Attributes and Elements</span></span>  
 <span data-ttu-id="56f32-110">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="56f32-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="56f32-111">Atributos</span><span class="sxs-lookup"><span data-stu-id="56f32-111">Attributes</span></span>  
  
|<span data-ttu-id="56f32-112">Atributo</span><span class="sxs-lookup"><span data-stu-id="56f32-112">Attribute</span></span>|<span data-ttu-id="56f32-113">Descrição</span><span class="sxs-lookup"><span data-stu-id="56f32-113">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="56f32-114">name</span><span class="sxs-lookup"><span data-stu-id="56f32-114">name</span></span>|<span data-ttu-id="56f32-115">Uma cadeia de caracteres que especifica o nome do tipo de contrato.</span><span class="sxs-lookup"><span data-stu-id="56f32-115">A string that specifies the name of the contract type.</span></span>|  
|<span data-ttu-id="56f32-116">namespace</span><span class="sxs-lookup"><span data-stu-id="56f32-116">namespace</span></span>|<span data-ttu-id="56f32-117">Uma cadeia de caracteres que especifica o namespace do tipo de contrato.</span><span class="sxs-lookup"><span data-stu-id="56f32-117">A string that specifies the namespace of the contract type.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="56f32-118">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="56f32-118">Child Elements</span></span>  
 <span data-ttu-id="56f32-119">Nenhum</span><span class="sxs-lookup"><span data-stu-id="56f32-119">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="56f32-120">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="56f32-120">Parent Elements</span></span>  
  
|<span data-ttu-id="56f32-121">Elemento</span><span class="sxs-lookup"><span data-stu-id="56f32-121">Element</span></span>|<span data-ttu-id="56f32-122">Descrição</span><span class="sxs-lookup"><span data-stu-id="56f32-122">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="56f32-123">\<contractTypeNames ></span><span class="sxs-lookup"><span data-stu-id="56f32-123">\<contractTypeNames></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/contracttypenames.md)|<span data-ttu-id="56f32-124">Uma coleção de nomes de tipo de contrato.</span><span class="sxs-lookup"><span data-stu-id="56f32-124">A collection of contract type names.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="56f32-125">Consulte também</span><span class="sxs-lookup"><span data-stu-id="56f32-125">See Also</span></span>  
 <xref:System.ServiceModel.Discovery.FindCriteria>  
 <xref:System.ServiceModel.Discovery.Configuration.FindCriteriaElement>  
 <xref:System.ServiceModel.Discovery.Configuration.ContractTypeNameElement>
