---
title: <add> de <entries>
ms.date: 03/30/2017
ms.assetid: 3af4805b-dc72-4f68-b168-da4fba8c6170
ms.openlocfilehash: 23b0a825ea593f85ade870d5b93367571eaa3ec0
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/06/2020
ms.locfileid: "70850513"
---
# <a name="add-of-entries"></a><span data-ttu-id="cd528-102">\<add> de \<entries></span><span class="sxs-lookup"><span data-stu-id="cd528-102">\<add> of \<entries></span></span>
<span data-ttu-id="cd528-103">Representa uma entrada de roteamento que mapeia um filtro para um ponto de extremidade do cliente que foi definido anteriormente.</span><span class="sxs-lookup"><span data-stu-id="cd528-103">Represents a routing entry that maps a filter to a client endpoint that was previously defined.</span></span> <span data-ttu-id="cd528-104">As mensagens correspondentes a este filtro serão enviadas para esse destino.</span><span class="sxs-lookup"><span data-stu-id="cd528-104">Messages matching this filter will be sent to this destination.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<routing>**](routing.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<filterTables>**](filtertables.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<filterTable>**](filtertable.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<entries>**](entries.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<add>**  
  
## <a name="syntax"></a><span data-ttu-id="cd528-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="cd528-105">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="cd528-106">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="cd528-106">Attributes and Elements</span></span>  
 <span data-ttu-id="cd528-107">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="cd528-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="cd528-108">Atributos</span><span class="sxs-lookup"><span data-stu-id="cd528-108">Attributes</span></span>  
  
|<span data-ttu-id="cd528-109">Atributo</span><span class="sxs-lookup"><span data-stu-id="cd528-109">Attribute</span></span>|<span data-ttu-id="cd528-110">Descrição</span><span class="sxs-lookup"><span data-stu-id="cd528-110">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="cd528-111">backupList</span><span class="sxs-lookup"><span data-stu-id="cd528-111">backupList</span></span>|<span data-ttu-id="cd528-112">Uma cadeia de caracteres que especifica uma referência a uma lista de pontos de extremidade de backup.</span><span class="sxs-lookup"><span data-stu-id="cd528-112">A string that specifies a reference to a backup list of endpoints.</span></span>|  
|<span data-ttu-id="cd528-113">endpoint</span><span class="sxs-lookup"><span data-stu-id="cd528-113">endpoint</span></span>|<span data-ttu-id="cd528-114">Uma cadeia de caracteres que especifica uma referência a um ponto de extremidade do cliente que receberá mensagens que correspondem ao filtro especificado pelo `filterName` atributo.</span><span class="sxs-lookup"><span data-stu-id="cd528-114">A string that specifies a reference to a client endpoint that will receive messages that match the filter specified by the `filterName` attribute.</span></span>|  
|<span data-ttu-id="cd528-115">Filter</span><span class="sxs-lookup"><span data-stu-id="cd528-115">filterName</span></span>|<span data-ttu-id="cd528-116">Uma cadeia de caracteres que especifica uma referência a um elemento de filtro.</span><span class="sxs-lookup"><span data-stu-id="cd528-116">A string that specifies a reference to a filter element.</span></span>|  
|<span data-ttu-id="cd528-117">priority</span><span class="sxs-lookup"><span data-stu-id="cd528-117">priority</span></span>|<span data-ttu-id="cd528-118">Um inteiro que especifica a prioridade desta entrada.</span><span class="sxs-lookup"><span data-stu-id="cd528-118">An integer that specifies the priority of this entry.</span></span><br /><br /> <span data-ttu-id="cd528-119">As entradas na tabela de roteamento serão avaliadas com base na prioridade, sendo que 0 é a prioridade mais baixa.</span><span class="sxs-lookup"><span data-stu-id="cd528-119">Entries in the routing table will be evaluated based on priority, with 0 being the lowest priority.</span></span> <span data-ttu-id="cd528-120">Todas as entradas de uma prioridade específica são avaliadas simultaneamente, se nenhuma entrada correspondente for encontrada para a prioridade atual, o próximo nível de prioridade será avaliado.</span><span class="sxs-lookup"><span data-stu-id="cd528-120">All entries for a specific priority are evaluated simultaneously, if no matching entry is found for the current priority, the next priority level will be evaluated.</span></span><br /><br /> <span data-ttu-id="cd528-121">Esse valor é opcional.</span><span class="sxs-lookup"><span data-stu-id="cd528-121">This value is optional.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="cd528-122">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="cd528-122">Child Elements</span></span>  
 <span data-ttu-id="cd528-123">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="cd528-123">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="cd528-124">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="cd528-124">Parent Elements</span></span>  
  
|<span data-ttu-id="cd528-125">Elemento</span><span class="sxs-lookup"><span data-stu-id="cd528-125">Element</span></span>|<span data-ttu-id="cd528-126">Descrição</span><span class="sxs-lookup"><span data-stu-id="cd528-126">Description</span></span>|  
|-------------|-----------------|  
|[\<routing>](routing.md)|<span data-ttu-id="cd528-127">Uma seção de configuração que contém entradas de mapeamento de roteamento.</span><span class="sxs-lookup"><span data-stu-id="cd528-127">A configuration section that contains routing mapping entries.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="cd528-128">Confira também</span><span class="sxs-lookup"><span data-stu-id="cd528-128">See also</span></span>

- <xref:System.ServiceModel.Routing.Configuration.RoutingSection?displayProperty=nameWithType>
- <xref:System.ServiceModel.Routing.Configuration.FilterTableEntryElement?displayProperty=nameWithType>
