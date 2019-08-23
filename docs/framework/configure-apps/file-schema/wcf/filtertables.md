---
title: <filterTables>
ms.date: 03/30/2017
ms.assetid: 41f1ac35-f559-473a-b2c3-8cc83a6a3831
ms.openlocfilehash: b0a344aa69085d50087eefc746236bc8ceacadaa
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69918849"
---
# <a name="filtertables"></a><span data-ttu-id="12ce2-101">\<> filterTables</span><span class="sxs-lookup"><span data-stu-id="12ce2-101">\<filterTables></span></span>
<span data-ttu-id="12ce2-102">Representa uma seção de configuração para definir tabelas de roteamento que contêm mapeamentos entre os filtros de roteamento e os pontos de extremidade de destino para enviar mensagens quando o filtro for correspondente.</span><span class="sxs-lookup"><span data-stu-id="12ce2-102">Represents a configuration section for defining routing tables that contain mappings between the routing filters and the target endpoints to send messages to when the filter matches.</span></span>  
  
 <span data-ttu-id="12ce2-103">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="12ce2-103">\<system.serviceModel></span></span>  
<span data-ttu-id="12ce2-104">\<> de roteamento</span><span class="sxs-lookup"><span data-stu-id="12ce2-104">\<routing></span></span>  
<span data-ttu-id="12ce2-105">\<routingTables></span><span class="sxs-lookup"><span data-stu-id="12ce2-105">\<routingTables></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="12ce2-106">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="12ce2-106">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="12ce2-107">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="12ce2-107">Attributes and Elements</span></span>  
 <span data-ttu-id="12ce2-108">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="12ce2-108">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="12ce2-109">Atributos</span><span class="sxs-lookup"><span data-stu-id="12ce2-109">Attributes</span></span>  
 <span data-ttu-id="12ce2-110">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="12ce2-110">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="12ce2-111">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="12ce2-111">Child Elements</span></span>  
  
|<span data-ttu-id="12ce2-112">Elemento</span><span class="sxs-lookup"><span data-stu-id="12ce2-112">Element</span></span>|<span data-ttu-id="12ce2-113">Descrição</span><span class="sxs-lookup"><span data-stu-id="12ce2-113">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="12ce2-114">\<filters></span><span class="sxs-lookup"><span data-stu-id="12ce2-114">\<filters></span></span>](filters-of-routing.md)|<span data-ttu-id="12ce2-115">Uma tabela de roteamento que contém mapeamentos entre os filtros de roteamento e os pontos de extremidade de destino para envio de mensagens quando o filtro é correspondente.</span><span class="sxs-lookup"><span data-stu-id="12ce2-115">A routing table that contain mappings between the routing filters and the target endpoints to send messages to when the filter matches.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="12ce2-116">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="12ce2-116">Parent Elements</span></span>  
  
|<span data-ttu-id="12ce2-117">Elemento</span><span class="sxs-lookup"><span data-stu-id="12ce2-117">Element</span></span>|<span data-ttu-id="12ce2-118">Descrição</span><span class="sxs-lookup"><span data-stu-id="12ce2-118">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="12ce2-119">\<routing></span><span class="sxs-lookup"><span data-stu-id="12ce2-119">\<routing></span></span>](routing.md)|<span data-ttu-id="12ce2-120">Uma seção de configuração que contém filtros de roteamento e tabelas de roteamento.</span><span class="sxs-lookup"><span data-stu-id="12ce2-120">A configuration section that contains routing filters and routing tables.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="12ce2-121">Consulte também</span><span class="sxs-lookup"><span data-stu-id="12ce2-121">See also</span></span>

- <xref:System.ServiceModel.Routing.Configuration.RoutingSection?displayProperty=nameWithType>
- <xref:System.ServiceModel.Routing.Configuration.FilterTableCollection?displayProperty=nameWithType>
