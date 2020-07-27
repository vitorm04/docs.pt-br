---
title: Implementando o padrão de controle GridItem de interface de usuário
description: Conheça as diretrizes e as convenções para implementar o padrão de controle GridItemPattern para itens de grade na automação da interface do usuário. Consulte membros necessários para IGridItemProvider.
ms.date: 03/30/2017
helpviewer_keywords:
- control patterns, GridItem
- UI Automation GridItem control pattern
- GridItem control pattern
ms.assetid: bffbae08-fe2a-42fd-ab84-f37187518916
ms.openlocfilehash: e0a0c616f3f0cf9bc091e4fbb496d71ab8550bd3
ms.sourcegitcommit: 87cfeb69226fef01acb17c56c86f978f4f4a13db
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/24/2020
ms.locfileid: "87165820"
---
# <a name="implementing-the-ui-automation-griditem-control-pattern"></a><span data-ttu-id="a9de7-104">Implementando o padrão de controle GridItem de interface de usuário</span><span class="sxs-lookup"><span data-stu-id="a9de7-104">Implementing the UI Automation GridItem Control Pattern</span></span>
> [!NOTE]
> <span data-ttu-id="a9de7-105">Esta documentação destina-se a desenvolvedores do .NET Framework que querem usar as classes da [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] gerenciadas definidas no namespace <xref:System.Windows.Automation>.</span><span class="sxs-lookup"><span data-stu-id="a9de7-105">This documentation is intended for .NET Framework developers who want to use the managed [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] classes defined in the <xref:System.Windows.Automation> namespace.</span></span> <span data-ttu-id="a9de7-106">Para obter as informações mais recentes sobre a [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], consulte [Windows Automation API: UI Automation](/windows/win32/winauto/entry-uiauto-win32) (API de Automação do Windows: Automação da Interface do Usuário).</span><span class="sxs-lookup"><span data-stu-id="a9de7-106">For the latest information about [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], see [Windows Automation API: UI Automation](/windows/win32/winauto/entry-uiauto-win32).</span></span>  
  
 <span data-ttu-id="a9de7-107">Este tópico apresenta diretrizes e convenções para implementação <xref:System.Windows.Automation.Provider.IGridItemProvider> , incluindo informações sobre propriedades.</span><span class="sxs-lookup"><span data-stu-id="a9de7-107">This topic introduces guidelines and conventions for implementing <xref:System.Windows.Automation.Provider.IGridItemProvider>, including information about properties.</span></span> <span data-ttu-id="a9de7-108">Links para referências adicionais são listados no final da visão geral.</span><span class="sxs-lookup"><span data-stu-id="a9de7-108">Links to additional references are listed at the end of the overview.</span></span>  
  
 <span data-ttu-id="a9de7-109">O <xref:System.Windows.Automation.GridItemPattern> padrão de controle é usado para dar suporte a controles filho individuais de contêineres que implementam <xref:System.Windows.Automation.Provider.IGridProvider> .</span><span class="sxs-lookup"><span data-stu-id="a9de7-109">The <xref:System.Windows.Automation.GridItemPattern> control pattern is used to support individual child controls of containers that implement <xref:System.Windows.Automation.Provider.IGridProvider>.</span></span> <span data-ttu-id="a9de7-110">Para obter exemplos de controles que implementam esse padrão de controle, consulte [mapeamento de padrão de controle para clientes de automação da interface do usuário](control-pattern-mapping-for-ui-automation-clients.md).</span><span class="sxs-lookup"><span data-stu-id="a9de7-110">For examples of controls that implement this control pattern, see [Control Pattern Mapping for UI Automation Clients](control-pattern-mapping-for-ui-automation-clients.md).</span></span>  
  
<a name="Implementation_Guidelines_and_Conventions"></a>
## <a name="implementation-guidelines-and-conventions"></a><span data-ttu-id="a9de7-111">Diretrizes e convenções de implementação</span><span class="sxs-lookup"><span data-stu-id="a9de7-111">Implementation Guidelines and Conventions</span></span>  
 <span data-ttu-id="a9de7-112">Ao implementar <xref:System.Windows.Automation.Provider.IGridProvider> , observe as seguintes diretrizes e convenções:</span><span class="sxs-lookup"><span data-stu-id="a9de7-112">When implementing <xref:System.Windows.Automation.Provider.IGridProvider>, note the following guidelines and conventions:</span></span>  
  
