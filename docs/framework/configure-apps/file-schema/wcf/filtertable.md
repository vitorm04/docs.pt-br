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
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 96425604fab8f70456ea1e0d97efb2c3bf843224
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/02/2017
---
# <a name="ltfiltertablegt"></a><span data-ttu-id="b7a2e-102">&lt;filterTable&gt;</span><span class="sxs-lookup"><span data-stu-id="b7a2e-102">&lt;filterTable&gt;</span></span>
<span data-ttu-id="b7a2e-103">Representa uma tabela de roteamento que contém uma lista de filtros para avaliar mensagens e o ponto de extremidade do cliente para rotear mensagens para se o filtro é avaliado como true.</span><span class="sxs-lookup"><span data-stu-id="b7a2e-103">Represents a routing table that contains a list of filters to evaluate messages against and the client endpoint to route messages to if the filter evaluates to true.</span></span>  
  
 <span data-ttu-id="b7a2e-104">\<System. ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="b7a2e-104">\<system.serviceModel></span></span>  
<span data-ttu-id="b7a2e-105">\<roteamento ></span><span class="sxs-lookup"><span data-stu-id="b7a2e-105">\<routing></span></span>  
<span data-ttu-id="b7a2e-106">\<routingTables ></span><span class="sxs-lookup"><span data-stu-id="b7a2e-106">\<routingTables></span></span>  
<span data-ttu-id="b7a2e-107">\<Tabela ></span><span class="sxs-lookup"><span data-stu-id="b7a2e-107">\<table></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b7a2e-108">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="b7a2e-108">Syntax</span></span>  
  
```xml
   <routing>      <filterTables>        <filterTable name="String">          <entries>            <add backupList="String"                 endpointName="String"                  filterName="String"                  priority="Integer" />          </entries>        </table>      </routingTables></routing>  
```

## <a name="attributes-and-elements"></a><span data-ttu-id="b7a2e-109">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="b7a2e-109">Attributes and Elements</span></span>  
 <span data-ttu-id="b7a2e-110">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="b7a2e-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="b7a2e-111">Atributos</span><span class="sxs-lookup"><span data-stu-id="b7a2e-111">Attributes</span></span>  
  
|<span data-ttu-id="b7a2e-112">Elemento</span><span class="sxs-lookup"><span data-stu-id="b7a2e-112">Element</span></span>|<span data-ttu-id="b7a2e-113">Descrição</span><span class="sxs-lookup"><span data-stu-id="b7a2e-113">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="b7a2e-114">name</span><span class="sxs-lookup"><span data-stu-id="b7a2e-114">name</span></span>|<span data-ttu-id="b7a2e-115">Uma cadeia de caracteres que contém o nome exclusivo deste elemento de configuração.</span><span class="sxs-lookup"><span data-stu-id="b7a2e-115">A string that contains the unique name of this configuration element.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="b7a2e-116">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="b7a2e-116">Child Elements</span></span>  
  
|<span data-ttu-id="b7a2e-117">Elemento</span><span class="sxs-lookup"><span data-stu-id="b7a2e-117">Element</span></span>|<span data-ttu-id="b7a2e-118">Descrição</span><span class="sxs-lookup"><span data-stu-id="b7a2e-118">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="b7a2e-119">\<Filtros ></span><span class="sxs-lookup"><span data-stu-id="b7a2e-119">\<filters></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/filters-of-routing.md)|<span data-ttu-id="b7a2e-120">Mapeamentos entre os filtros de roteamento e os pontos de extremidade de destino para enviar mensagens para quando o filtro corresponde.</span><span class="sxs-lookup"><span data-stu-id="b7a2e-120">Mappings between the routing filters and the target endpoints to send messages to when the filter matches.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="b7a2e-121">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="b7a2e-121">Parent Elements</span></span>  
  
|<span data-ttu-id="b7a2e-122">Elemento</span><span class="sxs-lookup"><span data-stu-id="b7a2e-122">Element</span></span>|<span data-ttu-id="b7a2e-123">Descrição</span><span class="sxs-lookup"><span data-stu-id="b7a2e-123">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="b7a2e-124">\<roteamento ></span><span class="sxs-lookup"><span data-stu-id="b7a2e-124">\<routing></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/routing.md)|<span data-ttu-id="b7a2e-125">Uma seção de configuração que contém tabelas de roteamento.</span><span class="sxs-lookup"><span data-stu-id="b7a2e-125">A configuration section that contains routing tables.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="b7a2e-126">Consulte também</span><span class="sxs-lookup"><span data-stu-id="b7a2e-126">See Also</span></span>  
 <xref:System.ServiceModel.Routing.Configuration.RoutingSection?displayProperty=nameWithType>    
