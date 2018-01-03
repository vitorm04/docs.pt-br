---
title: "Implementando o padrão de controle RangeValue de interface de usuário "
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-bcl
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- control patterns, Range Value
- Range Value control pattern
- UI Automation, Range Value control pattern
ms.assetid: 225feaa4-918e-418b-938e-7389338d0a69
caps.latest.revision: "19"
author: Xansky
ms.author: mhopkins
manager: markl
ms.workload: dotnet
ms.openlocfilehash: a53f5f802d451d7575188d4687b6d88f96ec64fb
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="implementing-the-ui-automation-rangevalue-control-pattern"></a><span data-ttu-id="a7b49-102">Implementando o padrão de controle RangeValue de interface de usuário</span><span class="sxs-lookup"><span data-stu-id="a7b49-102">Implementing the UI Automation RangeValue Control Pattern</span></span>
> [!NOTE]
>  <span data-ttu-id="a7b49-103">Esta documentação destina-se a desenvolvedores do .NET Framework que querem usar as classes da [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] gerenciadas definidas no namespace <xref:System.Windows.Automation>.</span><span class="sxs-lookup"><span data-stu-id="a7b49-103">This documentation is intended for .NET Framework developers who want to use the managed [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] classes defined in the <xref:System.Windows.Automation> namespace.</span></span> <span data-ttu-id="a7b49-104">Para obter as informações mais recentes sobre a [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], consulte [Windows Automation API: UI Automation](http://go.microsoft.com/fwlink/?LinkID=156746) (API de Automação do Windows: Automação da Interface do Usuário).</span><span class="sxs-lookup"><span data-stu-id="a7b49-104">For the latest information about [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], see [Windows Automation API: UI Automation](http://go.microsoft.com/fwlink/?LinkID=156746).</span></span>  
  
 <span data-ttu-id="a7b49-105">Este tópico apresenta diretrizes e convenções para implementar <xref:System.Windows.Automation.Provider.IRangeValueProvider>, incluindo informações sobre propriedades e eventos.</span><span class="sxs-lookup"><span data-stu-id="a7b49-105">This topic introduces guidelines and conventions for implementing <xref:System.Windows.Automation.Provider.IRangeValueProvider>, including information about events and properties.</span></span> <span data-ttu-id="a7b49-106">Links para referências adicionais são listadas no final do tópico.</span><span class="sxs-lookup"><span data-stu-id="a7b49-106">Links to additional references are listed at the end of the topic.</span></span>  
  
 <span data-ttu-id="a7b49-107">O <xref:System.Windows.Automation.RangeValuePattern> padrão de controle é usado para oferecer suporte aos controles que podem ser definidos para um valor dentro do intervalo.</span><span class="sxs-lookup"><span data-stu-id="a7b49-107">The <xref:System.Windows.Automation.RangeValuePattern> control pattern is used to support controls that can be set to a value within a range.</span></span> <span data-ttu-id="a7b49-108">Para obter exemplos de controles que implementam este padrão de controle, consulte [mapeamento de padrão de controle para clientes de automação de interface do usuário](../../../docs/framework/ui-automation/control-pattern-mapping-for-ui-automation-clients.md).</span><span class="sxs-lookup"><span data-stu-id="a7b49-108">For examples of controls that implement this control pattern, see [Control Pattern Mapping for UI Automation Clients](../../../docs/framework/ui-automation/control-pattern-mapping-for-ui-automation-clients.md).</span></span>  
  
<a name="Implementation_Guidelines_and_Conventions"></a>   
## <a name="implementation-guidelines-and-conventions"></a><span data-ttu-id="a7b49-109">Convenções e diretrizes de implementação</span><span class="sxs-lookup"><span data-stu-id="a7b49-109">Implementation Guidelines and Conventions</span></span>  
 <span data-ttu-id="a7b49-110">Ao implementar o padrão de controle de valor de intervalo, observe as seguintes diretrizes e convenções:</span><span class="sxs-lookup"><span data-stu-id="a7b49-110">When implementing the Range Value control pattern, note the following guidelines and conventions:</span></span>  
  
-   <span data-ttu-id="a7b49-111">Controles permitem recalibragem de suas propriedades com suporte com base na preferência de localidade ou usuário.</span><span class="sxs-lookup"><span data-stu-id="a7b49-111">Controls allow recalibration of their supported properties based upon locale or user preference.</span></span> <span data-ttu-id="a7b49-112">Um exemplo disso é um controle de termômetro que pode ser definido para exibir a temperatura em Fahrenheit ou em Celsius.</span><span class="sxs-lookup"><span data-stu-id="a7b49-112">An example of this is a thermometer control that can be set to display the temperature in Fahrenheit or Celsius.</span></span>  
  
-   <span data-ttu-id="a7b49-113">Controles que têm intervalos de valores ambíguos, como barras de progresso ou controles deslizantes, devem ter esses valores normalizados.</span><span class="sxs-lookup"><span data-stu-id="a7b49-113">Controls that have ambiguous range values, such as progress bars or sliders, should have those values normalized.</span></span>  
  
 <span data-ttu-id="a7b49-114">![Barra de progresso. ] (../../../docs/framework/ui-automation/media/uia-rangevaluepattern-progress-bar.PNG "UIA_RangeValuePattern_Progress_Bar")</span><span class="sxs-lookup"><span data-stu-id="a7b49-114">![Progress bar.](../../../docs/framework/ui-automation/media/uia-rangevaluepattern-progress-bar.PNG "UIA_RangeValuePattern_Progress_Bar")</span></span>  
<span data-ttu-id="a7b49-115">Exemplo de uma barra de progresso em que o valor é do tipo inteiro e valores de propriedade mínimo e máximo são normalizados para 0 e 100, respectivamente</span><span class="sxs-lookup"><span data-stu-id="a7b49-115">Example of a Progress Bar Where Value Is of Type Integer and Minimum and Maximum Property Values Are Normalized to 0 and 100, Respectively</span></span>  
  
<a name="Required_Members_for_the_IRangeValueProvider"></a>   
## <a name="required-members-for-irangevalueprovider"></a><span data-ttu-id="a7b49-116">Membros necessários para IRangeValueProvider</span><span class="sxs-lookup"><span data-stu-id="a7b49-116">Required Members for IRangeValueProvider</span></span>  
  
|<span data-ttu-id="a7b49-117">Membro necessário</span><span class="sxs-lookup"><span data-stu-id="a7b49-117">Required member</span></span>|<span data-ttu-id="a7b49-118">Tipo de membro</span><span class="sxs-lookup"><span data-stu-id="a7b49-118">Member type</span></span>|<span data-ttu-id="a7b49-119">Observações</span><span class="sxs-lookup"><span data-stu-id="a7b49-119">Notes</span></span>|  
|---------------------|-----------------|-----------|  
|<xref:System.Windows.Automation.RangeValuePattern.IsReadOnlyProperty>|<span data-ttu-id="a7b49-120">Propriedade</span><span class="sxs-lookup"><span data-stu-id="a7b49-120">Property</span></span>|<span data-ttu-id="a7b49-121">Nenhum</span><span class="sxs-lookup"><span data-stu-id="a7b49-121">None</span></span>|  
|<xref:System.Windows.Automation.RangeValuePattern.ValueProperty>|<span data-ttu-id="a7b49-122">Propriedade</span><span class="sxs-lookup"><span data-stu-id="a7b49-122">Property</span></span>|<span data-ttu-id="a7b49-123">Nenhum</span><span class="sxs-lookup"><span data-stu-id="a7b49-123">None</span></span>|  
|<xref:System.Windows.Automation.RangeValuePattern.LargeChangeProperty>|<span data-ttu-id="a7b49-124">Propriedade</span><span class="sxs-lookup"><span data-stu-id="a7b49-124">Property</span></span>|<span data-ttu-id="a7b49-125">Nenhum</span><span class="sxs-lookup"><span data-stu-id="a7b49-125">None</span></span>|  
|<xref:System.Windows.Automation.RangeValuePattern.SmallChangeProperty>|<span data-ttu-id="a7b49-126">Propriedade</span><span class="sxs-lookup"><span data-stu-id="a7b49-126">Property</span></span>|<span data-ttu-id="a7b49-127">Nenhum</span><span class="sxs-lookup"><span data-stu-id="a7b49-127">None</span></span>|  
|<xref:System.Windows.Automation.RangeValuePattern.MaximumProperty>|<span data-ttu-id="a7b49-128">Propriedade</span><span class="sxs-lookup"><span data-stu-id="a7b49-128">Property</span></span>|<span data-ttu-id="a7b49-129">Nenhum</span><span class="sxs-lookup"><span data-stu-id="a7b49-129">None</span></span>|  
|<xref:System.Windows.Automation.RangeValuePattern.MinimumProperty>|<span data-ttu-id="a7b49-130">Propriedade</span><span class="sxs-lookup"><span data-stu-id="a7b49-130">Property</span></span>|<span data-ttu-id="a7b49-131">Nenhum</span><span class="sxs-lookup"><span data-stu-id="a7b49-131">None</span></span>|  
|<xref:System.Windows.Automation.RangeValuePattern.SetValue%2A>|<span data-ttu-id="a7b49-132">Métodos</span><span class="sxs-lookup"><span data-stu-id="a7b49-132">Methods</span></span>|<span data-ttu-id="a7b49-133">Nenhum</span><span class="sxs-lookup"><span data-stu-id="a7b49-133">None</span></span>|  
  
 <span data-ttu-id="a7b49-134">Esse padrão de controle não possui eventos associados.</span><span class="sxs-lookup"><span data-stu-id="a7b49-134">This control pattern has no associated events.</span></span>  
  
<a name="Exceptions"></a>   
## <a name="exceptions"></a><span data-ttu-id="a7b49-135">Exceções</span><span class="sxs-lookup"><span data-stu-id="a7b49-135">Exceptions</span></span>  
 <span data-ttu-id="a7b49-136">Provedores devem lançar as exceções a seguir.</span><span class="sxs-lookup"><span data-stu-id="a7b49-136">Providers must throw the following exceptions.</span></span>  
  
|<span data-ttu-id="a7b49-137">Tipo de exceção</span><span class="sxs-lookup"><span data-stu-id="a7b49-137">Exception type</span></span>|<span data-ttu-id="a7b49-138">Condição</span><span class="sxs-lookup"><span data-stu-id="a7b49-138">Condition</span></span>|  
|--------------------|---------------|  
|<xref:System.ArgumentOutOfRangeException>|<span data-ttu-id="a7b49-139"><xref:System.Windows.Automation.RangeValuePattern.SetValue%2A>é chamado com um valor que seja maior do que <xref:System.Windows.Automation.RangeValuePattern.MaximumProperty> ou menor que <xref:System.Windows.Automation.RangeValuePattern.MinimumProperty>.</span><span class="sxs-lookup"><span data-stu-id="a7b49-139"><xref:System.Windows.Automation.RangeValuePattern.SetValue%2A> is called with a value that is either greater than <xref:System.Windows.Automation.RangeValuePattern.MaximumProperty> or less than <xref:System.Windows.Automation.RangeValuePattern.MinimumProperty>.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="a7b49-140">Consulte também</span><span class="sxs-lookup"><span data-stu-id="a7b49-140">See Also</span></span>  
 [<span data-ttu-id="a7b49-141">Visão geral de padrões de controle de automação da interface do usuário</span><span class="sxs-lookup"><span data-stu-id="a7b49-141">UI Automation Control Patterns Overview</span></span>](../../../docs/framework/ui-automation/ui-automation-control-patterns-overview.md)  
 [<span data-ttu-id="a7b49-142">Suporte a padrões de controle em um provedor de automação de interface do usuário</span><span class="sxs-lookup"><span data-stu-id="a7b49-142">Support Control Patterns in a UI Automation Provider</span></span>](../../../docs/framework/ui-automation/support-control-patterns-in-a-ui-automation-provider.md)  
 [<span data-ttu-id="a7b49-143">Padrões de controle de automação de interface do usuário para clientes</span><span class="sxs-lookup"><span data-stu-id="a7b49-143">UI Automation Control Patterns for Clients</span></span>](../../../docs/framework/ui-automation/ui-automation-control-patterns-for-clients.md)  
 [<span data-ttu-id="a7b49-144">Visão geral de árvore de automação de interface do usuário</span><span class="sxs-lookup"><span data-stu-id="a7b49-144">UI Automation Tree Overview</span></span>](../../../docs/framework/ui-automation/ui-automation-tree-overview.md)  
 [<span data-ttu-id="a7b49-145">Usar o cache em automação de interface do usuário</span><span class="sxs-lookup"><span data-stu-id="a7b49-145">Use Caching in UI Automation</span></span>](../../../docs/framework/ui-automation/use-caching-in-ui-automation.md)
