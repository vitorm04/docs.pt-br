---
title: <filterTables>
ms.date: 03/30/2017
ms.assetid: 41f1ac35-f559-473a-b2c3-8cc83a6a3831
ms.openlocfilehash: c49c7cf3a196595556c2bf1b4ed4365bfe1e4cbf
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61704239"
---
# <a name="filtertables"></a><span data-ttu-id="139f0-101">\<filterTables></span><span class="sxs-lookup"><span data-stu-id="139f0-101">\<filterTables></span></span>
<span data-ttu-id="139f0-102">Representa uma seção de configuração para definir as tabelas de roteamento que contêm mapeamentos entre os filtros de roteamento e os pontos de extremidade para enviar mensagens quando o filtro corresponde ao destino.</span><span class="sxs-lookup"><span data-stu-id="139f0-102">Represents a configuration section for defining routing tables that contain mappings between the routing filters and the target endpoints to send messages to when the filter matches.</span></span>  
  
 <span data-ttu-id="139f0-103">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="139f0-103">\<system.serviceModel></span></span>  
<span data-ttu-id="139f0-104">\<routing></span><span class="sxs-lookup"><span data-stu-id="139f0-104">\<routing></span></span>  
<span data-ttu-id="139f0-105">\<routingTables></span><span class="sxs-lookup"><span data-stu-id="139f0-105">\<routingTables></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="139f0-106">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="139f0-106">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="139f0-107">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="139f0-107">Attributes and Elements</span></span>  
 <span data-ttu-id="139f0-108">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="139f0-108">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="139f0-109">Atributos</span><span class="sxs-lookup"><span data-stu-id="139f0-109">Attributes</span></span>  
 <span data-ttu-id="139f0-110">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="139f0-110">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="139f0-111">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="139f0-111">Child Elements</span></span>  
  
|<span data-ttu-id="139f0-112">Elemento</span><span class="sxs-lookup"><span data-stu-id="139f0-112">Element</span></span>|<span data-ttu-id="139f0-113">Descrição</span><span class="sxs-lookup"><span data-stu-id="139f0-113">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="139f0-114">\<filters></span><span class="sxs-lookup"><span data-stu-id="139f0-114">\<filters></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/filters-of-routing.md)|<span data-ttu-id="139f0-115">Uma tabela de roteamento que contêm mapeamentos entre os filtros de roteamento e os pontos de extremidade para enviar mensagens para quando o filtro corresponde ao destino.</span><span class="sxs-lookup"><span data-stu-id="139f0-115">A routing table that contain mappings between the routing filters and the target endpoints to send messages to when the filter matches.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="139f0-116">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="139f0-116">Parent Elements</span></span>  
  
|<span data-ttu-id="139f0-117">Elemento</span><span class="sxs-lookup"><span data-stu-id="139f0-117">Element</span></span>|<span data-ttu-id="139f0-118">Descrição</span><span class="sxs-lookup"><span data-stu-id="139f0-118">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="139f0-119">\<routing></span><span class="sxs-lookup"><span data-stu-id="139f0-119">\<routing></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/routing.md)|<span data-ttu-id="139f0-120">Uma seção de configuração que contém tabelas de roteamento e os filtros de roteamento.</span><span class="sxs-lookup"><span data-stu-id="139f0-120">A configuration section that contains routing filters and routing tables.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="139f0-121">Consulte também</span><span class="sxs-lookup"><span data-stu-id="139f0-121">See also</span></span>

- <xref:System.ServiceModel.Routing.Configuration.RoutingSection?displayProperty=nameWithType>
- <xref:System.ServiceModel.Routing.Configuration.FilterTableCollection?displayProperty=nameWithType>
