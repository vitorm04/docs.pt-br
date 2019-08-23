---
title: <entries>
ms.date: 03/30/2017
ms.assetid: 202e430c-c1b9-4343-abe2-ac78c181a3b7
ms.openlocfilehash: 610ba29ec98f4b1f2a9b1db3542bcb3aefb46457
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69925660"
---
# <a name="entries"></a><span data-ttu-id="724ff-101">\<entradas ></span><span class="sxs-lookup"><span data-stu-id="724ff-101">\<entries></span></span>
<span data-ttu-id="724ff-102">Uma entrada de roteamento que contém mapeamentos entre os filtros de roteamento e os pontos de extremidade de destino para envio de mensagens quando o filtro é correspondente.</span><span class="sxs-lookup"><span data-stu-id="724ff-102">A routing entry that contain mappings between the routing filters and the target endpoints to send messages to when the filter matches.</span></span>  
  
 <span data-ttu-id="724ff-103">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="724ff-103">\<system.serviceModel></span></span>  
<span data-ttu-id="724ff-104">\<> de roteamento</span><span class="sxs-lookup"><span data-stu-id="724ff-104">\<routing></span></span>  
<span data-ttu-id="724ff-105">\<routingTables></span><span class="sxs-lookup"><span data-stu-id="724ff-105">\<routingTables></span></span>  
<span data-ttu-id="724ff-106">\<table></span><span class="sxs-lookup"><span data-stu-id="724ff-106">\<table></span></span>  
<span data-ttu-id="724ff-107">\<entradas ></span><span class="sxs-lookup"><span data-stu-id="724ff-107">\<entries></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="724ff-108">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="724ff-108">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="724ff-109">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="724ff-109">Attributes and Elements</span></span>  
 <span data-ttu-id="724ff-110">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="724ff-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="724ff-111">Atributos</span><span class="sxs-lookup"><span data-stu-id="724ff-111">Attributes</span></span>  
 <span data-ttu-id="724ff-112">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="724ff-112">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="724ff-113">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="724ff-113">Child Elements</span></span>  
  
|<span data-ttu-id="724ff-114">Elemento</span><span class="sxs-lookup"><span data-stu-id="724ff-114">Element</span></span>|<span data-ttu-id="724ff-115">Descrição</span><span class="sxs-lookup"><span data-stu-id="724ff-115">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="724ff-116">\<filters></span><span class="sxs-lookup"><span data-stu-id="724ff-116">\<filters></span></span>](filters-of-routing.md)|<span data-ttu-id="724ff-117">Mapeia um filtro para um ponto de extremidade do cliente que foi definido anteriormente.</span><span class="sxs-lookup"><span data-stu-id="724ff-117">Maps a filter to a client endpoint that was previously defined.</span></span> <span data-ttu-id="724ff-118">As mensagens correspondentes a este filtro serão enviadas para esse destino.</span><span class="sxs-lookup"><span data-stu-id="724ff-118">Messages matching this filter will be sent to this destination.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="724ff-119">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="724ff-119">Parent Elements</span></span>  
  
|<span data-ttu-id="724ff-120">Elemento</span><span class="sxs-lookup"><span data-stu-id="724ff-120">Element</span></span>|<span data-ttu-id="724ff-121">Descrição</span><span class="sxs-lookup"><span data-stu-id="724ff-121">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="724ff-122">\<routing></span><span class="sxs-lookup"><span data-stu-id="724ff-122">\<routing></span></span>](routing.md)|<span data-ttu-id="724ff-123">Uma seção de configuração que contém uma tabela de roteamento.</span><span class="sxs-lookup"><span data-stu-id="724ff-123">A configuration section that contains a routing table.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="724ff-124">Consulte também</span><span class="sxs-lookup"><span data-stu-id="724ff-124">See also</span></span>

- <xref:System.ServiceModel.Routing.Configuration.RoutingSection?displayProperty=nameWithType>
- <xref:System.ServiceModel.Routing.Configuration.FilterTableEntryElement?displayProperty=nameWithType>
