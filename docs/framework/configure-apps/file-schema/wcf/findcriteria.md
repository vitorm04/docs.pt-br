---
title: <findCriteria>
ms.date: 03/30/2017
ms.assetid: 5454cd19-6bf5-4ba8-94d1-f58d10dc1917
ms.openlocfilehash: 44e068ee205bc5e04382164e7ab00716b2c07dcf
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/10/2019
ms.locfileid: "70855157"
---
# <a name="findcriteria"></a><span data-ttu-id="384be-101">\<findCriteria></span><span class="sxs-lookup"><span data-stu-id="384be-101">\<findCriteria></span></span>
<span data-ttu-id="384be-102">Um elemento de configuração que fornece um conjunto de critérios usados por um aplicativo cliente para pesquisar um serviço de descoberta.</span><span class="sxs-lookup"><span data-stu-id="384be-102">A configuration element that supplies a set of criteria used by a client application to search for a discovery service.</span></span> <span data-ttu-id="384be-103">Os critérios podem ser agrupados em critérios de pesquisa (especificando quais serviços você está procurando) e localizar os critérios de encerramento (por quanto tempo a pesquisa deve durar).</span><span class="sxs-lookup"><span data-stu-id="384be-103">Criteria can be grouped into search criteria (specifying what services you’re looking for) and find termination criteria (how long the search should last).</span></span>  
  
<span data-ttu-id="384be-104">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="384be-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="384be-105">&nbsp;&nbsp;[ **\<> de System. serviceModel**](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="384be-105">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="384be-106">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> standardEndpoints**](standardendpoints.md)</span><span class="sxs-lookup"><span data-stu-id="384be-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<standardEndpoints>**](standardendpoints.md)</span></span>\
<span data-ttu-id="384be-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> dynamicEndpoint**](dynamicendpoint.md)</span><span class="sxs-lookup"><span data-stu-id="384be-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<dynamicEndpoint>**](dynamicendpoint.md)</span></span>\
<span data-ttu-id="384be-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<> standardEndpoint**</span><span class="sxs-lookup"><span data-stu-id="384be-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<standardEndpoint>**</span></span>\
<span data-ttu-id="384be-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> discoveryClientSettings**](discoveryclientsettings.md)</span><span class="sxs-lookup"><span data-stu-id="384be-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<discoveryClientSettings>**](discoveryclientsettings.md)</span></span>\
<span data-ttu-id="384be-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<> findCriteria**</span><span class="sxs-lookup"><span data-stu-id="384be-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<findCriteria>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="384be-111">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="384be-111">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="384be-112">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="384be-112">Attributes and Elements</span></span>  
 <span data-ttu-id="384be-113">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="384be-113">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="384be-114">Atributos</span><span class="sxs-lookup"><span data-stu-id="384be-114">Attributes</span></span>  
  
|<span data-ttu-id="384be-115">Atributo</span><span class="sxs-lookup"><span data-stu-id="384be-115">Attribute</span></span>|<span data-ttu-id="384be-116">Descrição</span><span class="sxs-lookup"><span data-stu-id="384be-116">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="384be-117">duration</span><span class="sxs-lookup"><span data-stu-id="384be-117">duration</span></span>|<span data-ttu-id="384be-118">Um valor TimeSpan que especifica o tempo máximo de espera para respostas de serviços na rede.</span><span class="sxs-lookup"><span data-stu-id="384be-118">A Timespan value that specifies the maximum time to wait for replies from services on the network.</span></span> <span data-ttu-id="384be-119">A duração padrão é de 20 segundos.</span><span class="sxs-lookup"><span data-stu-id="384be-119">The default duration is 20 seconds.</span></span>|  
|<span data-ttu-id="384be-120">maxResults</span><span class="sxs-lookup"><span data-stu-id="384be-120">maxResults</span></span>|<span data-ttu-id="384be-121">Um inteiro que especifica o número máximo de respostas a aguardar, de serviços em uma rede ou na Internet.</span><span class="sxs-lookup"><span data-stu-id="384be-121">An integer that specifies the maximum number of replies to wait for, from services on a network or the Internet.</span></span> <span data-ttu-id="384be-122">Se as respostas máximas forem recebidas antes que o `duration` valor especificado no atributo tenha decorrido, a operação Localizar será encerrada.</span><span class="sxs-lookup"><span data-stu-id="384be-122">If maximum replies are received before the value specified in the `duration` attribute has elapsed, the find operation ends.</span></span>|  
|<span data-ttu-id="384be-123">scopeMatchBy</span><span class="sxs-lookup"><span data-stu-id="384be-123">scopeMatchBy</span></span>|<span data-ttu-id="384be-124">Um URI que especifica o algoritmo de correspondência a ser usado ao corresponder os escopos na mensagem de investigação com o do ponto de extremidade.</span><span class="sxs-lookup"><span data-stu-id="384be-124">A URI that specify the matching algorithm to use while matching the scopes in the Probe message with that of the endpoint.</span></span><br /><br /> <span data-ttu-id="384be-125">Há cinco regras de correspondência de escopo com suporte.</span><span class="sxs-lookup"><span data-stu-id="384be-125">There are five supported scope-matching rules.</span></span> <span data-ttu-id="384be-126">Se você não especificar uma regra de correspondência de escopo, `ScopeMatchByPrefix` será usado.</span><span class="sxs-lookup"><span data-stu-id="384be-126">If you do not specify a scope-matching rule, `ScopeMatchByPrefix` is used.</span></span> <span data-ttu-id="384be-127">Para obter mais informações sobre isso, consulte <xref:System.ServiceModel.Discovery.FindCriteria>.</span><span class="sxs-lookup"><span data-stu-id="384be-127">For more information on this, see <xref:System.ServiceModel.Discovery.FindCriteria>.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="384be-128">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="384be-128">Child Elements</span></span>  
  
