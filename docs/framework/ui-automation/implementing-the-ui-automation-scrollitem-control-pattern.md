---
title: Implementando o padrão de controle ScrollItem de interface de usuário
description: Examine as diretrizes e convenções para implementar o padrão de controle ScrollItem na automação da interface do usuário. Consulte membros necessários para a interface IScrollItemProvider.
ms.date: 03/30/2017
helpviewer_keywords:
- control patterns, Scroll Item
- UI Automation, Scroll Item control pattern
- Scroll Item control pattern
ms.assetid: 903bab5c-80c1-44d7-bdc2-0a418893b987
ms.openlocfilehash: a548eb25280d9a8feddc4633a1ba3e7dc022af36
ms.sourcegitcommit: 87cfeb69226fef01acb17c56c86f978f4f4a13db
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/24/2020
ms.locfileid: "87163567"
---
# <a name="implementing-the-ui-automation-scrollitem-control-pattern"></a><span data-ttu-id="a3541-104">Implementando o padrão de controle ScrollItem de interface de usuário</span><span class="sxs-lookup"><span data-stu-id="a3541-104">Implementing the UI Automation ScrollItem Control Pattern</span></span>
> [!NOTE]
> <span data-ttu-id="a3541-105">Esta documentação destina-se a desenvolvedores do .NET Framework que querem usar as classes da [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] gerenciadas definidas no namespace <xref:System.Windows.Automation>.</span><span class="sxs-lookup"><span data-stu-id="a3541-105">This documentation is intended for .NET Framework developers who want to use the managed [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] classes defined in the <xref:System.Windows.Automation> namespace.</span></span> <span data-ttu-id="a3541-106">Para obter as informações mais recentes sobre a [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], consulte [Windows Automation API: UI Automation](/windows/win32/winauto/entry-uiauto-win32) (API de Automação do Windows: Automação da Interface do Usuário).</span><span class="sxs-lookup"><span data-stu-id="a3541-106">For the latest information about [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], see [Windows Automation API: UI Automation](/windows/win32/winauto/entry-uiauto-win32).</span></span>  
  
 <span data-ttu-id="a3541-107">Este tópico apresenta diretrizes e convenções para implementar o <xref:System.Windows.Automation.Provider.IScrollItemProvider> , incluindo informações sobre propriedades, métodos e eventos.</span><span class="sxs-lookup"><span data-stu-id="a3541-107">This topic introduces guidelines and conventions for implementing the <xref:System.Windows.Automation.Provider.IScrollItemProvider>, including information about properties, methods, and events.</span></span> <span data-ttu-id="a3541-108">Links para referências adicionais são listados no final do tópico.</span><span class="sxs-lookup"><span data-stu-id="a3541-108">Links to additional references are listed at the end of the topic.</span></span>  
  
 <span data-ttu-id="a3541-109">O <xref:System.Windows.Automation.ScrollItemPattern> padrão de controle é usado para dar suporte a controles filho individuais de contêineres que implementam <xref:System.Windows.Automation.Provider.IScrollProvider> .</span><span class="sxs-lookup"><span data-stu-id="a3541-109">The <xref:System.Windows.Automation.ScrollItemPattern> control pattern is used to support individual child controls of containers that implement <xref:System.Windows.Automation.Provider.IScrollProvider>.</span></span> <span data-ttu-id="a3541-110">Esse padrão de controle atua como um canal de comunicação entre um controle filho e seu contêiner para garantir que o contêiner possa alterar o conteúdo visível no momento (ou região) dentro de seu visor para exibir o controle filho.</span><span class="sxs-lookup"><span data-stu-id="a3541-110">This control pattern acts as a communication channel between a child control and its container to ensure that the container can change the currently visible content (or region) within its viewport to display the child control.</span></span> <span data-ttu-id="a3541-111">Para obter exemplos de controles que implementam esse padrão de controle, consulte [mapeamento de padrão de controle para clientes de automação da interface do usuário](control-pattern-mapping-for-ui-automation-clients.md).</span><span class="sxs-lookup"><span data-stu-id="a3541-111">For examples of controls that implement this control pattern, see [Control Pattern Mapping for UI Automation Clients](control-pattern-mapping-for-ui-automation-clients.md).</span></span>  
  
<a name="Implementation_Guidelines_and_Conventions"></a>
## <a name="implementation-guidelines-and-conventions"></a><span data-ttu-id="a3541-112">Diretrizes e convenções de implementação</span><span class="sxs-lookup"><span data-stu-id="a3541-112">Implementation Guidelines and Conventions</span></span>  
 <span data-ttu-id="a3541-113">Ao implementar o padrão de controle de item de rolagem, observe as seguintes diretrizes e convenções:</span><span class="sxs-lookup"><span data-stu-id="a3541-113">When implementing the Scroll Item control pattern, note the following guidelines and conventions:</span></span>  
  
