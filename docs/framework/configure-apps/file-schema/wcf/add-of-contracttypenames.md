---
title: <add> de <contractTypeNames>
ms.date: 03/30/2017
ms.assetid: 03aff6be-5dfb-4a64-ada3-e36227cd43c7
ms.openlocfilehash: 69a0bbbc8774251dbdc062875bb06453f355c882
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91149134"
---
# <a name="add-of-contracttypenames"></a><span data-ttu-id="40d05-102">\<add> de \<contractTypeNames></span><span class="sxs-lookup"><span data-stu-id="40d05-102">\<add> of \<contractTypeNames></span></span>

<span data-ttu-id="40d05-103">Um elemento de configuração que especifica o nome do contrato dos serviços que estão sendo pesquisados e os critérios normalmente usados durante a pesquisa de um serviço.</span><span class="sxs-lookup"><span data-stu-id="40d05-103">A configuration element that specifies the contract name of the services being searched for, and the criteria typically used when searching for a service.</span></span> <span data-ttu-id="40d05-104">Se mais de um nome de contrato for especificado, somente os pontos de extremidade de serviço correspondentes a todos os contratos serão respondidos.</span><span class="sxs-lookup"><span data-stu-id="40d05-104">If more than one contract name is specified, only service endpoints matching ALL contracts will reply.</span></span> <span data-ttu-id="40d05-105">Observe que no Windows Communication Foundation (WCF), um ponto de extremidade só pode dar suporte a um contrato.</span><span class="sxs-lookup"><span data-stu-id="40d05-105">Note that in Windows Communication Foundation (WCF), an endpoint can only support one contract.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<standardEndpoints>**](standardendpoints.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<dynamicEndpoint>**](dynamicendpoint.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<standardEndpoint>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<discoveryClientSettings>**](discoveryclientsettings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<findCriteria>**](findcriteria.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<contractTypeNames>**](contracttypenames.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<add>**  
  
## <a name="syntax"></a><span data-ttu-id="40d05-106">Syntax</span><span class="sxs-lookup"><span data-stu-id="40d05-106">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="40d05-107">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="40d05-107">Attributes and Elements</span></span>  

 <span data-ttu-id="40d05-108">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="40d05-108">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="40d05-109">Atributos</span><span class="sxs-lookup"><span data-stu-id="40d05-109">Attributes</span></span>  
  
|<span data-ttu-id="40d05-110">Atributo</span><span class="sxs-lookup"><span data-stu-id="40d05-110">Attribute</span></span>|<span data-ttu-id="40d05-111">Descrição</span><span class="sxs-lookup"><span data-stu-id="40d05-111">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="40d05-112">name</span><span class="sxs-lookup"><span data-stu-id="40d05-112">name</span></span>|<span data-ttu-id="40d05-113">Uma cadeia de caracteres que especifica o nome do tipo de contrato.</span><span class="sxs-lookup"><span data-stu-id="40d05-113">A string that specifies the name of the contract type.</span></span>|  
|<span data-ttu-id="40d05-114">namespace</span><span class="sxs-lookup"><span data-stu-id="40d05-114">namespace</span></span>|<span data-ttu-id="40d05-115">Uma cadeia de caracteres que especifica o namespace do tipo de contrato.</span><span class="sxs-lookup"><span data-stu-id="40d05-115">A string that specifies the namespace of the contract type.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="40d05-116">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="40d05-116">Child Elements</span></span>  

 <span data-ttu-id="40d05-117">Nenhum</span><span class="sxs-lookup"><span data-stu-id="40d05-117">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="40d05-118">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="40d05-118">Parent Elements</span></span>  
  
|<span data-ttu-id="40d05-119">Elemento</span><span class="sxs-lookup"><span data-stu-id="40d05-119">Element</span></span>|<span data-ttu-id="40d05-120">Descrição</span><span class="sxs-lookup"><span data-stu-id="40d05-120">Description</span></span>|  
|-------------|-----------------|  
|[\<contractTypeNames>](contracttypenames.md)|<span data-ttu-id="40d05-121">Uma coleção de nomes de tipo de contrato.</span><span class="sxs-lookup"><span data-stu-id="40d05-121">A collection of contract type names.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="40d05-122">Confira também</span><span class="sxs-lookup"><span data-stu-id="40d05-122">See also</span></span>

- <xref:System.ServiceModel.Discovery.FindCriteria>
- <xref:System.ServiceModel.Discovery.Configuration.FindCriteriaElement>
- <xref:System.ServiceModel.Discovery.Configuration.ContractTypeNameElement>