|<span data-ttu-id="384be-129">Elemento</span><span class="sxs-lookup"><span data-stu-id="384be-129">Element</span></span>|<span data-ttu-id="384be-130">Descrição</span><span class="sxs-lookup"><span data-stu-id="384be-130">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="384be-131">\<contractTypeNames></span><span class="sxs-lookup"><span data-stu-id="384be-131">\<contractTypeNames></span></span>](contracttypenames.md)|<span data-ttu-id="384be-132">Uma coleção de elementos de configuração que contém os nomes dos tipos de contrato de serviço de fluxo de trabalho.</span><span class="sxs-lookup"><span data-stu-id="384be-132">A collection of configuration elements that contain the names of workflow service contract types.</span></span>|  
|<span data-ttu-id="384be-133">\<extensões > do \<findCriteria ></span><span class="sxs-lookup"><span data-stu-id="384be-133">\<extensions> of \<findCriteria></span></span>|<span data-ttu-id="384be-134">Uma coleção de objetos de elemento XML que fornecem extensões.</span><span class="sxs-lookup"><span data-stu-id="384be-134">A collection of XML element objects that provide extensions.</span></span>|  
|[<span data-ttu-id="384be-135">\<scopes></span><span class="sxs-lookup"><span data-stu-id="384be-135">\<scopes></span></span>](scopes.md)|<span data-ttu-id="384be-136">Uma coleção de objetos que contêm URIs absolutos que são usados durante uma operação de localização para localizar um serviço ou serviços específicos.</span><span class="sxs-lookup"><span data-stu-id="384be-136">A collection of objects that contain absolute URIs that are used during a find operation to locate a specific service or services.</span></span><br /><br /> <span data-ttu-id="384be-137">Se o serviço específico for encontrado, uma correspondência bem-sucedida terá sido feita entre o URI do serviço e o URI do escopo, às vezes com a ajuda de regras de escopo que lidam com complicações de correspondência.</span><span class="sxs-lookup"><span data-stu-id="384be-137">If the specific service is found, a successful match has been made between the service URI and the Scope URI, sometimes with the help of scope rules that handle complications of matching.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="384be-138">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="384be-138">Parent Elements</span></span>  
  
|<span data-ttu-id="384be-139">Elemento</span><span class="sxs-lookup"><span data-stu-id="384be-139">Element</span></span>|<span data-ttu-id="384be-140">Descrição</span><span class="sxs-lookup"><span data-stu-id="384be-140">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="384be-141">\<standardEndpoints></span><span class="sxs-lookup"><span data-stu-id="384be-141">\<standardEndpoints></span></span>](standardendpoints.md)|<span data-ttu-id="384be-142">Contém as configurações necessárias para um aplicativo participar do processo de descoberta de serviço como um cliente.</span><span class="sxs-lookup"><span data-stu-id="384be-142">Contains the settings needed by an application to participate in the service discovery process as a client.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="384be-143">Consulte também</span><span class="sxs-lookup"><span data-stu-id="384be-143">See also</span></span>

- <xref:System.ServiceModel.Discovery.FindCriteria>
- <xref:System.ServiceModel.Discovery.Configuration.FindCriteriaElement>
