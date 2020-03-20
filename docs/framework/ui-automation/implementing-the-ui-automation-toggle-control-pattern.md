---
title: Implementando o padrão de controle Toggle de automação de interface de usuário
ms.date: 03/30/2017
helpviewer_keywords:
- Toggle control pattern
- control patterns, Toggle
- UI Automation, Toggle control pattern
ms.assetid: 3cfe875f-b0c0-413d-9703-5f14e6a1a30e
ms.openlocfilehash: 5f64842d31d46af3d648b9b570d1cfb210e2910a
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79180057"
---
# <a name="implementing-the-ui-automation-toggle-control-pattern"></a><span data-ttu-id="0450c-102">Implementando o padrão de controle Toggle de automação de interface de usuário</span><span class="sxs-lookup"><span data-stu-id="0450c-102">Implementing the UI Automation Toggle Control Pattern</span></span>
> [!NOTE]
> <span data-ttu-id="0450c-103">Esta documentação destina-se a desenvolvedores do .NET Framework que querem usar as classes da [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] gerenciadas definidas no namespace <xref:System.Windows.Automation>.</span><span class="sxs-lookup"><span data-stu-id="0450c-103">This documentation is intended for .NET Framework developers who want to use the managed [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] classes defined in the <xref:System.Windows.Automation> namespace.</span></span> <span data-ttu-id="0450c-104">Para obter as informações mais recentes sobre a [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], consulte [Windows Automation API: UI Automation](/windows/win32/winauto/entry-uiauto-win32) (API de Automação do Windows: Automação da Interface do Usuário).</span><span class="sxs-lookup"><span data-stu-id="0450c-104">For the latest information about [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], see [Windows Automation API: UI Automation](/windows/win32/winauto/entry-uiauto-win32).</span></span>  
  
 <span data-ttu-id="0450c-105">Este tópico introduz diretrizes e <xref:System.Windows.Automation.Provider.IToggleProvider>convenções para a implementação, incluindo informações sobre métodos e propriedades.</span><span class="sxs-lookup"><span data-stu-id="0450c-105">This topic introduces guidelines and conventions for implementing <xref:System.Windows.Automation.Provider.IToggleProvider>, including information about methods and properties.</span></span> <span data-ttu-id="0450c-106">Links para referências adicionais são listados no final do tópico.</span><span class="sxs-lookup"><span data-stu-id="0450c-106">Links to additional references are listed at the end of the topic.</span></span>  
  
 <span data-ttu-id="0450c-107">O <xref:System.Windows.Automation.TogglePattern> padrão de controle é usado para suportar controles que podem percorrer um conjunto de estados e manter um estado uma vez definido.</span><span class="sxs-lookup"><span data-stu-id="0450c-107">The <xref:System.Windows.Automation.TogglePattern> control pattern is used to support controls that can cycle through a set of states and maintain a state once set.</span></span> <span data-ttu-id="0450c-108">Para exemplos de controles que implementam esse padrão de controle, consulte Mapping de padrão de [controle para clientes de automação de interface do usuário](control-pattern-mapping-for-ui-automation-clients.md).</span><span class="sxs-lookup"><span data-stu-id="0450c-108">For examples of controls that implement this control pattern, see [Control Pattern Mapping for UI Automation Clients](control-pattern-mapping-for-ui-automation-clients.md).</span></span>  
  
<a name="Implementation_Guidelines_and_Conventions"></a>
## <a name="implementation-guidelines-and-conventions"></a><span data-ttu-id="0450c-109">Diretrizes e Convenções de Implementação</span><span class="sxs-lookup"><span data-stu-id="0450c-109">Implementation Guidelines and Conventions</span></span>  
 <span data-ttu-id="0450c-110">Ao implementar o padrão de controle Alternar, observe as seguintes diretrizes e convenções:</span><span class="sxs-lookup"><span data-stu-id="0450c-110">When implementing the Toggle control pattern, note the following guidelines and conventions:</span></span>  
  
- <span data-ttu-id="0450c-111">Controles que não mantêm o estado quando ativados, como botões, botões de <xref:System.Windows.Automation.Provider.IInvokeProvider> barra de ferramentas e hiperlinks, devem ser implementados em seu lugar.</span><span class="sxs-lookup"><span data-stu-id="0450c-111">Controls that do not maintain state when activated, such as buttons, toolbar buttons, and hyperlinks, must implement <xref:System.Windows.Automation.Provider.IInvokeProvider> instead.</span></span>  
  
- <span data-ttu-id="0450c-112">Um controle deve <xref:System.Windows.Automation.ToggleState> percorrer a sua <xref:System.Windows.Automation.ToggleState.On> <xref:System.Windows.Automation.ToggleState.Off> na seguinte ordem: <xref:System.Windows.Automation.ToggleState.Indeterminate>, e, se apoiado, .</span><span class="sxs-lookup"><span data-stu-id="0450c-112">A control must cycle through its <xref:System.Windows.Automation.ToggleState> in the following order: <xref:System.Windows.Automation.ToggleState.On>, <xref:System.Windows.Automation.ToggleState.Off> and, if supported, <xref:System.Windows.Automation.ToggleState.Indeterminate>.</span></span>  
  
