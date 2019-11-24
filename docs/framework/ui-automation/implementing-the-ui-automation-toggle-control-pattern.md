---
title: Implementando o padrão de controle Toggle de automação de interface de usuário
ms.date: 03/30/2017
helpviewer_keywords:
- Toggle control pattern
- control patterns, Toggle
- UI Automation, Toggle control pattern
ms.assetid: 3cfe875f-b0c0-413d-9703-5f14e6a1a30e
ms.openlocfilehash: c25f2d3b73e90adb3299ff8c4ff7c8a77fc5fc5e
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74447065"
---
# <a name="implementing-the-ui-automation-toggle-control-pattern"></a><span data-ttu-id="d5bb7-102">Implementando o padrão de controle Toggle de automação de interface de usuário</span><span class="sxs-lookup"><span data-stu-id="d5bb7-102">Implementing the UI Automation Toggle Control Pattern</span></span>
> [!NOTE]
> <span data-ttu-id="d5bb7-103">Esta documentação destina-se a desenvolvedores do .NET Framework que querem usar as classes da [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] gerenciadas definidas no namespace <xref:System.Windows.Automation>.</span><span class="sxs-lookup"><span data-stu-id="d5bb7-103">This documentation is intended for .NET Framework developers who want to use the managed [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] classes defined in the <xref:System.Windows.Automation> namespace.</span></span> <span data-ttu-id="d5bb7-104">Para obter as informações mais recentes sobre a [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], consulte [Windows Automation API: UI Automation](/windows/win32/winauto/entry-uiauto-win32) (API de Automação do Windows: Automação da Interface do Usuário).</span><span class="sxs-lookup"><span data-stu-id="d5bb7-104">For the latest information about [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], see [Windows Automation API: UI Automation](/windows/win32/winauto/entry-uiauto-win32).</span></span>  
  
 <span data-ttu-id="d5bb7-105">This topic introduces guidelines and conventions for implementing <xref:System.Windows.Automation.Provider.IToggleProvider>, including information about methods and properties.</span><span class="sxs-lookup"><span data-stu-id="d5bb7-105">This topic introduces guidelines and conventions for implementing <xref:System.Windows.Automation.Provider.IToggleProvider>, including information about methods and properties.</span></span> <span data-ttu-id="d5bb7-106">Links to additional references are listed at the end of the topic.</span><span class="sxs-lookup"><span data-stu-id="d5bb7-106">Links to additional references are listed at the end of the topic.</span></span>  
  
 <span data-ttu-id="d5bb7-107">The <xref:System.Windows.Automation.TogglePattern> control pattern is used to support controls that can cycle through a set of states and maintain a state once set.</span><span class="sxs-lookup"><span data-stu-id="d5bb7-107">The <xref:System.Windows.Automation.TogglePattern> control pattern is used to support controls that can cycle through a set of states and maintain a state once set.</span></span> <span data-ttu-id="d5bb7-108">For examples of controls that implement this control pattern, see [Control Pattern Mapping for UI Automation Clients](control-pattern-mapping-for-ui-automation-clients.md).</span><span class="sxs-lookup"><span data-stu-id="d5bb7-108">For examples of controls that implement this control pattern, see [Control Pattern Mapping for UI Automation Clients](control-pattern-mapping-for-ui-automation-clients.md).</span></span>  
  
<a name="Implementation_Guidelines_and_Conventions"></a>   
## <a name="implementation-guidelines-and-conventions"></a><span data-ttu-id="d5bb7-109">Implementation Guidelines and Conventions</span><span class="sxs-lookup"><span data-stu-id="d5bb7-109">Implementation Guidelines and Conventions</span></span>  
 <span data-ttu-id="d5bb7-110">When implementing the Toggle control pattern, note the following guidelines and conventions:</span><span class="sxs-lookup"><span data-stu-id="d5bb7-110">When implementing the Toggle control pattern, note the following guidelines and conventions:</span></span>  
  
- <span data-ttu-id="d5bb7-111">Controls that do not maintain state when activated, such as buttons, toolbar buttons, and hyperlinks, must implement <xref:System.Windows.Automation.Provider.IInvokeProvider> instead.</span><span class="sxs-lookup"><span data-stu-id="d5bb7-111">Controls that do not maintain state when activated, such as buttons, toolbar buttons, and hyperlinks, must implement <xref:System.Windows.Automation.Provider.IInvokeProvider> instead.</span></span>  
  
- <span data-ttu-id="d5bb7-112">A control must cycle through its <xref:System.Windows.Automation.ToggleState> in the following order: <xref:System.Windows.Automation.ToggleState.On>, <xref:System.Windows.Automation.ToggleState.Off> and, if supported, <xref:System.Windows.Automation.ToggleState.Indeterminate>.</span><span class="sxs-lookup"><span data-stu-id="d5bb7-112">A control must cycle through its <xref:System.Windows.Automation.ToggleState> in the following order: <xref:System.Windows.Automation.ToggleState.On>, <xref:System.Windows.Automation.ToggleState.Off> and, if supported, <xref:System.Windows.Automation.ToggleState.Indeterminate>.</span></span>  
  
