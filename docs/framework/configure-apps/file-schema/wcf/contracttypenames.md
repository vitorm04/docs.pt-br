---
title: <contractTypeNames>
ms.date: 03/30/2017
ms.assetid: 5ec5efc6-87f8-4160-9be0-dcd2e01df3df
ms.openlocfilehash: c67e5b9e82b96e27ce73512680bd4236b26ef4dd
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/06/2020
ms.locfileid: "70855445"
---
# \<contractTypeNames>
<span data-ttu-id="f06b8-101">Uma seção de configuração que especifica uma lista de nomes de tipo de contrato, que são os nomes de contrato dos serviços que estão sendo pesquisados e os critérios normalmente usados ao pesquisar um serviço.</span><span class="sxs-lookup"><span data-stu-id="f06b8-101">A configuration section that specifies a list of contract type names, which are the contract names of the services being searched for, and the criteria typically used when searching for a service.</span></span> <span data-ttu-id="f06b8-102">Se mais de um nome de contrato for especificado, somente os pontos de extremidade de serviço correspondentes a todos os contratos serão respondidos.</span><span class="sxs-lookup"><span data-stu-id="f06b8-102">If more than one contract name is specified, only service endpoints matching ALL contracts will reply.</span></span> <span data-ttu-id="f06b8-103">Observe que no Windows Communication Foundation (WCF), um ponto de extremidade só pode dar suporte a um contrato.</span><span class="sxs-lookup"><span data-stu-id="f06b8-103">Note that in Windows Communication Foundation (WCF), an endpoint can only support one contract.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<standardEndpoints>**](standardendpoints.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<dynamicEndpoint>**](dynamicendpoint.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<standardEndpoint>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<discoveryClientSettings>**](discoveryclientsettings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<findCriteria>**](findcriteria.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<contractTypeNames>**  
  
## <a name="syntax"></a><span data-ttu-id="f06b8-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="f06b8-104">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="f06b8-105">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="f06b8-105">Attributes and Elements</span></span>  
 <span data-ttu-id="f06b8-106">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="f06b8-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="f06b8-107">Atributos</span><span class="sxs-lookup"><span data-stu-id="f06b8-107">Attributes</span></span>  
 <span data-ttu-id="f06b8-108">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="f06b8-108">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="f06b8-109">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="f06b8-109">Child Elements</span></span>  
  
|<span data-ttu-id="f06b8-110">Elemento</span><span class="sxs-lookup"><span data-stu-id="f06b8-110">Element</span></span>|<span data-ttu-id="f06b8-111">Descrição</span><span class="sxs-lookup"><span data-stu-id="f06b8-111">Description</span></span>|  
|-------------|-----------------|  
|[\<add>](contracttypenames.md)|<span data-ttu-id="f06b8-112">Um nome de tipo de contrato é uma propriedade que se refere ao conjunto de critérios normalmente usado ao pesquisar um serviço.</span><span class="sxs-lookup"><span data-stu-id="f06b8-112">A contract type name is a property that refers to the set of criteria typically used when searching for a service.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="f06b8-113">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="f06b8-113">Parent Elements</span></span>  
  
|<span data-ttu-id="f06b8-114">Elemento</span><span class="sxs-lookup"><span data-stu-id="f06b8-114">Element</span></span>|<span data-ttu-id="f06b8-115">Descrição</span><span class="sxs-lookup"><span data-stu-id="f06b8-115">Description</span></span>|  
|-------------|-----------------|  
|[\<findCriteria>](findcriteria.md)|<span data-ttu-id="f06b8-116">Um elemento de configuração que fornece um conjunto de critérios usados por um aplicativo cliente para pesquisar um serviço de descoberta.</span><span class="sxs-lookup"><span data-stu-id="f06b8-116">A configuration element that supplies a set of criteria used by a client application to search for a discovery service.</span></span> <span data-ttu-id="f06b8-117">Os critérios podem ser agrupados em critérios de pesquisa (especificando quais serviços você está procurando) e localizar os critérios de encerramento (por quanto tempo a pesquisa deve durar).</span><span class="sxs-lookup"><span data-stu-id="f06b8-117">Criteria can be grouped into search criteria (specifying what services you’re looking for) and find termination criteria (how long the search should last).</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="f06b8-118">Confira também</span><span class="sxs-lookup"><span data-stu-id="f06b8-118">See also</span></span>

- <xref:System.ServiceModel.Discovery.FindCriteria>
- <xref:System.ServiceModel.Discovery.Configuration.FindCriteriaElement>
- <xref:System.ServiceModel.Discovery.Configuration.ContractTypeNameElementCollection>
