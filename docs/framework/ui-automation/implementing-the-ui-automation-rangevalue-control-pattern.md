---
title: Implementando o padrão de controle RangeValue de interface de usuário
ms.date: 03/30/2017
helpviewer_keywords:
- control patterns, Range Value
- Range Value control pattern
- UI Automation, Range Value control pattern
ms.assetid: 225feaa4-918e-418b-938e-7389338d0a69
ms.openlocfilehash: 04db9f97ccea10cf8c65df0f0117c272a5e868dd
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74435110"
---
# <a name="implementing-the-ui-automation-rangevalue-control-pattern"></a><span data-ttu-id="73156-102">Implementando o padrão de controle RangeValue de interface de usuário</span><span class="sxs-lookup"><span data-stu-id="73156-102">Implementing the UI Automation RangeValue Control Pattern</span></span>
> [!NOTE]
> <span data-ttu-id="73156-103">Esta documentação destina-se a desenvolvedores do .NET Framework que querem usar as classes da [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] gerenciadas definidas no namespace <xref:System.Windows.Automation>.</span><span class="sxs-lookup"><span data-stu-id="73156-103">This documentation is intended for .NET Framework developers who want to use the managed [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] classes defined in the <xref:System.Windows.Automation> namespace.</span></span> <span data-ttu-id="73156-104">Para obter as informações mais recentes sobre a [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], consulte [Windows Automation API: UI Automation](/windows/win32/winauto/entry-uiauto-win32) (API de Automação do Windows: Automação da Interface do Usuário).</span><span class="sxs-lookup"><span data-stu-id="73156-104">For the latest information about [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], see [Windows Automation API: UI Automation](/windows/win32/winauto/entry-uiauto-win32).</span></span>  
  
 <span data-ttu-id="73156-105">Este tópico apresenta as diretrizes e convenções para implementar <xref:System.Windows.Automation.Provider.IRangeValueProvider>, incluindo informações sobre eventos e propriedades.</span><span class="sxs-lookup"><span data-stu-id="73156-105">This topic introduces guidelines and conventions for implementing <xref:System.Windows.Automation.Provider.IRangeValueProvider>, including information about events and properties.</span></span> <span data-ttu-id="73156-106">Links para referências adicionais são listados no final do tópico.</span><span class="sxs-lookup"><span data-stu-id="73156-106">Links to additional references are listed at the end of the topic.</span></span>  
  
 <span data-ttu-id="73156-107">O padrão de controle <xref:System.Windows.Automation.RangeValuePattern> é usado para dar suporte a controles que podem ser definidos para um valor dentro de um intervalo.</span><span class="sxs-lookup"><span data-stu-id="73156-107">The <xref:System.Windows.Automation.RangeValuePattern> control pattern is used to support controls that can be set to a value within a range.</span></span> <span data-ttu-id="73156-108">Para obter exemplos de controles que implementam esse padrão de controle, consulte [mapeamento de padrão de controle para clientes de automação da interface do usuário](control-pattern-mapping-for-ui-automation-clients.md).</span><span class="sxs-lookup"><span data-stu-id="73156-108">For examples of controls that implement this control pattern, see [Control Pattern Mapping for UI Automation Clients](control-pattern-mapping-for-ui-automation-clients.md).</span></span>  
  
<a name="Implementation_Guidelines_and_Conventions"></a>   
## <a name="implementation-guidelines-and-conventions"></a><span data-ttu-id="73156-109">Diretrizes e convenções de implementação</span><span class="sxs-lookup"><span data-stu-id="73156-109">Implementation Guidelines and Conventions</span></span>  
 <span data-ttu-id="73156-110">Ao implementar o padrão de controle de valor de intervalo, observe as seguintes diretrizes e convenções:</span><span class="sxs-lookup"><span data-stu-id="73156-110">When implementing the Range Value control pattern, note the following guidelines and conventions:</span></span>  
  
