---
title: Implementando o padrão de controle GridItem de interface de usuário
ms.date: 03/30/2017
helpviewer_keywords:
- control patterns, GridItem
- UI Automation GridItem control pattern
- GridItem control pattern
ms.assetid: bffbae08-fe2a-42fd-ab84-f37187518916
ms.openlocfilehash: 832a53e072afc5533f2eeb7feb0cc326771cf23d
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74435258"
---
# <a name="implementing-the-ui-automation-griditem-control-pattern"></a><span data-ttu-id="77882-102">Implementando o padrão de controle GridItem de interface de usuário</span><span class="sxs-lookup"><span data-stu-id="77882-102">Implementing the UI Automation GridItem Control Pattern</span></span>
> [!NOTE]
> <span data-ttu-id="77882-103">Esta documentação destina-se a desenvolvedores do .NET Framework que querem usar as classes da [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] gerenciadas definidas no namespace <xref:System.Windows.Automation>.</span><span class="sxs-lookup"><span data-stu-id="77882-103">This documentation is intended for .NET Framework developers who want to use the managed [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] classes defined in the <xref:System.Windows.Automation> namespace.</span></span> <span data-ttu-id="77882-104">Para obter as informações mais recentes sobre a [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], consulte [Windows Automation API: UI Automation](/windows/win32/winauto/entry-uiauto-win32) (API de Automação do Windows: Automação da Interface do Usuário).</span><span class="sxs-lookup"><span data-stu-id="77882-104">For the latest information about [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], see [Windows Automation API: UI Automation](/windows/win32/winauto/entry-uiauto-win32).</span></span>  
  
 <span data-ttu-id="77882-105">This topic introduces guidelines and conventions for implementing <xref:System.Windows.Automation.Provider.IGridItemProvider>, including information about properties.</span><span class="sxs-lookup"><span data-stu-id="77882-105">This topic introduces guidelines and conventions for implementing <xref:System.Windows.Automation.Provider.IGridItemProvider>, including information about properties.</span></span> <span data-ttu-id="77882-106">Links to additional references are listed at the end of the overview.</span><span class="sxs-lookup"><span data-stu-id="77882-106">Links to additional references are listed at the end of the overview.</span></span>  
  
 <span data-ttu-id="77882-107">The <xref:System.Windows.Automation.GridItemPattern> control pattern is used to support individual child controls of containers that implement <xref:System.Windows.Automation.Provider.IGridProvider>.</span><span class="sxs-lookup"><span data-stu-id="77882-107">The <xref:System.Windows.Automation.GridItemPattern> control pattern is used to support individual child controls of containers that implement <xref:System.Windows.Automation.Provider.IGridProvider>.</span></span> <span data-ttu-id="77882-108">For examples of controls that implement this control pattern, see [Control Pattern Mapping for UI Automation Clients](control-pattern-mapping-for-ui-automation-clients.md).</span><span class="sxs-lookup"><span data-stu-id="77882-108">For examples of controls that implement this control pattern, see [Control Pattern Mapping for UI Automation Clients](control-pattern-mapping-for-ui-automation-clients.md).</span></span>  
  
<a name="Implementation_Guidelines_and_Conventions"></a>   
## <a name="implementation-guidelines-and-conventions"></a><span data-ttu-id="77882-109">Implementation Guidelines and Conventions</span><span class="sxs-lookup"><span data-stu-id="77882-109">Implementation Guidelines and Conventions</span></span>  
 <span data-ttu-id="77882-110">When implementing <xref:System.Windows.Automation.Provider.IGridProvider>, note the following guidelines and conventions:</span><span class="sxs-lookup"><span data-stu-id="77882-110">When implementing <xref:System.Windows.Automation.Provider.IGridProvider>, note the following guidelines and conventions:</span></span>  
  
- <span data-ttu-id="77882-111">Grid coordinates are zero-based with the upper left cell having coordinates (0, 0).</span><span class="sxs-lookup"><span data-stu-id="77882-111">Grid coordinates are zero-based with the upper left cell having coordinates (0, 0).</span></span>  
  
- <span data-ttu-id="77882-112">Merged cells will report their <xref:System.Windows.Automation.Provider.IGridItemProvider.Row%2A> and <xref:System.Windows.Automation.Provider.IGridItemProvider.Column%2A> properties based on their underlying anchor cell as defined by the UI Automation provider.</span><span class="sxs-lookup"><span data-stu-id="77882-112">Merged cells will report their <xref:System.Windows.Automation.Provider.IGridItemProvider.Row%2A> and <xref:System.Windows.Automation.Provider.IGridItemProvider.Column%2A> properties based on their underlying anchor cell as defined by the UI Automation provider.</span></span> <span data-ttu-id="77882-113">Typically, it will be the topmost and leftmost row or column.</span><span class="sxs-lookup"><span data-stu-id="77882-113">Typically, it will be the topmost and leftmost row or column.</span></span>  
  
- <span data-ttu-id="77882-114"><xref:System.Windows.Automation.Provider.IGridItemProvider> does not provide for active manipulation of the grid such as merging or splitting cells.</span><span class="sxs-lookup"><span data-stu-id="77882-114"><xref:System.Windows.Automation.Provider.IGridItemProvider> does not provide for active manipulation of the grid such as merging or splitting cells.</span></span>  
  
- <span data-ttu-id="77882-115">Controls that implement <xref:System.Windows.Automation.Provider.IGridItemProvider> can typically be traversed (that is, a UI Automation client can move to adjacent controls) by using the keyboard.</span><span class="sxs-lookup"><span data-stu-id="77882-115">Controls that implement <xref:System.Windows.Automation.Provider.IGridItemProvider> can typically be traversed (that is, a UI Automation client can move to adjacent controls) by using the keyboard.</span></span>  
  
