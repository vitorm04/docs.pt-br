---
title: '&lt;filterTables&gt;'
ms.date: 03/30/2017
ms.assetid: 41f1ac35-f559-473a-b2c3-8cc83a6a3831
ms.openlocfilehash: 966556a1a8bde72e33640dcc6fd37ae7a044ceef
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/03/2018
---
# <a name="ltfiltertablesgt"></a><span data-ttu-id="54676-102">&lt;filterTables&gt;</span><span class="sxs-lookup"><span data-stu-id="54676-102">&lt;filterTables&gt;</span></span>
<span data-ttu-id="54676-103">Representa uma seção de configuração para definir as tabelas de roteamento que contêm mapeamentos entre os filtros de roteamento e os pontos de extremidade de destino para enviar mensagens quando correspondências de filtro.</span><span class="sxs-lookup"><span data-stu-id="54676-103">Represents a configuration section for defining routing tables that contain mappings between the routing filters and the target endpoints to send messages to when the filter matches.</span></span>  
  
 <span data-ttu-id="54676-104">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="54676-104">\<system.serviceModel></span></span>  
<span data-ttu-id="54676-105">\<roteamento ></span><span class="sxs-lookup"><span data-stu-id="54676-105">\<routing></span></span>  
<span data-ttu-id="54676-106">\<routingTables ></span><span class="sxs-lookup"><span data-stu-id="54676-106">\<routingTables></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="54676-107">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="54676-107">Syntax</span></span>  
  
```xml
   <routing>      <filterTables>        <filterTable name="String">          <entries>            <add backupList="String"                 endpointName="String"                  filterName="String"                  priority="Integer" />          </entries>        </table>      </routingTables></routing>  
```

## <a name="attributes-and-elements"></a><span data-ttu-id="54676-108">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="54676-108">Attributes and Elements</span></span>  
 <span data-ttu-id="54676-109">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="54676-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="54676-110">Atributos</span><span class="sxs-lookup"><span data-stu-id="54676-110">Attributes</span></span>  
 <span data-ttu-id="54676-111">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="54676-111">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="54676-112">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="54676-112">Child Elements</span></span>  
  
|<span data-ttu-id="54676-113">Elemento</span><span class="sxs-lookup"><span data-stu-id="54676-113">Element</span></span>|<span data-ttu-id="54676-114">Descrição</span><span class="sxs-lookup"><span data-stu-id="54676-114">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="54676-115">\<Filtros ></span><span class="sxs-lookup"><span data-stu-id="54676-115">\<filters></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/filters-of-routing.md)|<span data-ttu-id="54676-116">Uma tabela de roteamento que contêm mapeamentos entre os filtros de roteamento e os pontos de extremidade de destino para enviar mensagens para quando o filtro corresponde.</span><span class="sxs-lookup"><span data-stu-id="54676-116">A routing table that contain mappings between the routing filters and the target endpoints to send messages to when the filter matches.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="54676-117">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="54676-117">Parent Elements</span></span>  
  
|<span data-ttu-id="54676-118">Elemento</span><span class="sxs-lookup"><span data-stu-id="54676-118">Element</span></span>|<span data-ttu-id="54676-119">Descrição</span><span class="sxs-lookup"><span data-stu-id="54676-119">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="54676-120">\<roteamento ></span><span class="sxs-lookup"><span data-stu-id="54676-120">\<routing></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/routing.md)|<span data-ttu-id="54676-121">Uma seção de configuração que contém tabelas de roteamento e os filtros de roteamento.</span><span class="sxs-lookup"><span data-stu-id="54676-121">A configuration section that contains routing filters and routing tables.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="54676-122">Consulte também</span><span class="sxs-lookup"><span data-stu-id="54676-122">See Also</span></span>  
 <xref:System.ServiceModel.Routing.Configuration.RoutingSection?displayProperty=nameWithType>       
 <xref:System.ServiceModel.Routing.Configuration.FilterTableCollection?displayProperty=nameWithType>    
