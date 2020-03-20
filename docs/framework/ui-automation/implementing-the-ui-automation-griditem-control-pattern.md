---
title: 'Implementando o padrão de controle GridItem de interface de usuário '
ms.date: 03/30/2017
helpviewer_keywords:
- control patterns, GridItem
- UI Automation GridItem control pattern
- GridItem control pattern
ms.assetid: bffbae08-fe2a-42fd-ab84-f37187518916
ms.openlocfilehash: d561587e6bb98ba857b27ba89b4c1a45ba964ffd
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79180195"
---
# <a name="implementing-the-ui-automation-griditem-control-pattern"></a><span data-ttu-id="2406e-102">Implementando o padrão de controle GridItem de interface de usuário </span><span class="sxs-lookup"><span data-stu-id="2406e-102">Implementing the UI Automation GridItem Control Pattern</span></span>
> [!NOTE]
> <span data-ttu-id="2406e-103">Esta documentação destina-se a desenvolvedores do .NET Framework que querem usar as classes da [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] gerenciadas definidas no namespace <xref:System.Windows.Automation>.</span><span class="sxs-lookup"><span data-stu-id="2406e-103">This documentation is intended for .NET Framework developers who want to use the managed [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] classes defined in the <xref:System.Windows.Automation> namespace.</span></span> <span data-ttu-id="2406e-104">Para obter as informações mais recentes sobre a [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], consulte [Windows Automation API: UI Automation](/windows/win32/winauto/entry-uiauto-win32) (API de Automação do Windows: Automação da Interface do Usuário).</span><span class="sxs-lookup"><span data-stu-id="2406e-104">For the latest information about [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], see [Windows Automation API: UI Automation](/windows/win32/winauto/entry-uiauto-win32).</span></span>  
  
 <span data-ttu-id="2406e-105">Este tópico introduz diretrizes e <xref:System.Windows.Automation.Provider.IGridItemProvider>convenções para a implementação, incluindo informações sobre propriedades.</span><span class="sxs-lookup"><span data-stu-id="2406e-105">This topic introduces guidelines and conventions for implementing <xref:System.Windows.Automation.Provider.IGridItemProvider>, including information about properties.</span></span> <span data-ttu-id="2406e-106">Os links para referências adicionais são listados no final da visão geral.</span><span class="sxs-lookup"><span data-stu-id="2406e-106">Links to additional references are listed at the end of the overview.</span></span>  
  
 <span data-ttu-id="2406e-107">O <xref:System.Windows.Automation.GridItemPattern> padrão de controle é usado para apoiar <xref:System.Windows.Automation.Provider.IGridProvider>controles individuais de crianças de recipientes que implementam .</span><span class="sxs-lookup"><span data-stu-id="2406e-107">The <xref:System.Windows.Automation.GridItemPattern> control pattern is used to support individual child controls of containers that implement <xref:System.Windows.Automation.Provider.IGridProvider>.</span></span> <span data-ttu-id="2406e-108">Para exemplos de controles que implementam esse padrão de controle, consulte Mapping de padrão de [controle para clientes de automação de interface do usuário](control-pattern-mapping-for-ui-automation-clients.md).</span><span class="sxs-lookup"><span data-stu-id="2406e-108">For examples of controls that implement this control pattern, see [Control Pattern Mapping for UI Automation Clients](control-pattern-mapping-for-ui-automation-clients.md).</span></span>  
  
<a name="Implementation_Guidelines_and_Conventions"></a>
## <a name="implementation-guidelines-and-conventions"></a><span data-ttu-id="2406e-109">Diretrizes e Convenções de Implementação</span><span class="sxs-lookup"><span data-stu-id="2406e-109">Implementation Guidelines and Conventions</span></span>  
 <span data-ttu-id="2406e-110">Ao <xref:System.Windows.Automation.Provider.IGridProvider>implementar, observe as seguintes diretrizes e convenções:</span><span class="sxs-lookup"><span data-stu-id="2406e-110">When implementing <xref:System.Windows.Automation.Provider.IGridProvider>, note the following guidelines and conventions:</span></span>  
  
