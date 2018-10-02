---
title: 'Implementando o padrão de controle ScrollItem de interface de usuário '
ms.date: 03/30/2017
helpviewer_keywords:
- control patterns, Scroll Item
- UI Automation, Scroll Item control pattern
- Scroll Item control pattern
ms.assetid: 903bab5c-80c1-44d7-bdc2-0a418893b987
author: Xansky
ms.author: mhopkins
ms.openlocfilehash: 4c3dfc6eb42fef0c3464b49f7513425038d9091b
ms.sourcegitcommit: daa8788af67ac2d1cecd24f9f3409babb2f978c9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/01/2018
ms.locfileid: "47862758"
---
# <a name="implementing-the-ui-automation-scrollitem-control-pattern"></a><span data-ttu-id="966a3-102">Implementando o padrão de controle ScrollItem de interface de usuário</span><span class="sxs-lookup"><span data-stu-id="966a3-102">Implementing the UI Automation ScrollItem Control Pattern</span></span>
> [!NOTE]
>  <span data-ttu-id="966a3-103">Esta documentação destina-se a desenvolvedores do .NET Framework que querem usar as classes da [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] gerenciadas definidas no namespace <xref:System.Windows.Automation>.</span><span class="sxs-lookup"><span data-stu-id="966a3-103">This documentation is intended for .NET Framework developers who want to use the managed [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] classes defined in the <xref:System.Windows.Automation> namespace.</span></span> <span data-ttu-id="966a3-104">Para obter as informações mais recentes sobre a [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], consulte [Windows Automation API: UI Automation](https://go.microsoft.com/fwlink/?LinkID=156746) (API de Automação do Windows: Automação da Interface do Usuário).</span><span class="sxs-lookup"><span data-stu-id="966a3-104">For the latest information about [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], see [Windows Automation API: UI Automation](https://go.microsoft.com/fwlink/?LinkID=156746).</span></span>  
  
 <span data-ttu-id="966a3-105">Este tópico apresenta diretrizes e convenções para implementar o <xref:System.Windows.Automation.Provider.IScrollItemProvider>, incluindo informações sobre propriedades, métodos e eventos.</span><span class="sxs-lookup"><span data-stu-id="966a3-105">This topic introduces guidelines and conventions for implementing the <xref:System.Windows.Automation.Provider.IScrollItemProvider>, including information about properties, methods, and events.</span></span> <span data-ttu-id="966a3-106">Links para referências adicionais são listadas no final do tópico.</span><span class="sxs-lookup"><span data-stu-id="966a3-106">Links to additional references are listed at the end of the topic.</span></span>  
  
 <span data-ttu-id="966a3-107">O <xref:System.Windows.Automation.ScrollItemPattern> padrão de controle é usado para dar suporte a controles filhos individuais de contêineres que implementam <xref:System.Windows.Automation.Provider.IScrollProvider>.</span><span class="sxs-lookup"><span data-stu-id="966a3-107">The <xref:System.Windows.Automation.ScrollItemPattern> control pattern is used to support individual child controls of containers that implement <xref:System.Windows.Automation.Provider.IScrollProvider>.</span></span> <span data-ttu-id="966a3-108">Esse padrão de controle atua como um canal de comunicação entre um controle filho e seu recipiente para garantir que o contêiner pode alterar o conteúdo visível no momento (ou região) no seu viewport para exibir o controle filho.</span><span class="sxs-lookup"><span data-stu-id="966a3-108">This control pattern acts as a communication channel between a child control and its container to ensure that the container can change the currently visible content (or region) within its viewport to display the child control.</span></span> <span data-ttu-id="966a3-109">Para obter exemplos de controles que implementam esse padrão de controle, consulte [mapeamento de padrão de controle para clientes de automação de interface do usuário](../../../docs/framework/ui-automation/control-pattern-mapping-for-ui-automation-clients.md).</span><span class="sxs-lookup"><span data-stu-id="966a3-109">For examples of controls that implement this control pattern, see [Control Pattern Mapping for UI Automation Clients](../../../docs/framework/ui-automation/control-pattern-mapping-for-ui-automation-clients.md).</span></span>  
  
<a name="Implementation_Guidelines_and_Conventions"></a>   
## <a name="implementation-guidelines-and-conventions"></a><span data-ttu-id="966a3-110">As convenções e diretrizes de implementação</span><span class="sxs-lookup"><span data-stu-id="966a3-110">Implementation Guidelines and Conventions</span></span>  
 <span data-ttu-id="966a3-111">Ao implementar o padrão de controle de Item de rolagem, observe as seguintes diretrizes e convenções:</span><span class="sxs-lookup"><span data-stu-id="966a3-111">When implementing the Scroll Item control pattern, note the following guidelines and conventions:</span></span>  
  
-   <span data-ttu-id="966a3-112">Itens contidos em um controle de janela ou tela não são necessários para implementar a interface IScrollItemProvider.</span><span class="sxs-lookup"><span data-stu-id="966a3-112">Items contained within a Window or Canvas control are not required to implement the IScrollItemProvider interface.</span></span> <span data-ttu-id="966a3-113">Como alternativa, no entanto, eles devem expor um local válido para o <xref:System.Windows.Automation.AutomationElementIdentifiers.BoundingRectangleProperty>.</span><span class="sxs-lookup"><span data-stu-id="966a3-113">As an alternative, however, they must expose a valid location for the <xref:System.Windows.Automation.AutomationElementIdentifiers.BoundingRectangleProperty>.</span></span> <span data-ttu-id="966a3-114">Isso permitirá que um aplicativo de cliente de automação de interface do usuário para usar o <xref:System.Windows.Automation.ScrollPattern> controlar métodos padrão no contêiner para exibir o item filho.</span><span class="sxs-lookup"><span data-stu-id="966a3-114">This will allow a UI Automation client application to use the <xref:System.Windows.Automation.ScrollPattern> control pattern methods on the container to display the child item.</span></span>  
  
<a name="Required_Members_for_IScrollItemProvider"></a>   
## <a name="required-members-for-iscrollitemprovider"></a><span data-ttu-id="966a3-115">Membros necessários para IScrollItemProvider</span><span class="sxs-lookup"><span data-stu-id="966a3-115">Required Members for IScrollItemProvider</span></span>  
 <span data-ttu-id="966a3-116">O método a seguir é necessário para implementar a interface IScrollProvider.</span><span class="sxs-lookup"><span data-stu-id="966a3-116">The following method is required for implementing the IScrollProvider interface.</span></span>  
  
|<span data-ttu-id="966a3-117">Membros necessários</span><span class="sxs-lookup"><span data-stu-id="966a3-117">Required members</span></span>|<span data-ttu-id="966a3-118">Tipo de membro</span><span class="sxs-lookup"><span data-stu-id="966a3-118">Member type</span></span>|<span data-ttu-id="966a3-119">Observações</span><span class="sxs-lookup"><span data-stu-id="966a3-119">Notes</span></span>|  
|----------------------|-----------------|-----------|  
|<xref:System.Windows.Automation.Provider.IScrollItemProvider.ScrollIntoView%2A>|<span data-ttu-id="966a3-120">-Método</span><span class="sxs-lookup"><span data-stu-id="966a3-120">-   Method</span></span>|<span data-ttu-id="966a3-121">Nenhum</span><span class="sxs-lookup"><span data-stu-id="966a3-121">None</span></span>|  
  
 <span data-ttu-id="966a3-122">Esse padrão de controle não tem propriedades associadas ou eventos.</span><span class="sxs-lookup"><span data-stu-id="966a3-122">This control pattern has no associated properties or events.</span></span>  
  
<a name="Exceptions"></a>   
## <a name="exceptions"></a><span data-ttu-id="966a3-123">Exceções</span><span class="sxs-lookup"><span data-stu-id="966a3-123">Exceptions</span></span>  
 <span data-ttu-id="966a3-124">Provedores devem lançar as exceções a seguir.</span><span class="sxs-lookup"><span data-stu-id="966a3-124">Providers must throw the following exceptions.</span></span>  
  
|<span data-ttu-id="966a3-125">Tipo de exceção</span><span class="sxs-lookup"><span data-stu-id="966a3-125">Exception Type</span></span>|<span data-ttu-id="966a3-126">Condição</span><span class="sxs-lookup"><span data-stu-id="966a3-126">Condition</span></span>|  
|--------------------|---------------|  
|<xref:System.InvalidOperationException>|<span data-ttu-id="966a3-127">Se um item não pode ser rolado para exibição:</span><span class="sxs-lookup"><span data-stu-id="966a3-127">If an item cannot be scrolled into view:</span></span><br /><br /> -   <xref:System.Windows.Automation.ScrollItemPattern.ScrollIntoView%2A>|  
  
## <a name="see-also"></a><span data-ttu-id="966a3-128">Consulte também</span><span class="sxs-lookup"><span data-stu-id="966a3-128">See Also</span></span>  
 [<span data-ttu-id="966a3-129">Visão geral de padrões de controle de automação da interface do usuário</span><span class="sxs-lookup"><span data-stu-id="966a3-129">UI Automation Control Patterns Overview</span></span>](../../../docs/framework/ui-automation/ui-automation-control-patterns-overview.md)  
 [<span data-ttu-id="966a3-130">Suporte a padrões de controle em um provedor de automação de interface do usuário</span><span class="sxs-lookup"><span data-stu-id="966a3-130">Support Control Patterns in a UI Automation Provider</span></span>](../../../docs/framework/ui-automation/support-control-patterns-in-a-ui-automation-provider.md)  
 [<span data-ttu-id="966a3-131">Padrões de controle de automação de interface do usuário para clientes</span><span class="sxs-lookup"><span data-stu-id="966a3-131">UI Automation Control Patterns for Clients</span></span>](../../../docs/framework/ui-automation/ui-automation-control-patterns-for-clients.md)  
 [<span data-ttu-id="966a3-132">Visão geral de árvore de automação de interface do usuário</span><span class="sxs-lookup"><span data-stu-id="966a3-132">UI Automation Tree Overview</span></span>](../../../docs/framework/ui-automation/ui-automation-tree-overview.md)  
 [<span data-ttu-id="966a3-133">Usar o cache em automação de interface do usuário</span><span class="sxs-lookup"><span data-stu-id="966a3-133">Use Caching in UI Automation</span></span>](../../../docs/framework/ui-automation/use-caching-in-ui-automation.md)
