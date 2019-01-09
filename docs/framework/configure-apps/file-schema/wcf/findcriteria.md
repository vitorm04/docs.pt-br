---
title: '&lt;FindCriteria&gt;'
ms.date: 03/30/2017
ms.assetid: 5454cd19-6bf5-4ba8-94d1-f58d10dc1917
ms.openlocfilehash: 0a2fb7ae641f8ec34c518d8dc2c11fbc2ae26190
ms.sourcegitcommit: 4ac80713f6faa220e5a119d5165308a58f7ccdc8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/09/2019
ms.locfileid: "54146921"
---
# <a name="ltfindcriteriagt"></a><span data-ttu-id="59b04-102">&lt;FindCriteria&gt;</span><span class="sxs-lookup"><span data-stu-id="59b04-102">&lt;findCriteria&gt;</span></span>
<span data-ttu-id="59b04-103">Um elemento de configuração que fornece um conjunto de critérios utilizados por um aplicativo cliente para pesquisar para um serviço de descoberta.</span><span class="sxs-lookup"><span data-stu-id="59b04-103">A configuration element that supplies a set of criteria used by a client application to search for a discovery service.</span></span> <span data-ttu-id="59b04-104">Critérios podem ser agrupados em critérios de pesquisa (especificando quais serviços você está procurando) e encontre os critérios de término (quanto tempo a pesquisa deve durar).</span><span class="sxs-lookup"><span data-stu-id="59b04-104">Criteria can be grouped into search criteria (specifying what services you’re looking for) and find termination criteria (how long the search should last).</span></span>  
  
 <span data-ttu-id="59b04-105">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="59b04-105">\<system.ServiceModel></span></span>  
<span data-ttu-id="59b04-106">\<standardEndpoints ></span><span class="sxs-lookup"><span data-stu-id="59b04-106">\<standardEndpoints></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="59b04-107">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="59b04-107">Syntax</span></span>  
  
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
            </contractTypeNames>
            <extensions />
            <scopes>
              <add scope="URI" />
            </scopes>
          </findCriteria>
        </discoveryClientSettings>
      </standardEndpoint>
    </dynamicEndpoint>
  </standardEndpoints>
</system.serviceModel>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="59b04-108">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="59b04-108">Attributes and Elements</span></span>  
 <span data-ttu-id="59b04-109">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="59b04-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="59b04-110">Atributos</span><span class="sxs-lookup"><span data-stu-id="59b04-110">Attributes</span></span>  
  
|<span data-ttu-id="59b04-111">Atributo</span><span class="sxs-lookup"><span data-stu-id="59b04-111">Attribute</span></span>|<span data-ttu-id="59b04-112">Descrição</span><span class="sxs-lookup"><span data-stu-id="59b04-112">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="59b04-113">duration</span><span class="sxs-lookup"><span data-stu-id="59b04-113">duration</span></span>|<span data-ttu-id="59b04-114">Um valor de Timespan que especifica o tempo máximo de espera por respostas de serviços na rede.</span><span class="sxs-lookup"><span data-stu-id="59b04-114">A Timespan value that specifies the maximum time to wait for replies from services on the network.</span></span> <span data-ttu-id="59b04-115">A duração padrão é 20 segundos.</span><span class="sxs-lookup"><span data-stu-id="59b04-115">The default duration is 20 seconds.</span></span>|  
|<span data-ttu-id="59b04-116">maxResults</span><span class="sxs-lookup"><span data-stu-id="59b04-116">maxResults</span></span>|<span data-ttu-id="59b04-117">Um inteiro que especifica o número máximo de respostas a esperar, de serviços em uma rede ou Internet.</span><span class="sxs-lookup"><span data-stu-id="59b04-117">An integer that specifies the maximum number of replies to wait for, from services on a network or the Internet.</span></span> <span data-ttu-id="59b04-118">Se o máximo respostas são recebidas antes do valor especificado no `duration` atributo tiver decorrido, o término da operação de localizar.</span><span class="sxs-lookup"><span data-stu-id="59b04-118">If maximum replies are received before the value specified in the `duration` attribute has elapsed, the find operation ends.</span></span>|  
|<span data-ttu-id="59b04-119">scopeMatchBy</span><span class="sxs-lookup"><span data-stu-id="59b04-119">scopeMatchBy</span></span>|<span data-ttu-id="59b04-120">Um URI que especifica o algoritmo correspondente a ser usado ao casar os escopos na mensagem do Probe com isso do ponto de extremidade.</span><span class="sxs-lookup"><span data-stu-id="59b04-120">A URI that specify the matching algorithm to use while matching the scopes in the Probe message with that of the endpoint.</span></span><br /><br /> <span data-ttu-id="59b04-121">Há cinco regras de correspondência de escopo com suporte.</span><span class="sxs-lookup"><span data-stu-id="59b04-121">There are five supported scope-matching rules.</span></span> <span data-ttu-id="59b04-122">Se você não especificar uma regra de correspondência de escopo, `ScopeMatchByPrefix` é usado.</span><span class="sxs-lookup"><span data-stu-id="59b04-122">If you do not specify a scope-matching rule, `ScopeMatchByPrefix` is used.</span></span> <span data-ttu-id="59b04-123">Para obter mais informações sobre isso, consulte <xref:System.ServiceModel.Discovery.FindCriteria>.</span><span class="sxs-lookup"><span data-stu-id="59b04-123">For more information on this, see <xref:System.ServiceModel.Discovery.FindCriteria>.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="59b04-124">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="59b04-124">Child Elements</span></span>  
  
