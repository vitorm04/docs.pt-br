---
title: Implementando o padrão de controle RangeValue de interface de usuário
ms.date: 03/30/2017
helpviewer_keywords:
- control patterns, Range Value
- Range Value control pattern
- UI Automation, Range Value control pattern
ms.assetid: 225feaa4-918e-418b-938e-7389338d0a69
ms.openlocfilehash: 847a8aae3fd0c3d6965c910d19a4cec11cd2a3b7
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79180177"
---
# <a name="implementing-the-ui-automation-rangevalue-control-pattern"></a><span data-ttu-id="5019e-102">Implementando o padrão de controle RangeValue de interface de usuário</span><span class="sxs-lookup"><span data-stu-id="5019e-102">Implementing the UI Automation RangeValue Control Pattern</span></span>
> [!NOTE]
> <span data-ttu-id="5019e-103">Esta documentação destina-se a desenvolvedores do .NET Framework que querem usar as classes da [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] gerenciadas definidas no namespace <xref:System.Windows.Automation>.</span><span class="sxs-lookup"><span data-stu-id="5019e-103">This documentation is intended for .NET Framework developers who want to use the managed [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] classes defined in the <xref:System.Windows.Automation> namespace.</span></span> <span data-ttu-id="5019e-104">Para obter as informações mais recentes sobre a [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], consulte [Windows Automation API: UI Automation](/windows/win32/winauto/entry-uiauto-win32) (API de Automação do Windows: Automação da Interface do Usuário).</span><span class="sxs-lookup"><span data-stu-id="5019e-104">For the latest information about [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], see [Windows Automation API: UI Automation](/windows/win32/winauto/entry-uiauto-win32).</span></span>  
  
 <span data-ttu-id="5019e-105">Este tópico introduz diretrizes e <xref:System.Windows.Automation.Provider.IRangeValueProvider>convenções para a implementação, incluindo informações sobre eventos e propriedades.</span><span class="sxs-lookup"><span data-stu-id="5019e-105">This topic introduces guidelines and conventions for implementing <xref:System.Windows.Automation.Provider.IRangeValueProvider>, including information about events and properties.</span></span> <span data-ttu-id="5019e-106">Links para referências adicionais são listados no final do tópico.</span><span class="sxs-lookup"><span data-stu-id="5019e-106">Links to additional references are listed at the end of the topic.</span></span>  
  
 <span data-ttu-id="5019e-107">O <xref:System.Windows.Automation.RangeValuePattern> padrão de controle é usado para suportar controles que podem ser definidos como um valor dentro de um intervalo.</span><span class="sxs-lookup"><span data-stu-id="5019e-107">The <xref:System.Windows.Automation.RangeValuePattern> control pattern is used to support controls that can be set to a value within a range.</span></span> <span data-ttu-id="5019e-108">Para exemplos de controles que implementam esse padrão de controle, consulte Mapping de padrão de [controle para clientes de automação de interface do usuário](control-pattern-mapping-for-ui-automation-clients.md).</span><span class="sxs-lookup"><span data-stu-id="5019e-108">For examples of controls that implement this control pattern, see [Control Pattern Mapping for UI Automation Clients](control-pattern-mapping-for-ui-automation-clients.md).</span></span>  
  
<a name="Implementation_Guidelines_and_Conventions"></a>
## <a name="implementation-guidelines-and-conventions"></a><span data-ttu-id="5019e-109">Diretrizes e Convenções de Implementação</span><span class="sxs-lookup"><span data-stu-id="5019e-109">Implementation Guidelines and Conventions</span></span>  
 <span data-ttu-id="5019e-110">Ao implementar o padrão de controle de valor de intervalo, observe as seguintes diretrizes e convenções:</span><span class="sxs-lookup"><span data-stu-id="5019e-110">When implementing the Range Value control pattern, note the following guidelines and conventions:</span></span>  
  
