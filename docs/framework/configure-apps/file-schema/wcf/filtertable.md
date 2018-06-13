---
title: '&lt;filterTable&gt;'
ms.date: 03/30/2017
ms.assetid: e9f05441-3ad1-49b9-a267-71724aa094b4
ms.openlocfilehash: 7bdc76ba7a8e2927b93fa0207f48cc569279482f
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32747405"
---
# <a name="ltfiltertablegt"></a><span data-ttu-id="fbbc9-102">&lt;filterTable&gt;</span><span class="sxs-lookup"><span data-stu-id="fbbc9-102">&lt;filterTable&gt;</span></span>
<span data-ttu-id="fbbc9-103">Representa uma tabela de roteamento que contém uma lista de filtros para avaliar mensagens e o ponto de extremidade do cliente para rotear mensagens para se o filtro é avaliado como true.</span><span class="sxs-lookup"><span data-stu-id="fbbc9-103">Represents a routing table that contains a list of filters to evaluate messages against and the client endpoint to route messages to if the filter evaluates to true.</span></span>  
  
 <span data-ttu-id="fbbc9-104">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="fbbc9-104">\<system.serviceModel></span></span>  
<span data-ttu-id="fbbc9-105">\<roteamento ></span><span class="sxs-lookup"><span data-stu-id="fbbc9-105">\<routing></span></span>  
<span data-ttu-id="fbbc9-106">\<routingTables ></span><span class="sxs-lookup"><span data-stu-id="fbbc9-106">\<routingTables></span></span>  
<span data-ttu-id="fbbc9-107">\<Tabela ></span><span class="sxs-lookup"><span data-stu-id="fbbc9-107">\<table></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fbbc9-108">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="fbbc9-108">Syntax</span></span>  
  
```xml
   <routing>      <filterTables>        <filterTable name="String">          <entries>            <add backupList="String"                 endpointName="String"                  filterName="String"                  priority="Integer" />          </entries>        </table>      </routingTables></routing>  
```

## <a name="attributes-and-elements"></a><span data-ttu-id="fbbc9-109">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="fbbc9-109">Attributes and Elements</span></span>  
 <span data-ttu-id="fbbc9-110">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="fbbc9-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="fbbc9-111">Atributos</span><span class="sxs-lookup"><span data-stu-id="fbbc9-111">Attributes</span></span>  
  
|<span data-ttu-id="fbbc9-112">Elemento</span><span class="sxs-lookup"><span data-stu-id="fbbc9-112">Element</span></span>|<span data-ttu-id="fbbc9-113">Descrição</span><span class="sxs-lookup"><span data-stu-id="fbbc9-113">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="fbbc9-114">name</span><span class="sxs-lookup"><span data-stu-id="fbbc9-114">name</span></span>|<span data-ttu-id="fbbc9-115">Uma cadeia de caracteres que contém o nome exclusivo deste elemento de configuração.</span><span class="sxs-lookup"><span data-stu-id="fbbc9-115">A string that contains the unique name of this configuration element.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="fbbc9-116">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="fbbc9-116">Child Elements</span></span>  
  
|<span data-ttu-id="fbbc9-117">Elemento</span><span class="sxs-lookup"><span data-stu-id="fbbc9-117">Element</span></span>|<span data-ttu-id="fbbc9-118">Descrição</span><span class="sxs-lookup"><span data-stu-id="fbbc9-118">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="fbbc9-119">\<Filtros ></span><span class="sxs-lookup"><span data-stu-id="fbbc9-119">\<filters></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/filters-of-routing.md)|<span data-ttu-id="fbbc9-120">Mapeamentos entre os filtros de roteamento e os pontos de extremidade de destino para enviar mensagens para quando o filtro corresponde.</span><span class="sxs-lookup"><span data-stu-id="fbbc9-120">Mappings between the routing filters and the target endpoints to send messages to when the filter matches.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="fbbc9-121">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="fbbc9-121">Parent Elements</span></span>  
  
|<span data-ttu-id="fbbc9-122">Elemento</span><span class="sxs-lookup"><span data-stu-id="fbbc9-122">Element</span></span>|<span data-ttu-id="fbbc9-123">Descrição</span><span class="sxs-lookup"><span data-stu-id="fbbc9-123">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="fbbc9-124">\<roteamento ></span><span class="sxs-lookup"><span data-stu-id="fbbc9-124">\<routing></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/routing.md)|<span data-ttu-id="fbbc9-125">Uma seção de configuração que contém tabelas de roteamento.</span><span class="sxs-lookup"><span data-stu-id="fbbc9-125">A configuration section that contains routing tables.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="fbbc9-126">Consulte também</span><span class="sxs-lookup"><span data-stu-id="fbbc9-126">See Also</span></span>  
 <xref:System.ServiceModel.Routing.Configuration.RoutingSection?displayProperty=nameWithType>    
