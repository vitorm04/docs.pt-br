---
title: '&lt;entradas&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 202e430c-c1b9-4343-abe2-ac78c181a3b7
caps.latest.revision: "5"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: b1bd6fd679d3f6440ff685c8cd2646b1fa0a13e2
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="ltentriesgt"></a><span data-ttu-id="922a6-102">&lt;entradas&gt;</span><span class="sxs-lookup"><span data-stu-id="922a6-102">&lt;entries&gt;</span></span>
<span data-ttu-id="922a6-103">Uma entrada de roteamento que contêm mapeamentos entre os filtros de roteamento e os pontos de extremidade de destino para enviar mensagens para quando o filtro corresponde.</span><span class="sxs-lookup"><span data-stu-id="922a6-103">A routing entry that contain mappings between the routing filters and the target endpoints to send messages to when the filter matches.</span></span>  
  
 <span data-ttu-id="922a6-104">\<System. ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="922a6-104">\<system.serviceModel></span></span>  
<span data-ttu-id="922a6-105">\<roteamento ></span><span class="sxs-lookup"><span data-stu-id="922a6-105">\<routing></span></span>  
<span data-ttu-id="922a6-106">\<routingTables ></span><span class="sxs-lookup"><span data-stu-id="922a6-106">\<routingTables></span></span>  
<span data-ttu-id="922a6-107">\<Tabela ></span><span class="sxs-lookup"><span data-stu-id="922a6-107">\<table></span></span>  
<span data-ttu-id="922a6-108">\<entradas ></span><span class="sxs-lookup"><span data-stu-id="922a6-108">\<entries></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="922a6-109">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="922a6-109">Syntax</span></span>  
  
```xml
   <routing>      <filterTables>        <filterTable name="String">          <entries>            <add backupList="String"                 endpointName="String"                  filterName="String"                  priority="Integer" />          </entries>        </table>      </routingTables></routing>  
```

## <a name="attributes-and-elements"></a><span data-ttu-id="922a6-110">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="922a6-110">Attributes and Elements</span></span>  
 <span data-ttu-id="922a6-111">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="922a6-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="922a6-112">Atributos</span><span class="sxs-lookup"><span data-stu-id="922a6-112">Attributes</span></span>  
 <span data-ttu-id="922a6-113">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="922a6-113">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="922a6-114">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="922a6-114">Child Elements</span></span>  
  
|<span data-ttu-id="922a6-115">Elemento</span><span class="sxs-lookup"><span data-stu-id="922a6-115">Element</span></span>|<span data-ttu-id="922a6-116">Descrição</span><span class="sxs-lookup"><span data-stu-id="922a6-116">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="922a6-117">\<Filtros ></span><span class="sxs-lookup"><span data-stu-id="922a6-117">\<filters></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/filters-of-routing.md)|<span data-ttu-id="922a6-118">Mapeia um filtro para um ponto de extremidade do cliente que foi definido anteriormente.</span><span class="sxs-lookup"><span data-stu-id="922a6-118">Maps a filter to a client endpoint that was previously defined.</span></span> <span data-ttu-id="922a6-119">As mensagens que correspondem a este filtro serão enviadas para este destino.</span><span class="sxs-lookup"><span data-stu-id="922a6-119">Messages matching this filter will be sent to this destination.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="922a6-120">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="922a6-120">Parent Elements</span></span>  
  
|<span data-ttu-id="922a6-121">Elemento</span><span class="sxs-lookup"><span data-stu-id="922a6-121">Element</span></span>|<span data-ttu-id="922a6-122">Descrição</span><span class="sxs-lookup"><span data-stu-id="922a6-122">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="922a6-123">\<roteamento ></span><span class="sxs-lookup"><span data-stu-id="922a6-123">\<routing></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/routing.md)|<span data-ttu-id="922a6-124">Uma seção de configuração que contém uma tabela de roteamento.</span><span class="sxs-lookup"><span data-stu-id="922a6-124">A configuration section that contains a routing table.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="922a6-125">Consulte também</span><span class="sxs-lookup"><span data-stu-id="922a6-125">See Also</span></span>  
 <xref:System.ServiceModel.Routing.Configuration.RoutingSection?displayProperty=nameWithType>       
 <xref:System.ServiceModel.Routing.Configuration.FilterTableEntryElement?displayProperty=nameWithType>    
