---
title: '&lt;filterTable&gt;'
ms.date: 03/30/2017
ms.assetid: e9f05441-3ad1-49b9-a267-71724aa094b4
ms.openlocfilehash: 83339eebef9a4f1b7f69e0bd1dd16b8278a68258
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54534599"
---
# <a name="ltfiltertablegt"></a><span data-ttu-id="d6450-102">&lt;filterTable&gt;</span><span class="sxs-lookup"><span data-stu-id="d6450-102">&lt;filterTable&gt;</span></span>
<span data-ttu-id="d6450-103">Representa uma tabela de roteamento que contém uma lista de filtros para avaliar mensagens e o ponto de extremidade do cliente para rotear mensagens para se o filtro é avaliada como true.</span><span class="sxs-lookup"><span data-stu-id="d6450-103">Represents a routing table that contains a list of filters to evaluate messages against and the client endpoint to route messages to if the filter evaluates to true.</span></span>  
  
 <span data-ttu-id="d6450-104">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="d6450-104">\<system.serviceModel></span></span>  
<span data-ttu-id="d6450-105">\<routing></span><span class="sxs-lookup"><span data-stu-id="d6450-105">\<routing></span></span>  
<span data-ttu-id="d6450-106">\<routingTables></span><span class="sxs-lookup"><span data-stu-id="d6450-106">\<routingTables></span></span>  
<span data-ttu-id="d6450-107">\<table></span><span class="sxs-lookup"><span data-stu-id="d6450-107">\<table></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d6450-108">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="d6450-108">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="d6450-109">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="d6450-109">Attributes and Elements</span></span>  
 <span data-ttu-id="d6450-110">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="d6450-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="d6450-111">Atributos</span><span class="sxs-lookup"><span data-stu-id="d6450-111">Attributes</span></span>  
  
|<span data-ttu-id="d6450-112">Elemento</span><span class="sxs-lookup"><span data-stu-id="d6450-112">Element</span></span>|<span data-ttu-id="d6450-113">Descrição</span><span class="sxs-lookup"><span data-stu-id="d6450-113">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="d6450-114">name</span><span class="sxs-lookup"><span data-stu-id="d6450-114">name</span></span>|<span data-ttu-id="d6450-115">Uma cadeia de caracteres que contém o nome exclusivo deste elemento de configuração.</span><span class="sxs-lookup"><span data-stu-id="d6450-115">A string that contains the unique name of this configuration element.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="d6450-116">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="d6450-116">Child Elements</span></span>  
  
|<span data-ttu-id="d6450-117">Elemento</span><span class="sxs-lookup"><span data-stu-id="d6450-117">Element</span></span>|<span data-ttu-id="d6450-118">Descrição</span><span class="sxs-lookup"><span data-stu-id="d6450-118">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="d6450-119">\<filters></span><span class="sxs-lookup"><span data-stu-id="d6450-119">\<filters></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/filters-of-routing.md)|<span data-ttu-id="d6450-120">Mapeamentos entre os filtros de roteamento e os pontos de extremidade para enviar mensagens para quando o filtro corresponde ao destino.</span><span class="sxs-lookup"><span data-stu-id="d6450-120">Mappings between the routing filters and the target endpoints to send messages to when the filter matches.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="d6450-121">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="d6450-121">Parent Elements</span></span>  
  
|<span data-ttu-id="d6450-122">Elemento</span><span class="sxs-lookup"><span data-stu-id="d6450-122">Element</span></span>|<span data-ttu-id="d6450-123">Descrição</span><span class="sxs-lookup"><span data-stu-id="d6450-123">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="d6450-124">\<routing></span><span class="sxs-lookup"><span data-stu-id="d6450-124">\<routing></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/routing.md)|<span data-ttu-id="d6450-125">Uma seção de configuração que contém tabelas de roteamento.</span><span class="sxs-lookup"><span data-stu-id="d6450-125">A configuration section that contains routing tables.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="d6450-126">Consulte também</span><span class="sxs-lookup"><span data-stu-id="d6450-126">See also</span></span>
- <xref:System.ServiceModel.Routing.Configuration.RoutingSection?displayProperty=nameWithType>
