---
title: '&lt;filterTables&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 41f1ac35-f559-473a-b2c3-8cc83a6a3831
caps.latest.revision: "5"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 75e06b0258f2e4f65d441c25b5081cf7a6627518
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="ltfiltertablesgt"></a><span data-ttu-id="c3b50-102">&lt;filterTables&gt;</span><span class="sxs-lookup"><span data-stu-id="c3b50-102">&lt;filterTables&gt;</span></span>
<span data-ttu-id="c3b50-103">Representa uma seção de configuração para definir as tabelas de roteamento que contêm mapeamentos entre os filtros de roteamento e os pontos de extremidade de destino para enviar mensagens quando correspondências de filtro.</span><span class="sxs-lookup"><span data-stu-id="c3b50-103">Represents a configuration section for defining routing tables that contain mappings between the routing filters and the target endpoints to send messages to when the filter matches.</span></span>  
  
 <span data-ttu-id="c3b50-104">\<System. ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="c3b50-104">\<system.serviceModel></span></span>  
<span data-ttu-id="c3b50-105">\<roteamento ></span><span class="sxs-lookup"><span data-stu-id="c3b50-105">\<routing></span></span>  
<span data-ttu-id="c3b50-106">\<routingTables ></span><span class="sxs-lookup"><span data-stu-id="c3b50-106">\<routingTables></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c3b50-107">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="c3b50-107">Syntax</span></span>  
  
```xml
   <routing>      <filterTables>        <filterTable name="String">          <entries>            <add backupList="String"                 endpointName="String"                  filterName="String"                  priority="Integer" />          </entries>        </table>      </routingTables></routing>  
```

## <a name="attributes-and-elements"></a><span data-ttu-id="c3b50-108">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="c3b50-108">Attributes and Elements</span></span>  
 <span data-ttu-id="c3b50-109">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="c3b50-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="c3b50-110">Atributos</span><span class="sxs-lookup"><span data-stu-id="c3b50-110">Attributes</span></span>  
 <span data-ttu-id="c3b50-111">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="c3b50-111">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="c3b50-112">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="c3b50-112">Child Elements</span></span>  
  
|<span data-ttu-id="c3b50-113">Elemento</span><span class="sxs-lookup"><span data-stu-id="c3b50-113">Element</span></span>|<span data-ttu-id="c3b50-114">Descrição</span><span class="sxs-lookup"><span data-stu-id="c3b50-114">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="c3b50-115">\<Filtros ></span><span class="sxs-lookup"><span data-stu-id="c3b50-115">\<filters></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/filters-of-routing.md)|<span data-ttu-id="c3b50-116">Uma tabela de roteamento que contêm mapeamentos entre os filtros de roteamento e os pontos de extremidade de destino para enviar mensagens para quando o filtro corresponde.</span><span class="sxs-lookup"><span data-stu-id="c3b50-116">A routing table that contain mappings between the routing filters and the target endpoints to send messages to when the filter matches.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="c3b50-117">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="c3b50-117">Parent Elements</span></span>  
  
|<span data-ttu-id="c3b50-118">Elemento</span><span class="sxs-lookup"><span data-stu-id="c3b50-118">Element</span></span>|<span data-ttu-id="c3b50-119">Descrição</span><span class="sxs-lookup"><span data-stu-id="c3b50-119">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="c3b50-120">\<roteamento ></span><span class="sxs-lookup"><span data-stu-id="c3b50-120">\<routing></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/routing.md)|<span data-ttu-id="c3b50-121">Uma seção de configuração que contém tabelas de roteamento e os filtros de roteamento.</span><span class="sxs-lookup"><span data-stu-id="c3b50-121">A configuration section that contains routing filters and routing tables.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="c3b50-122">Consulte também</span><span class="sxs-lookup"><span data-stu-id="c3b50-122">See Also</span></span>  
 <xref:System.ServiceModel.Routing.Configuration.RoutingSection?displayProperty=nameWithType>       
 <xref:System.ServiceModel.Routing.Configuration.FilterTableCollection?displayProperty=nameWithType>    
