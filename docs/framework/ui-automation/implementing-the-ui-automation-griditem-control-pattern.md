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
# <a name="implementing-the-ui-automation-griditem-control-pattern"></a><span data-ttu-id="bb56f-102">Implementando o padrão de controle GridItem de interface de usuário</span><span class="sxs-lookup"><span data-stu-id="bb56f-102">Implementing the UI Automation GridItem Control Pattern</span></span>
> [!NOTE]
> <span data-ttu-id="bb56f-103">Esta documentação destina-se a desenvolvedores do .NET Framework que querem usar as classes da [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] gerenciadas definidas no namespace <xref:System.Windows.Automation>.</span><span class="sxs-lookup"><span data-stu-id="bb56f-103">This documentation is intended for .NET Framework developers who want to use the managed [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] classes defined in the <xref:System.Windows.Automation> namespace.</span></span> <span data-ttu-id="bb56f-104">Para obter as informações mais recentes sobre a [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], consulte [Windows Automation API: UI Automation](/windows/win32/winauto/entry-uiauto-win32) (API de Automação do Windows: Automação da Interface do Usuário).</span><span class="sxs-lookup"><span data-stu-id="bb56f-104">For the latest information about [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], see [Windows Automation API: UI Automation](/windows/win32/winauto/entry-uiauto-win32).</span></span>  
  
 <span data-ttu-id="bb56f-105">Este tópico apresenta as diretrizes e convenções para implementar <xref:System.Windows.Automation.Provider.IGridItemProvider>, incluindo informações sobre propriedades.</span><span class="sxs-lookup"><span data-stu-id="bb56f-105">This topic introduces guidelines and conventions for implementing <xref:System.Windows.Automation.Provider.IGridItemProvider>, including information about properties.</span></span> <span data-ttu-id="bb56f-106">Links para referências adicionais são listados no final da visão geral.</span><span class="sxs-lookup"><span data-stu-id="bb56f-106">Links to additional references are listed at the end of the overview.</span></span>  
  
 <span data-ttu-id="bb56f-107">O padrão de controle <xref:System.Windows.Automation.GridItemPattern> é usado para dar suporte a controles filho individuais de contêineres que implementam <xref:System.Windows.Automation.Provider.IGridProvider>.</span><span class="sxs-lookup"><span data-stu-id="bb56f-107">The <xref:System.Windows.Automation.GridItemPattern> control pattern is used to support individual child controls of containers that implement <xref:System.Windows.Automation.Provider.IGridProvider>.</span></span> <span data-ttu-id="bb56f-108">Para obter exemplos de controles que implementam esse padrão de controle, consulte [mapeamento de padrão de controle para clientes de automação da interface do usuário](control-pattern-mapping-for-ui-automation-clients.md).</span><span class="sxs-lookup"><span data-stu-id="bb56f-108">For examples of controls that implement this control pattern, see [Control Pattern Mapping for UI Automation Clients](control-pattern-mapping-for-ui-automation-clients.md).</span></span>  
  
<a name="Implementation_Guidelines_and_Conventions"></a>   
## <a name="implementation-guidelines-and-conventions"></a><span data-ttu-id="bb56f-109">Diretrizes e convenções de implementação</span><span class="sxs-lookup"><span data-stu-id="bb56f-109">Implementation Guidelines and Conventions</span></span>  
 <span data-ttu-id="bb56f-110">Ao implementar <xref:System.Windows.Automation.Provider.IGridProvider>, observe as seguintes diretrizes e convenções:</span><span class="sxs-lookup"><span data-stu-id="bb56f-110">When implementing <xref:System.Windows.Automation.Provider.IGridProvider>, note the following guidelines and conventions:</span></span>  
  
- <span data-ttu-id="bb56f-111">As coordenadas de grade são baseadas em zero com a célula superior esquerda com coordenadas (0, 0).</span><span class="sxs-lookup"><span data-stu-id="bb56f-111">Grid coordinates are zero-based with the upper left cell having coordinates (0, 0).</span></span>  
  