- <span data-ttu-id="73156-111">Os controles permitem a recalibração de suas propriedades com suporte com base na localidade ou na preferência do usuário.</span><span class="sxs-lookup"><span data-stu-id="73156-111">Controls allow recalibration of their supported properties based upon locale or user preference.</span></span> <span data-ttu-id="73156-112">Um exemplo disso é um controle de termômetro que pode ser definido para exibir a temperatura em Fahrenheit ou Celsius.</span><span class="sxs-lookup"><span data-stu-id="73156-112">An example of this is a thermometer control that can be set to display the temperature in Fahrenheit or Celsius.</span></span>  
  
- <span data-ttu-id="73156-113">Controles que têm valores de intervalo ambíguos, como barras de progresso ou controles deslizantes, devem ter esses valores normalizados.</span><span class="sxs-lookup"><span data-stu-id="73156-113">Controls that have ambiguous range values, such as progress bars or sliders, should have those values normalized.</span></span>  
  
 <span data-ttu-id="73156-114">![Barra de progresso.](./media/uia-rangevaluepattern-progress-bar.PNG "UIA_RangeValuePattern_Progress_Bar")</span><span class="sxs-lookup"><span data-stu-id="73156-114">![Progress bar.](./media/uia-rangevaluepattern-progress-bar.PNG "UIA_RangeValuePattern_Progress_Bar")</span></span>  
<span data-ttu-id="73156-115">Exemplo de uma barra de progresso em que o valor é do tipo inteiro e os valores de propriedade mínimo e máximo são normalizados para 0 e 100, respectivamente</span><span class="sxs-lookup"><span data-stu-id="73156-115">Example of a Progress Bar Where Value Is of Type Integer and Minimum and Maximum Property Values Are Normalized to 0 and 100, Respectively</span></span>  
  
<a name="Required_Members_for_the_IRangeValueProvider"></a>   
## <a name="required-members-for-irangevalueprovider"></a><span data-ttu-id="73156-116">Membros necessários para IRangeValueProvider</span><span class="sxs-lookup"><span data-stu-id="73156-116">Required Members for IRangeValueProvider</span></span>  
  
|<span data-ttu-id="73156-117">Membro necessário</span><span class="sxs-lookup"><span data-stu-id="73156-117">Required member</span></span>|<span data-ttu-id="73156-118">Tipo de membro</span><span class="sxs-lookup"><span data-stu-id="73156-118">Member type</span></span>|<span data-ttu-id="73156-119">{1&gt;Observações&lt;1}</span><span class="sxs-lookup"><span data-stu-id="73156-119">Notes</span></span>|  
|---------------------|-----------------|-----------|  
|<xref:System.Windows.Automation.RangeValuePattern.IsReadOnlyProperty>|<span data-ttu-id="73156-120">Propriedade</span><span class="sxs-lookup"><span data-stu-id="73156-120">Property</span></span>|<span data-ttu-id="73156-121">Nenhum</span><span class="sxs-lookup"><span data-stu-id="73156-121">None</span></span>|  
|<xref:System.Windows.Automation.RangeValuePattern.ValueProperty>|<span data-ttu-id="73156-122">Propriedade</span><span class="sxs-lookup"><span data-stu-id="73156-122">Property</span></span>|<span data-ttu-id="73156-123">Nenhum</span><span class="sxs-lookup"><span data-stu-id="73156-123">None</span></span>|  
|<xref:System.Windows.Automation.RangeValuePattern.LargeChangeProperty>|<span data-ttu-id="73156-124">Propriedade</span><span class="sxs-lookup"><span data-stu-id="73156-124">Property</span></span>|<span data-ttu-id="73156-125">Nenhum</span><span class="sxs-lookup"><span data-stu-id="73156-125">None</span></span>|  
|<xref:System.Windows.Automation.RangeValuePattern.SmallChangeProperty>|<span data-ttu-id="73156-126">Propriedade</span><span class="sxs-lookup"><span data-stu-id="73156-126">Property</span></span>|<span data-ttu-id="73156-127">Nenhum</span><span class="sxs-lookup"><span data-stu-id="73156-127">None</span></span>|  
|<xref:System.Windows.Automation.RangeValuePattern.MaximumProperty>|<span data-ttu-id="73156-128">Propriedade</span><span class="sxs-lookup"><span data-stu-id="73156-128">Property</span></span>|<span data-ttu-id="73156-129">Nenhum</span><span class="sxs-lookup"><span data-stu-id="73156-129">None</span></span>|  
|<xref:System.Windows.Automation.RangeValuePattern.MinimumProperty>|<span data-ttu-id="73156-130">Propriedade</span><span class="sxs-lookup"><span data-stu-id="73156-130">Property</span></span>|<span data-ttu-id="73156-131">Nenhum</span><span class="sxs-lookup"><span data-stu-id="73156-131">None</span></span>|  
|<xref:System.Windows.Automation.RangeValuePattern.SetValue%2A>|<span data-ttu-id="73156-132">{1&gt;Métodos&lt;1}</span><span class="sxs-lookup"><span data-stu-id="73156-132">Methods</span></span>|<span data-ttu-id="73156-133">Nenhum</span><span class="sxs-lookup"><span data-stu-id="73156-133">None</span></span>|  
  
 <span data-ttu-id="73156-134">Este padrão de controle não tem eventos associados.</span><span class="sxs-lookup"><span data-stu-id="73156-134">This control pattern has no associated events.</span></span>  
  
