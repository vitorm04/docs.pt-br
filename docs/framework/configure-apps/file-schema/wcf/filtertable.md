---
title: '&lt;filterTable&gt;'
ms.date: 03/30/2017
ms.assetid: e9f05441-3ad1-49b9-a267-71724aa094b4
ms.openlocfilehash: f790e294b832f43a595d0636c60a8a67da5ad56a
ms.sourcegitcommit: 4ac80713f6faa220e5a119d5165308a58f7ccdc8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/09/2019
ms.locfileid: "54147875"
---
# <a name="ltfiltertablegt"></a><span data-ttu-id="be580-102">&lt;filterTable&gt;</span><span class="sxs-lookup"><span data-stu-id="be580-102">&lt;filterTable&gt;</span></span>
<span data-ttu-id="be580-103">Representa uma tabela de roteamento que contém uma lista de filtros para avaliar mensagens e o ponto de extremidade do cliente para rotear mensagens para se o filtro é avaliada como true.</span><span class="sxs-lookup"><span data-stu-id="be580-103">Represents a routing table that contains a list of filters to evaluate messages against and the client endpoint to route messages to if the filter evaluates to true.</span></span>  
  
 <span data-ttu-id="be580-104">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="be580-104">\<system.serviceModel></span></span>  
<span data-ttu-id="be580-105">\<roteamento ></span><span class="sxs-lookup"><span data-stu-id="be580-105">\<routing></span></span>  
<span data-ttu-id="be580-106">\<routingTables ></span><span class="sxs-lookup"><span data-stu-id="be580-106">\<routingTables></span></span>  
<span data-ttu-id="be580-107">\<Tabela ></span><span class="sxs-lookup"><span data-stu-id="be580-107">\<table></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="be580-108">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="be580-108">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="be580-109">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="be580-109">Attributes and Elements</span></span>  
 <span data-ttu-id="be580-110">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="be580-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="be580-111">Atributos</span><span class="sxs-lookup"><span data-stu-id="be580-111">Attributes</span></span>  
  
|<span data-ttu-id="be580-112">Elemento</span><span class="sxs-lookup"><span data-stu-id="be580-112">Element</span></span>|<span data-ttu-id="be580-113">Descrição</span><span class="sxs-lookup"><span data-stu-id="be580-113">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="be580-114">name</span><span class="sxs-lookup"><span data-stu-id="be580-114">name</span></span>|<span data-ttu-id="be580-115">Uma cadeia de caracteres que contém o nome exclusivo deste elemento de configuração.</span><span class="sxs-lookup"><span data-stu-id="be580-115">A string that contains the unique name of this configuration element.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="be580-116">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="be580-116">Child Elements</span></span>  
  
|<span data-ttu-id="be580-117">Elemento</span><span class="sxs-lookup"><span data-stu-id="be580-117">Element</span></span>|<span data-ttu-id="be580-118">Descrição</span><span class="sxs-lookup"><span data-stu-id="be580-118">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="be580-119">\<Filtros ></span><span class="sxs-lookup"><span data-stu-id="be580-119">\<filters></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/filters-of-routing.md)|<span data-ttu-id="be580-120">Mapeamentos entre os filtros de roteamento e os pontos de extremidade para enviar mensagens para quando o filtro corresponde ao destino.</span><span class="sxs-lookup"><span data-stu-id="be580-120">Mappings between the routing filters and the target endpoints to send messages to when the filter matches.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="be580-121">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="be580-121">Parent Elements</span></span>  
  
|<span data-ttu-id="be580-122">Elemento</span><span class="sxs-lookup"><span data-stu-id="be580-122">Element</span></span>|<span data-ttu-id="be580-123">Descrição</span><span class="sxs-lookup"><span data-stu-id="be580-123">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="be580-124">\<roteamento ></span><span class="sxs-lookup"><span data-stu-id="be580-124">\<routing></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/routing.md)|<span data-ttu-id="be580-125">Uma seção de configuração que contém tabelas de roteamento.</span><span class="sxs-lookup"><span data-stu-id="be580-125">A configuration section that contains routing tables.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="be580-126">Consulte também</span><span class="sxs-lookup"><span data-stu-id="be580-126">See Also</span></span>  
 <xref:System.ServiceModel.Routing.Configuration.RoutingSection?displayProperty=nameWithType>    
