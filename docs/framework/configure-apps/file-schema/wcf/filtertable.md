---
title: <filterTable>
ms.date: 03/30/2017
ms.assetid: e9f05441-3ad1-49b9-a267-71724aa094b4
ms.openlocfilehash: 4e5c7d56e35afe3001f4c70064adbfef7702c720
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59229271"
---
# <a name="filtertable"></a><span data-ttu-id="0450b-101">\<filterTable></span><span class="sxs-lookup"><span data-stu-id="0450b-101">\<filterTable></span></span>
<span data-ttu-id="0450b-102">Representa uma tabela de roteamento que contém uma lista de filtros para avaliar mensagens e o ponto de extremidade do cliente para rotear mensagens para se o filtro é avaliada como true.</span><span class="sxs-lookup"><span data-stu-id="0450b-102">Represents a routing table that contains a list of filters to evaluate messages against and the client endpoint to route messages to if the filter evaluates to true.</span></span>  
  
 <span data-ttu-id="0450b-103">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="0450b-103">\<system.serviceModel></span></span>  
<span data-ttu-id="0450b-104">\<routing></span><span class="sxs-lookup"><span data-stu-id="0450b-104">\<routing></span></span>  
<span data-ttu-id="0450b-105">\<routingTables></span><span class="sxs-lookup"><span data-stu-id="0450b-105">\<routingTables></span></span>  
<span data-ttu-id="0450b-106">\<table></span><span class="sxs-lookup"><span data-stu-id="0450b-106">\<table></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0450b-107">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="0450b-107">Syntax</span></span>  
  
```xml  
<routing>
  <filterTables>
    <filterTable name="String">
      <entries>
        <add backupList="String"
             endpointName="String"
             filterName="String"
             priority="Integer" />
      </entries>
    </filterTable>
  </filterTables>
</routing>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="0450b-108">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="0450b-108">Attributes and Elements</span></span>  
 <span data-ttu-id="0450b-109">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="0450b-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="0450b-110">Atributos</span><span class="sxs-lookup"><span data-stu-id="0450b-110">Attributes</span></span>  
  
|<span data-ttu-id="0450b-111">Elemento</span><span class="sxs-lookup"><span data-stu-id="0450b-111">Element</span></span>|<span data-ttu-id="0450b-112">Descrição</span><span class="sxs-lookup"><span data-stu-id="0450b-112">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="0450b-113">name</span><span class="sxs-lookup"><span data-stu-id="0450b-113">name</span></span>|<span data-ttu-id="0450b-114">Uma cadeia de caracteres que contém o nome exclusivo deste elemento de configuração.</span><span class="sxs-lookup"><span data-stu-id="0450b-114">A string that contains the unique name of this configuration element.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="0450b-115">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="0450b-115">Child Elements</span></span>  
  
|<span data-ttu-id="0450b-116">Elemento</span><span class="sxs-lookup"><span data-stu-id="0450b-116">Element</span></span>|<span data-ttu-id="0450b-117">Descrição</span><span class="sxs-lookup"><span data-stu-id="0450b-117">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="0450b-118">\<filters></span><span class="sxs-lookup"><span data-stu-id="0450b-118">\<filters></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/filters-of-routing.md)|<span data-ttu-id="0450b-119">Mapeamentos entre os filtros de roteamento e os pontos de extremidade para enviar mensagens para quando o filtro corresponde ao destino.</span><span class="sxs-lookup"><span data-stu-id="0450b-119">Mappings between the routing filters and the target endpoints to send messages to when the filter matches.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="0450b-120">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="0450b-120">Parent Elements</span></span>  
  
|<span data-ttu-id="0450b-121">Elemento</span><span class="sxs-lookup"><span data-stu-id="0450b-121">Element</span></span>|<span data-ttu-id="0450b-122">Descrição</span><span class="sxs-lookup"><span data-stu-id="0450b-122">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="0450b-123">\<routing></span><span class="sxs-lookup"><span data-stu-id="0450b-123">\<routing></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/routing.md)|<span data-ttu-id="0450b-124">Uma seção de configuração que contém tabelas de roteamento.</span><span class="sxs-lookup"><span data-stu-id="0450b-124">A configuration section that contains routing tables.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="0450b-125">Consulte também</span><span class="sxs-lookup"><span data-stu-id="0450b-125">See also</span></span>

- <xref:System.ServiceModel.Routing.Configuration.RoutingSection?displayProperty=nameWithType>
