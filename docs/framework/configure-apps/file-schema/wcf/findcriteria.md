---
title: <findCriteria>
ms.date: 03/30/2017
ms.assetid: 5454cd19-6bf5-4ba8-94d1-f58d10dc1917
ms.openlocfilehash: e82312cb17fbd3f76f781ea37f761e946319a0a0
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/05/2019
ms.locfileid: "57351847"
---
# <a name="findcriteria"></a><span data-ttu-id="ee444-101">\<findCriteria></span><span class="sxs-lookup"><span data-stu-id="ee444-101">\<findCriteria></span></span>
<span data-ttu-id="ee444-102">Um elemento de configuração que fornece um conjunto de critérios utilizados por um aplicativo cliente para pesquisar para um serviço de descoberta.</span><span class="sxs-lookup"><span data-stu-id="ee444-102">A configuration element that supplies a set of criteria used by a client application to search for a discovery service.</span></span> <span data-ttu-id="ee444-103">Critérios podem ser agrupados em critérios de pesquisa (especificando quais serviços você está procurando) e encontre os critérios de término (quanto tempo a pesquisa deve durar).</span><span class="sxs-lookup"><span data-stu-id="ee444-103">Criteria can be grouped into search criteria (specifying what services you’re looking for) and find termination criteria (how long the search should last).</span></span>  
  
 <span data-ttu-id="ee444-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="ee444-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="ee444-105">\<standardEndpoints></span><span class="sxs-lookup"><span data-stu-id="ee444-105">\<standardEndpoints></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ee444-106">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="ee444-106">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="ee444-107">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="ee444-107">Attributes and Elements</span></span>  
 <span data-ttu-id="ee444-108">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="ee444-108">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="ee444-109">Atributos</span><span class="sxs-lookup"><span data-stu-id="ee444-109">Attributes</span></span>  
  
|<span data-ttu-id="ee444-110">Atributo</span><span class="sxs-lookup"><span data-stu-id="ee444-110">Attribute</span></span>|<span data-ttu-id="ee444-111">Descrição</span><span class="sxs-lookup"><span data-stu-id="ee444-111">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="ee444-112">duration</span><span class="sxs-lookup"><span data-stu-id="ee444-112">duration</span></span>|<span data-ttu-id="ee444-113">Um valor de Timespan que especifica o tempo máximo de espera por respostas de serviços na rede.</span><span class="sxs-lookup"><span data-stu-id="ee444-113">A Timespan value that specifies the maximum time to wait for replies from services on the network.</span></span> <span data-ttu-id="ee444-114">A duração padrão é 20 segundos.</span><span class="sxs-lookup"><span data-stu-id="ee444-114">The default duration is 20 seconds.</span></span>|  
|<span data-ttu-id="ee444-115">maxResults</span><span class="sxs-lookup"><span data-stu-id="ee444-115">maxResults</span></span>|<span data-ttu-id="ee444-116">Um inteiro que especifica o número máximo de respostas a esperar, de serviços em uma rede ou Internet.</span><span class="sxs-lookup"><span data-stu-id="ee444-116">An integer that specifies the maximum number of replies to wait for, from services on a network or the Internet.</span></span> <span data-ttu-id="ee444-117">Se o máximo respostas são recebidas antes do valor especificado no `duration` atributo tiver decorrido, o término da operação de localizar.</span><span class="sxs-lookup"><span data-stu-id="ee444-117">If maximum replies are received before the value specified in the `duration` attribute has elapsed, the find operation ends.</span></span>|  
|<span data-ttu-id="ee444-118">scopeMatchBy</span><span class="sxs-lookup"><span data-stu-id="ee444-118">scopeMatchBy</span></span>|<span data-ttu-id="ee444-119">Um URI que especifica o algoritmo correspondente a ser usado ao casar os escopos na mensagem do Probe com isso do ponto de extremidade.</span><span class="sxs-lookup"><span data-stu-id="ee444-119">A URI that specify the matching algorithm to use while matching the scopes in the Probe message with that of the endpoint.</span></span><br /><br /> <span data-ttu-id="ee444-120">Há cinco regras de correspondência de escopo com suporte.</span><span class="sxs-lookup"><span data-stu-id="ee444-120">There are five supported scope-matching rules.</span></span> <span data-ttu-id="ee444-121">Se você não especificar uma regra de correspondência de escopo, `ScopeMatchByPrefix` é usado.</span><span class="sxs-lookup"><span data-stu-id="ee444-121">If you do not specify a scope-matching rule, `ScopeMatchByPrefix` is used.</span></span> <span data-ttu-id="ee444-122">Para obter mais informações sobre isso, consulte <xref:System.ServiceModel.Discovery.FindCriteria>.</span><span class="sxs-lookup"><span data-stu-id="ee444-122">For more information on this, see <xref:System.ServiceModel.Discovery.FindCriteria>.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="ee444-123">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="ee444-123">Child Elements</span></span>  
  
