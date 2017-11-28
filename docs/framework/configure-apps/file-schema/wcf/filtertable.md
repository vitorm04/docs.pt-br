---
title: '&lt;filterTable&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: e9f05441-3ad1-49b9-a267-71724aa094b4
caps.latest.revision: "6"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 04780d51cfd1d1d0049fc608cf7bd304be382b9b
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="ltfiltertablegt"></a><span data-ttu-id="587c9-102">&lt;filterTable&gt;</span><span class="sxs-lookup"><span data-stu-id="587c9-102">&lt;filterTable&gt;</span></span>
<span data-ttu-id="587c9-103">Representa uma tabela de roteamento que contém uma lista de filtros para avaliar mensagens e o ponto de extremidade do cliente para rotear mensagens para se o filtro é avaliado como true.</span><span class="sxs-lookup"><span data-stu-id="587c9-103">Represents a routing table that contains a list of filters to evaluate messages against and the client endpoint to route messages to if the filter evaluates to true.</span></span>  
  
 <span data-ttu-id="587c9-104">\<System. ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="587c9-104">\<system.serviceModel></span></span>  
<span data-ttu-id="587c9-105">\<roteamento ></span><span class="sxs-lookup"><span data-stu-id="587c9-105">\<routing></span></span>  
<span data-ttu-id="587c9-106">\<routingTables ></span><span class="sxs-lookup"><span data-stu-id="587c9-106">\<routingTables></span></span>  
<span data-ttu-id="587c9-107">\<Tabela ></span><span class="sxs-lookup"><span data-stu-id="587c9-107">\<table></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="587c9-108">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="587c9-108">Syntax</span></span>  
  
```xml
   <routing>      <filterTables>        <filterTable name="String">          <entries>            <add backupList="String"                 endpointName="String"                  filterName="String"                  priority="Integer" />          </entries>        </table>      </routingTables></routing>  
```

## <a name="attributes-and-elements"></a><span data-ttu-id="587c9-109">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="587c9-109">Attributes and Elements</span></span>  
 <span data-ttu-id="587c9-110">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="587c9-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="587c9-111">Atributos</span><span class="sxs-lookup"><span data-stu-id="587c9-111">Attributes</span></span>  
  
|<span data-ttu-id="587c9-112">Elemento</span><span class="sxs-lookup"><span data-stu-id="587c9-112">Element</span></span>|<span data-ttu-id="587c9-113">Descrição</span><span class="sxs-lookup"><span data-stu-id="587c9-113">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="587c9-114">name</span><span class="sxs-lookup"><span data-stu-id="587c9-114">name</span></span>|<span data-ttu-id="587c9-115">Uma cadeia de caracteres que contém o nome exclusivo deste elemento de configuração.</span><span class="sxs-lookup"><span data-stu-id="587c9-115">A string that contains the unique name of this configuration element.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="587c9-116">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="587c9-116">Child Elements</span></span>  
  
|<span data-ttu-id="587c9-117">Elemento</span><span class="sxs-lookup"><span data-stu-id="587c9-117">Element</span></span>|<span data-ttu-id="587c9-118">Descrição</span><span class="sxs-lookup"><span data-stu-id="587c9-118">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="587c9-119">\<Filtros ></span><span class="sxs-lookup"><span data-stu-id="587c9-119">\<filters></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/filters-of-routing.md)|<span data-ttu-id="587c9-120">Mapeamentos entre os filtros de roteamento e os pontos de extremidade de destino para enviar mensagens para quando o filtro corresponde.</span><span class="sxs-lookup"><span data-stu-id="587c9-120">Mappings between the routing filters and the target endpoints to send messages to when the filter matches.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="587c9-121">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="587c9-121">Parent Elements</span></span>  
  
|<span data-ttu-id="587c9-122">Elemento</span><span class="sxs-lookup"><span data-stu-id="587c9-122">Element</span></span>|<span data-ttu-id="587c9-123">Descrição</span><span class="sxs-lookup"><span data-stu-id="587c9-123">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="587c9-124">\<roteamento ></span><span class="sxs-lookup"><span data-stu-id="587c9-124">\<routing></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/routing.md)|<span data-ttu-id="587c9-125">Uma seção de configuração que contém tabelas de roteamento.</span><span class="sxs-lookup"><span data-stu-id="587c9-125">A configuration section that contains routing tables.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="587c9-126">Consulte também</span><span class="sxs-lookup"><span data-stu-id="587c9-126">See Also</span></span>  
 <xref:System.ServiceModel.Routing.Configuration.RoutingSection?displayProperty=nameWithType>    