<a name="Required_Members_for_IGridItemProvider"></a>   
## <a name="required-members-for-igriditemprovider"></a><span data-ttu-id="77882-116">Required Members for IGridItemProvider</span><span class="sxs-lookup"><span data-stu-id="77882-116">Required Members for IGridItemProvider</span></span>  
 <span data-ttu-id="77882-117">The following properties and methods are required for implementing <xref:System.Windows.Automation.Provider.IGridItemProvider>.</span><span class="sxs-lookup"><span data-stu-id="77882-117">The following properties and methods are required for implementing <xref:System.Windows.Automation.Provider.IGridItemProvider>.</span></span>  
  
|<span data-ttu-id="77882-118">Required members</span><span class="sxs-lookup"><span data-stu-id="77882-118">Required members</span></span>|<span data-ttu-id="77882-119">Member type</span><span class="sxs-lookup"><span data-stu-id="77882-119">Member type</span></span>|<span data-ttu-id="77882-120">Anotações</span><span class="sxs-lookup"><span data-stu-id="77882-120">Notes</span></span>|  
|----------------------|-----------------|-----------|  
|<xref:System.Windows.Automation.Provider.IGridItemProvider.Row%2A>|<span data-ttu-id="77882-121">propriedade</span><span class="sxs-lookup"><span data-stu-id="77882-121">Property</span></span>|<span data-ttu-id="77882-122">Nenhum</span><span class="sxs-lookup"><span data-stu-id="77882-122">None</span></span>|  
|<xref:System.Windows.Automation.Provider.IGridItemProvider.Column%2A>|<span data-ttu-id="77882-123">propriedade</span><span class="sxs-lookup"><span data-stu-id="77882-123">Property</span></span>|<span data-ttu-id="77882-124">Nenhum</span><span class="sxs-lookup"><span data-stu-id="77882-124">None</span></span>|  
|<xref:System.Windows.Automation.Provider.IGridItemProvider.RowSpan%2A>|<span data-ttu-id="77882-125">propriedade</span><span class="sxs-lookup"><span data-stu-id="77882-125">Property</span></span>|<span data-ttu-id="77882-126">Nenhum</span><span class="sxs-lookup"><span data-stu-id="77882-126">None</span></span>|  
|<xref:System.Windows.Automation.Provider.IGridItemProvider.ColumnSpan%2A>|<span data-ttu-id="77882-127">propriedade</span><span class="sxs-lookup"><span data-stu-id="77882-127">Property</span></span>|<span data-ttu-id="77882-128">Nenhum</span><span class="sxs-lookup"><span data-stu-id="77882-128">None</span></span>|  
|<xref:System.Windows.Automation.Provider.IGridItemProvider.ContainingGrid%2A>|<span data-ttu-id="77882-129">propriedade</span><span class="sxs-lookup"><span data-stu-id="77882-129">Property</span></span>|<span data-ttu-id="77882-130">Nenhum</span><span class="sxs-lookup"><span data-stu-id="77882-130">None</span></span>|  
  
 <span data-ttu-id="77882-131">This control pattern has no associated methods or events.</span><span class="sxs-lookup"><span data-stu-id="77882-131">This control pattern has no associated methods or events.</span></span>  
  
<a name="Exceptions"></a>   
## <a name="exceptions"></a><span data-ttu-id="77882-132">Exceções</span><span class="sxs-lookup"><span data-stu-id="77882-132">Exceptions</span></span>  
 <span data-ttu-id="77882-133">This control pattern has no associated exceptions.</span><span class="sxs-lookup"><span data-stu-id="77882-133">This control pattern has no associated exceptions.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="77882-134">Consulte também</span><span class="sxs-lookup"><span data-stu-id="77882-134">See also</span></span>

- [<span data-ttu-id="77882-135">Visão geral de padrões de controle de automação da interface do usuário</span><span class="sxs-lookup"><span data-stu-id="77882-135">UI Automation Control Patterns Overview</span></span>](ui-automation-control-patterns-overview.md)
- [<span data-ttu-id="77882-136">Suporte a padrões de controle em um provedor de automação de interface do usuário</span><span class="sxs-lookup"><span data-stu-id="77882-136">Support Control Patterns in a UI Automation Provider</span></span>](support-control-patterns-in-a-ui-automation-provider.md)
- [<span data-ttu-id="77882-137">Padrões de controle de automação de interface do usuário para clientes</span><span class="sxs-lookup"><span data-stu-id="77882-137">UI Automation Control Patterns for Clients</span></span>](ui-automation-control-patterns-for-clients.md)
- [<span data-ttu-id="77882-138">Implementando o padrão de controle Grid de automação de interface do usuário</span><span class="sxs-lookup"><span data-stu-id="77882-138">Implementing the UI Automation Grid Control Pattern</span></span>](implementing-the-ui-automation-grid-control-pattern.md)
- [<span data-ttu-id="77882-139">Visão geral de árvore de automação de interface do usuário</span><span class="sxs-lookup"><span data-stu-id="77882-139">UI Automation Tree Overview</span></span>](ui-automation-tree-overview.md)
- [<span data-ttu-id="77882-140">Usar o cache em automação de interface do usuário</span><span class="sxs-lookup"><span data-stu-id="77882-140">Use Caching in UI Automation</span></span>](use-caching-in-ui-automation.md)
