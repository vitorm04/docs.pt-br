---
title: '&lt;adicionar&gt; &lt;entradas&gt;'
ms.date: 03/30/2017
ms.assetid: 3af4805b-dc72-4f68-b168-da4fba8c6170
ms.openlocfilehash: a6960c16c84c13d905f0993ee3cfc1cf67df07fc
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/03/2018
---
# <a name="ltaddgt-of-ltentriesgt"></a><span data-ttu-id="7e299-102">&lt;adicionar&gt; &lt;entradas&gt;</span><span class="sxs-lookup"><span data-stu-id="7e299-102">&lt;add&gt; of &lt;entries&gt;</span></span>
<span data-ttu-id="7e299-103">Representa uma entrada de roteamento que mapeia um filtro para um ponto de extremidade do cliente que foi definido anteriormente.</span><span class="sxs-lookup"><span data-stu-id="7e299-103">Represents a routing entry that maps a filter to a client endpoint that was previously defined.</span></span> <span data-ttu-id="7e299-104">As mensagens que correspondem a este filtro serão enviadas para este destino.</span><span class="sxs-lookup"><span data-stu-id="7e299-104">Messages matching this filter will be sent to this destination.</span></span>  
  
 <span data-ttu-id="7e299-105">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="7e299-105">\<system.serviceModel></span></span>  
<span data-ttu-id="7e299-106">\<roteamento ></span><span class="sxs-lookup"><span data-stu-id="7e299-106">\<routing></span></span>  
<span data-ttu-id="7e299-107">\<routingTables ></span><span class="sxs-lookup"><span data-stu-id="7e299-107">\<routingTables></span></span>  
<span data-ttu-id="7e299-108">\<Tabela ></span><span class="sxs-lookup"><span data-stu-id="7e299-108">\<table></span></span>  
<span data-ttu-id="7e299-109">\<entradas ></span><span class="sxs-lookup"><span data-stu-id="7e299-109">\<entries></span></span>  
<span data-ttu-id="7e299-110">\<add></span><span class="sxs-lookup"><span data-stu-id="7e299-110">\<add></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7e299-111">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="7e299-111">Syntax</span></span>  
  
```xml
   <routing>      <filterTables>        <filterTable name="String">          <entries>            <add backupList="String"                 endpointName="String"                  filterName="String"                  priority="Integer" />          </entries>        </table>      </routingTables></routing>  
```  
  
```csharp  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="7e299-112">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="7e299-112">Attributes and Elements</span></span>  
 <span data-ttu-id="7e299-113">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="7e299-113">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="7e299-114">Atributos</span><span class="sxs-lookup"><span data-stu-id="7e299-114">Attributes</span></span>  
  
|<span data-ttu-id="7e299-115">Atributo</span><span class="sxs-lookup"><span data-stu-id="7e299-115">Attribute</span></span>|<span data-ttu-id="7e299-116">Descrição</span><span class="sxs-lookup"><span data-stu-id="7e299-116">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="7e299-117">backupList</span><span class="sxs-lookup"><span data-stu-id="7e299-117">backupList</span></span>|<span data-ttu-id="7e299-118">Uma cadeia de caracteres que especifica uma referência a uma lista de pontos de extremidade de backup.</span><span class="sxs-lookup"><span data-stu-id="7e299-118">A string that specifies a reference to a backup list of endpoints.</span></span>|  
|<span data-ttu-id="7e299-119">ponto de extremidade</span><span class="sxs-lookup"><span data-stu-id="7e299-119">endpoint</span></span>|<span data-ttu-id="7e299-120">Uma cadeia de caracteres que especifica uma referência a um ponto de extremidade do cliente que receberá as mensagens que correspondem ao filtro especificado pelo `filterName` atributo.</span><span class="sxs-lookup"><span data-stu-id="7e299-120">A string that specifies a reference to a client endpoint that will receive messages that match the filter specified by the `filterName` attribute.</span></span>|  
|<span data-ttu-id="7e299-121">filterName</span><span class="sxs-lookup"><span data-stu-id="7e299-121">filterName</span></span>|<span data-ttu-id="7e299-122">Uma cadeia de caracteres que especifica uma referência a um elemento de filtro.</span><span class="sxs-lookup"><span data-stu-id="7e299-122">A string that specifies a reference to a filter element.</span></span>|  
|<span data-ttu-id="7e299-123">priority</span><span class="sxs-lookup"><span data-stu-id="7e299-123">priority</span></span>|<span data-ttu-id="7e299-124">Um inteiro que especifica a prioridade desta entrada.</span><span class="sxs-lookup"><span data-stu-id="7e299-124">An integer that specifies the priority of this entry.</span></span><br /><br /> <span data-ttu-id="7e299-125">As entradas na tabela de roteamento com base na prioridade, com 0, sendo a prioridade mais baixa serão avaliadas.</span><span class="sxs-lookup"><span data-stu-id="7e299-125">Entries in the routing table will be evaluated based on priority, with 0 being the lowest priority.</span></span> <span data-ttu-id="7e299-126">Todas as entradas para uma prioridade específica são avaliadas simultaneamente, se nenhuma correspondência de entrada foi encontrada para a prioridade atual, o próximo nível de prioridade será avaliado.</span><span class="sxs-lookup"><span data-stu-id="7e299-126">All entries for a specific priority are evaluated simultaneously, if no matching entry is found for the current priority, the next priority level will be evaluated.</span></span><br /><br /> <span data-ttu-id="7e299-127">Esse valor é opcional.</span><span class="sxs-lookup"><span data-stu-id="7e299-127">This value is optional.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="7e299-128">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="7e299-128">Child Elements</span></span>  
 <span data-ttu-id="7e299-129">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="7e299-129">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="7e299-130">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="7e299-130">Parent Elements</span></span>  
  
|<span data-ttu-id="7e299-131">Elemento</span><span class="sxs-lookup"><span data-stu-id="7e299-131">Element</span></span>|<span data-ttu-id="7e299-132">Descrição</span><span class="sxs-lookup"><span data-stu-id="7e299-132">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="7e299-133">\<roteamento ></span><span class="sxs-lookup"><span data-stu-id="7e299-133">\<routing></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/routing.md)|<span data-ttu-id="7e299-134">Uma seção de configuração que contém as entradas de mapeamento de roteamento.</span><span class="sxs-lookup"><span data-stu-id="7e299-134">A configuration section that contains routing mapping entries.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="7e299-135">Consulte também</span><span class="sxs-lookup"><span data-stu-id="7e299-135">See Also</span></span>  
 <xref:System.ServiceModel.Routing.Configuration.RoutingSection?displayProperty=nameWithType>      
 <xref:System.ServiceModel.Routing.Configuration.FilterTableEntryElement?displayProperty=nameWithType> 
