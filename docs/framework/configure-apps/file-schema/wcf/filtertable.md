---
title: <filterTable>
ms.date: 03/30/2017
ms.assetid: e9f05441-3ad1-49b9-a267-71724aa094b4
ms.openlocfilehash: ba65d3858cdbdf6b49c50e60f4e3cc9624fef136
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/30/2019
ms.locfileid: "55254399"
---
# <a name="filtertable"></a><span data-ttu-id="0bd8c-101">\<filterTable></span><span class="sxs-lookup"><span data-stu-id="0bd8c-101">\<filterTable></span></span>
<span data-ttu-id="0bd8c-102">Representa uma tabela de roteamento que contém uma lista de filtros para avaliar mensagens e o ponto de extremidade do cliente para rotear mensagens para se o filtro é avaliada como true.</span><span class="sxs-lookup"><span data-stu-id="0bd8c-102">Represents a routing table that contains a list of filters to evaluate messages against and the client endpoint to route messages to if the filter evaluates to true.</span></span>  
  
 <span data-ttu-id="0bd8c-103">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="0bd8c-103">\<system.serviceModel></span></span>  
<span data-ttu-id="0bd8c-104">\<routing></span><span class="sxs-lookup"><span data-stu-id="0bd8c-104">\<routing></span></span>  
<span data-ttu-id="0bd8c-105">\<routingTables></span><span class="sxs-lookup"><span data-stu-id="0bd8c-105">\<routingTables></span></span>  
<span data-ttu-id="0bd8c-106">\<table></span><span class="sxs-lookup"><span data-stu-id="0bd8c-106">\<table></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0bd8c-107">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="0bd8c-107">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="0bd8c-108">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="0bd8c-108">Attributes and Elements</span></span>  
 <span data-ttu-id="0bd8c-109">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="0bd8c-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="0bd8c-110">Atributos</span><span class="sxs-lookup"><span data-stu-id="0bd8c-110">Attributes</span></span>  
  
|<span data-ttu-id="0bd8c-111">Elemento</span><span class="sxs-lookup"><span data-stu-id="0bd8c-111">Element</span></span>|<span data-ttu-id="0bd8c-112">Descrição</span><span class="sxs-lookup"><span data-stu-id="0bd8c-112">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="0bd8c-113">name</span><span class="sxs-lookup"><span data-stu-id="0bd8c-113">name</span></span>|<span data-ttu-id="0bd8c-114">Uma cadeia de caracteres que contém o nome exclusivo deste elemento de configuração.</span><span class="sxs-lookup"><span data-stu-id="0bd8c-114">A string that contains the unique name of this configuration element.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="0bd8c-115">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="0bd8c-115">Child Elements</span></span>  
  
|<span data-ttu-id="0bd8c-116">Elemento</span><span class="sxs-lookup"><span data-stu-id="0bd8c-116">Element</span></span>|<span data-ttu-id="0bd8c-117">Descrição</span><span class="sxs-lookup"><span data-stu-id="0bd8c-117">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="0bd8c-118">\<filters></span><span class="sxs-lookup"><span data-stu-id="0bd8c-118">\<filters></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/filters-of-routing.md)|<span data-ttu-id="0bd8c-119">Mapeamentos entre os filtros de roteamento e os pontos de extremidade para enviar mensagens para quando o filtro corresponde ao destino.</span><span class="sxs-lookup"><span data-stu-id="0bd8c-119">Mappings between the routing filters and the target endpoints to send messages to when the filter matches.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="0bd8c-120">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="0bd8c-120">Parent Elements</span></span>  
  
|<span data-ttu-id="0bd8c-121">Elemento</span><span class="sxs-lookup"><span data-stu-id="0bd8c-121">Element</span></span>|<span data-ttu-id="0bd8c-122">Descrição</span><span class="sxs-lookup"><span data-stu-id="0bd8c-122">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="0bd8c-123">\<routing></span><span class="sxs-lookup"><span data-stu-id="0bd8c-123">\<routing></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/routing.md)|<span data-ttu-id="0bd8c-124">Uma seção de configuração que contém tabelas de roteamento.</span><span class="sxs-lookup"><span data-stu-id="0bd8c-124">A configuration section that contains routing tables.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="0bd8c-125">Consulte também</span><span class="sxs-lookup"><span data-stu-id="0bd8c-125">See also</span></span>
- <xref:System.ServiceModel.Routing.Configuration.RoutingSection?displayProperty=nameWithType>
