---
title: '&lt;Entradas&gt;'
ms.date: 03/30/2017
ms.assetid: 202e430c-c1b9-4343-abe2-ac78c181a3b7
ms.openlocfilehash: b9cc7f7736ffefaca68a0f197bd064a99c4dca9a
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32746703"
---
# <a name="ltentriesgt"></a><span data-ttu-id="9aece-102">&lt;Entradas&gt;</span><span class="sxs-lookup"><span data-stu-id="9aece-102">&lt;entries&gt;</span></span>
<span data-ttu-id="9aece-103">Uma entrada de roteamento que contêm mapeamentos entre os filtros de roteamento e os pontos de extremidade de destino para enviar mensagens para quando o filtro corresponde.</span><span class="sxs-lookup"><span data-stu-id="9aece-103">A routing entry that contain mappings between the routing filters and the target endpoints to send messages to when the filter matches.</span></span>  
  
 <span data-ttu-id="9aece-104">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="9aece-104">\<system.serviceModel></span></span>  
<span data-ttu-id="9aece-105">\<roteamento ></span><span class="sxs-lookup"><span data-stu-id="9aece-105">\<routing></span></span>  
<span data-ttu-id="9aece-106">\<routingTables ></span><span class="sxs-lookup"><span data-stu-id="9aece-106">\<routingTables></span></span>  
<span data-ttu-id="9aece-107">\<Tabela ></span><span class="sxs-lookup"><span data-stu-id="9aece-107">\<table></span></span>  
<span data-ttu-id="9aece-108">\<entradas ></span><span class="sxs-lookup"><span data-stu-id="9aece-108">\<entries></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9aece-109">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="9aece-109">Syntax</span></span>  
  
```xml
   <routing>      <filterTables>        <filterTable name="String">          <entries>            <add backupList="String"                 endpointName="String"                  filterName="String"                  priority="Integer" />          </entries>        </table>      </routingTables></routing>  
```

## <a name="attributes-and-elements"></a><span data-ttu-id="9aece-110">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="9aece-110">Attributes and Elements</span></span>  
 <span data-ttu-id="9aece-111">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="9aece-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="9aece-112">Atributos</span><span class="sxs-lookup"><span data-stu-id="9aece-112">Attributes</span></span>  
 <span data-ttu-id="9aece-113">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="9aece-113">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="9aece-114">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="9aece-114">Child Elements</span></span>  
  
|<span data-ttu-id="9aece-115">Elemento</span><span class="sxs-lookup"><span data-stu-id="9aece-115">Element</span></span>|<span data-ttu-id="9aece-116">Descrição</span><span class="sxs-lookup"><span data-stu-id="9aece-116">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="9aece-117">\<Filtros ></span><span class="sxs-lookup"><span data-stu-id="9aece-117">\<filters></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/filters-of-routing.md)|<span data-ttu-id="9aece-118">Mapeia um filtro para um ponto de extremidade do cliente que foi definido anteriormente.</span><span class="sxs-lookup"><span data-stu-id="9aece-118">Maps a filter to a client endpoint that was previously defined.</span></span> <span data-ttu-id="9aece-119">As mensagens que correspondem a este filtro serão enviadas para este destino.</span><span class="sxs-lookup"><span data-stu-id="9aece-119">Messages matching this filter will be sent to this destination.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="9aece-120">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="9aece-120">Parent Elements</span></span>  
  
|<span data-ttu-id="9aece-121">Elemento</span><span class="sxs-lookup"><span data-stu-id="9aece-121">Element</span></span>|<span data-ttu-id="9aece-122">Descrição</span><span class="sxs-lookup"><span data-stu-id="9aece-122">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="9aece-123">\<roteamento ></span><span class="sxs-lookup"><span data-stu-id="9aece-123">\<routing></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/routing.md)|<span data-ttu-id="9aece-124">Uma seção de configuração que contém uma tabela de roteamento.</span><span class="sxs-lookup"><span data-stu-id="9aece-124">A configuration section that contains a routing table.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="9aece-125">Consulte também</span><span class="sxs-lookup"><span data-stu-id="9aece-125">See Also</span></span>  
 <xref:System.ServiceModel.Routing.Configuration.RoutingSection?displayProperty=nameWithType>       
 <xref:System.ServiceModel.Routing.Configuration.FilterTableEntryElement?displayProperty=nameWithType>    
