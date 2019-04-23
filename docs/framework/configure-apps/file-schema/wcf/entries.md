---
title: <entries>
ms.date: 03/30/2017
ms.assetid: 202e430c-c1b9-4343-abe2-ac78c181a3b7
ms.openlocfilehash: 5561cf61cef2258ec61bd32770538add1c69f5c1
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59201787"
---
# <a name="entries"></a><span data-ttu-id="42573-101">\<entries></span><span class="sxs-lookup"><span data-stu-id="42573-101">\<entries></span></span>
<span data-ttu-id="42573-102">Uma entrada de roteamento que contêm mapeamentos entre os filtros de roteamento e os pontos de extremidade para enviar mensagens para quando o filtro corresponde ao destino.</span><span class="sxs-lookup"><span data-stu-id="42573-102">A routing entry that contain mappings between the routing filters and the target endpoints to send messages to when the filter matches.</span></span>  
  
 <span data-ttu-id="42573-103">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="42573-103">\<system.serviceModel></span></span>  
<span data-ttu-id="42573-104">\<routing></span><span class="sxs-lookup"><span data-stu-id="42573-104">\<routing></span></span>  
<span data-ttu-id="42573-105">\<routingTables></span><span class="sxs-lookup"><span data-stu-id="42573-105">\<routingTables></span></span>  
<span data-ttu-id="42573-106">\<table></span><span class="sxs-lookup"><span data-stu-id="42573-106">\<table></span></span>  
<span data-ttu-id="42573-107">\<entries></span><span class="sxs-lookup"><span data-stu-id="42573-107">\<entries></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="42573-108">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="42573-108">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="42573-109">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="42573-109">Attributes and Elements</span></span>  
 <span data-ttu-id="42573-110">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="42573-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="42573-111">Atributos</span><span class="sxs-lookup"><span data-stu-id="42573-111">Attributes</span></span>  
 <span data-ttu-id="42573-112">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="42573-112">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="42573-113">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="42573-113">Child Elements</span></span>  
  
|<span data-ttu-id="42573-114">Elemento</span><span class="sxs-lookup"><span data-stu-id="42573-114">Element</span></span>|<span data-ttu-id="42573-115">Descrição</span><span class="sxs-lookup"><span data-stu-id="42573-115">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="42573-116">\<filters></span><span class="sxs-lookup"><span data-stu-id="42573-116">\<filters></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/filters-of-routing.md)|<span data-ttu-id="42573-117">Mapeia um filtro para um ponto de extremidade do cliente que foi definido anteriormente.</span><span class="sxs-lookup"><span data-stu-id="42573-117">Maps a filter to a client endpoint that was previously defined.</span></span> <span data-ttu-id="42573-118">As mensagens que correspondem a esse filtro serão enviadas para este destino.</span><span class="sxs-lookup"><span data-stu-id="42573-118">Messages matching this filter will be sent to this destination.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="42573-119">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="42573-119">Parent Elements</span></span>  
  
|<span data-ttu-id="42573-120">Elemento</span><span class="sxs-lookup"><span data-stu-id="42573-120">Element</span></span>|<span data-ttu-id="42573-121">Descrição</span><span class="sxs-lookup"><span data-stu-id="42573-121">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="42573-122">\<routing></span><span class="sxs-lookup"><span data-stu-id="42573-122">\<routing></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/routing.md)|<span data-ttu-id="42573-123">Uma seção de configuração que contém uma tabela de roteamento.</span><span class="sxs-lookup"><span data-stu-id="42573-123">A configuration section that contains a routing table.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="42573-124">Consulte também</span><span class="sxs-lookup"><span data-stu-id="42573-124">See also</span></span>

- <xref:System.ServiceModel.Routing.Configuration.RoutingSection?displayProperty=nameWithType>
- <xref:System.ServiceModel.Routing.Configuration.FilterTableEntryElement?displayProperty=nameWithType>
