---
title: Implementando o padrão de controle Toggle de automação de interface de usuário
ms.date: 03/30/2017
helpviewer_keywords:
- Toggle control pattern
- control patterns, Toggle
- UI Automation, Toggle control pattern
ms.assetid: 3cfe875f-b0c0-413d-9703-5f14e6a1a30e
author: Xansky
ms.author: mhopkins
manager: markl
ms.openlocfilehash: eed3f6771526f7a026bd411b3f12c39b4bb64bf4
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33407989"
---
# <a name="implementing-the-ui-automation-toggle-control-pattern"></a><span data-ttu-id="71476-102">Implementando o padrão de controle Toggle de automação de interface de usuário</span><span class="sxs-lookup"><span data-stu-id="71476-102">Implementing the UI Automation Toggle Control Pattern</span></span>
> [!NOTE]
>  <span data-ttu-id="71476-103">Esta documentação destina-se a desenvolvedores do .NET Framework que querem usar as classes da [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] gerenciadas definidas no namespace <xref:System.Windows.Automation>.</span><span class="sxs-lookup"><span data-stu-id="71476-103">This documentation is intended for .NET Framework developers who want to use the managed [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] classes defined in the <xref:System.Windows.Automation> namespace.</span></span> <span data-ttu-id="71476-104">Para obter as informações mais recentes sobre a [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], consulte [Windows Automation API: UI Automation](http://go.microsoft.com/fwlink/?LinkID=156746) (API de Automação do Windows: Automação da Interface do Usuário).</span><span class="sxs-lookup"><span data-stu-id="71476-104">For the latest information about [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], see [Windows Automation API: UI Automation](http://go.microsoft.com/fwlink/?LinkID=156746).</span></span>  
  
 <span data-ttu-id="71476-105">Este tópico apresenta diretrizes e convenções para implementar <xref:System.Windows.Automation.Provider.IToggleProvider>, incluindo informações sobre os métodos e propriedades.</span><span class="sxs-lookup"><span data-stu-id="71476-105">This topic introduces guidelines and conventions for implementing <xref:System.Windows.Automation.Provider.IToggleProvider>, including information about methods and properties.</span></span> <span data-ttu-id="71476-106">Links para referências adicionais são listadas no final do tópico.</span><span class="sxs-lookup"><span data-stu-id="71476-106">Links to additional references are listed at the end of the topic.</span></span>  
  
 <span data-ttu-id="71476-107">O <xref:System.Windows.Automation.TogglePattern> padrão de controle é usado para oferecer suporte aos controles que podem alternar entre um conjunto de estados e manter um estado definido uma vez.</span><span class="sxs-lookup"><span data-stu-id="71476-107">The <xref:System.Windows.Automation.TogglePattern> control pattern is used to support controls that can cycle through a set of states and maintain a state once set.</span></span> <span data-ttu-id="71476-108">Para obter exemplos de controles que implementam este padrão de controle, consulte [mapeamento de padrão de controle para clientes de automação de interface do usuário](../../../docs/framework/ui-automation/control-pattern-mapping-for-ui-automation-clients.md).</span><span class="sxs-lookup"><span data-stu-id="71476-108">For examples of controls that implement this control pattern, see [Control Pattern Mapping for UI Automation Clients](../../../docs/framework/ui-automation/control-pattern-mapping-for-ui-automation-clients.md).</span></span>  
  
<a name="Implementation_Guidelines_and_Conventions"></a>   
## <a name="implementation-guidelines-and-conventions"></a><span data-ttu-id="71476-109">Convenções e diretrizes de implementação</span><span class="sxs-lookup"><span data-stu-id="71476-109">Implementation Guidelines and Conventions</span></span>  
 <span data-ttu-id="71476-110">Ao implementar o padrão de controle Toggle, observe as seguintes diretrizes e convenções:</span><span class="sxs-lookup"><span data-stu-id="71476-110">When implementing the Toggle control pattern, note the following guidelines and conventions:</span></span>  
  
-   <span data-ttu-id="71476-111">Controles que não mantêm o estado quando ativado, como botões, botões da barra de ferramentas e hiperlinks, devem implementar <xref:System.Windows.Automation.Provider.IInvokeProvider> em vez disso.</span><span class="sxs-lookup"><span data-stu-id="71476-111">Controls that do not maintain state when activated, such as buttons, toolbar buttons, and hyperlinks, must implement <xref:System.Windows.Automation.Provider.IInvokeProvider> instead.</span></span>  
  
-   <span data-ttu-id="71476-112">Um controle deve percorrer seu <xref:System.Windows.Automation.ToggleState> na seguinte ordem: <xref:System.Windows.Automation.ToggleState.On>, <xref:System.Windows.Automation.ToggleState.Off> e, se suportado, <xref:System.Windows.Automation.ToggleState.Indeterminate>.</span><span class="sxs-lookup"><span data-stu-id="71476-112">A control must cycle through its <xref:System.Windows.Automation.ToggleState> in the following order: <xref:System.Windows.Automation.ToggleState.On>, <xref:System.Windows.Automation.ToggleState.Off> and, if supported, <xref:System.Windows.Automation.ToggleState.Indeterminate>.</span></span>  
  
-   <span data-ttu-id="71476-113"><xref:System.Windows.Automation.TogglePattern> não fornece um método SetState devido a problemas envolvendo a configuração direta de uma caixa de seleção de três estados sem percorrer seu apropriado <xref:System.Windows.Automation.ToggleState> sequência.</span><span class="sxs-lookup"><span data-stu-id="71476-113"><xref:System.Windows.Automation.TogglePattern> does not provide a SetState(newState) method due to issues surrounding the direct setting of a tri-state CheckBox without cycling through its appropriate <xref:System.Windows.Automation.ToggleState> sequence.</span></span>  
  
-   <span data-ttu-id="71476-114">O controle RadioButton não implementa <xref:System.Windows.Automation.Provider.IToggleProvider>, pois não é capaz de percorrendo seus estados válidos.</span><span class="sxs-lookup"><span data-stu-id="71476-114">The RadioButton control does not implement <xref:System.Windows.Automation.Provider.IToggleProvider>, as it is not capable of cycling through its valid states.</span></span>  
  
<a name="Required_Members_for_IToggleProvider"></a>   
## <a name="required-members-for-itoggleprovider"></a><span data-ttu-id="71476-115">Membros necessários para IToggleProvider</span><span class="sxs-lookup"><span data-stu-id="71476-115">Required Members for IToggleProvider</span></span>  
 <span data-ttu-id="71476-116">As propriedades e métodos a seguir são necessários para implementar <xref:System.Windows.Automation.Provider.IToggleProvider>.</span><span class="sxs-lookup"><span data-stu-id="71476-116">The following properties and methods are required for implementing <xref:System.Windows.Automation.Provider.IToggleProvider>.</span></span>  
  
|<span data-ttu-id="71476-117">Membro necessário</span><span class="sxs-lookup"><span data-stu-id="71476-117">Required member</span></span>|<span data-ttu-id="71476-118">Tipo de membro</span><span class="sxs-lookup"><span data-stu-id="71476-118">Member type</span></span>|<span data-ttu-id="71476-119">Observações</span><span class="sxs-lookup"><span data-stu-id="71476-119">Notes</span></span>|  
|---------------------|-----------------|-----------|  
|<xref:System.Windows.Automation.TogglePattern.Toggle%2A>|<span data-ttu-id="71476-120">Método</span><span class="sxs-lookup"><span data-stu-id="71476-120">Method</span></span>|<span data-ttu-id="71476-121">Nenhum</span><span class="sxs-lookup"><span data-stu-id="71476-121">None</span></span>|  
|<xref:System.Windows.Automation.TogglePatternIdentifiers.ToggleStateProperty>|<span data-ttu-id="71476-122">Propriedade</span><span class="sxs-lookup"><span data-stu-id="71476-122">Property</span></span>|<span data-ttu-id="71476-123">Nenhum</span><span class="sxs-lookup"><span data-stu-id="71476-123">None</span></span>|  
  
 <span data-ttu-id="71476-124">Esse padrão de controle não possui eventos associados.</span><span class="sxs-lookup"><span data-stu-id="71476-124">This control pattern has no associated events.</span></span>  
  
<a name="Exceptions"></a>   
## <a name="exceptions"></a><span data-ttu-id="71476-125">Exceções</span><span class="sxs-lookup"><span data-stu-id="71476-125">Exceptions</span></span>  
 <span data-ttu-id="71476-126">Esse padrão de controle não tem exceção associada.</span><span class="sxs-lookup"><span data-stu-id="71476-126">This control pattern has no associated exceptions.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="71476-127">Consulte também</span><span class="sxs-lookup"><span data-stu-id="71476-127">See Also</span></span>  
 [<span data-ttu-id="71476-128">Visão geral de padrões de controle de automação da interface do usuário</span><span class="sxs-lookup"><span data-stu-id="71476-128">UI Automation Control Patterns Overview</span></span>](../../../docs/framework/ui-automation/ui-automation-control-patterns-overview.md)  
 [<span data-ttu-id="71476-129">Suporte a padrões de controle em um provedor de automação de interface do usuário</span><span class="sxs-lookup"><span data-stu-id="71476-129">Support Control Patterns in a UI Automation Provider</span></span>](../../../docs/framework/ui-automation/support-control-patterns-in-a-ui-automation-provider.md)  
 [<span data-ttu-id="71476-130">Padrões de controle de automação de interface do usuário para clientes</span><span class="sxs-lookup"><span data-stu-id="71476-130">UI Automation Control Patterns for Clients</span></span>](../../../docs/framework/ui-automation/ui-automation-control-patterns-for-clients.md)  
 [<span data-ttu-id="71476-131">Obter o estado de Alternância de uma caixa de seleção usando automação de interface do usuário</span><span class="sxs-lookup"><span data-stu-id="71476-131">Get the Toggle State of a Check Box Using UI Automation</span></span>](../../../docs/framework/ui-automation/get-the-toggle-state-of-a-check-box-using-ui-automation.md)  
 [<span data-ttu-id="71476-132">Visão geral de árvore de automação de interface do usuário</span><span class="sxs-lookup"><span data-stu-id="71476-132">UI Automation Tree Overview</span></span>](../../../docs/framework/ui-automation/ui-automation-tree-overview.md)  
 [<span data-ttu-id="71476-133">Usar o cache em automação de interface do usuário</span><span class="sxs-lookup"><span data-stu-id="71476-133">Use Caching in UI Automation</span></span>](../../../docs/framework/ui-automation/use-caching-in-ui-automation.md)
