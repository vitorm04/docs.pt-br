---
title: "Implementando o padrão de controle ScrollItem de interface de usuário "
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-bcl
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- control patterns, Scroll Item
- UI Automation, Scroll Item control pattern
- Scroll Item control pattern
ms.assetid: 903bab5c-80c1-44d7-bdc2-0a418893b987
caps.latest.revision: "16"
author: Xansky
ms.author: mhopkins
manager: markl
ms.workload: dotnet
ms.openlocfilehash: ef089e72c3b8dd089db5022ea1808cee98c27ecd
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="implementing-the-ui-automation-scrollitem-control-pattern"></a><span data-ttu-id="9de5d-102">Implementando o padrão de controle ScrollItem de interface de usuário</span><span class="sxs-lookup"><span data-stu-id="9de5d-102">Implementing the UI Automation ScrollItem Control Pattern</span></span>
> [!NOTE]
>  <span data-ttu-id="9de5d-103">Esta documentação destina-se a desenvolvedores do .NET Framework que querem usar as classes da [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] gerenciadas definidas no namespace <xref:System.Windows.Automation>.</span><span class="sxs-lookup"><span data-stu-id="9de5d-103">This documentation is intended for .NET Framework developers who want to use the managed [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] classes defined in the <xref:System.Windows.Automation> namespace.</span></span> <span data-ttu-id="9de5d-104">Para obter as informações mais recentes sobre a [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], consulte [Windows Automation API: UI Automation](http://go.microsoft.com/fwlink/?LinkID=156746) (API de Automação do Windows: Automação da Interface do Usuário).</span><span class="sxs-lookup"><span data-stu-id="9de5d-104">For the latest information about [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], see [Windows Automation API: UI Automation](http://go.microsoft.com/fwlink/?LinkID=156746).</span></span>  
  
 <span data-ttu-id="9de5d-105">Este tópico apresenta diretrizes e convenções para implementar o <xref:System.Windows.Automation.Provider.IScrollItemProvider>, incluindo informações sobre propriedades, métodos e eventos.</span><span class="sxs-lookup"><span data-stu-id="9de5d-105">This topic introduces guidelines and conventions for implementing the <xref:System.Windows.Automation.Provider.IScrollItemProvider>, including information about properties, methods, and events.</span></span> <span data-ttu-id="9de5d-106">Links para referências adicionais são listadas no final do tópico.</span><span class="sxs-lookup"><span data-stu-id="9de5d-106">Links to additional references are listed at the end of the topic.</span></span>  
  
 <span data-ttu-id="9de5d-107">O <xref:System.Windows.Automation.ScrollItemPattern> padrão de controle é usado para suportar controles filhos individuais de contêiners que implementam <xref:System.Windows.Automation.Provider.IScrollProvider>.</span><span class="sxs-lookup"><span data-stu-id="9de5d-107">The <xref:System.Windows.Automation.ScrollItemPattern> control pattern is used to support individual child controls of containers that implement <xref:System.Windows.Automation.Provider.IScrollProvider>.</span></span> <span data-ttu-id="9de5d-108">Esse padrão de controle atua como um canal de comunicação entre um controle filho e seu recipiente para garantir que o recipiente pode mudar o conteúdo visível no momento (ou região) no seu viewport para exibir o controle filho.</span><span class="sxs-lookup"><span data-stu-id="9de5d-108">This control pattern acts as a communication channel between a child control and its container to ensure that the container can change the currently visible content (or region) within its viewport to display the child control.</span></span> <span data-ttu-id="9de5d-109">Para obter exemplos de controles que implementam este padrão de controle, consulte [mapeamento de padrão de controle para clientes de automação de interface do usuário](../../../docs/framework/ui-automation/control-pattern-mapping-for-ui-automation-clients.md).</span><span class="sxs-lookup"><span data-stu-id="9de5d-109">For examples of controls that implement this control pattern, see [Control Pattern Mapping for UI Automation Clients](../../../docs/framework/ui-automation/control-pattern-mapping-for-ui-automation-clients.md).</span></span>  
  
<a name="Implementation_Guidelines_and_Conventions"></a>   
## <a name="implementation-guidelines-and-conventions"></a><span data-ttu-id="9de5d-110">Convenções e diretrizes de implementação</span><span class="sxs-lookup"><span data-stu-id="9de5d-110">Implementation Guidelines and Conventions</span></span>  
 <span data-ttu-id="9de5d-111">Ao implementar o padrão de controle Item de rolagem, observe as seguintes diretrizes e convenções:</span><span class="sxs-lookup"><span data-stu-id="9de5d-111">When implementing the Scroll Item control pattern, note the following guidelines and conventions:</span></span>  
  
-   <span data-ttu-id="9de5d-112">Os itens contidos em um controle de janela ou tela não são necessários para implementar a interface IScrollItemProvider.</span><span class="sxs-lookup"><span data-stu-id="9de5d-112">Items contained within a Window or Canvas control are not required to implement the IScrollItemProvider interface.</span></span> <span data-ttu-id="9de5d-113">Como alternativa, no entanto, eles devem expor um local válido para o <xref:System.Windows.Automation.AutomationElementIdentifiers.BoundingRectangleProperty>.</span><span class="sxs-lookup"><span data-stu-id="9de5d-113">As an alternative, however, they must expose a valid location for the <xref:System.Windows.Automation.AutomationElementIdentifiers.BoundingRectangleProperty>.</span></span> <span data-ttu-id="9de5d-114">Isso permitirá que um aplicativo de cliente de automação de interface do usuário para usar o <xref:System.Windows.Automation.ScrollPattern> controlar os métodos padrão no contêiner para exibir o item filho.</span><span class="sxs-lookup"><span data-stu-id="9de5d-114">This will allow a UI Automation client application to use the <xref:System.Windows.Automation.ScrollPattern> control pattern methods on the container to display the child item.</span></span>  
  
<a name="Required_Members_for_IScrollItemProvider"></a>   
## <a name="required-members-for-iscrollitemprovider"></a><span data-ttu-id="9de5d-115">Membros necessários para IScrollItemProvider</span><span class="sxs-lookup"><span data-stu-id="9de5d-115">Required Members for IScrollItemProvider</span></span>  
 <span data-ttu-id="9de5d-116">O método a seguir é necessário para implementar a interface IScrollProvider.</span><span class="sxs-lookup"><span data-stu-id="9de5d-116">The following method is required for implementing the IScrollProvider interface.</span></span>  
  
|<span data-ttu-id="9de5d-117">Membros necessários</span><span class="sxs-lookup"><span data-stu-id="9de5d-117">Required members</span></span>|<span data-ttu-id="9de5d-118">Tipo de membro</span><span class="sxs-lookup"><span data-stu-id="9de5d-118">Member type</span></span>|<span data-ttu-id="9de5d-119">Observações</span><span class="sxs-lookup"><span data-stu-id="9de5d-119">Notes</span></span>|  
|----------------------|-----------------|-----------|  
|<xref:System.Windows.Automation.Provider.IScrollItemProvider.ScrollIntoView%2A>|<span data-ttu-id="9de5d-120">-Método</span><span class="sxs-lookup"><span data-stu-id="9de5d-120">-   Method</span></span>|<span data-ttu-id="9de5d-121">Nenhum</span><span class="sxs-lookup"><span data-stu-id="9de5d-121">None</span></span>|  
  
 <span data-ttu-id="9de5d-122">Esse padrão de controle não tem propriedades associadas ou eventos.</span><span class="sxs-lookup"><span data-stu-id="9de5d-122">This control pattern has no associated properties or events.</span></span>  
  
<a name="Exceptions"></a>   
## <a name="exceptions"></a><span data-ttu-id="9de5d-123">Exceções</span><span class="sxs-lookup"><span data-stu-id="9de5d-123">Exceptions</span></span>  
 <span data-ttu-id="9de5d-124">Provedores devem lançar as exceções a seguir.</span><span class="sxs-lookup"><span data-stu-id="9de5d-124">Providers must throw the following exceptions.</span></span>  
  
|<span data-ttu-id="9de5d-125">Tipo de exceção</span><span class="sxs-lookup"><span data-stu-id="9de5d-125">Exception Type</span></span>|<span data-ttu-id="9de5d-126">Condição</span><span class="sxs-lookup"><span data-stu-id="9de5d-126">Condition</span></span>|  
|--------------------|---------------|  
|<xref:System.InvalidOperationException>|<span data-ttu-id="9de5d-127">Se um item não pode ser rolado para a exibição:</span><span class="sxs-lookup"><span data-stu-id="9de5d-127">If an item cannot be scrolled into view:</span></span><br /><br /> -   <xref:System.Windows.Automation.ScrollItemPattern.ScrollIntoView%2A>|  
  
## <a name="see-also"></a><span data-ttu-id="9de5d-128">Consulte também</span><span class="sxs-lookup"><span data-stu-id="9de5d-128">See Also</span></span>  
 [<span data-ttu-id="9de5d-129">Visão geral de padrões de controle de automação da interface do usuário</span><span class="sxs-lookup"><span data-stu-id="9de5d-129">UI Automation Control Patterns Overview</span></span>](../../../docs/framework/ui-automation/ui-automation-control-patterns-overview.md)  
 [<span data-ttu-id="9de5d-130">Suporte a padrões de controle em um provedor de automação de interface do usuário</span><span class="sxs-lookup"><span data-stu-id="9de5d-130">Support Control Patterns in a UI Automation Provider</span></span>](../../../docs/framework/ui-automation/support-control-patterns-in-a-ui-automation-provider.md)  
 [<span data-ttu-id="9de5d-131">Padrões de controle de automação de interface do usuário para clientes</span><span class="sxs-lookup"><span data-stu-id="9de5d-131">UI Automation Control Patterns for Clients</span></span>](../../../docs/framework/ui-automation/ui-automation-control-patterns-for-clients.md)  
 [<span data-ttu-id="9de5d-132">Visão geral de árvore de automação de interface do usuário</span><span class="sxs-lookup"><span data-stu-id="9de5d-132">UI Automation Tree Overview</span></span>](../../../docs/framework/ui-automation/ui-automation-tree-overview.md)  
 [<span data-ttu-id="9de5d-133">Usar o cache em automação de interface do usuário</span><span class="sxs-lookup"><span data-stu-id="9de5d-133">Use Caching in UI Automation</span></span>](../../../docs/framework/ui-automation/use-caching-in-ui-automation.md)
