---
title: <add> de <contractTypeNames>
ms.date: 03/30/2017
ms.assetid: 03aff6be-5dfb-4a64-ada3-e36227cd43c7
ms.openlocfilehash: 696752470aa39c2bcc66a1337f84119031742ae9
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/06/2020
ms.locfileid: "70850537"
---
# <a name="add-of-contracttypenames"></a><span data-ttu-id="a4301-102">\<add> de \<contractTypeNames></span><span class="sxs-lookup"><span data-stu-id="a4301-102">\<add> of \<contractTypeNames></span></span>
<span data-ttu-id="a4301-103">Um elemento de configuração que especifica o nome do contrato dos serviços que estão sendo pesquisados e os critérios normalmente usados durante a pesquisa de um serviço.</span><span class="sxs-lookup"><span data-stu-id="a4301-103">A configuration element that specifies the contract name of the services being searched for, and the criteria typically used when searching for a service.</span></span> <span data-ttu-id="a4301-104">Se mais de um nome de contrato for especificado, somente os pontos de extremidade de serviço correspondentes a todos os contratos serão respondidos.</span><span class="sxs-lookup"><span data-stu-id="a4301-104">If more than one contract name is specified, only service endpoints matching ALL contracts will reply.</span></span> <span data-ttu-id="a4301-105">Observe que no Windows Communication Foundation (WCF), um ponto de extremidade só pode dar suporte a um contrato.</span><span class="sxs-lookup"><span data-stu-id="a4301-105">Note that in Windows Communication Foundation (WCF), an endpoint can only support one contract.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<standardEndpoints>**](standardendpoints.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<dynamicEndpoint>**](dynamicendpoint.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<standardEndpoint>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<discoveryClientSettings>**](discoveryclientsettings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<findCriteria>**](findcriteria.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<contractTypeNames>**](contracttypenames.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<add>**  
  
## <a name="syntax"></a><span data-ttu-id="a4301-106">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="a4301-106">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="a4301-107">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="a4301-107">Attributes and Elements</span></span>  
 <span data-ttu-id="a4301-108">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="a4301-108">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="a4301-109">Atributos</span><span class="sxs-lookup"><span data-stu-id="a4301-109">Attributes</span></span>  
  
|<span data-ttu-id="a4301-110">Atributo</span><span class="sxs-lookup"><span data-stu-id="a4301-110">Attribute</span></span>|<span data-ttu-id="a4301-111">Descrição</span><span class="sxs-lookup"><span data-stu-id="a4301-111">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="a4301-112">name</span><span class="sxs-lookup"><span data-stu-id="a4301-112">name</span></span>|<span data-ttu-id="a4301-113">Uma cadeia de caracteres que especifica o nome do tipo de contrato.</span><span class="sxs-lookup"><span data-stu-id="a4301-113">A string that specifies the name of the contract type.</span></span>|  
|<span data-ttu-id="a4301-114">namespace</span><span class="sxs-lookup"><span data-stu-id="a4301-114">namespace</span></span>|<span data-ttu-id="a4301-115">Uma cadeia de caracteres que especifica o namespace do tipo de contrato.</span><span class="sxs-lookup"><span data-stu-id="a4301-115">A string that specifies the namespace of the contract type.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="a4301-116">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="a4301-116">Child Elements</span></span>  
 <span data-ttu-id="a4301-117">Nenhum</span><span class="sxs-lookup"><span data-stu-id="a4301-117">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="a4301-118">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="a4301-118">Parent Elements</span></span>  
  
|<span data-ttu-id="a4301-119">Elemento</span><span class="sxs-lookup"><span data-stu-id="a4301-119">Element</span></span>|<span data-ttu-id="a4301-120">Descrição</span><span class="sxs-lookup"><span data-stu-id="a4301-120">Description</span></span>|  
|-------------|-----------------|  
|[\<contractTypeNames>](contracttypenames.md)|<span data-ttu-id="a4301-121">Uma coleção de nomes de tipo de contrato.</span><span class="sxs-lookup"><span data-stu-id="a4301-121">A collection of contract type names.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="a4301-122">Confira também</span><span class="sxs-lookup"><span data-stu-id="a4301-122">See also</span></span>

- <xref:System.ServiceModel.Discovery.FindCriteria>
- <xref:System.ServiceModel.Discovery.Configuration.FindCriteriaElement>
- <xref:System.ServiceModel.Discovery.Configuration.ContractTypeNameElement>
