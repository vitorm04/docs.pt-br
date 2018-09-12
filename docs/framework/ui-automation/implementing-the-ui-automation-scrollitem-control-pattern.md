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
manager: markl
ms.openlocfilehash: 0346b70b4400c5f7a8d282d945e029701973dad1
ms.sourcegitcommit: 8c2ece71e54f46aef9a2153540d0bda7e74b19a9
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/12/2018
ms.locfileid: "44514391"
---
# <a name="implementing-the-ui-automation-scrollitem-control-pattern"></a><span data-ttu-id="1d8e7-102">Implementando o padrão de controle ScrollItem de interface de usuário</span><span class="sxs-lookup"><span data-stu-id="1d8e7-102">Implementing the UI Automation ScrollItem Control Pattern</span></span>
> [!NOTE]
>  <span data-ttu-id="1d8e7-103">Esta documentação destina-se a desenvolvedores do .NET Framework que querem usar as classes da [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] gerenciadas definidas no namespace <xref:System.Windows.Automation>.</span><span class="sxs-lookup"><span data-stu-id="1d8e7-103">This documentation is intended for .NET Framework developers who want to use the managed [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] classes defined in the <xref:System.Windows.Automation> namespace.</span></span> <span data-ttu-id="1d8e7-104">Para obter as informações mais recentes sobre a [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], consulte [Windows Automation API: UI Automation](https://go.microsoft.com/fwlink/?LinkID=156746) (API de Automação do Windows: Automação da Interface do Usuário).</span><span class="sxs-lookup"><span data-stu-id="1d8e7-104">For the latest information about [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], see [Windows Automation API: UI Automation](https://go.microsoft.com/fwlink/?LinkID=156746).</span></span>  
  
 <span data-ttu-id="1d8e7-105">Este tópico apresenta diretrizes e convenções para implementar o <xref:System.Windows.Automation.Provider.IScrollItemProvider>, incluindo informações sobre propriedades, métodos e eventos.</span><span class="sxs-lookup"><span data-stu-id="1d8e7-105">This topic introduces guidelines and conventions for implementing the <xref:System.Windows.Automation.Provider.IScrollItemProvider>, including information about properties, methods, and events.</span></span> <span data-ttu-id="1d8e7-106">Links para referências adicionais são listadas no final do tópico.</span><span class="sxs-lookup"><span data-stu-id="1d8e7-106">Links to additional references are listed at the end of the topic.</span></span>  
  
 <span data-ttu-id="1d8e7-107">O <xref:System.Windows.Automation.ScrollItemPattern> padrão de controle é usado para dar suporte a controles filhos individuais de contêineres que implementam <xref:System.Windows.Automation.Provider.IScrollProvider>.</span><span class="sxs-lookup"><span data-stu-id="1d8e7-107">The <xref:System.Windows.Automation.ScrollItemPattern> control pattern is used to support individual child controls of containers that implement <xref:System.Windows.Automation.Provider.IScrollProvider>.</span></span> <span data-ttu-id="1d8e7-108">Esse padrão de controle atua como um canal de comunicação entre um controle filho e seu recipiente para garantir que o contêiner pode alterar o conteúdo visível no momento (ou região) no seu viewport para exibir o controle filho.</span><span class="sxs-lookup"><span data-stu-id="1d8e7-108">This control pattern acts as a communication channel between a child control and its container to ensure that the container can change the currently visible content (or region) within its viewport to display the child control.</span></span> <span data-ttu-id="1d8e7-109">Para obter exemplos de controles que implementam esse padrão de controle, consulte [mapeamento de padrão de controle para clientes de automação de interface do usuário](../../../docs/framework/ui-automation/control-pattern-mapping-for-ui-automation-clients.md).</span><span class="sxs-lookup"><span data-stu-id="1d8e7-109">For examples of controls that implement this control pattern, see [Control Pattern Mapping for UI Automation Clients](../../../docs/framework/ui-automation/control-pattern-mapping-for-ui-automation-clients.md).</span></span>  
  
<a name="Implementation_Guidelines_and_Conventions"></a>   
## <a name="implementation-guidelines-and-conventions"></a><span data-ttu-id="1d8e7-110">As convenções e diretrizes de implementação</span><span class="sxs-lookup"><span data-stu-id="1d8e7-110">Implementation Guidelines and Conventions</span></span>  
 <span data-ttu-id="1d8e7-111">Ao implementar o padrão de controle de Item de rolagem, observe as seguintes diretrizes e convenções:</span><span class="sxs-lookup"><span data-stu-id="1d8e7-111">When implementing the Scroll Item control pattern, note the following guidelines and conventions:</span></span>  
  
-   <span data-ttu-id="1d8e7-112">Itens contidos em um controle de janela ou tela não são necessários para implementar a interface IScrollItemProvider.</span><span class="sxs-lookup"><span data-stu-id="1d8e7-112">Items contained within a Window or Canvas control are not required to implement the IScrollItemProvider interface.</span></span> <span data-ttu-id="1d8e7-113">Como alternativa, no entanto, eles devem expor um local válido para o <xref:System.Windows.Automation.AutomationElementIdentifiers.BoundingRectangleProperty>.</span><span class="sxs-lookup"><span data-stu-id="1d8e7-113">As an alternative, however, they must expose a valid location for the <xref:System.Windows.Automation.AutomationElementIdentifiers.BoundingRectangleProperty>.</span></span> <span data-ttu-id="1d8e7-114">Isso permitirá que um aplicativo de cliente de automação de interface do usuário para usar o <xref:System.Windows.Automation.ScrollPattern> controlar métodos padrão no contêiner para exibir o item filho.</span><span class="sxs-lookup"><span data-stu-id="1d8e7-114">This will allow a UI Automation client application to use the <xref:System.Windows.Automation.ScrollPattern> control pattern methods on the container to display the child item.</span></span>  
  
<a name="Required_Members_for_IScrollItemProvider"></a>   
## <a name="required-members-for-iscrollitemprovider"></a><span data-ttu-id="1d8e7-115">Membros necessários para IScrollItemProvider</span><span class="sxs-lookup"><span data-stu-id="1d8e7-115">Required Members for IScrollItemProvider</span></span>  
 <span data-ttu-id="1d8e7-116">O método a seguir é necessário para implementar a interface IScrollProvider.</span><span class="sxs-lookup"><span data-stu-id="1d8e7-116">The following method is required for implementing the IScrollProvider interface.</span></span>  
  
|<span data-ttu-id="1d8e7-117">Membros necessários</span><span class="sxs-lookup"><span data-stu-id="1d8e7-117">Required members</span></span>|<span data-ttu-id="1d8e7-118">Tipo de membro</span><span class="sxs-lookup"><span data-stu-id="1d8e7-118">Member type</span></span>|<span data-ttu-id="1d8e7-119">Observações</span><span class="sxs-lookup"><span data-stu-id="1d8e7-119">Notes</span></span>|  
|----------------------|-----------------|-----------|  
|<xref:System.Windows.Automation.Provider.IScrollItemProvider.ScrollIntoView%2A>|<span data-ttu-id="1d8e7-120">-Método</span><span class="sxs-lookup"><span data-stu-id="1d8e7-120">-   Method</span></span>|<span data-ttu-id="1d8e7-121">Nenhum</span><span class="sxs-lookup"><span data-stu-id="1d8e7-121">None</span></span>|  
  
 <span data-ttu-id="1d8e7-122">Esse padrão de controle não tem propriedades associadas ou eventos.</span><span class="sxs-lookup"><span data-stu-id="1d8e7-122">This control pattern has no associated properties or events.</span></span>  
  
<a name="Exceptions"></a>   
## <a name="exceptions"></a><span data-ttu-id="1d8e7-123">Exceções</span><span class="sxs-lookup"><span data-stu-id="1d8e7-123">Exceptions</span></span>  
 <span data-ttu-id="1d8e7-124">Provedores devem lançar as exceções a seguir.</span><span class="sxs-lookup"><span data-stu-id="1d8e7-124">Providers must throw the following exceptions.</span></span>  
  
|<span data-ttu-id="1d8e7-125">Tipo de exceção</span><span class="sxs-lookup"><span data-stu-id="1d8e7-125">Exception Type</span></span>|<span data-ttu-id="1d8e7-126">Condição</span><span class="sxs-lookup"><span data-stu-id="1d8e7-126">Condition</span></span>|  
|--------------------|---------------|  
|<xref:System.InvalidOperationException>|<span data-ttu-id="1d8e7-127">Se um item não pode ser rolado para exibição:</span><span class="sxs-lookup"><span data-stu-id="1d8e7-127">If an item cannot be scrolled into view:</span></span><br /><br /> -   <xref:System.Windows.Automation.ScrollItemPattern.ScrollIntoView%2A>|  
  
## <a name="see-also"></a><span data-ttu-id="1d8e7-128">Consulte também</span><span class="sxs-lookup"><span data-stu-id="1d8e7-128">See Also</span></span>  
 [<span data-ttu-id="1d8e7-129">Visão geral de padrões de controle de automação da interface do usuário</span><span class="sxs-lookup"><span data-stu-id="1d8e7-129">UI Automation Control Patterns Overview</span></span>](../../../docs/framework/ui-automation/ui-automation-control-patterns-overview.md)  
 [<span data-ttu-id="1d8e7-130">Suporte a padrões de controle em um provedor de automação de interface do usuário</span><span class="sxs-lookup"><span data-stu-id="1d8e7-130">Support Control Patterns in a UI Automation Provider</span></span>](../../../docs/framework/ui-automation/support-control-patterns-in-a-ui-automation-provider.md)  
 [<span data-ttu-id="1d8e7-131">Padrões de controle de automação de interface do usuário para clientes</span><span class="sxs-lookup"><span data-stu-id="1d8e7-131">UI Automation Control Patterns for Clients</span></span>](../../../docs/framework/ui-automation/ui-automation-control-patterns-for-clients.md)  
 [<span data-ttu-id="1d8e7-132">Visão geral de árvore de automação de interface do usuário</span><span class="sxs-lookup"><span data-stu-id="1d8e7-132">UI Automation Tree Overview</span></span>](../../../docs/framework/ui-automation/ui-automation-tree-overview.md)  
 [<span data-ttu-id="1d8e7-133">Usar o cache em automação de interface do usuário</span><span class="sxs-lookup"><span data-stu-id="1d8e7-133">Use Caching in UI Automation</span></span>](../../../docs/framework/ui-automation/use-caching-in-ui-automation.md)
