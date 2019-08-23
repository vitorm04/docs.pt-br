---
title: <add> de <entries>
ms.date: 03/30/2017
ms.assetid: 3af4805b-dc72-4f68-b168-da4fba8c6170
ms.openlocfilehash: 690fd07159e07b7e037f7330b31fdcba423e80f9
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69920123"
---
# <a name="add-of-entries"></a><span data-ttu-id="5e4e5-102">\<Adicionar > de \<entradas ></span><span class="sxs-lookup"><span data-stu-id="5e4e5-102">\<add> of \<entries></span></span>
<span data-ttu-id="5e4e5-103">Representa uma entrada de roteamento que mapeia um filtro para um ponto de extremidade do cliente que foi definido anteriormente.</span><span class="sxs-lookup"><span data-stu-id="5e4e5-103">Represents a routing entry that maps a filter to a client endpoint that was previously defined.</span></span> <span data-ttu-id="5e4e5-104">As mensagens correspondentes a este filtro serão enviadas para esse destino.</span><span class="sxs-lookup"><span data-stu-id="5e4e5-104">Messages matching this filter will be sent to this destination.</span></span>  
  
 <span data-ttu-id="5e4e5-105">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="5e4e5-105">\<system.serviceModel></span></span>  
<span data-ttu-id="5e4e5-106">\<> de roteamento</span><span class="sxs-lookup"><span data-stu-id="5e4e5-106">\<routing></span></span>  
<span data-ttu-id="5e4e5-107">\<> filterTables</span><span class="sxs-lookup"><span data-stu-id="5e4e5-107">\<filterTables></span></span>  
<span data-ttu-id="5e4e5-108">\<filterTable></span><span class="sxs-lookup"><span data-stu-id="5e4e5-108">\<filterTable></span></span>  
<span data-ttu-id="5e4e5-109">\<entradas ></span><span class="sxs-lookup"><span data-stu-id="5e4e5-109">\<entries></span></span>  
<span data-ttu-id="5e4e5-110">\<add></span><span class="sxs-lookup"><span data-stu-id="5e4e5-110">\<add></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5e4e5-111">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="5e4e5-111">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="5e4e5-112">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="5e4e5-112">Attributes and Elements</span></span>  
 <span data-ttu-id="5e4e5-113">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="5e4e5-113">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="5e4e5-114">Atributos</span><span class="sxs-lookup"><span data-stu-id="5e4e5-114">Attributes</span></span>  
  
|<span data-ttu-id="5e4e5-115">Atributo</span><span class="sxs-lookup"><span data-stu-id="5e4e5-115">Attribute</span></span>|<span data-ttu-id="5e4e5-116">Descrição</span><span class="sxs-lookup"><span data-stu-id="5e4e5-116">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="5e4e5-117">backupList</span><span class="sxs-lookup"><span data-stu-id="5e4e5-117">backupList</span></span>|<span data-ttu-id="5e4e5-118">Uma cadeia de caracteres que especifica uma referência a uma lista de pontos de extremidade de backup.</span><span class="sxs-lookup"><span data-stu-id="5e4e5-118">A string that specifies a reference to a backup list of endpoints.</span></span>|  
|<span data-ttu-id="5e4e5-119">ponto de extremidade</span><span class="sxs-lookup"><span data-stu-id="5e4e5-119">endpoint</span></span>|<span data-ttu-id="5e4e5-120">Uma cadeia de caracteres que especifica uma referência a um ponto de extremidade do cliente que receberá mensagens que correspondem `filterName` ao filtro especificado pelo atributo.</span><span class="sxs-lookup"><span data-stu-id="5e4e5-120">A string that specifies a reference to a client endpoint that will receive messages that match the filter specified by the `filterName` attribute.</span></span>|  
|<span data-ttu-id="5e4e5-121">filterName</span><span class="sxs-lookup"><span data-stu-id="5e4e5-121">filterName</span></span>|<span data-ttu-id="5e4e5-122">Uma cadeia de caracteres que especifica uma referência a um elemento de filtro.</span><span class="sxs-lookup"><span data-stu-id="5e4e5-122">A string that specifies a reference to a filter element.</span></span>|  
|<span data-ttu-id="5e4e5-123">priority</span><span class="sxs-lookup"><span data-stu-id="5e4e5-123">priority</span></span>|<span data-ttu-id="5e4e5-124">Um inteiro que especifica a prioridade desta entrada.</span><span class="sxs-lookup"><span data-stu-id="5e4e5-124">An integer that specifies the priority of this entry.</span></span><br /><br /> <span data-ttu-id="5e4e5-125">As entradas na tabela de roteamento serão avaliadas com base na prioridade, sendo que 0 é a prioridade mais baixa.</span><span class="sxs-lookup"><span data-stu-id="5e4e5-125">Entries in the routing table will be evaluated based on priority, with 0 being the lowest priority.</span></span> <span data-ttu-id="5e4e5-126">Todas as entradas de uma prioridade específica são avaliadas simultaneamente, se nenhuma entrada correspondente for encontrada para a prioridade atual, o próximo nível de prioridade será avaliado.</span><span class="sxs-lookup"><span data-stu-id="5e4e5-126">All entries for a specific priority are evaluated simultaneously, if no matching entry is found for the current priority, the next priority level will be evaluated.</span></span><br /><br /> <span data-ttu-id="5e4e5-127">Esse valor é opcional.</span><span class="sxs-lookup"><span data-stu-id="5e4e5-127">This value is optional.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="5e4e5-128">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="5e4e5-128">Child Elements</span></span>  
 <span data-ttu-id="5e4e5-129">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="5e4e5-129">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="5e4e5-130">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="5e4e5-130">Parent Elements</span></span>  
  
|<span data-ttu-id="5e4e5-131">Elemento</span><span class="sxs-lookup"><span data-stu-id="5e4e5-131">Element</span></span>|<span data-ttu-id="5e4e5-132">Descrição</span><span class="sxs-lookup"><span data-stu-id="5e4e5-132">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="5e4e5-133">\<routing></span><span class="sxs-lookup"><span data-stu-id="5e4e5-133">\<routing></span></span>](routing.md)|<span data-ttu-id="5e4e5-134">Uma seção de configuração que contém entradas de mapeamento de roteamento.</span><span class="sxs-lookup"><span data-stu-id="5e4e5-134">A configuration section that contains routing mapping entries.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="5e4e5-135">Consulte também</span><span class="sxs-lookup"><span data-stu-id="5e4e5-135">See also</span></span>

- <xref:System.ServiceModel.Routing.Configuration.RoutingSection?displayProperty=nameWithType>
- <xref:System.ServiceModel.Routing.Configuration.FilterTableEntryElement?displayProperty=nameWithType>