- <span data-ttu-id="2406e-111">As coordenadas da grade são baseadas em zero com a célula superior esquerda tendo coordenadas (0,0).</span><span class="sxs-lookup"><span data-stu-id="2406e-111">Grid coordinates are zero-based with the upper left cell having coordinates (0, 0).</span></span>  
  
- <span data-ttu-id="2406e-112">As células mescladas <xref:System.Windows.Automation.Provider.IGridItemProvider.Row%2A> <xref:System.Windows.Automation.Provider.IGridItemProvider.Column%2A> reportarão suas propriedades com base em sua célula âncora subjacente, conforme definido pelo provedor de Automação de UI.</span><span class="sxs-lookup"><span data-stu-id="2406e-112">Merged cells will report their <xref:System.Windows.Automation.Provider.IGridItemProvider.Row%2A> and <xref:System.Windows.Automation.Provider.IGridItemProvider.Column%2A> properties based on their underlying anchor cell as defined by the UI Automation provider.</span></span> <span data-ttu-id="2406e-113">Normalmente, será a linha ou coluna mais alta e mais à esquerda.</span><span class="sxs-lookup"><span data-stu-id="2406e-113">Typically, it will be the topmost and leftmost row or column.</span></span>  
  
- <span data-ttu-id="2406e-114"><xref:System.Windows.Automation.Provider.IGridItemProvider>não prevê manipulação ativa da grade, como a fusão ou divisão de células.</span><span class="sxs-lookup"><span data-stu-id="2406e-114"><xref:System.Windows.Automation.Provider.IGridItemProvider> does not provide for active manipulation of the grid such as merging or splitting cells.</span></span>  
  
- <span data-ttu-id="2406e-115">Os controles <xref:System.Windows.Automation.Provider.IGridItemProvider> que implementam podem ser normalmente atravessados (ou seja, um cliente de Automação de IU pode se mover para controles adjacentes) usando o teclado.</span><span class="sxs-lookup"><span data-stu-id="2406e-115">Controls that implement <xref:System.Windows.Automation.Provider.IGridItemProvider> can typically be traversed (that is, a UI Automation client can move to adjacent controls) by using the keyboard.</span></span>  
  
<a name="Required_Members_for_IGridItemProvider"></a>
## <a name="required-members-for-igriditemprovider"></a><span data-ttu-id="2406e-116">Membros obrigatórios para IGridItemProvider</span><span class="sxs-lookup"><span data-stu-id="2406e-116">Required Members for IGridItemProvider</span></span>  
 <span data-ttu-id="2406e-117">As seguintes propriedades e métodos <xref:System.Windows.Automation.Provider.IGridItemProvider>são necessários para a implementação.</span><span class="sxs-lookup"><span data-stu-id="2406e-117">The following properties and methods are required for implementing <xref:System.Windows.Automation.Provider.IGridItemProvider>.</span></span>  
  
