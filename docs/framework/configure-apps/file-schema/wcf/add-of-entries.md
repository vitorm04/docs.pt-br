---
title: <add> De <entries>
ms.date: 03/30/2017
ms.assetid: 3af4805b-dc72-4f68-b168-da4fba8c6170
ms.openlocfilehash: 7267b8719987ecd25bcca78a7897a0d4172a42ef
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/30/2019
ms.locfileid: "55264564"
---
# <a name="add-of-entries"></a><span data-ttu-id="b3a06-102">\<Adicionar > de \<entradas ></span><span class="sxs-lookup"><span data-stu-id="b3a06-102">\<add> of \<entries></span></span>
<span data-ttu-id="b3a06-103">Representa uma entrada de roteamento que mapeia um filtro para um ponto de extremidade do cliente que foi definido anteriormente.</span><span class="sxs-lookup"><span data-stu-id="b3a06-103">Represents a routing entry that maps a filter to a client endpoint that was previously defined.</span></span> <span data-ttu-id="b3a06-104">As mensagens que correspondem a esse filtro serão enviadas para este destino.</span><span class="sxs-lookup"><span data-stu-id="b3a06-104">Messages matching this filter will be sent to this destination.</span></span>  
  
 <span data-ttu-id="b3a06-105">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="b3a06-105">\<system.serviceModel></span></span>  
<span data-ttu-id="b3a06-106">\<routing></span><span class="sxs-lookup"><span data-stu-id="b3a06-106">\<routing></span></span>  
<span data-ttu-id="b3a06-107">\<filterTables></span><span class="sxs-lookup"><span data-stu-id="b3a06-107">\<filterTables></span></span>  
<span data-ttu-id="b3a06-108">\<filterTable></span><span class="sxs-lookup"><span data-stu-id="b3a06-108">\<filterTable></span></span>  
<span data-ttu-id="b3a06-109">\<entries></span><span class="sxs-lookup"><span data-stu-id="b3a06-109">\<entries></span></span>  
<span data-ttu-id="b3a06-110">\<add></span><span class="sxs-lookup"><span data-stu-id="b3a06-110">\<add></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b3a06-111">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="b3a06-111">Syntax</span></span>  
  
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
  
```csharp  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="b3a06-112">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="b3a06-112">Attributes and Elements</span></span>  
 <span data-ttu-id="b3a06-113">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="b3a06-113">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="b3a06-114">Atributos</span><span class="sxs-lookup"><span data-stu-id="b3a06-114">Attributes</span></span>  
  
|<span data-ttu-id="b3a06-115">Atributo</span><span class="sxs-lookup"><span data-stu-id="b3a06-115">Attribute</span></span>|<span data-ttu-id="b3a06-116">Descrição</span><span class="sxs-lookup"><span data-stu-id="b3a06-116">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="b3a06-117">backupList</span><span class="sxs-lookup"><span data-stu-id="b3a06-117">backupList</span></span>|<span data-ttu-id="b3a06-118">Uma cadeia de caracteres que especifica uma referência a uma lista de pontos de extremidade de backup.</span><span class="sxs-lookup"><span data-stu-id="b3a06-118">A string that specifies a reference to a backup list of endpoints.</span></span>|  
|<span data-ttu-id="b3a06-119">ponto de extremidade</span><span class="sxs-lookup"><span data-stu-id="b3a06-119">endpoint</span></span>|<span data-ttu-id="b3a06-120">Uma cadeia de caracteres que especifica uma referência a um ponto de extremidade do cliente que receberá as mensagens que correspondem ao filtro especificado pelo `filterName` atributo.</span><span class="sxs-lookup"><span data-stu-id="b3a06-120">A string that specifies a reference to a client endpoint that will receive messages that match the filter specified by the `filterName` attribute.</span></span>|  
|<span data-ttu-id="b3a06-121">filterName</span><span class="sxs-lookup"><span data-stu-id="b3a06-121">filterName</span></span>|<span data-ttu-id="b3a06-122">Uma cadeia de caracteres que especifica uma referência a um elemento de filtro.</span><span class="sxs-lookup"><span data-stu-id="b3a06-122">A string that specifies a reference to a filter element.</span></span>|  
|<span data-ttu-id="b3a06-123">priority</span><span class="sxs-lookup"><span data-stu-id="b3a06-123">priority</span></span>|<span data-ttu-id="b3a06-124">Um inteiro que especifica a prioridade desta entrada.</span><span class="sxs-lookup"><span data-stu-id="b3a06-124">An integer that specifies the priority of this entry.</span></span><br /><br /> <span data-ttu-id="b3a06-125">As entradas na tabela de roteamento serão avaliadas com base na prioridade, com 0 sendo a prioridade mais baixa.</span><span class="sxs-lookup"><span data-stu-id="b3a06-125">Entries in the routing table will be evaluated based on priority, with 0 being the lowest priority.</span></span> <span data-ttu-id="b3a06-126">Todas as entradas para uma prioridade específica são avaliadas simultaneamente, se nenhuma correspondência de entrada for encontrada para a prioridade atual, o próximo nível de prioridade será avaliado.</span><span class="sxs-lookup"><span data-stu-id="b3a06-126">All entries for a specific priority are evaluated simultaneously, if no matching entry is found for the current priority, the next priority level will be evaluated.</span></span><br /><br /> <span data-ttu-id="b3a06-127">Esse valor é opcional.</span><span class="sxs-lookup"><span data-stu-id="b3a06-127">This value is optional.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="b3a06-128">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="b3a06-128">Child Elements</span></span>  
 <span data-ttu-id="b3a06-129">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="b3a06-129">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="b3a06-130">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="b3a06-130">Parent Elements</span></span>  
  
|<span data-ttu-id="b3a06-131">Elemento</span><span class="sxs-lookup"><span data-stu-id="b3a06-131">Element</span></span>|<span data-ttu-id="b3a06-132">Descrição</span><span class="sxs-lookup"><span data-stu-id="b3a06-132">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="b3a06-133">\<routing></span><span class="sxs-lookup"><span data-stu-id="b3a06-133">\<routing></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/routing.md)|<span data-ttu-id="b3a06-134">Uma seção de configuração que contém as entradas de mapeamento de roteamento.</span><span class="sxs-lookup"><span data-stu-id="b3a06-134">A configuration section that contains routing mapping entries.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="b3a06-135">Consulte também</span><span class="sxs-lookup"><span data-stu-id="b3a06-135">See also</span></span>
- <xref:System.ServiceModel.Routing.Configuration.RoutingSection?displayProperty=nameWithType>
- <xref:System.ServiceModel.Routing.Configuration.FilterTableEntryElement?displayProperty=nameWithType>
