---
title: '&lt;adicionar&gt; &lt;contractTypeNames&gt;'
ms.date: 03/30/2017
ms.assetid: 03aff6be-5dfb-4a64-ada3-e36227cd43c7
ms.openlocfilehash: 159ab5a40a69c075b648a0c161babe604d13377b
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32750187"
---
# <a name="ltaddgt-of-ltcontracttypenamesgt"></a><span data-ttu-id="ada44-102">&lt;adicionar&gt; &lt;contractTypeNames&gt;</span><span class="sxs-lookup"><span data-stu-id="ada44-102">&lt;add&gt; of &lt;contractTypeNames&gt;</span></span>
<span data-ttu-id="ada44-103">Um elemento de configuração que especifica o nome do contrato dos serviços que está sendo pesquisados e os critérios usados normalmente durante a pesquisa de um serviço.</span><span class="sxs-lookup"><span data-stu-id="ada44-103">A configuration element that specifies the contract name of the services being searched for, and the criteria typically used when searching for a service.</span></span> <span data-ttu-id="ada44-104">Se mais de um nome de contrato for especificado, somente pontos de extremidade correspondente a todos os contratos responderá.</span><span class="sxs-lookup"><span data-stu-id="ada44-104">If more than one contract name is specified, only service endpoints matching ALL contracts will reply.</span></span> <span data-ttu-id="ada44-105">Observe que no Windows Communication Foundation (WCF), um ponto de extremidade suporta apenas um contrato.</span><span class="sxs-lookup"><span data-stu-id="ada44-105">Note that in Windows Communication Foundation (WCF), an endpoint can only support one contract.</span></span>  
  
 <span data-ttu-id="ada44-106">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="ada44-106">\<system.ServiceModel></span></span>  
<span data-ttu-id="ada44-107">\<standardEndpoints ></span><span class="sxs-lookup"><span data-stu-id="ada44-107">\<standardEndpoints></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ada44-108">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="ada44-108">Syntax</span></span>  
  
```xml  
<system.serviceModel>  
    <standardEndpoints>       <dynamicEndpoint>           <standardEndpoint>             <discoveryClientSettings discoveryEndpoint="String" >               <findCriteria duration="TimeSpan"                  maxResults="Integer"                   scopeMatchBy="Uri" >                  <contractTypeNames>                     <add name="String" namespace="String" />                  <contractTypeNames>                  <extensions />                  <scopes>                    <add scope="URI"/>                  </scopes>               </findCriteria>             </discoveryClientSettings>          <standardEndpoint>       </dynamicEndpoint>            </standardEndpoints>  
</system.serviceModel>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="ada44-109">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="ada44-109">Attributes and Elements</span></span>  
 <span data-ttu-id="ada44-110">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="ada44-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="ada44-111">Atributos</span><span class="sxs-lookup"><span data-stu-id="ada44-111">Attributes</span></span>  
  
|<span data-ttu-id="ada44-112">Atributo</span><span class="sxs-lookup"><span data-stu-id="ada44-112">Attribute</span></span>|<span data-ttu-id="ada44-113">Descrição</span><span class="sxs-lookup"><span data-stu-id="ada44-113">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="ada44-114">name</span><span class="sxs-lookup"><span data-stu-id="ada44-114">name</span></span>|<span data-ttu-id="ada44-115">Uma cadeia de caracteres que especifica o nome do tipo de contrato.</span><span class="sxs-lookup"><span data-stu-id="ada44-115">A string that specifies the name of the contract type.</span></span>|  
|<span data-ttu-id="ada44-116">namespace</span><span class="sxs-lookup"><span data-stu-id="ada44-116">namespace</span></span>|<span data-ttu-id="ada44-117">Uma cadeia de caracteres que especifica o namespace do tipo de contrato.</span><span class="sxs-lookup"><span data-stu-id="ada44-117">A string that specifies the namespace of the contract type.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="ada44-118">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="ada44-118">Child Elements</span></span>  
 <span data-ttu-id="ada44-119">Nenhum</span><span class="sxs-lookup"><span data-stu-id="ada44-119">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="ada44-120">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="ada44-120">Parent Elements</span></span>  
  
|<span data-ttu-id="ada44-121">Elemento</span><span class="sxs-lookup"><span data-stu-id="ada44-121">Element</span></span>|<span data-ttu-id="ada44-122">Descrição</span><span class="sxs-lookup"><span data-stu-id="ada44-122">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="ada44-123">\<contractTypeNames ></span><span class="sxs-lookup"><span data-stu-id="ada44-123">\<contractTypeNames></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/contracttypenames.md)|<span data-ttu-id="ada44-124">Uma coleção de nomes de tipo de contrato.</span><span class="sxs-lookup"><span data-stu-id="ada44-124">A collection of contract type names.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="ada44-125">Consulte também</span><span class="sxs-lookup"><span data-stu-id="ada44-125">See Also</span></span>  
 <xref:System.ServiceModel.Discovery.FindCriteria>  
 <xref:System.ServiceModel.Discovery.Configuration.FindCriteriaElement>  
 <xref:System.ServiceModel.Discovery.Configuration.ContractTypeNameElement>