<a name="Exceptions"></a>   
## <a name="exceptions"></a><span data-ttu-id="73156-135">Exceções</span><span class="sxs-lookup"><span data-stu-id="73156-135">Exceptions</span></span>  
 <span data-ttu-id="73156-136">Os provedores devem lançar as seguintes exceções.</span><span class="sxs-lookup"><span data-stu-id="73156-136">Providers must throw the following exceptions.</span></span>  
  
|<span data-ttu-id="73156-137">Tipo de exceção</span><span class="sxs-lookup"><span data-stu-id="73156-137">Exception type</span></span>|<span data-ttu-id="73156-138">Condição</span><span class="sxs-lookup"><span data-stu-id="73156-138">Condition</span></span>|  
|--------------------|---------------|  
|<xref:System.ArgumentOutOfRangeException>|<span data-ttu-id="73156-139"><xref:System.Windows.Automation.RangeValuePattern.SetValue%2A> é chamado com um valor maior que <xref:System.Windows.Automation.RangeValuePattern.MaximumProperty> ou menor que <xref:System.Windows.Automation.RangeValuePattern.MinimumProperty>.</span><span class="sxs-lookup"><span data-stu-id="73156-139"><xref:System.Windows.Automation.RangeValuePattern.SetValue%2A> is called with a value that is either greater than <xref:System.Windows.Automation.RangeValuePattern.MaximumProperty> or less than <xref:System.Windows.Automation.RangeValuePattern.MinimumProperty>.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="73156-140">Consulte também</span><span class="sxs-lookup"><span data-stu-id="73156-140">See also</span></span>

- [<span data-ttu-id="73156-141">Visão geral de padrões de controle de automação da interface do usuário</span><span class="sxs-lookup"><span data-stu-id="73156-141">UI Automation Control Patterns Overview</span></span>](ui-automation-control-patterns-overview.md)
- [<span data-ttu-id="73156-142">Suporte a padrões de controle em um provedor de automação de interface do usuário</span><span class="sxs-lookup"><span data-stu-id="73156-142">Support Control Patterns in a UI Automation Provider</span></span>](support-control-patterns-in-a-ui-automation-provider.md)
- [<span data-ttu-id="73156-143">Padrões de controle de automação de interface do usuário para clientes</span><span class="sxs-lookup"><span data-stu-id="73156-143">UI Automation Control Patterns for Clients</span></span>](ui-automation-control-patterns-for-clients.md)
- [<span data-ttu-id="73156-144">Visão geral de árvore de automação de interface do usuário</span><span class="sxs-lookup"><span data-stu-id="73156-144">UI Automation Tree Overview</span></span>](ui-automation-tree-overview.md)
- [<span data-ttu-id="73156-145">Usar o cache em automação de interface do usuário</span><span class="sxs-lookup"><span data-stu-id="73156-145">Use Caching in UI Automation</span></span>](use-caching-in-ui-automation.md)
