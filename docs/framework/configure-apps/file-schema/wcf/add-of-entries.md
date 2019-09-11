---
title: <add> de <entries>
ms.date: 03/30/2017
ms.assetid: 3af4805b-dc72-4f68-b168-da4fba8c6170
ms.openlocfilehash: 23b0a825ea593f85ade870d5b93367571eaa3ec0
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/10/2019
ms.locfileid: "70850513"
---
# <a name="add-of-entries"></a><span data-ttu-id="675a1-102">\<Adicionar > de \<entradas ></span><span class="sxs-lookup"><span data-stu-id="675a1-102">\<add> of \<entries></span></span>
<span data-ttu-id="675a1-103">Representa uma entrada de roteamento que mapeia um filtro para um ponto de extremidade do cliente que foi definido anteriormente.</span><span class="sxs-lookup"><span data-stu-id="675a1-103">Represents a routing entry that maps a filter to a client endpoint that was previously defined.</span></span> <span data-ttu-id="675a1-104">As mensagens correspondentes a este filtro serão enviadas para esse destino.</span><span class="sxs-lookup"><span data-stu-id="675a1-104">Messages matching this filter will be sent to this destination.</span></span>  
  
<span data-ttu-id="675a1-105">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="675a1-105">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="675a1-106">&nbsp;&nbsp;[ **\<> de System. serviceModel**](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="675a1-106">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="675a1-107">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> de roteamento**](routing.md)</span><span class="sxs-lookup"><span data-stu-id="675a1-107">&nbsp;&nbsp;&nbsp;&nbsp;[**\<routing>**](routing.md)</span></span>\
<span data-ttu-id="675a1-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> filterTables**](filtertables.md)</span><span class="sxs-lookup"><span data-stu-id="675a1-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<filterTables>**](filtertables.md)</span></span>\
<span data-ttu-id="675a1-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> de FilterTable**](filtertable.md)</span><span class="sxs-lookup"><span data-stu-id="675a1-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<filterTable>**](filtertable.md)</span></span>\
<span data-ttu-id="675a1-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<entradas >** ](entries.md)</span><span class="sxs-lookup"><span data-stu-id="675a1-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<entries>**](entries.md)</span></span>\
<span data-ttu-id="675a1-111">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<Adicionar >**</span><span class="sxs-lookup"><span data-stu-id="675a1-111">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<add>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="675a1-112">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="675a1-112">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="675a1-113">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="675a1-113">Attributes and Elements</span></span>  
 <span data-ttu-id="675a1-114">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="675a1-114">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="675a1-115">Atributos</span><span class="sxs-lookup"><span data-stu-id="675a1-115">Attributes</span></span>  
  
|<span data-ttu-id="675a1-116">Atributo</span><span class="sxs-lookup"><span data-stu-id="675a1-116">Attribute</span></span>|<span data-ttu-id="675a1-117">Descrição</span><span class="sxs-lookup"><span data-stu-id="675a1-117">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="675a1-118">backupList</span><span class="sxs-lookup"><span data-stu-id="675a1-118">backupList</span></span>|<span data-ttu-id="675a1-119">Uma cadeia de caracteres que especifica uma referência a uma lista de pontos de extremidade de backup.</span><span class="sxs-lookup"><span data-stu-id="675a1-119">A string that specifies a reference to a backup list of endpoints.</span></span>|  
|<span data-ttu-id="675a1-120">ponto de extremidade</span><span class="sxs-lookup"><span data-stu-id="675a1-120">endpoint</span></span>|<span data-ttu-id="675a1-121">Uma cadeia de caracteres que especifica uma referência a um ponto de extremidade do cliente que receberá mensagens que correspondem `filterName` ao filtro especificado pelo atributo.</span><span class="sxs-lookup"><span data-stu-id="675a1-121">A string that specifies a reference to a client endpoint that will receive messages that match the filter specified by the `filterName` attribute.</span></span>|  
|<span data-ttu-id="675a1-122">filterName</span><span class="sxs-lookup"><span data-stu-id="675a1-122">filterName</span></span>|<span data-ttu-id="675a1-123">Uma cadeia de caracteres que especifica uma referência a um elemento de filtro.</span><span class="sxs-lookup"><span data-stu-id="675a1-123">A string that specifies a reference to a filter element.</span></span>|  
|<span data-ttu-id="675a1-124">priority</span><span class="sxs-lookup"><span data-stu-id="675a1-124">priority</span></span>|<span data-ttu-id="675a1-125">Um inteiro que especifica a prioridade desta entrada.</span><span class="sxs-lookup"><span data-stu-id="675a1-125">An integer that specifies the priority of this entry.</span></span><br /><br /> <span data-ttu-id="675a1-126">As entradas na tabela de roteamento serão avaliadas com base na prioridade, sendo que 0 é a prioridade mais baixa.</span><span class="sxs-lookup"><span data-stu-id="675a1-126">Entries in the routing table will be evaluated based on priority, with 0 being the lowest priority.</span></span> <span data-ttu-id="675a1-127">Todas as entradas de uma prioridade específica são avaliadas simultaneamente, se nenhuma entrada correspondente for encontrada para a prioridade atual, o próximo nível de prioridade será avaliado.</span><span class="sxs-lookup"><span data-stu-id="675a1-127">All entries for a specific priority are evaluated simultaneously, if no matching entry is found for the current priority, the next priority level will be evaluated.</span></span><br /><br /> <span data-ttu-id="675a1-128">Esse valor é opcional.</span><span class="sxs-lookup"><span data-stu-id="675a1-128">This value is optional.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="675a1-129">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="675a1-129">Child Elements</span></span>  
 <span data-ttu-id="675a1-130">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="675a1-130">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="675a1-131">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="675a1-131">Parent Elements</span></span>  
  
|<span data-ttu-id="675a1-132">Elemento</span><span class="sxs-lookup"><span data-stu-id="675a1-132">Element</span></span>|<span data-ttu-id="675a1-133">Descrição</span><span class="sxs-lookup"><span data-stu-id="675a1-133">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="675a1-134">\<routing></span><span class="sxs-lookup"><span data-stu-id="675a1-134">\<routing></span></span>](routing.md)|<span data-ttu-id="675a1-135">Uma seção de configuração que contém entradas de mapeamento de roteamento.</span><span class="sxs-lookup"><span data-stu-id="675a1-135">A configuration section that contains routing mapping entries.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="675a1-136">Consulte também</span><span class="sxs-lookup"><span data-stu-id="675a1-136">See also</span></span>

- <xref:System.ServiceModel.Routing.Configuration.RoutingSection?displayProperty=nameWithType>
- <xref:System.ServiceModel.Routing.Configuration.FilterTableEntryElement?displayProperty=nameWithType>
