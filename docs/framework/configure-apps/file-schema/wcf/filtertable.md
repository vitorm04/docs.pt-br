---
title: <filterTable>
ms.date: 03/30/2017
ms.assetid: e9f05441-3ad1-49b9-a267-71724aa094b4
ms.openlocfilehash: f9e64e667befb70d617574b2a03c3e6bebb2a143
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69925597"
---
# <a name="filtertable"></a><span data-ttu-id="f9160-101">\<filterTable></span><span class="sxs-lookup"><span data-stu-id="f9160-101">\<filterTable></span></span>
<span data-ttu-id="f9160-102">Representa uma tabela de roteamento que contém uma lista de filtros para avaliar as mensagens e o ponto de extremidade do cliente para rotear mensagens se o filtro for avaliado como verdadeiro.</span><span class="sxs-lookup"><span data-stu-id="f9160-102">Represents a routing table that contains a list of filters to evaluate messages against and the client endpoint to route messages to if the filter evaluates to true.</span></span>  
  
 <span data-ttu-id="f9160-103">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="f9160-103">\<system.serviceModel></span></span>  
<span data-ttu-id="f9160-104">\<> de roteamento</span><span class="sxs-lookup"><span data-stu-id="f9160-104">\<routing></span></span>  
<span data-ttu-id="f9160-105">\<routingTables></span><span class="sxs-lookup"><span data-stu-id="f9160-105">\<routingTables></span></span>  
<span data-ttu-id="f9160-106">\<table></span><span class="sxs-lookup"><span data-stu-id="f9160-106">\<table></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f9160-107">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="f9160-107">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="f9160-108">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="f9160-108">Attributes and Elements</span></span>  
 <span data-ttu-id="f9160-109">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="f9160-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="f9160-110">Atributos</span><span class="sxs-lookup"><span data-stu-id="f9160-110">Attributes</span></span>  
  
|<span data-ttu-id="f9160-111">Elemento</span><span class="sxs-lookup"><span data-stu-id="f9160-111">Element</span></span>|<span data-ttu-id="f9160-112">Descrição</span><span class="sxs-lookup"><span data-stu-id="f9160-112">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="f9160-113">name</span><span class="sxs-lookup"><span data-stu-id="f9160-113">name</span></span>|<span data-ttu-id="f9160-114">Uma cadeia de caracteres que contém o nome exclusivo deste elemento de configuração.</span><span class="sxs-lookup"><span data-stu-id="f9160-114">A string that contains the unique name of this configuration element.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="f9160-115">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="f9160-115">Child Elements</span></span>  
  
|<span data-ttu-id="f9160-116">Elemento</span><span class="sxs-lookup"><span data-stu-id="f9160-116">Element</span></span>|<span data-ttu-id="f9160-117">Descrição</span><span class="sxs-lookup"><span data-stu-id="f9160-117">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="f9160-118">\<filters></span><span class="sxs-lookup"><span data-stu-id="f9160-118">\<filters></span></span>](filters-of-routing.md)|<span data-ttu-id="f9160-119">Mapeamentos entre os filtros de roteamento e os pontos de extremidade de destino para enviar mensagens quando o filtro for correspondente.</span><span class="sxs-lookup"><span data-stu-id="f9160-119">Mappings between the routing filters and the target endpoints to send messages to when the filter matches.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="f9160-120">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="f9160-120">Parent Elements</span></span>  
  
|<span data-ttu-id="f9160-121">Elemento</span><span class="sxs-lookup"><span data-stu-id="f9160-121">Element</span></span>|<span data-ttu-id="f9160-122">Descrição</span><span class="sxs-lookup"><span data-stu-id="f9160-122">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="f9160-123">\<routing></span><span class="sxs-lookup"><span data-stu-id="f9160-123">\<routing></span></span>](routing.md)|<span data-ttu-id="f9160-124">Uma seção de configuração que contém tabelas de roteamento.</span><span class="sxs-lookup"><span data-stu-id="f9160-124">A configuration section that contains routing tables.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="f9160-125">Consulte também</span><span class="sxs-lookup"><span data-stu-id="f9160-125">See also</span></span>

- <xref:System.ServiceModel.Routing.Configuration.RoutingSection?displayProperty=nameWithType>