|<span data-ttu-id="59b04-125">Elemento</span><span class="sxs-lookup"><span data-stu-id="59b04-125">Element</span></span>|<span data-ttu-id="59b04-126">Descrição</span><span class="sxs-lookup"><span data-stu-id="59b04-126">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="59b04-127">\<contractTypeNames ></span><span class="sxs-lookup"><span data-stu-id="59b04-127">\<contractTypeNames></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/contracttypenames.md)|<span data-ttu-id="59b04-128">Uma coleção de elementos de configuração que contêm os nomes dos tipos de contrato de serviço de fluxo de trabalho.</span><span class="sxs-lookup"><span data-stu-id="59b04-128">A collection of configuration elements that contain the names of workflow service contract types.</span></span>|  
|<span data-ttu-id="59b04-129">\<Extensões > de \<findCriteria ></span><span class="sxs-lookup"><span data-stu-id="59b04-129">\<extensions> of \<findCriteria></span></span>|<span data-ttu-id="59b04-130">Uma coleção de objetos de elemento XML que fornecem extensões.</span><span class="sxs-lookup"><span data-stu-id="59b04-130">A collection of XML element objects that provide extensions.</span></span>|  
|[<span data-ttu-id="59b04-131">\<escopos ></span><span class="sxs-lookup"><span data-stu-id="59b04-131">\<scopes></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/scopes.md)|<span data-ttu-id="59b04-132">Uma coleção de objetos que contêm URIs absolutos que são usados durante uma operação de localização para localizar um serviço específico ou serviços.</span><span class="sxs-lookup"><span data-stu-id="59b04-132">A collection of objects that contain absolute URIs that are used during a find operation to locate a specific service or services.</span></span><br /><br /> <span data-ttu-id="59b04-133">Se o serviço específico for encontrado, foi feita uma correspondência bem-sucedida entre o URI do serviço e o URI de escopo, às vezes, com a Ajuda das regras de escopo que lidam com complicações de correspondência.</span><span class="sxs-lookup"><span data-stu-id="59b04-133">If the specific service is found, a successful match has been made between the service URI and the Scope URI, sometimes with the help of scope rules that handle complications of matching.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="59b04-134">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="59b04-134">Parent Elements</span></span>  
  
|<span data-ttu-id="59b04-135">Elemento</span><span class="sxs-lookup"><span data-stu-id="59b04-135">Element</span></span>|<span data-ttu-id="59b04-136">Descrição</span><span class="sxs-lookup"><span data-stu-id="59b04-136">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="59b04-137">\<standardEndpoints ></span><span class="sxs-lookup"><span data-stu-id="59b04-137">\<standardEndpoints></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/standardendpoints.md)|<span data-ttu-id="59b04-138">Contém as configurações necessitadas por um aplicativo para participar do processo de descoberta de serviço como um cliente.</span><span class="sxs-lookup"><span data-stu-id="59b04-138">Contains the settings needed by an application to participate in the service discovery process as a client.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="59b04-139">Consulte também</span><span class="sxs-lookup"><span data-stu-id="59b04-139">See Also</span></span>  
 <xref:System.ServiceModel.Discovery.FindCriteria>  
 <xref:System.ServiceModel.Discovery.Configuration.FindCriteriaElement>