- <span data-ttu-id="d5bb7-113"><xref:System.Windows.Automation.TogglePattern> does not provide a SetState(newState) method due to issues surrounding the direct setting of a tri-state CheckBox without cycling through its appropriate <xref:System.Windows.Automation.ToggleState> sequence.</span><span class="sxs-lookup"><span data-stu-id="d5bb7-113"><xref:System.Windows.Automation.TogglePattern> does not provide a SetState(newState) method due to issues surrounding the direct setting of a tri-state CheckBox without cycling through its appropriate <xref:System.Windows.Automation.ToggleState> sequence.</span></span>  
  
- <span data-ttu-id="d5bb7-114">The RadioButton control does not implement <xref:System.Windows.Automation.Provider.IToggleProvider>, as it is not capable of cycling through its valid states.</span><span class="sxs-lookup"><span data-stu-id="d5bb7-114">The RadioButton control does not implement <xref:System.Windows.Automation.Provider.IToggleProvider>, as it is not capable of cycling through its valid states.</span></span>  
  
<a name="Required_Members_for_IToggleProvider"></a>   
## <a name="required-members-for-itoggleprovider"></a><span data-ttu-id="d5bb7-115">Required Members for IToggleProvider</span><span class="sxs-lookup"><span data-stu-id="d5bb7-115">Required Members for IToggleProvider</span></span>  
 <span data-ttu-id="d5bb7-116">The following properties and methods are required for implementing <xref:System.Windows.Automation.Provider.IToggleProvider>.</span><span class="sxs-lookup"><span data-stu-id="d5bb7-116">The following properties and methods are required for implementing <xref:System.Windows.Automation.Provider.IToggleProvider>.</span></span>  
  
|<span data-ttu-id="d5bb7-117">Required member</span><span class="sxs-lookup"><span data-stu-id="d5bb7-117">Required member</span></span>|<span data-ttu-id="d5bb7-118">Member type</span><span class="sxs-lookup"><span data-stu-id="d5bb7-118">Member type</span></span>|<span data-ttu-id="d5bb7-119">Anotações</span><span class="sxs-lookup"><span data-stu-id="d5bb7-119">Notes</span></span>|  
|---------------------|-----------------|-----------|  
|<xref:System.Windows.Automation.TogglePattern.Toggle%2A>|<span data-ttu-id="d5bb7-120">Método</span><span class="sxs-lookup"><span data-stu-id="d5bb7-120">Method</span></span>|<span data-ttu-id="d5bb7-121">Nenhum</span><span class="sxs-lookup"><span data-stu-id="d5bb7-121">None</span></span>|  
|<xref:System.Windows.Automation.TogglePatternIdentifiers.ToggleStateProperty>|<span data-ttu-id="d5bb7-122">propriedade</span><span class="sxs-lookup"><span data-stu-id="d5bb7-122">Property</span></span>|<span data-ttu-id="d5bb7-123">Nenhum</span><span class="sxs-lookup"><span data-stu-id="d5bb7-123">None</span></span>|  
  
 <span data-ttu-id="d5bb7-124">This control pattern has no associated events.</span><span class="sxs-lookup"><span data-stu-id="d5bb7-124">This control pattern has no associated events.</span></span>  
  
<a name="Exceptions"></a>   
## <a name="exceptions"></a><span data-ttu-id="d5bb7-125">Exceções</span><span class="sxs-lookup"><span data-stu-id="d5bb7-125">Exceptions</span></span>  
 <span data-ttu-id="d5bb7-126">This control pattern has no associated exceptions.</span><span class="sxs-lookup"><span data-stu-id="d5bb7-126">This control pattern has no associated exceptions.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d5bb7-127">Consulte também</span><span class="sxs-lookup"><span data-stu-id="d5bb7-127">See also</span></span>

- [<span data-ttu-id="d5bb7-128">Visão geral de padrões de controle de automação da interface do usuário</span><span class="sxs-lookup"><span data-stu-id="d5bb7-128">UI Automation Control Patterns Overview</span></span>](ui-automation-control-patterns-overview.md)
- [<span data-ttu-id="d5bb7-129">Suporte a padrões de controle em um provedor de automação de interface do usuário</span><span class="sxs-lookup"><span data-stu-id="d5bb7-129">Support Control Patterns in a UI Automation Provider</span></span>](support-control-patterns-in-a-ui-automation-provider.md)
- [<span data-ttu-id="d5bb7-130">Padrões de controle de automação de interface do usuário para clientes</span><span class="sxs-lookup"><span data-stu-id="d5bb7-130">UI Automation Control Patterns for Clients</span></span>](ui-automation-control-patterns-for-clients.md)
- [<span data-ttu-id="d5bb7-131">Obter o estado de Alternância de uma caixa de seleção usando automação de interface do usuário</span><span class="sxs-lookup"><span data-stu-id="d5bb7-131">Get the Toggle State of a Check Box Using UI Automation</span></span>](get-the-toggle-state-of-a-check-box-using-ui-automation.md)
- [<span data-ttu-id="d5bb7-132">Visão geral de árvore de automação de interface do usuário</span><span class="sxs-lookup"><span data-stu-id="d5bb7-132">UI Automation Tree Overview</span></span>](ui-automation-tree-overview.md)
- [<span data-ttu-id="d5bb7-133">Usar o cache em automação de interface do usuário</span><span class="sxs-lookup"><span data-stu-id="d5bb7-133">Use Caching in UI Automation</span></span>](use-caching-in-ui-automation.md)