- <span data-ttu-id="a9de7-113">As coordenadas de grade são baseadas em zero com a célula superior esquerda com coordenadas (0, 0).</span><span class="sxs-lookup"><span data-stu-id="a9de7-113">Grid coordinates are zero-based with the upper left cell having coordinates (0, 0).</span></span>  
  
- <span data-ttu-id="a9de7-114">As células mescladas relatarão suas <xref:System.Windows.Automation.Provider.IGridItemProvider.Row%2A> <xref:System.Windows.Automation.Provider.IGridItemProvider.Column%2A> Propriedades e com base em sua célula de âncora subjacente, conforme definido pelo provedor de automação de interface do usuário.</span><span class="sxs-lookup"><span data-stu-id="a9de7-114">Merged cells will report their <xref:System.Windows.Automation.Provider.IGridItemProvider.Row%2A> and <xref:System.Windows.Automation.Provider.IGridItemProvider.Column%2A> properties based on their underlying anchor cell as defined by the UI Automation provider.</span></span> <span data-ttu-id="a9de7-115">Normalmente, será a linha ou coluna mais alta e mais à esquerda.</span><span class="sxs-lookup"><span data-stu-id="a9de7-115">Typically, it will be the topmost and leftmost row or column.</span></span>  
  
- <span data-ttu-id="a9de7-116"><xref:System.Windows.Automation.Provider.IGridItemProvider>não fornece manipulação ativa da grade, como mesclagem ou divisão de células.</span><span class="sxs-lookup"><span data-stu-id="a9de7-116"><xref:System.Windows.Automation.Provider.IGridItemProvider> does not provide for active manipulation of the grid such as merging or splitting cells.</span></span>  
  
- <span data-ttu-id="a9de7-117">Os controles que implementam <xref:System.Windows.Automation.Provider.IGridItemProvider> normalmente podem ser percorridos (ou seja, um cliente de automação da interface do usuário pode mover para controles adjacentes) usando o teclado.</span><span class="sxs-lookup"><span data-stu-id="a9de7-117">Controls that implement <xref:System.Windows.Automation.Provider.IGridItemProvider> can typically be traversed (that is, a UI Automation client can move to adjacent controls) by using the keyboard.</span></span>  
  
<a name="Required_Members_for_IGridItemProvider"></a>
## <a name="required-members-for-igriditemprovider"></a><span data-ttu-id="a9de7-118">Membros necessários para IGridItemProvider</span><span class="sxs-lookup"><span data-stu-id="a9de7-118">Required Members for IGridItemProvider</span></span>  
 <span data-ttu-id="a9de7-119">As propriedades e os métodos a seguir são necessários para implementar o <xref:System.Windows.Automation.Provider.IGridItemProvider> .</span><span class="sxs-lookup"><span data-stu-id="a9de7-119">The following properties and methods are required for implementing <xref:System.Windows.Automation.Provider.IGridItemProvider>.</span></span>  
  