- <span data-ttu-id="5019e-111">Os controles permitem a recalibração de suas propriedades suportadas com base na localização ou preferência do usuário.</span><span class="sxs-lookup"><span data-stu-id="5019e-111">Controls allow recalibration of their supported properties based upon locale or user preference.</span></span> <span data-ttu-id="5019e-112">Um exemplo disso é um controle de termômetro que pode ser definido para exibir a temperatura em Fahrenheit ou Celsius.</span><span class="sxs-lookup"><span data-stu-id="5019e-112">An example of this is a thermometer control that can be set to display the temperature in Fahrenheit or Celsius.</span></span>  
  
- <span data-ttu-id="5019e-113">Controles que tenham valores de alcance ambíguos, como barras de progresso ou controles deslizantes, devem ter esses valores normalizados.</span><span class="sxs-lookup"><span data-stu-id="5019e-113">Controls that have ambiguous range values, such as progress bars or sliders, should have those values normalized.</span></span>  
  
 <span data-ttu-id="5019e-114">![Barra de progresso.](./media/uia-rangevaluepattern-progress-bar.PNG "UIA_RangeValuePattern_Progress_Bar")</span><span class="sxs-lookup"><span data-stu-id="5019e-114">![Progress bar.](./media/uia-rangevaluepattern-progress-bar.PNG "UIA_RangeValuePattern_Progress_Bar")</span></span>  
<span data-ttu-id="5019e-115">Exemplo de barra de progresso onde o valor é do tipo inteiro e os valores mínimos e máximos da propriedade são normalizados em 0 e 100, respectivamente</span><span class="sxs-lookup"><span data-stu-id="5019e-115">Example of a Progress Bar Where Value Is of Type Integer and Minimum and Maximum Property Values Are Normalized to 0 and 100, Respectively</span></span>  
  
<a name="Required_Members_for_the_IRangeValueProvider"></a>
## <a name="required-members-for-irangevalueprovider"></a><span data-ttu-id="5019e-116">Membros obrigatórios para IRangeValueProvider</span><span class="sxs-lookup"><span data-stu-id="5019e-116">Required Members for IRangeValueProvider</span></span>  
  
|<span data-ttu-id="5019e-117">Membro obrigatório</span><span class="sxs-lookup"><span data-stu-id="5019e-117">Required member</span></span>|<span data-ttu-id="5019e-118">Tipo de membro</span><span class="sxs-lookup"><span data-stu-id="5019e-118">Member type</span></span>|<span data-ttu-id="5019e-119">Observações</span><span class="sxs-lookup"><span data-stu-id="5019e-119">Notes</span></span>|  
|---------------------|-----------------|-----------|  
|<xref:System.Windows.Automation.RangeValuePattern.IsReadOnlyProperty>|<span data-ttu-id="5019e-120">Propriedade</span><span class="sxs-lookup"><span data-stu-id="5019e-120">Property</span></span>|<span data-ttu-id="5019e-121">Nenhum</span><span class="sxs-lookup"><span data-stu-id="5019e-121">None</span></span>|  
|<xref:System.Windows.Automation.RangeValuePattern.ValueProperty>|<span data-ttu-id="5019e-122">Propriedade</span><span class="sxs-lookup"><span data-stu-id="5019e-122">Property</span></span>|<span data-ttu-id="5019e-123">Nenhum</span><span class="sxs-lookup"><span data-stu-id="5019e-123">None</span></span>|  
|<xref:System.Windows.Automation.RangeValuePattern.LargeChangeProperty>|<span data-ttu-id="5019e-124">Propriedade</span><span class="sxs-lookup"><span data-stu-id="5019e-124">Property</span></span>|<span data-ttu-id="5019e-125">Nenhum</span><span class="sxs-lookup"><span data-stu-id="5019e-125">None</span></span>|  
|<xref:System.Windows.Automation.RangeValuePattern.SmallChangeProperty>|<span data-ttu-id="5019e-126">Propriedade</span><span class="sxs-lookup"><span data-stu-id="5019e-126">Property</span></span>|<span data-ttu-id="5019e-127">Nenhum</span><span class="sxs-lookup"><span data-stu-id="5019e-127">None</span></span>|  
|<xref:System.Windows.Automation.RangeValuePattern.MaximumProperty>|<span data-ttu-id="5019e-128">Propriedade</span><span class="sxs-lookup"><span data-stu-id="5019e-128">Property</span></span>|<span data-ttu-id="5019e-129">Nenhum</span><span class="sxs-lookup"><span data-stu-id="5019e-129">None</span></span>|  
|<xref:System.Windows.Automation.RangeValuePattern.MinimumProperty>|<span data-ttu-id="5019e-130">Propriedade</span><span class="sxs-lookup"><span data-stu-id="5019e-130">Property</span></span>|<span data-ttu-id="5019e-131">Nenhum</span><span class="sxs-lookup"><span data-stu-id="5019e-131">None</span></span>|  
|<xref:System.Windows.Automation.RangeValuePattern.SetValue%2A>|<span data-ttu-id="5019e-132">Métodos</span><span class="sxs-lookup"><span data-stu-id="5019e-132">Methods</span></span>|<span data-ttu-id="5019e-133">Nenhum</span><span class="sxs-lookup"><span data-stu-id="5019e-133">None</span></span>|  
  
 <span data-ttu-id="5019e-134">Este padrão de controle não tem eventos associados.</span><span class="sxs-lookup"><span data-stu-id="5019e-134">This control pattern has no associated events.</span></span>  
  
