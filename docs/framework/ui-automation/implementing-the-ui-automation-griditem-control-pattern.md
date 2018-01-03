---
title: "Implementando o padrão de controle GridItem de interface de usuário "
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-bcl
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- control patterns, GridItem
- UI Automation GridItem control pattern
- GridItem control pattern
ms.assetid: bffbae08-fe2a-42fd-ab84-f37187518916
caps.latest.revision: "15"
author: Xansky
ms.author: mhopkins
manager: markl
ms.workload: dotnet
ms.openlocfilehash: d234ea6f15706a47f6a758528dbe4eda0f3b778a
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="implementing-the-ui-automation-griditem-control-pattern"></a><span data-ttu-id="09b70-102">Implementando o padrão de controle GridItem de interface de usuário</span><span class="sxs-lookup"><span data-stu-id="09b70-102">Implementing the UI Automation GridItem Control Pattern</span></span>
> [!NOTE]
>  <span data-ttu-id="09b70-103">Esta documentação destina-se a desenvolvedores do .NET Framework que querem usar as classes da [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] gerenciadas definidas no namespace <xref:System.Windows.Automation>.</span><span class="sxs-lookup"><span data-stu-id="09b70-103">This documentation is intended for .NET Framework developers who want to use the managed [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] classes defined in the <xref:System.Windows.Automation> namespace.</span></span> <span data-ttu-id="09b70-104">Para obter as informações mais recentes sobre a [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], consulte [Windows Automation API: UI Automation](http://go.microsoft.com/fwlink/?LinkID=156746) (API de Automação do Windows: Automação da Interface do Usuário).</span><span class="sxs-lookup"><span data-stu-id="09b70-104">For the latest information about [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], see [Windows Automation API: UI Automation](http://go.microsoft.com/fwlink/?LinkID=156746).</span></span>  
  
 <span data-ttu-id="09b70-105">Este tópico apresenta diretrizes e convenções para implementar <xref:System.Windows.Automation.Provider.IGridItemProvider>, incluindo informações sobre propriedades.</span><span class="sxs-lookup"><span data-stu-id="09b70-105">This topic introduces guidelines and conventions for implementing <xref:System.Windows.Automation.Provider.IGridItemProvider>, including information about properties.</span></span> <span data-ttu-id="09b70-106">Links para referências adicionais são listadas no final da visão geral.</span><span class="sxs-lookup"><span data-stu-id="09b70-106">Links to additional references are listed at the end of the overview.</span></span>  
  
 <span data-ttu-id="09b70-107">O <xref:System.Windows.Automation.GridItemPattern> padrão de controle é usado para suportar controles filhos individuais de contêiners que implementam <xref:System.Windows.Automation.Provider.IGridProvider>.</span><span class="sxs-lookup"><span data-stu-id="09b70-107">The <xref:System.Windows.Automation.GridItemPattern> control pattern is used to support individual child controls of containers that implement <xref:System.Windows.Automation.Provider.IGridProvider>.</span></span> <span data-ttu-id="09b70-108">Para obter exemplos de controles que implementam este padrão de controle, consulte [mapeamento de padrão de controle para clientes de automação de interface do usuário](../../../docs/framework/ui-automation/control-pattern-mapping-for-ui-automation-clients.md).</span><span class="sxs-lookup"><span data-stu-id="09b70-108">For examples of controls that implement this control pattern, see [Control Pattern Mapping for UI Automation Clients](../../../docs/framework/ui-automation/control-pattern-mapping-for-ui-automation-clients.md).</span></span>  
  
<a name="Implementation_Guidelines_and_Conventions"></a>   
## <a name="implementation-guidelines-and-conventions"></a><span data-ttu-id="09b70-109">Convenções e diretrizes de implementação</span><span class="sxs-lookup"><span data-stu-id="09b70-109">Implementation Guidelines and Conventions</span></span>  
 <span data-ttu-id="09b70-110">Ao implementar <xref:System.Windows.Automation.Provider.IGridProvider>, observe as seguintes diretrizes e convenções:</span><span class="sxs-lookup"><span data-stu-id="09b70-110">When implementing <xref:System.Windows.Automation.Provider.IGridProvider>, note the following guidelines and conventions:</span></span>  
  
-   <span data-ttu-id="09b70-111">Coordenadas da grade são baseadas em zero com a célula superior esquerda tendo coordenadas (0, 0).</span><span class="sxs-lookup"><span data-stu-id="09b70-111">Grid coordinates are zero-based with the upper left cell having coordinates (0, 0).</span></span>  
  
-   <span data-ttu-id="09b70-112">As células mescladas relatará seus <xref:System.Windows.Automation.Provider.IGridItemProvider.Row%2A> e <xref:System.Windows.Automation.Provider.IGridItemProvider.Column%2A> propriedades com base em suas células âncoras subjacentes, conforme definido pelo provedor de automação de interface do usuário.</span><span class="sxs-lookup"><span data-stu-id="09b70-112">Merged cells will report their <xref:System.Windows.Automation.Provider.IGridItemProvider.Row%2A> and <xref:System.Windows.Automation.Provider.IGridItemProvider.Column%2A> properties based on their underlying anchor cell as defined by the UI Automation provider.</span></span> <span data-ttu-id="09b70-113">Normalmente, será mais à esquerda e superior de linha ou coluna.</span><span class="sxs-lookup"><span data-stu-id="09b70-113">Typically, it will be the topmost and leftmost row or column.</span></span>  
  
-   <span data-ttu-id="09b70-114"><xref:System.Windows.Automation.Provider.IGridItemProvider>não dá para manipulação ativa de grade como mesclar ou dividir células.</span><span class="sxs-lookup"><span data-stu-id="09b70-114"><xref:System.Windows.Automation.Provider.IGridItemProvider> does not provide for active manipulation of the grid such as merging or splitting cells.</span></span>  
  
-   <span data-ttu-id="09b70-115">Controles que implementam <xref:System.Windows.Automation.Provider.IGridItemProvider> normalmente podem ser percorridos (isto é, um cliente de automação de interface do usuário pode mover para controles adjacentes) usando o teclado.</span><span class="sxs-lookup"><span data-stu-id="09b70-115">Controls that implement <xref:System.Windows.Automation.Provider.IGridItemProvider> can typically be traversed (that is, a UI Automation client can move to adjacent controls) by using the keyboard.</span></span>  
  
<a name="Required_Members_for_IGridItemProvider"></a>   
## <a name="required-members-for-igriditemprovider"></a><span data-ttu-id="09b70-116">Membros necessários para IGridItemProvider</span><span class="sxs-lookup"><span data-stu-id="09b70-116">Required Members for IGridItemProvider</span></span>  
 <span data-ttu-id="09b70-117">As propriedades e métodos a seguir são necessários para implementar <xref:System.Windows.Automation.Provider.IGridItemProvider>.</span><span class="sxs-lookup"><span data-stu-id="09b70-117">The following properties and methods are required for implementing <xref:System.Windows.Automation.Provider.IGridItemProvider>.</span></span>  
  
|<span data-ttu-id="09b70-118">Membros necessários</span><span class="sxs-lookup"><span data-stu-id="09b70-118">Required members</span></span>|<span data-ttu-id="09b70-119">Tipo de membro</span><span class="sxs-lookup"><span data-stu-id="09b70-119">Member type</span></span>|<span data-ttu-id="09b70-120">Observações</span><span class="sxs-lookup"><span data-stu-id="09b70-120">Notes</span></span>|  
|----------------------|-----------------|-----------|  
|<xref:System.Windows.Automation.Provider.IGridItemProvider.Row%2A>|<span data-ttu-id="09b70-121">Propriedade</span><span class="sxs-lookup"><span data-stu-id="09b70-121">Property</span></span>|<span data-ttu-id="09b70-122">Nenhum</span><span class="sxs-lookup"><span data-stu-id="09b70-122">None</span></span>|  
|<xref:System.Windows.Automation.Provider.IGridItemProvider.Column%2A>|<span data-ttu-id="09b70-123">Propriedade</span><span class="sxs-lookup"><span data-stu-id="09b70-123">Property</span></span>|<span data-ttu-id="09b70-124">Nenhum</span><span class="sxs-lookup"><span data-stu-id="09b70-124">None</span></span>|  
|<xref:System.Windows.Automation.Provider.IGridItemProvider.RowSpan%2A>|<span data-ttu-id="09b70-125">Propriedade</span><span class="sxs-lookup"><span data-stu-id="09b70-125">Property</span></span>|<span data-ttu-id="09b70-126">Nenhum</span><span class="sxs-lookup"><span data-stu-id="09b70-126">None</span></span>|  
|<xref:System.Windows.Automation.Provider.IGridItemProvider.ColumnSpan%2A>|<span data-ttu-id="09b70-127">Propriedade</span><span class="sxs-lookup"><span data-stu-id="09b70-127">Property</span></span>|<span data-ttu-id="09b70-128">Nenhum</span><span class="sxs-lookup"><span data-stu-id="09b70-128">None</span></span>|  
|<xref:System.Windows.Automation.Provider.IGridItemProvider.ContainingGrid%2A>|<span data-ttu-id="09b70-129">Propriedade</span><span class="sxs-lookup"><span data-stu-id="09b70-129">Property</span></span>|<span data-ttu-id="09b70-130">Nenhum</span><span class="sxs-lookup"><span data-stu-id="09b70-130">None</span></span>|  
  
 <span data-ttu-id="09b70-131">Esse padrão de controle não tem métodos associados ou eventos.</span><span class="sxs-lookup"><span data-stu-id="09b70-131">This control pattern has no associated methods or events.</span></span>  
  
<a name="Exceptions"></a>   
## <a name="exceptions"></a><span data-ttu-id="09b70-132">Exceções</span><span class="sxs-lookup"><span data-stu-id="09b70-132">Exceptions</span></span>  
 <span data-ttu-id="09b70-133">Esse padrão de controle não tem exceção associada.</span><span class="sxs-lookup"><span data-stu-id="09b70-133">This control pattern has no associated exceptions.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="09b70-134">Consulte também</span><span class="sxs-lookup"><span data-stu-id="09b70-134">See Also</span></span>  
 [<span data-ttu-id="09b70-135">Visão geral de padrões de controle de automação da interface do usuário</span><span class="sxs-lookup"><span data-stu-id="09b70-135">UI Automation Control Patterns Overview</span></span>](../../../docs/framework/ui-automation/ui-automation-control-patterns-overview.md)  
 [<span data-ttu-id="09b70-136">Suporte a padrões de controle em um provedor de automação de interface do usuário</span><span class="sxs-lookup"><span data-stu-id="09b70-136">Support Control Patterns in a UI Automation Provider</span></span>](../../../docs/framework/ui-automation/support-control-patterns-in-a-ui-automation-provider.md)  
 [<span data-ttu-id="09b70-137">Padrões de controle de automação de interface do usuário para clientes</span><span class="sxs-lookup"><span data-stu-id="09b70-137">UI Automation Control Patterns for Clients</span></span>](../../../docs/framework/ui-automation/ui-automation-control-patterns-for-clients.md)  
 [<span data-ttu-id="09b70-138">Implementando o padrão de controle Grid de automação de interface do usuário</span><span class="sxs-lookup"><span data-stu-id="09b70-138">Implementing the UI Automation Grid Control Pattern</span></span>](../../../docs/framework/ui-automation/implementing-the-ui-automation-grid-control-pattern.md)  
 [<span data-ttu-id="09b70-139">Visão geral de árvore de automação de interface do usuário</span><span class="sxs-lookup"><span data-stu-id="09b70-139">UI Automation Tree Overview</span></span>](../../../docs/framework/ui-automation/ui-automation-tree-overview.md)  
 [<span data-ttu-id="09b70-140">Usar o cache em automação de interface do usuário</span><span class="sxs-lookup"><span data-stu-id="09b70-140">Use Caching in UI Automation</span></span>](../../../docs/framework/ui-automation/use-caching-in-ui-automation.md)