|<span data-ttu-id="ee444-124">Elemento</span><span class="sxs-lookup"><span data-stu-id="ee444-124">Element</span></span>|<span data-ttu-id="ee444-125">Descrição</span><span class="sxs-lookup"><span data-stu-id="ee444-125">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="ee444-126">\<contractTypeNames></span><span class="sxs-lookup"><span data-stu-id="ee444-126">\<contractTypeNames></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/contracttypenames.md)|<span data-ttu-id="ee444-127">Uma coleção de elementos de configuração que contêm os nomes dos tipos de contrato de serviço de fluxo de trabalho.</span><span class="sxs-lookup"><span data-stu-id="ee444-127">A collection of configuration elements that contain the names of workflow service contract types.</span></span>|  
|<span data-ttu-id="ee444-128">\<Extensões > de \<findCriteria ></span><span class="sxs-lookup"><span data-stu-id="ee444-128">\<extensions> of \<findCriteria></span></span>|<span data-ttu-id="ee444-129">Uma coleção de objetos de elemento XML que fornecem extensões.</span><span class="sxs-lookup"><span data-stu-id="ee444-129">A collection of XML element objects that provide extensions.</span></span>|  
|[<span data-ttu-id="ee444-130">\<scopes></span><span class="sxs-lookup"><span data-stu-id="ee444-130">\<scopes></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/scopes.md)|<span data-ttu-id="ee444-131">Uma coleção de objetos que contêm URIs absolutos que são usados durante uma operação de localização para localizar um serviço específico ou serviços.</span><span class="sxs-lookup"><span data-stu-id="ee444-131">A collection of objects that contain absolute URIs that are used during a find operation to locate a specific service or services.</span></span><br /><br /> <span data-ttu-id="ee444-132">Se o serviço específico for encontrado, foi feita uma correspondência bem-sucedida entre o URI do serviço e o URI de escopo, às vezes, com a Ajuda das regras de escopo que lidam com complicações de correspondência.</span><span class="sxs-lookup"><span data-stu-id="ee444-132">If the specific service is found, a successful match has been made between the service URI and the Scope URI, sometimes with the help of scope rules that handle complications of matching.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="ee444-133">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="ee444-133">Parent Elements</span></span>  
  
|<span data-ttu-id="ee444-134">Elemento</span><span class="sxs-lookup"><span data-stu-id="ee444-134">Element</span></span>|<span data-ttu-id="ee444-135">Descrição</span><span class="sxs-lookup"><span data-stu-id="ee444-135">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="ee444-136">\<standardEndpoints></span><span class="sxs-lookup"><span data-stu-id="ee444-136">\<standardEndpoints></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/standardendpoints.md)|<span data-ttu-id="ee444-137">Contém as configurações necessitadas por um aplicativo para participar do processo de descoberta de serviço como um cliente.</span><span class="sxs-lookup"><span data-stu-id="ee444-137">Contains the settings needed by an application to participate in the service discovery process as a client.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="ee444-138">Consulte também</span><span class="sxs-lookup"><span data-stu-id="ee444-138">See also</span></span>
- <xref:System.ServiceModel.Discovery.FindCriteria>
- <xref:System.ServiceModel.Discovery.Configuration.FindCriteriaElement>
