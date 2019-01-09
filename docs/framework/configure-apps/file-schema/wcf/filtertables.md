---
title: '&lt;filterTables&gt;'
ms.date: 03/30/2017
ms.assetid: 41f1ac35-f559-473a-b2c3-8cc83a6a3831
ms.openlocfilehash: 2b537619a276f32c50576561aea03b5fbbb58e7d
ms.sourcegitcommit: 4ac80713f6faa220e5a119d5165308a58f7ccdc8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/09/2019
ms.locfileid: "54147779"
---
# <a name="ltfiltertablesgt"></a><span data-ttu-id="1665f-102">&lt;filterTables&gt;</span><span class="sxs-lookup"><span data-stu-id="1665f-102">&lt;filterTables&gt;</span></span>
<span data-ttu-id="1665f-103">Representa uma seção de configuração para definir as tabelas de roteamento que contêm mapeamentos entre os filtros de roteamento e os pontos de extremidade para enviar mensagens quando o filtro corresponde ao destino.</span><span class="sxs-lookup"><span data-stu-id="1665f-103">Represents a configuration section for defining routing tables that contain mappings between the routing filters and the target endpoints to send messages to when the filter matches.</span></span>  
  
 <span data-ttu-id="1665f-104">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="1665f-104">\<system.serviceModel></span></span>  
<span data-ttu-id="1665f-105">\<roteamento ></span><span class="sxs-lookup"><span data-stu-id="1665f-105">\<routing></span></span>  
<span data-ttu-id="1665f-106">\<routingTables ></span><span class="sxs-lookup"><span data-stu-id="1665f-106">\<routingTables></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1665f-107">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="1665f-107">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="1665f-108">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="1665f-108">Attributes and Elements</span></span>  
 <span data-ttu-id="1665f-109">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="1665f-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="1665f-110">Atributos</span><span class="sxs-lookup"><span data-stu-id="1665f-110">Attributes</span></span>  
 <span data-ttu-id="1665f-111">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="1665f-111">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="1665f-112">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="1665f-112">Child Elements</span></span>  
  
|<span data-ttu-id="1665f-113">Elemento</span><span class="sxs-lookup"><span data-stu-id="1665f-113">Element</span></span>|<span data-ttu-id="1665f-114">Descrição</span><span class="sxs-lookup"><span data-stu-id="1665f-114">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="1665f-115">\<Filtros ></span><span class="sxs-lookup"><span data-stu-id="1665f-115">\<filters></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/filters-of-routing.md)|<span data-ttu-id="1665f-116">Uma tabela de roteamento que contêm mapeamentos entre os filtros de roteamento e os pontos de extremidade para enviar mensagens para quando o filtro corresponde ao destino.</span><span class="sxs-lookup"><span data-stu-id="1665f-116">A routing table that contain mappings between the routing filters and the target endpoints to send messages to when the filter matches.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="1665f-117">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="1665f-117">Parent Elements</span></span>  
  
|<span data-ttu-id="1665f-118">Elemento</span><span class="sxs-lookup"><span data-stu-id="1665f-118">Element</span></span>|<span data-ttu-id="1665f-119">Descrição</span><span class="sxs-lookup"><span data-stu-id="1665f-119">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="1665f-120">\<roteamento ></span><span class="sxs-lookup"><span data-stu-id="1665f-120">\<routing></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/routing.md)|<span data-ttu-id="1665f-121">Uma seção de configuração que contém tabelas de roteamento e os filtros de roteamento.</span><span class="sxs-lookup"><span data-stu-id="1665f-121">A configuration section that contains routing filters and routing tables.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="1665f-122">Consulte também</span><span class="sxs-lookup"><span data-stu-id="1665f-122">See Also</span></span>  
 <xref:System.ServiceModel.Routing.Configuration.RoutingSection?displayProperty=nameWithType>       
 <xref:System.ServiceModel.Routing.Configuration.FilterTableCollection?displayProperty=nameWithType>    