<a name="Exceptions"></a>
## <a name="exceptions"></a><span data-ttu-id="5019e-135">Exceções</span><span class="sxs-lookup"><span data-stu-id="5019e-135">Exceptions</span></span>  
 <span data-ttu-id="5019e-136">Os provedores devem lançar as seguintes exceções.</span><span class="sxs-lookup"><span data-stu-id="5019e-136">Providers must throw the following exceptions.</span></span>  
  
|<span data-ttu-id="5019e-137">Tipo de exceção</span><span class="sxs-lookup"><span data-stu-id="5019e-137">Exception type</span></span>|<span data-ttu-id="5019e-138">Condição</span><span class="sxs-lookup"><span data-stu-id="5019e-138">Condition</span></span>|  
|--------------------|---------------|  
|<xref:System.ArgumentOutOfRangeException>|<span data-ttu-id="5019e-139"><xref:System.Windows.Automation.RangeValuePattern.SetValue%2A>é chamado com um valor <xref:System.Windows.Automation.RangeValuePattern.MaximumProperty> que é <xref:System.Windows.Automation.RangeValuePattern.MinimumProperty>maior ou menor do que .</span><span class="sxs-lookup"><span data-stu-id="5019e-139"><xref:System.Windows.Automation.RangeValuePattern.SetValue%2A> is called with a value that is either greater than <xref:System.Windows.Automation.RangeValuePattern.MaximumProperty> or less than <xref:System.Windows.Automation.RangeValuePattern.MinimumProperty>.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="5019e-140">Confira também</span><span class="sxs-lookup"><span data-stu-id="5019e-140">See also</span></span>

- [<span data-ttu-id="5019e-141">Visão Geral de Padrões de Controle de Automação de Interface de Usuário</span><span class="sxs-lookup"><span data-stu-id="5019e-141">UI Automation Control Patterns Overview</span></span>](ui-automation-control-patterns-overview.md)
- [<span data-ttu-id="5019e-142">Padrões de controle de suporte em um provedor de automação da interface do usuário</span><span class="sxs-lookup"><span data-stu-id="5019e-142">Support Control Patterns in a UI Automation Provider</span></span>](support-control-patterns-in-a-ui-automation-provider.md)
- [<span data-ttu-id="5019e-143">Padrões de controle de automação de interface do usuário para clientes</span><span class="sxs-lookup"><span data-stu-id="5019e-143">UI Automation Control Patterns for Clients</span></span>](ui-automation-control-patterns-for-clients.md)
- [<span data-ttu-id="5019e-144">Visão geral da árvore de automação de interface do usuário</span><span class="sxs-lookup"><span data-stu-id="5019e-144">UI Automation Tree Overview</span></span>](ui-automation-tree-overview.md)
- [<span data-ttu-id="5019e-145">Usar armazenamento em cache em automação de interface do usuário</span><span class="sxs-lookup"><span data-stu-id="5019e-145">Use Caching in UI Automation</span></span>](use-caching-in-ui-automation.md)