- <span data-ttu-id="a3541-114">Os itens contidos em um controle de janela ou Canvas não são necessários para implementar a interface IScrollItemProvider.</span><span class="sxs-lookup"><span data-stu-id="a3541-114">Items contained within a Window or Canvas control are not required to implement the IScrollItemProvider interface.</span></span> <span data-ttu-id="a3541-115">No entanto, como alternativa, eles devem expor um local válido para o <xref:System.Windows.Automation.AutomationElementIdentifiers.BoundingRectangleProperty> .</span><span class="sxs-lookup"><span data-stu-id="a3541-115">As an alternative, however, they must expose a valid location for the <xref:System.Windows.Automation.AutomationElementIdentifiers.BoundingRectangleProperty>.</span></span> <span data-ttu-id="a3541-116">Isso permitirá que um aplicativo cliente de automação da interface do usuário use os <xref:System.Windows.Automation.ScrollPattern> métodos de padrão de controle no contêiner para exibir o item filho.</span><span class="sxs-lookup"><span data-stu-id="a3541-116">This will allow a UI Automation client application to use the <xref:System.Windows.Automation.ScrollPattern> control pattern methods on the container to display the child item.</span></span>  
  
<a name="Required_Members_for_IScrollItemProvider"></a>
## <a name="required-members-for-iscrollitemprovider"></a><span data-ttu-id="a3541-117">Membros necessários para IScrollItemProvider</span><span class="sxs-lookup"><span data-stu-id="a3541-117">Required Members for IScrollItemProvider</span></span>  
 <span data-ttu-id="a3541-118">O método a seguir é necessário para implementar a interface IScrollProvider.</span><span class="sxs-lookup"><span data-stu-id="a3541-118">The following method is required for implementing the IScrollProvider interface.</span></span>  
  
|<span data-ttu-id="a3541-119">Membros necessários</span><span class="sxs-lookup"><span data-stu-id="a3541-119">Required members</span></span>|<span data-ttu-id="a3541-120">Tipo de membro</span><span class="sxs-lookup"><span data-stu-id="a3541-120">Member type</span></span>|<span data-ttu-id="a3541-121">Observações</span><span class="sxs-lookup"><span data-stu-id="a3541-121">Notes</span></span>|  
|----------------------|-----------------|-----------|  
|<xref:System.Windows.Automation.Provider.IScrollItemProvider.ScrollIntoView%2A>|<span data-ttu-id="a3541-122">-Método</span><span class="sxs-lookup"><span data-stu-id="a3541-122">-   Method</span></span>|<span data-ttu-id="a3541-123">Nenhum</span><span class="sxs-lookup"><span data-stu-id="a3541-123">None</span></span>|  
  
 <span data-ttu-id="a3541-124">Este padrão de controle não tem propriedades ou eventos associados.</span><span class="sxs-lookup"><span data-stu-id="a3541-124">This control pattern has no associated properties or events.</span></span>  
  
<a name="Exceptions"></a>
## <a name="exceptions"></a><span data-ttu-id="a3541-125">Exceções</span><span class="sxs-lookup"><span data-stu-id="a3541-125">Exceptions</span></span>  
 <span data-ttu-id="a3541-126">Os provedores devem lançar as seguintes exceções.</span><span class="sxs-lookup"><span data-stu-id="a3541-126">Providers must throw the following exceptions.</span></span>  
  
|<span data-ttu-id="a3541-127">Tipo de exceção</span><span class="sxs-lookup"><span data-stu-id="a3541-127">Exception Type</span></span>|<span data-ttu-id="a3541-128">Condição</span><span class="sxs-lookup"><span data-stu-id="a3541-128">Condition</span></span>|  
|--------------------|---------------|  
|<xref:System.InvalidOperationException>|<span data-ttu-id="a3541-129">Se um item não puder ser rolado para a exibição:</span><span class="sxs-lookup"><span data-stu-id="a3541-129">If an item cannot be scrolled into view:</span></span><br /><br /> -   <xref:System.Windows.Automation.ScrollItemPattern.ScrollIntoView%2A>|  
  
## <a name="see-also"></a><span data-ttu-id="a3541-130">Confira também</span><span class="sxs-lookup"><span data-stu-id="a3541-130">See also</span></span>

- [<span data-ttu-id="a3541-131">Visão Geral de Padrões de Controle de Automação de Interface de Usuário</span><span class="sxs-lookup"><span data-stu-id="a3541-131">UI Automation Control Patterns Overview</span></span>](ui-automation-control-patterns-overview.md)
- [<span data-ttu-id="a3541-132">Padrões de controle de suporte em um provedor de automação da interface do usuário</span><span class="sxs-lookup"><span data-stu-id="a3541-132">Support Control Patterns in a UI Automation Provider</span></span>](support-control-patterns-in-a-ui-automation-provider.md)
- [<span data-ttu-id="a3541-133">Padrões de Controle para Clientes de Automação de IU</span><span class="sxs-lookup"><span data-stu-id="a3541-133">UI Automation Control Patterns for Clients</span></span>](ui-automation-control-patterns-for-clients.md)
- [<span data-ttu-id="a3541-134">Visão geral da árvore de automação de interface do usuário</span><span class="sxs-lookup"><span data-stu-id="a3541-134">UI Automation Tree Overview</span></span>](ui-automation-tree-overview.md)
- [<span data-ttu-id="a3541-135">Usar armazenamento em cache em automação de interface do usuário</span><span class="sxs-lookup"><span data-stu-id="a3541-135">Use Caching in UI Automation</span></span>](use-caching-in-ui-automation.md)