|<span data-ttu-id="a9de7-120">Membros necessários</span><span class="sxs-lookup"><span data-stu-id="a9de7-120">Required members</span></span>|<span data-ttu-id="a9de7-121">Tipo de membro</span><span class="sxs-lookup"><span data-stu-id="a9de7-121">Member type</span></span>|<span data-ttu-id="a9de7-122">Observações</span><span class="sxs-lookup"><span data-stu-id="a9de7-122">Notes</span></span>|  
|----------------------|-----------------|-----------|  
|<xref:System.Windows.Automation.Provider.IGridItemProvider.Row%2A>|<span data-ttu-id="a9de7-123">Propriedade</span><span class="sxs-lookup"><span data-stu-id="a9de7-123">Property</span></span>|<span data-ttu-id="a9de7-124">Nenhum</span><span class="sxs-lookup"><span data-stu-id="a9de7-124">None</span></span>|  
|<xref:System.Windows.Automation.Provider.IGridItemProvider.Column%2A>|<span data-ttu-id="a9de7-125">Propriedade</span><span class="sxs-lookup"><span data-stu-id="a9de7-125">Property</span></span>|<span data-ttu-id="a9de7-126">Nenhum</span><span class="sxs-lookup"><span data-stu-id="a9de7-126">None</span></span>|  
|<xref:System.Windows.Automation.Provider.IGridItemProvider.RowSpan%2A>|<span data-ttu-id="a9de7-127">Propriedade</span><span class="sxs-lookup"><span data-stu-id="a9de7-127">Property</span></span>|<span data-ttu-id="a9de7-128">Nenhum</span><span class="sxs-lookup"><span data-stu-id="a9de7-128">None</span></span>|  
|<xref:System.Windows.Automation.Provider.IGridItemProvider.ColumnSpan%2A>|<span data-ttu-id="a9de7-129">Propriedade</span><span class="sxs-lookup"><span data-stu-id="a9de7-129">Property</span></span>|<span data-ttu-id="a9de7-130">Nenhum</span><span class="sxs-lookup"><span data-stu-id="a9de7-130">None</span></span>|  
|<xref:System.Windows.Automation.Provider.IGridItemProvider.ContainingGrid%2A>|<span data-ttu-id="a9de7-131">Propriedade</span><span class="sxs-lookup"><span data-stu-id="a9de7-131">Property</span></span>|<span data-ttu-id="a9de7-132">Nenhum</span><span class="sxs-lookup"><span data-stu-id="a9de7-132">None</span></span>|  
  
 <span data-ttu-id="a9de7-133">Este padrão de controle não tem nenhum método ou evento associado.</span><span class="sxs-lookup"><span data-stu-id="a9de7-133">This control pattern has no associated methods or events.</span></span>  
  
<a name="Exceptions"></a>
## <a name="exceptions"></a><span data-ttu-id="a9de7-134">Exceções</span><span class="sxs-lookup"><span data-stu-id="a9de7-134">Exceptions</span></span>  
 <span data-ttu-id="a9de7-135">Este padrão de controle não tem nenhuma exceção associada.</span><span class="sxs-lookup"><span data-stu-id="a9de7-135">This control pattern has no associated exceptions.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a9de7-136">Confira também</span><span class="sxs-lookup"><span data-stu-id="a9de7-136">See also</span></span>

- [<span data-ttu-id="a9de7-137">Visão Geral de Padrões de Controle de Automação de Interface de Usuário</span><span class="sxs-lookup"><span data-stu-id="a9de7-137">UI Automation Control Patterns Overview</span></span>](ui-automation-control-patterns-overview.md)
- [<span data-ttu-id="a9de7-138">Padrões de controle de suporte em um provedor de automação da interface do usuário</span><span class="sxs-lookup"><span data-stu-id="a9de7-138">Support Control Patterns in a UI Automation Provider</span></span>](support-control-patterns-in-a-ui-automation-provider.md)
- [<span data-ttu-id="a9de7-139">Padrões de Controle para Clientes de Automação de IU</span><span class="sxs-lookup"><span data-stu-id="a9de7-139">UI Automation Control Patterns for Clients</span></span>](ui-automation-control-patterns-for-clients.md)
- [<span data-ttu-id="a9de7-140">Implementando o Padrão de Controle Grid de Automação de Interface de Usuário</span><span class="sxs-lookup"><span data-stu-id="a9de7-140">Implementing the UI Automation Grid Control Pattern</span></span>](implementing-the-ui-automation-grid-control-pattern.md)
- [<span data-ttu-id="a9de7-141">Visão geral da árvore de automação de interface do usuário</span><span class="sxs-lookup"><span data-stu-id="a9de7-141">UI Automation Tree Overview</span></span>](ui-automation-tree-overview.md)
- [<span data-ttu-id="a9de7-142">Usar armazenamento em cache em automação de interface do usuário</span><span class="sxs-lookup"><span data-stu-id="a9de7-142">Use Caching in UI Automation</span></span>](use-caching-in-ui-automation.md)
