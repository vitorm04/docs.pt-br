---
title: 'Implementando o padrão de controle GridItem de interface de usuário '
ms.date: 03/30/2017
helpviewer_keywords:
- control patterns, GridItem
- UI Automation GridItem control pattern
- GridItem control pattern
ms.assetid: bffbae08-fe2a-42fd-ab84-f37187518916
ms.openlocfilehash: 932eb0af6afbe958695d5c084d2cb0c0bc188830
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59176612"
---
# <a name="implementing-the-ui-automation-griditem-control-pattern"></a><span data-ttu-id="32480-102">Implementando o padrão de controle GridItem de interface de usuário </span><span class="sxs-lookup"><span data-stu-id="32480-102">Implementing the UI Automation GridItem Control Pattern</span></span>
> [!NOTE]
>  <span data-ttu-id="32480-103">Esta documentação destina-se a desenvolvedores do .NET Framework que querem usar as classes da [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] gerenciadas definidas no namespace <xref:System.Windows.Automation>.</span><span class="sxs-lookup"><span data-stu-id="32480-103">This documentation is intended for .NET Framework developers who want to use the managed [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] classes defined in the <xref:System.Windows.Automation> namespace.</span></span> <span data-ttu-id="32480-104">Para obter as informações mais recentes sobre [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], consulte [Windows Automation API: Automação de interface do usuário](https://go.microsoft.com/fwlink/?LinkID=156746).</span><span class="sxs-lookup"><span data-stu-id="32480-104">For the latest information about [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], see [Windows Automation API: UI Automation](https://go.microsoft.com/fwlink/?LinkID=156746).</span></span>  
  
 <span data-ttu-id="32480-105">Este tópico apresenta diretrizes e convenções para implementar <xref:System.Windows.Automation.Provider.IGridItemProvider>, incluindo informações sobre as propriedades.</span><span class="sxs-lookup"><span data-stu-id="32480-105">This topic introduces guidelines and conventions for implementing <xref:System.Windows.Automation.Provider.IGridItemProvider>, including information about properties.</span></span> <span data-ttu-id="32480-106">Links para referências adicionais são listadas no final da visão geral.</span><span class="sxs-lookup"><span data-stu-id="32480-106">Links to additional references are listed at the end of the overview.</span></span>  
  
 <span data-ttu-id="32480-107">O <xref:System.Windows.Automation.GridItemPattern> padrão de controle é usado para dar suporte a controles filhos individuais de contêineres que implementam <xref:System.Windows.Automation.Provider.IGridProvider>.</span><span class="sxs-lookup"><span data-stu-id="32480-107">The <xref:System.Windows.Automation.GridItemPattern> control pattern is used to support individual child controls of containers that implement <xref:System.Windows.Automation.Provider.IGridProvider>.</span></span> <span data-ttu-id="32480-108">Para obter exemplos de controles que implementam esse padrão de controle, consulte [mapeamento de padrão de controle para clientes de automação de interface do usuário](../../../docs/framework/ui-automation/control-pattern-mapping-for-ui-automation-clients.md).</span><span class="sxs-lookup"><span data-stu-id="32480-108">For examples of controls that implement this control pattern, see [Control Pattern Mapping for UI Automation Clients](../../../docs/framework/ui-automation/control-pattern-mapping-for-ui-automation-clients.md).</span></span>  
  
<a name="Implementation_Guidelines_and_Conventions"></a>   
## <a name="implementation-guidelines-and-conventions"></a><span data-ttu-id="32480-109">As convenções e diretrizes de implementação</span><span class="sxs-lookup"><span data-stu-id="32480-109">Implementation Guidelines and Conventions</span></span>  
 <span data-ttu-id="32480-110">Ao implementar <xref:System.Windows.Automation.Provider.IGridProvider>, observe as seguintes diretrizes e convenções:</span><span class="sxs-lookup"><span data-stu-id="32480-110">When implementing <xref:System.Windows.Automation.Provider.IGridProvider>, note the following guidelines and conventions:</span></span>  
  
-   <span data-ttu-id="32480-111">Coordenadas de grade são baseadas em zero com a célula superior esquerda tendo as coordenadas (0, 0).</span><span class="sxs-lookup"><span data-stu-id="32480-111">Grid coordinates are zero-based with the upper left cell having coordinates (0, 0).</span></span>  
  
-   <span data-ttu-id="32480-112">As células mescladas relatará suas <xref:System.Windows.Automation.Provider.IGridItemProvider.Row%2A> e <xref:System.Windows.Automation.Provider.IGridItemProvider.Column%2A> propriedades com base em suas células âncoras subjacentes, conforme definido pelo provedor de automação de interface do usuário.</span><span class="sxs-lookup"><span data-stu-id="32480-112">Merged cells will report their <xref:System.Windows.Automation.Provider.IGridItemProvider.Row%2A> and <xref:System.Windows.Automation.Provider.IGridItemProvider.Column%2A> properties based on their underlying anchor cell as defined by the UI Automation provider.</span></span> <span data-ttu-id="32480-113">Normalmente, ele será a mais à esquerda e superior de linha ou coluna.</span><span class="sxs-lookup"><span data-stu-id="32480-113">Typically, it will be the topmost and leftmost row or column.</span></span>  
  
-   <xref:System.Windows.Automation.Provider.IGridItemProvider> <span data-ttu-id="32480-114">não fornece para manipulação ativa da grade como mesclar ou dividir células.</span><span class="sxs-lookup"><span data-stu-id="32480-114">does not provide for active manipulation of the grid such as merging or splitting cells.</span></span>  
  
-   <span data-ttu-id="32480-115">Controles que implementam <xref:System.Windows.Automation.Provider.IGridItemProvider> normalmente pode ser percorrido (isto é, um cliente de automação de interface do usuário pode mover para os controles adjacentes) usando o teclado.</span><span class="sxs-lookup"><span data-stu-id="32480-115">Controls that implement <xref:System.Windows.Automation.Provider.IGridItemProvider> can typically be traversed (that is, a UI Automation client can move to adjacent controls) by using the keyboard.</span></span>  
  
<a name="Required_Members_for_IGridItemProvider"></a>   
## <a name="required-members-for-igriditemprovider"></a><span data-ttu-id="32480-116">Membros necessários para IGridItemProvider</span><span class="sxs-lookup"><span data-stu-id="32480-116">Required Members for IGridItemProvider</span></span>  
 <span data-ttu-id="32480-117">As propriedades e métodos a seguir são necessários para implementar <xref:System.Windows.Automation.Provider.IGridItemProvider>.</span><span class="sxs-lookup"><span data-stu-id="32480-117">The following properties and methods are required for implementing <xref:System.Windows.Automation.Provider.IGridItemProvider>.</span></span>  
  
|<span data-ttu-id="32480-118">Membros necessários</span><span class="sxs-lookup"><span data-stu-id="32480-118">Required members</span></span>|<span data-ttu-id="32480-119">Tipo de membro</span><span class="sxs-lookup"><span data-stu-id="32480-119">Member type</span></span>|<span data-ttu-id="32480-120">Observações</span><span class="sxs-lookup"><span data-stu-id="32480-120">Notes</span></span>|  
|----------------------|-----------------|-----------|  
|<xref:System.Windows.Automation.Provider.IGridItemProvider.Row%2A>|<span data-ttu-id="32480-121">Propriedade</span><span class="sxs-lookup"><span data-stu-id="32480-121">Property</span></span>|<span data-ttu-id="32480-122">Nenhum</span><span class="sxs-lookup"><span data-stu-id="32480-122">None</span></span>|  
|<xref:System.Windows.Automation.Provider.IGridItemProvider.Column%2A>|<span data-ttu-id="32480-123">Propriedade</span><span class="sxs-lookup"><span data-stu-id="32480-123">Property</span></span>|<span data-ttu-id="32480-124">Nenhum</span><span class="sxs-lookup"><span data-stu-id="32480-124">None</span></span>|  
|<xref:System.Windows.Automation.Provider.IGridItemProvider.RowSpan%2A>|<span data-ttu-id="32480-125">Propriedade</span><span class="sxs-lookup"><span data-stu-id="32480-125">Property</span></span>|<span data-ttu-id="32480-126">Nenhum</span><span class="sxs-lookup"><span data-stu-id="32480-126">None</span></span>|  
|<xref:System.Windows.Automation.Provider.IGridItemProvider.ColumnSpan%2A>|<span data-ttu-id="32480-127">Propriedade</span><span class="sxs-lookup"><span data-stu-id="32480-127">Property</span></span>|<span data-ttu-id="32480-128">Nenhum</span><span class="sxs-lookup"><span data-stu-id="32480-128">None</span></span>|  
|<xref:System.Windows.Automation.Provider.IGridItemProvider.ContainingGrid%2A>|<span data-ttu-id="32480-129">Propriedade</span><span class="sxs-lookup"><span data-stu-id="32480-129">Property</span></span>|<span data-ttu-id="32480-130">Nenhum</span><span class="sxs-lookup"><span data-stu-id="32480-130">None</span></span>|  
  
 <span data-ttu-id="32480-131">Esse padrão de controle não tem métodos associados ou eventos.</span><span class="sxs-lookup"><span data-stu-id="32480-131">This control pattern has no associated methods or events.</span></span>  
  
<a name="Exceptions"></a>   
## <a name="exceptions"></a><span data-ttu-id="32480-132">Exceções</span><span class="sxs-lookup"><span data-stu-id="32480-132">Exceptions</span></span>  
 <span data-ttu-id="32480-133">Esse padrão de controle não tem exceção associada.</span><span class="sxs-lookup"><span data-stu-id="32480-133">This control pattern has no associated exceptions.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="32480-134">Consulte também</span><span class="sxs-lookup"><span data-stu-id="32480-134">See also</span></span>

- [<span data-ttu-id="32480-135">Visão Geral de Padrões de Controle de Automação de Interface de Usuário</span><span class="sxs-lookup"><span data-stu-id="32480-135">UI Automation Control Patterns Overview</span></span>](../../../docs/framework/ui-automation/ui-automation-control-patterns-overview.md)
- [<span data-ttu-id="32480-136">Padrões de controle de suporte em um provedor de automação da interface do usuário</span><span class="sxs-lookup"><span data-stu-id="32480-136">Support Control Patterns in a UI Automation Provider</span></span>](../../../docs/framework/ui-automation/support-control-patterns-in-a-ui-automation-provider.md)
- [<span data-ttu-id="32480-137">Padrões de Controle para Clientes de Automação de IU</span><span class="sxs-lookup"><span data-stu-id="32480-137">UI Automation Control Patterns for Clients</span></span>](../../../docs/framework/ui-automation/ui-automation-control-patterns-for-clients.md)
- [<span data-ttu-id="32480-138">Implementando o Padrão de Controle Grid de Automação de Interface de Usuário</span><span class="sxs-lookup"><span data-stu-id="32480-138">Implementing the UI Automation Grid Control Pattern</span></span>](../../../docs/framework/ui-automation/implementing-the-ui-automation-grid-control-pattern.md)
- [<span data-ttu-id="32480-139">Visão geral da árvore de automação de interface do usuário</span><span class="sxs-lookup"><span data-stu-id="32480-139">UI Automation Tree Overview</span></span>](../../../docs/framework/ui-automation/ui-automation-tree-overview.md)
- [<span data-ttu-id="32480-140">Usar armazenamento em cache em automação de interface do usuário</span><span class="sxs-lookup"><span data-stu-id="32480-140">Use Caching in UI Automation</span></span>](../../../docs/framework/ui-automation/use-caching-in-ui-automation.md)
