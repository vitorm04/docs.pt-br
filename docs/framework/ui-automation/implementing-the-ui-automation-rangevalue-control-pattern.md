---
title: Implementando o padrão de controle RangeValue de interface de usuário
ms.date: 03/30/2017
helpviewer_keywords:
- control patterns, Range Value
- Range Value control pattern
- UI Automation, Range Value control pattern
ms.assetid: 225feaa4-918e-418b-938e-7389338d0a69
ms.openlocfilehash: 57986fa28a7a1bb7f70409b332147ff5b9615ec0
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/17/2019
ms.locfileid: "71043419"
---
# <a name="implementing-the-ui-automation-rangevalue-control-pattern"></a><span data-ttu-id="46fb4-102">Implementando o padrão de controle RangeValue de interface de usuário</span><span class="sxs-lookup"><span data-stu-id="46fb4-102">Implementing the UI Automation RangeValue Control Pattern</span></span>
> [!NOTE]
> <span data-ttu-id="46fb4-103">Esta documentação destina-se a desenvolvedores do .NET Framework que querem usar as classes da [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] gerenciadas definidas no namespace <xref:System.Windows.Automation>.</span><span class="sxs-lookup"><span data-stu-id="46fb4-103">This documentation is intended for .NET Framework developers who want to use the managed [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] classes defined in the <xref:System.Windows.Automation> namespace.</span></span> <span data-ttu-id="46fb4-104">Para obter as informações mais [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]recentes sobre [o, consulte API de automação do Windows: Automação](https://go.microsoft.com/fwlink/?LinkID=156746)da interface do usuário.</span><span class="sxs-lookup"><span data-stu-id="46fb4-104">For the latest information about [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], see [Windows Automation API: UI Automation](https://go.microsoft.com/fwlink/?LinkID=156746).</span></span>  
  
 <span data-ttu-id="46fb4-105">Este tópico apresenta diretrizes e convenções para implementação <xref:System.Windows.Automation.Provider.IRangeValueProvider>, incluindo informações sobre eventos e propriedades.</span><span class="sxs-lookup"><span data-stu-id="46fb4-105">This topic introduces guidelines and conventions for implementing <xref:System.Windows.Automation.Provider.IRangeValueProvider>, including information about events and properties.</span></span> <span data-ttu-id="46fb4-106">Links para referências adicionais são listados no final do tópico.</span><span class="sxs-lookup"><span data-stu-id="46fb4-106">Links to additional references are listed at the end of the topic.</span></span>  
  
 <span data-ttu-id="46fb4-107">O <xref:System.Windows.Automation.RangeValuePattern> padrão de controle é usado para dar suporte a controles que podem ser definidos para um valor dentro de um intervalo.</span><span class="sxs-lookup"><span data-stu-id="46fb4-107">The <xref:System.Windows.Automation.RangeValuePattern> control pattern is used to support controls that can be set to a value within a range.</span></span> <span data-ttu-id="46fb4-108">Para obter exemplos de controles que implementam esse padrão de controle, consulte [mapeamento de padrão de controle para clientes de automação da interface do usuário](control-pattern-mapping-for-ui-automation-clients.md).</span><span class="sxs-lookup"><span data-stu-id="46fb4-108">For examples of controls that implement this control pattern, see [Control Pattern Mapping for UI Automation Clients](control-pattern-mapping-for-ui-automation-clients.md).</span></span>  
  
<a name="Implementation_Guidelines_and_Conventions"></a>   
## <a name="implementation-guidelines-and-conventions"></a><span data-ttu-id="46fb4-109">Diretrizes e convenções de implementação</span><span class="sxs-lookup"><span data-stu-id="46fb4-109">Implementation Guidelines and Conventions</span></span>  
 <span data-ttu-id="46fb4-110">Ao implementar o padrão de controle de valor de intervalo, observe as seguintes diretrizes e convenções:</span><span class="sxs-lookup"><span data-stu-id="46fb4-110">When implementing the Range Value control pattern, note the following guidelines and conventions:</span></span>  
  
- <span data-ttu-id="46fb4-111">Os controles permitem a recalibração de suas propriedades com suporte com base na localidade ou na preferência do usuário.</span><span class="sxs-lookup"><span data-stu-id="46fb4-111">Controls allow recalibration of their supported properties based upon locale or user preference.</span></span> <span data-ttu-id="46fb4-112">Um exemplo disso é um controle de termômetro que pode ser definido para exibir a temperatura em Fahrenheit ou Celsius.</span><span class="sxs-lookup"><span data-stu-id="46fb4-112">An example of this is a thermometer control that can be set to display the temperature in Fahrenheit or Celsius.</span></span>  
  
- <span data-ttu-id="46fb4-113">Controles que têm valores de intervalo ambíguos, como barras de progresso ou controles deslizantes, devem ter esses valores normalizados.</span><span class="sxs-lookup"><span data-stu-id="46fb4-113">Controls that have ambiguous range values, such as progress bars or sliders, should have those values normalized.</span></span>  
  
 <span data-ttu-id="46fb4-114">![Barra de progresso.](./media/uia-rangevaluepattern-progress-bar.PNG "UIA_RangeValuePattern_Progress_Bar")</span><span class="sxs-lookup"><span data-stu-id="46fb4-114">![Progress bar.](./media/uia-rangevaluepattern-progress-bar.PNG "UIA_RangeValuePattern_Progress_Bar")</span></span>  
<span data-ttu-id="46fb4-115">Exemplo de uma barra de progresso em que o valor é do tipo inteiro e os valores de propriedade mínimo e máximo são normalizados para 0 e 100, respectivamente</span><span class="sxs-lookup"><span data-stu-id="46fb4-115">Example of a Progress Bar Where Value Is of Type Integer and Minimum and Maximum Property Values Are Normalized to 0 and 100, Respectively</span></span>  
  
<a name="Required_Members_for_the_IRangeValueProvider"></a>   
## <a name="required-members-for-irangevalueprovider"></a><span data-ttu-id="46fb4-116">Membros necessários para IRangeValueProvider</span><span class="sxs-lookup"><span data-stu-id="46fb4-116">Required Members for IRangeValueProvider</span></span>  
  
|<span data-ttu-id="46fb4-117">Membro necessário</span><span class="sxs-lookup"><span data-stu-id="46fb4-117">Required member</span></span>|<span data-ttu-id="46fb4-118">Tipo de membro</span><span class="sxs-lookup"><span data-stu-id="46fb4-118">Member type</span></span>|<span data-ttu-id="46fb4-119">Observações</span><span class="sxs-lookup"><span data-stu-id="46fb4-119">Notes</span></span>|  
|---------------------|-----------------|-----------|  
|<xref:System.Windows.Automation.RangeValuePattern.IsReadOnlyProperty>|<span data-ttu-id="46fb4-120">Propriedade</span><span class="sxs-lookup"><span data-stu-id="46fb4-120">Property</span></span>|<span data-ttu-id="46fb4-121">Nenhum</span><span class="sxs-lookup"><span data-stu-id="46fb4-121">None</span></span>|  
|<xref:System.Windows.Automation.RangeValuePattern.ValueProperty>|<span data-ttu-id="46fb4-122">Propriedade</span><span class="sxs-lookup"><span data-stu-id="46fb4-122">Property</span></span>|<span data-ttu-id="46fb4-123">Nenhum</span><span class="sxs-lookup"><span data-stu-id="46fb4-123">None</span></span>|  
|<xref:System.Windows.Automation.RangeValuePattern.LargeChangeProperty>|<span data-ttu-id="46fb4-124">Propriedade</span><span class="sxs-lookup"><span data-stu-id="46fb4-124">Property</span></span>|<span data-ttu-id="46fb4-125">Nenhum</span><span class="sxs-lookup"><span data-stu-id="46fb4-125">None</span></span>|  
|<xref:System.Windows.Automation.RangeValuePattern.SmallChangeProperty>|<span data-ttu-id="46fb4-126">Propriedade</span><span class="sxs-lookup"><span data-stu-id="46fb4-126">Property</span></span>|<span data-ttu-id="46fb4-127">Nenhum</span><span class="sxs-lookup"><span data-stu-id="46fb4-127">None</span></span>|  
|<xref:System.Windows.Automation.RangeValuePattern.MaximumProperty>|<span data-ttu-id="46fb4-128">Propriedade</span><span class="sxs-lookup"><span data-stu-id="46fb4-128">Property</span></span>|<span data-ttu-id="46fb4-129">Nenhum</span><span class="sxs-lookup"><span data-stu-id="46fb4-129">None</span></span>|  
|<xref:System.Windows.Automation.RangeValuePattern.MinimumProperty>|<span data-ttu-id="46fb4-130">Propriedade</span><span class="sxs-lookup"><span data-stu-id="46fb4-130">Property</span></span>|<span data-ttu-id="46fb4-131">Nenhum</span><span class="sxs-lookup"><span data-stu-id="46fb4-131">None</span></span>|  
|<xref:System.Windows.Automation.RangeValuePattern.SetValue%2A>|<span data-ttu-id="46fb4-132">Métodos</span><span class="sxs-lookup"><span data-stu-id="46fb4-132">Methods</span></span>|<span data-ttu-id="46fb4-133">Nenhum</span><span class="sxs-lookup"><span data-stu-id="46fb4-133">None</span></span>|  
  
 <span data-ttu-id="46fb4-134">Este padrão de controle não tem eventos associados.</span><span class="sxs-lookup"><span data-stu-id="46fb4-134">This control pattern has no associated events.</span></span>  
  
<a name="Exceptions"></a>   
## <a name="exceptions"></a><span data-ttu-id="46fb4-135">Exceções</span><span class="sxs-lookup"><span data-stu-id="46fb4-135">Exceptions</span></span>  
 <span data-ttu-id="46fb4-136">Os provedores devem lançar as seguintes exceções.</span><span class="sxs-lookup"><span data-stu-id="46fb4-136">Providers must throw the following exceptions.</span></span>  
  
|<span data-ttu-id="46fb4-137">Tipo de exceção</span><span class="sxs-lookup"><span data-stu-id="46fb4-137">Exception type</span></span>|<span data-ttu-id="46fb4-138">Condição</span><span class="sxs-lookup"><span data-stu-id="46fb4-138">Condition</span></span>|  
|--------------------|---------------|  
|<xref:System.ArgumentOutOfRangeException>|<span data-ttu-id="46fb4-139"><xref:System.Windows.Automation.RangeValuePattern.SetValue%2A>é chamado com um valor que é maior <xref:System.Windows.Automation.RangeValuePattern.MaximumProperty> ou menor que. <xref:System.Windows.Automation.RangeValuePattern.MinimumProperty></span><span class="sxs-lookup"><span data-stu-id="46fb4-139"><xref:System.Windows.Automation.RangeValuePattern.SetValue%2A> is called with a value that is either greater than <xref:System.Windows.Automation.RangeValuePattern.MaximumProperty> or less than <xref:System.Windows.Automation.RangeValuePattern.MinimumProperty>.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="46fb4-140">Consulte também</span><span class="sxs-lookup"><span data-stu-id="46fb4-140">See also</span></span>

- [<span data-ttu-id="46fb4-141">Visão geral de padrões de controle de automação da interface do usuário</span><span class="sxs-lookup"><span data-stu-id="46fb4-141">UI Automation Control Patterns Overview</span></span>](ui-automation-control-patterns-overview.md)
- [<span data-ttu-id="46fb4-142">Suporte a padrões de controle em um provedor de automação de interface do usuário</span><span class="sxs-lookup"><span data-stu-id="46fb4-142">Support Control Patterns in a UI Automation Provider</span></span>](support-control-patterns-in-a-ui-automation-provider.md)
- [<span data-ttu-id="46fb4-143">Padrões de controle de automação de interface do usuário para clientes</span><span class="sxs-lookup"><span data-stu-id="46fb4-143">UI Automation Control Patterns for Clients</span></span>](ui-automation-control-patterns-for-clients.md)
- [<span data-ttu-id="46fb4-144">Visão geral de árvore de automação de interface do usuário</span><span class="sxs-lookup"><span data-stu-id="46fb4-144">UI Automation Tree Overview</span></span>](ui-automation-tree-overview.md)
- [<span data-ttu-id="46fb4-145">Usar o cache em automação de interface do usuário</span><span class="sxs-lookup"><span data-stu-id="46fb4-145">Use Caching in UI Automation</span></span>](use-caching-in-ui-automation.md)
