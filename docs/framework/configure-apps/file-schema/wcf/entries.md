---
title: '&lt;Entradas&gt;'
ms.date: 03/30/2017
ms.assetid: 202e430c-c1b9-4343-abe2-ac78c181a3b7
ms.openlocfilehash: 33f98cb4b138307622a14463ce5a3008058b6e31
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54587054"
---
# <a name="ltentriesgt"></a><span data-ttu-id="f406d-102">&lt;Entradas&gt;</span><span class="sxs-lookup"><span data-stu-id="f406d-102">&lt;entries&gt;</span></span>
<span data-ttu-id="f406d-103">Uma entrada de roteamento que contêm mapeamentos entre os filtros de roteamento e os pontos de extremidade para enviar mensagens para quando o filtro corresponde ao destino.</span><span class="sxs-lookup"><span data-stu-id="f406d-103">A routing entry that contain mappings between the routing filters and the target endpoints to send messages to when the filter matches.</span></span>  
  
 <span data-ttu-id="f406d-104">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="f406d-104">\<system.serviceModel></span></span>  
<span data-ttu-id="f406d-105">\<routing></span><span class="sxs-lookup"><span data-stu-id="f406d-105">\<routing></span></span>  
<span data-ttu-id="f406d-106">\<routingTables></span><span class="sxs-lookup"><span data-stu-id="f406d-106">\<routingTables></span></span>  
<span data-ttu-id="f406d-107">\<table></span><span class="sxs-lookup"><span data-stu-id="f406d-107">\<table></span></span>  
<span data-ttu-id="f406d-108">\<entries></span><span class="sxs-lookup"><span data-stu-id="f406d-108">\<entries></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f406d-109">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="f406d-109">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="f406d-110">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="f406d-110">Attributes and Elements</span></span>  
 <span data-ttu-id="f406d-111">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="f406d-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="f406d-112">Atributos</span><span class="sxs-lookup"><span data-stu-id="f406d-112">Attributes</span></span>  
 <span data-ttu-id="f406d-113">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="f406d-113">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="f406d-114">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="f406d-114">Child Elements</span></span>  
  
|<span data-ttu-id="f406d-115">Elemento</span><span class="sxs-lookup"><span data-stu-id="f406d-115">Element</span></span>|<span data-ttu-id="f406d-116">Descrição</span><span class="sxs-lookup"><span data-stu-id="f406d-116">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="f406d-117">\<filters></span><span class="sxs-lookup"><span data-stu-id="f406d-117">\<filters></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/filters-of-routing.md)|<span data-ttu-id="f406d-118">Mapeia um filtro para um ponto de extremidade do cliente que foi definido anteriormente.</span><span class="sxs-lookup"><span data-stu-id="f406d-118">Maps a filter to a client endpoint that was previously defined.</span></span> <span data-ttu-id="f406d-119">As mensagens que correspondem a esse filtro serão enviadas para este destino.</span><span class="sxs-lookup"><span data-stu-id="f406d-119">Messages matching this filter will be sent to this destination.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="f406d-120">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="f406d-120">Parent Elements</span></span>  
  
|<span data-ttu-id="f406d-121">Elemento</span><span class="sxs-lookup"><span data-stu-id="f406d-121">Element</span></span>|<span data-ttu-id="f406d-122">Descrição</span><span class="sxs-lookup"><span data-stu-id="f406d-122">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="f406d-123">\<routing></span><span class="sxs-lookup"><span data-stu-id="f406d-123">\<routing></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/routing.md)|<span data-ttu-id="f406d-124">Uma seção de configuração que contém uma tabela de roteamento.</span><span class="sxs-lookup"><span data-stu-id="f406d-124">A configuration section that contains a routing table.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="f406d-125">Consulte também</span><span class="sxs-lookup"><span data-stu-id="f406d-125">See also</span></span>
- <xref:System.ServiceModel.Routing.Configuration.RoutingSection?displayProperty=nameWithType>
- <xref:System.ServiceModel.Routing.Configuration.FilterTableEntryElement?displayProperty=nameWithType>