- <span data-ttu-id="0450c-113"><xref:System.Windows.Automation.TogglePattern>não fornece um método SetState (newState) devido a problemas envolvendo a configuração <xref:System.Windows.Automation.ToggleState> direta de uma Caixa de Seleção de três estados sem passar por sua seqüência apropriada.</span><span class="sxs-lookup"><span data-stu-id="0450c-113"><xref:System.Windows.Automation.TogglePattern> does not provide a SetState(newState) method due to issues surrounding the direct setting of a tri-state CheckBox without cycling through its appropriate <xref:System.Windows.Automation.ToggleState> sequence.</span></span>  
  
- <span data-ttu-id="0450c-114">O controle RadioButton <xref:System.Windows.Automation.Provider.IToggleProvider>não implementa, pois não é capaz de pedalar através de seus estados válidos.</span><span class="sxs-lookup"><span data-stu-id="0450c-114">The RadioButton control does not implement <xref:System.Windows.Automation.Provider.IToggleProvider>, as it is not capable of cycling through its valid states.</span></span>  
  
<a name="Required_Members_for_IToggleProvider"></a>
## <a name="required-members-for-itoggleprovider"></a><span data-ttu-id="0450c-115">Membros obrigatórios para IToggleProvider</span><span class="sxs-lookup"><span data-stu-id="0450c-115">Required Members for IToggleProvider</span></span>  
 <span data-ttu-id="0450c-116">As seguintes propriedades e métodos <xref:System.Windows.Automation.Provider.IToggleProvider>são necessários para a implementação.</span><span class="sxs-lookup"><span data-stu-id="0450c-116">The following properties and methods are required for implementing <xref:System.Windows.Automation.Provider.IToggleProvider>.</span></span>  
  
|<span data-ttu-id="0450c-117">Membro obrigatório</span><span class="sxs-lookup"><span data-stu-id="0450c-117">Required member</span></span>|<span data-ttu-id="0450c-118">Tipo de membro</span><span class="sxs-lookup"><span data-stu-id="0450c-118">Member type</span></span>|<span data-ttu-id="0450c-119">Observações</span><span class="sxs-lookup"><span data-stu-id="0450c-119">Notes</span></span>|  
|---------------------|-----------------|-----------|  
|<xref:System.Windows.Automation.TogglePattern.Toggle%2A>|<span data-ttu-id="0450c-120">Método</span><span class="sxs-lookup"><span data-stu-id="0450c-120">Method</span></span>|<span data-ttu-id="0450c-121">Nenhum</span><span class="sxs-lookup"><span data-stu-id="0450c-121">None</span></span>|  
|<xref:System.Windows.Automation.TogglePatternIdentifiers.ToggleStateProperty>|<span data-ttu-id="0450c-122">Propriedade</span><span class="sxs-lookup"><span data-stu-id="0450c-122">Property</span></span>|<span data-ttu-id="0450c-123">Nenhum</span><span class="sxs-lookup"><span data-stu-id="0450c-123">None</span></span>|  
  
 <span data-ttu-id="0450c-124">Este padrão de controle não tem eventos associados.</span><span class="sxs-lookup"><span data-stu-id="0450c-124">This control pattern has no associated events.</span></span>  
  
<a name="Exceptions"></a>
## <a name="exceptions"></a><span data-ttu-id="0450c-125">Exceções</span><span class="sxs-lookup"><span data-stu-id="0450c-125">Exceptions</span></span>  
 <span data-ttu-id="0450c-126">Este padrão de controle não tem exceções associadas.</span><span class="sxs-lookup"><span data-stu-id="0450c-126">This control pattern has no associated exceptions.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0450c-127">Confira também</span><span class="sxs-lookup"><span data-stu-id="0450c-127">See also</span></span>

- [<span data-ttu-id="0450c-128">Visão Geral de Padrões de Controle de Automação de Interface de Usuário</span><span class="sxs-lookup"><span data-stu-id="0450c-128">UI Automation Control Patterns Overview</span></span>](ui-automation-control-patterns-overview.md)
- [<span data-ttu-id="0450c-129">Padrões de controle de suporte em um provedor de automação da interface do usuário</span><span class="sxs-lookup"><span data-stu-id="0450c-129">Support Control Patterns in a UI Automation Provider</span></span>](support-control-patterns-in-a-ui-automation-provider.md)
- [<span data-ttu-id="0450c-130">Padrões de controle de automação de interface do usuário para clientes</span><span class="sxs-lookup"><span data-stu-id="0450c-130">UI Automation Control Patterns for Clients</span></span>](ui-automation-control-patterns-for-clients.md)
- [<span data-ttu-id="0450c-131">Obter o estado Toggle de uma caixa de seleção usando automação de interface do usuário</span><span class="sxs-lookup"><span data-stu-id="0450c-131">Get the Toggle State of a Check Box Using UI Automation</span></span>](get-the-toggle-state-of-a-check-box-using-ui-automation.md)
- [<span data-ttu-id="0450c-132">Visão geral da árvore de automação de interface do usuário</span><span class="sxs-lookup"><span data-stu-id="0450c-132">UI Automation Tree Overview</span></span>](ui-automation-tree-overview.md)
- [<span data-ttu-id="0450c-133">Usar armazenamento em cache em automação de interface do usuário</span><span class="sxs-lookup"><span data-stu-id="0450c-133">Use Caching in UI Automation</span></span>](use-caching-in-ui-automation.md)