|<span data-ttu-id="2406e-118">Membros necessários</span><span class="sxs-lookup"><span data-stu-id="2406e-118">Required members</span></span>|<span data-ttu-id="2406e-119">Tipo de membro</span><span class="sxs-lookup"><span data-stu-id="2406e-119">Member type</span></span>|<span data-ttu-id="2406e-120">Observações</span><span class="sxs-lookup"><span data-stu-id="2406e-120">Notes</span></span>|  
|----------------------|-----------------|-----------|  
|<xref:System.Windows.Automation.Provider.IGridItemProvider.Row%2A>|<span data-ttu-id="2406e-121">Propriedade</span><span class="sxs-lookup"><span data-stu-id="2406e-121">Property</span></span>|<span data-ttu-id="2406e-122">Nenhum</span><span class="sxs-lookup"><span data-stu-id="2406e-122">None</span></span>|  
|<xref:System.Windows.Automation.Provider.IGridItemProvider.Column%2A>|<span data-ttu-id="2406e-123">Propriedade</span><span class="sxs-lookup"><span data-stu-id="2406e-123">Property</span></span>|<span data-ttu-id="2406e-124">Nenhum</span><span class="sxs-lookup"><span data-stu-id="2406e-124">None</span></span>|  
|<xref:System.Windows.Automation.Provider.IGridItemProvider.RowSpan%2A>|<span data-ttu-id="2406e-125">Propriedade</span><span class="sxs-lookup"><span data-stu-id="2406e-125">Property</span></span>|<span data-ttu-id="2406e-126">Nenhum</span><span class="sxs-lookup"><span data-stu-id="2406e-126">None</span></span>|  
|<xref:System.Windows.Automation.Provider.IGridItemProvider.ColumnSpan%2A>|<span data-ttu-id="2406e-127">Propriedade</span><span class="sxs-lookup"><span data-stu-id="2406e-127">Property</span></span>|<span data-ttu-id="2406e-128">Nenhum</span><span class="sxs-lookup"><span data-stu-id="2406e-128">None</span></span>|  
|<xref:System.Windows.Automation.Provider.IGridItemProvider.ContainingGrid%2A>|<span data-ttu-id="2406e-129">Propriedade</span><span class="sxs-lookup"><span data-stu-id="2406e-129">Property</span></span>|<span data-ttu-id="2406e-130">Nenhum</span><span class="sxs-lookup"><span data-stu-id="2406e-130">None</span></span>|  
  
 <span data-ttu-id="2406e-131">Este padrão de controle não tem métodos ou eventos associados.</span><span class="sxs-lookup"><span data-stu-id="2406e-131">This control pattern has no associated methods or events.</span></span>  
  
<a name="Exceptions"></a>
## <a name="exceptions"></a><span data-ttu-id="2406e-132">Exceções</span><span class="sxs-lookup"><span data-stu-id="2406e-132">Exceptions</span></span>  
 <span data-ttu-id="2406e-133">Este padrão de controle não tem exceções associadas.</span><span class="sxs-lookup"><span data-stu-id="2406e-133">This control pattern has no associated exceptions.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2406e-134">Confira também</span><span class="sxs-lookup"><span data-stu-id="2406e-134">See also</span></span>

- [<span data-ttu-id="2406e-135">Visão Geral de Padrões de Controle de Automação de Interface de Usuário</span><span class="sxs-lookup"><span data-stu-id="2406e-135">UI Automation Control Patterns Overview</span></span>](ui-automation-control-patterns-overview.md)
- [<span data-ttu-id="2406e-136">Padrões de controle de suporte em um provedor de automação da interface do usuário</span><span class="sxs-lookup"><span data-stu-id="2406e-136">Support Control Patterns in a UI Automation Provider</span></span>](support-control-patterns-in-a-ui-automation-provider.md)
- [<span data-ttu-id="2406e-137">Padrões de controle de automação de interface do usuário para clientes</span><span class="sxs-lookup"><span data-stu-id="2406e-137">UI Automation Control Patterns for Clients</span></span>](ui-automation-control-patterns-for-clients.md)
- [<span data-ttu-id="2406e-138">Implementando o Padrão de Controle Grid de Automação de Interface de Usuário</span><span class="sxs-lookup"><span data-stu-id="2406e-138">Implementing the UI Automation Grid Control Pattern</span></span>](implementing-the-ui-automation-grid-control-pattern.md)
- [<span data-ttu-id="2406e-139">Visão geral da árvore de automação de interface do usuário</span><span class="sxs-lookup"><span data-stu-id="2406e-139">UI Automation Tree Overview</span></span>](ui-automation-tree-overview.md)
- [<span data-ttu-id="2406e-140">Usar armazenamento em cache em automação de interface do usuário</span><span class="sxs-lookup"><span data-stu-id="2406e-140">Use Caching in UI Automation</span></span>](use-caching-in-ui-automation.md)
