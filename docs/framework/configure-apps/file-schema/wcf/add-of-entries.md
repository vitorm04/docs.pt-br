---
title: '&lt;adicionar&gt; &lt;entradas&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 3af4805b-dc72-4f68-b168-da4fba8c6170
caps.latest.revision: "3"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: d62236c604cd91c2dfe4b92cfaac4004fc18d439
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="ltaddgt-of-ltentriesgt"></a><span data-ttu-id="7fa56-102">&lt;adicionar&gt; &lt;entradas&gt;</span><span class="sxs-lookup"><span data-stu-id="7fa56-102">&lt;add&gt; of &lt;entries&gt;</span></span>
<span data-ttu-id="7fa56-103">Representa uma entrada de roteamento que mapeia um filtro para um ponto de extremidade do cliente que foi definido anteriormente.</span><span class="sxs-lookup"><span data-stu-id="7fa56-103">Represents a routing entry that maps a filter to a client endpoint that was previously defined.</span></span> <span data-ttu-id="7fa56-104">As mensagens que correspondem a este filtro serão enviadas para este destino.</span><span class="sxs-lookup"><span data-stu-id="7fa56-104">Messages matching this filter will be sent to this destination.</span></span>  
  
 <span data-ttu-id="7fa56-105">\<System. ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="7fa56-105">\<system.serviceModel></span></span>  
<span data-ttu-id="7fa56-106">\<roteamento ></span><span class="sxs-lookup"><span data-stu-id="7fa56-106">\<routing></span></span>  
<span data-ttu-id="7fa56-107">\<routingTables ></span><span class="sxs-lookup"><span data-stu-id="7fa56-107">\<routingTables></span></span>  
<span data-ttu-id="7fa56-108">\<Tabela ></span><span class="sxs-lookup"><span data-stu-id="7fa56-108">\<table></span></span>  
<span data-ttu-id="7fa56-109">\<entradas ></span><span class="sxs-lookup"><span data-stu-id="7fa56-109">\<entries></span></span>  
<span data-ttu-id="7fa56-110">\<add></span><span class="sxs-lookup"><span data-stu-id="7fa56-110">\<add></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7fa56-111">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="7fa56-111">Syntax</span></span>  
  
```xml
   <routing>      <filterTables>        <filterTable name="String">          <entries>            <add backupList="String"                 endpointName="String"                  filterName="String"                  priority="Integer" />          </entries>        </table>      </routingTables></routing>  
```  
  
```csharp  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="7fa56-112">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="7fa56-112">Attributes and Elements</span></span>  
 <span data-ttu-id="7fa56-113">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="7fa56-113">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="7fa56-114">Atributos</span><span class="sxs-lookup"><span data-stu-id="7fa56-114">Attributes</span></span>  
  
|<span data-ttu-id="7fa56-115">Atributo</span><span class="sxs-lookup"><span data-stu-id="7fa56-115">Attribute</span></span>|<span data-ttu-id="7fa56-116">Descrição</span><span class="sxs-lookup"><span data-stu-id="7fa56-116">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="7fa56-117">backupList</span><span class="sxs-lookup"><span data-stu-id="7fa56-117">backupList</span></span>|<span data-ttu-id="7fa56-118">Uma cadeia de caracteres que especifica uma referência a uma lista de pontos de extremidade de backup.</span><span class="sxs-lookup"><span data-stu-id="7fa56-118">A string that specifies a reference to a backup list of endpoints.</span></span>|  
|<span data-ttu-id="7fa56-119">ponto de extremidade</span><span class="sxs-lookup"><span data-stu-id="7fa56-119">endpoint</span></span>|<span data-ttu-id="7fa56-120">Uma cadeia de caracteres que especifica uma referência a um ponto de extremidade do cliente que receberá as mensagens que correspondem ao filtro especificado pelo `filterName` atributo.</span><span class="sxs-lookup"><span data-stu-id="7fa56-120">A string that specifies a reference to a client endpoint that will receive messages that match the filter specified by the `filterName` attribute.</span></span>|  
|<span data-ttu-id="7fa56-121">filterName</span><span class="sxs-lookup"><span data-stu-id="7fa56-121">filterName</span></span>|<span data-ttu-id="7fa56-122">Uma cadeia de caracteres que especifica uma referência a um elemento de filtro.</span><span class="sxs-lookup"><span data-stu-id="7fa56-122">A string that specifies a reference to a filter element.</span></span>|  
|<span data-ttu-id="7fa56-123">priority</span><span class="sxs-lookup"><span data-stu-id="7fa56-123">priority</span></span>|<span data-ttu-id="7fa56-124">Um inteiro que especifica a prioridade desta entrada.</span><span class="sxs-lookup"><span data-stu-id="7fa56-124">An integer that specifies the priority of this entry.</span></span><br /><br /> <span data-ttu-id="7fa56-125">As entradas na tabela de roteamento com base na prioridade, com 0, sendo a prioridade mais baixa serão avaliadas.</span><span class="sxs-lookup"><span data-stu-id="7fa56-125">Entries in the routing table will be evaluated based on priority, with 0 being the lowest priority.</span></span> <span data-ttu-id="7fa56-126">Todas as entradas para uma prioridade específica são avaliadas simultaneamente, se nenhuma correspondência de entrada foi encontrada para a prioridade atual, o próximo nível de prioridade será avaliado.</span><span class="sxs-lookup"><span data-stu-id="7fa56-126">All entries for a specific priority are evaluated simultaneously, if no matching entry is found for the current priority, the next priority level will be evaluated.</span></span><br /><br /> <span data-ttu-id="7fa56-127">Esse valor é opcional.</span><span class="sxs-lookup"><span data-stu-id="7fa56-127">This value is optional.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="7fa56-128">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="7fa56-128">Child Elements</span></span>  
 <span data-ttu-id="7fa56-129">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="7fa56-129">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="7fa56-130">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="7fa56-130">Parent Elements</span></span>  
  
|<span data-ttu-id="7fa56-131">Elemento</span><span class="sxs-lookup"><span data-stu-id="7fa56-131">Element</span></span>|<span data-ttu-id="7fa56-132">Descrição</span><span class="sxs-lookup"><span data-stu-id="7fa56-132">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="7fa56-133">\<roteamento ></span><span class="sxs-lookup"><span data-stu-id="7fa56-133">\<routing></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/routing.md)|<span data-ttu-id="7fa56-134">Uma seção de configuração que contém as entradas de mapeamento de roteamento.</span><span class="sxs-lookup"><span data-stu-id="7fa56-134">A configuration section that contains routing mapping entries.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="7fa56-135">Consulte também</span><span class="sxs-lookup"><span data-stu-id="7fa56-135">See Also</span></span>  
 <xref:System.ServiceModel.Routing.Configuration.RoutingSection?displayProperty=nameWithType>      
 <xref:System.ServiceModel.Routing.Configuration.FilterTableEntryElement?displayProperty=nameWithType> 