- <span data-ttu-id="bb56f-112">As células mescladas relatarão suas <xref:System.Windows.Automation.Provider.IGridItemProvider.Row%2A> e <xref:System.Windows.Automation.Provider.IGridItemProvider.Column%2A> Propriedades com base em sua célula de âncora subjacente, conforme definido pelo provedor de automação de interface do usuário.</span><span class="sxs-lookup"><span data-stu-id="bb56f-112">Merged cells will report their <xref:System.Windows.Automation.Provider.IGridItemProvider.Row%2A> and <xref:System.Windows.Automation.Provider.IGridItemProvider.Column%2A> properties based on their underlying anchor cell as defined by the UI Automation provider.</span></span> <span data-ttu-id="bb56f-113">Normalmente, será a linha ou coluna mais alta e mais à esquerda.</span><span class="sxs-lookup"><span data-stu-id="bb56f-113">Typically, it will be the topmost and leftmost row or column.</span></span>  
  
- <span data-ttu-id="bb56f-114"><xref:System.Windows.Automation.Provider.IGridItemProvider> não fornece manipulação ativa da grade, como mesclagem ou divisão de células.</span><span class="sxs-lookup"><span data-stu-id="bb56f-114"><xref:System.Windows.Automation.Provider.IGridItemProvider> does not provide for active manipulation of the grid such as merging or splitting cells.</span></span>  
  
- <span data-ttu-id="bb56f-115">Controles que implementam <xref:System.Windows.Automation.Provider.IGridItemProvider> normalmente podem ser percorridos (ou seja, um cliente de automação da interface do usuário pode mover para controles adjacentes) usando o teclado.</span><span class="sxs-lookup"><span data-stu-id="bb56f-115">Controls that implement <xref:System.Windows.Automation.Provider.IGridItemProvider> can typically be traversed (that is, a UI Automation client can move to adjacent controls) by using the keyboard.</span></span>  
  
<a name="Required_Members_for_IGridItemProvider"></a>   
## <a name="required-members-for-igriditemprovider"></a><span data-ttu-id="bb56f-116">Membros necessários para IGridItemProvider</span><span class="sxs-lookup"><span data-stu-id="bb56f-116">Required Members for IGridItemProvider</span></span>  
 <span data-ttu-id="bb56f-117">As propriedades e os métodos a seguir são necessários para implementar <xref:System.Windows.Automation.Provider.IGridItemProvider>.</span><span class="sxs-lookup"><span data-stu-id="bb56f-117">The following properties and methods are required for implementing <xref:System.Windows.Automation.Provider.IGridItemProvider>.</span></span>  
  
|<span data-ttu-id="bb56f-118">Membros necessários</span><span class="sxs-lookup"><span data-stu-id="bb56f-118">Required members</span></span>|<span data-ttu-id="bb56f-119">Tipo de membro</span><span class="sxs-lookup"><span data-stu-id="bb56f-119">Member type</span></span>|<span data-ttu-id="bb56f-120">{1&gt;Observações&lt;1}</span><span class="sxs-lookup"><span data-stu-id="bb56f-120">Notes</span></span>|  
|----------------------|-----------------|-----------|  
|<xref:System.Windows.Automation.Provider.IGridItemProvider.Row%2A>|<span data-ttu-id="bb56f-121">Propriedade</span><span class="sxs-lookup"><span data-stu-id="bb56f-121">Property</span></span>|<span data-ttu-id="bb56f-122">Nenhum</span><span class="sxs-lookup"><span data-stu-id="bb56f-122">None</span></span>|  
|<xref:System.Windows.Automation.Provider.IGridItemProvider.Column%2A>|<span data-ttu-id="bb56f-123">Propriedade</span><span class="sxs-lookup"><span data-stu-id="bb56f-123">Property</span></span>|<span data-ttu-id="bb56f-124">Nenhum</span><span class="sxs-lookup"><span data-stu-id="bb56f-124">None</span></span>|  
|<xref:System.Windows.Automation.Provider.IGridItemProvider.RowSpan%2A>|<span data-ttu-id="bb56f-125">Propriedade</span><span class="sxs-lookup"><span data-stu-id="bb56f-125">Property</span></span>|<span data-ttu-id="bb56f-126">Nenhum</span><span class="sxs-lookup"><span data-stu-id="bb56f-126">None</span></span>|  
|<xref:System.Windows.Automation.Provider.IGridItemProvider.ColumnSpan%2A>|<span data-ttu-id="bb56f-127">Propriedade</span><span class="sxs-lookup"><span data-stu-id="bb56f-127">Property</span></span>|<span data-ttu-id="bb56f-128">Nenhum</span><span class="sxs-lookup"><span data-stu-id="bb56f-128">None</span></span>|  
|<xref:System.Windows.Automation.Provider.IGridItemProvider.ContainingGrid%2A>|<span data-ttu-id="bb56f-129">Propriedade</span><span class="sxs-lookup"><span data-stu-id="bb56f-129">Property</span></span>|<span data-ttu-id="bb56f-130">Nenhum</span><span class="sxs-lookup"><span data-stu-id="bb56f-130">None</span></span>|  
  
 <span data-ttu-id="bb56f-131">Este padrão de controle não tem nenhum método ou evento associado.</span><span class="sxs-lookup"><span data-stu-id="bb56f-131">This control pattern has no associated methods or events.</span></span>  
  
<a name="Exceptions"></a>   
## <a name="exceptions"></a><span data-ttu-id="bb56f-132">Exceções</span><span class="sxs-lookup"><span data-stu-id="bb56f-132">Exceptions</span></span>  
 <span data-ttu-id="bb56f-133">Este padrão de controle não tem nenhuma exceção associada.</span><span class="sxs-lookup"><span data-stu-id="bb56f-133">This control pattern has no associated exceptions.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bb56f-134">Consulte também</span><span class="sxs-lookup"><span data-stu-id="bb56f-134">See also</span></span>

- [<span data-ttu-id="bb56f-135">Visão geral de padrões de controle de automação da interface do usuário</span><span class="sxs-lookup"><span data-stu-id="bb56f-135">UI Automation Control Patterns Overview</span></span>](ui-automation-control-patterns-overview.md)
- [<span data-ttu-id="bb56f-136">Suporte a padrões de controle em um provedor de automação de interface do usuário</span><span class="sxs-lookup"><span data-stu-id="bb56f-136">Support Control Patterns in a UI Automation Provider</span></span>](support-control-patterns-in-a-ui-automation-provider.md)
- [<span data-ttu-id="bb56f-137">Padrões de controle de automação de interface do usuário para clientes</span><span class="sxs-lookup"><span data-stu-id="bb56f-137">UI Automation Control Patterns for Clients</span></span>](ui-automation-control-patterns-for-clients.md)
- [<span data-ttu-id="bb56f-138">Implementando o padrão de controle Grid de automação de interface do usuário</span><span class="sxs-lookup"><span data-stu-id="bb56f-138">Implementing the UI Automation Grid Control Pattern</span></span>](implementing-the-ui-automation-grid-control-pattern.md)
- [<span data-ttu-id="bb56f-139">Visão geral de árvore de automação de interface do usuário</span><span class="sxs-lookup"><span data-stu-id="bb56f-139">UI Automation Tree Overview</span></span>](ui-automation-tree-overview.md)
- [<span data-ttu-id="bb56f-140">Usar o cache em automação de interface do usuário</span><span class="sxs-lookup"><span data-stu-id="bb56f-140">Use Caching in UI Automation</span></span>](use-caching-in-ui-automation.md)
