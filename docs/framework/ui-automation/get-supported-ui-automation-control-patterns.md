---
title: Obter Padrões de Controle de Automação de IU Suportados
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- control patterns, getting
- UI Automation, getting control patterns
- getting, control patterns
ms.assetid: 006c54c9-50bf-48d9-a855-9d62eb95603a
ms.openlocfilehash: 8987526a572d3c9a239885407c19bd1ad3674f0e
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69968986"
---
# <a name="get-supported-ui-automation-control-patterns"></a><span data-ttu-id="23ed3-102">Obter Padrões de Controle de Automação de IU Suportados</span><span class="sxs-lookup"><span data-stu-id="23ed3-102">Get Supported UI Automation Control Patterns</span></span>
> [!NOTE]
> <span data-ttu-id="23ed3-103">Esta documentação destina-se a desenvolvedores do .NET Framework que querem usar as classes da [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] gerenciadas definidas no namespace <xref:System.Windows.Automation>.</span><span class="sxs-lookup"><span data-stu-id="23ed3-103">This documentation is intended for .NET Framework developers who want to use the managed [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] classes defined in the <xref:System.Windows.Automation> namespace.</span></span> <span data-ttu-id="23ed3-104">Para obter as informações mais [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]recentes sobre [o, consulte API de automação do Windows: Automação](https://go.microsoft.com/fwlink/?LinkID=156746)da interface do usuário.</span><span class="sxs-lookup"><span data-stu-id="23ed3-104">For the latest information about [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], see [Windows Automation API: UI Automation](https://go.microsoft.com/fwlink/?LinkID=156746).</span></span>  
  
 <span data-ttu-id="23ed3-105">Este tópico mostra como recuperar objetos de padrão de controle [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] de elementos.</span><span class="sxs-lookup"><span data-stu-id="23ed3-105">This topic shows how to retrieve control pattern objects from [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] elements.</span></span>  
  
### <a name="obtain-all-control-patterns"></a><span data-ttu-id="23ed3-106">Obter todos os padrões de controle</span><span class="sxs-lookup"><span data-stu-id="23ed3-106">Obtain All Control Patterns</span></span>  
  
1. <span data-ttu-id="23ed3-107">Obtenha os <xref:System.Windows.Automation.AutomationElement> padrões de controle cujos quais você está interessado.</span><span class="sxs-lookup"><span data-stu-id="23ed3-107">Get the <xref:System.Windows.Automation.AutomationElement> whose control patterns you are interested in.</span></span>  
  
2. <span data-ttu-id="23ed3-108">Chame <xref:System.Windows.Automation.AutomationElement.GetSupportedPatterns%2A> para obter todos os padrões de controle do elemento.</span><span class="sxs-lookup"><span data-stu-id="23ed3-108">Call <xref:System.Windows.Automation.AutomationElement.GetSupportedPatterns%2A> to get all control patterns from the element.</span></span>  
  
> [!CAUTION]
>  <span data-ttu-id="23ed3-109">É altamente recomendável que um cliente não use <xref:System.Windows.Automation.AutomationElement.GetSupportedPatterns%2A>.</span><span class="sxs-lookup"><span data-stu-id="23ed3-109">It is strongly recommended that a client not use <xref:System.Windows.Automation.AutomationElement.GetSupportedPatterns%2A>.</span></span> <span data-ttu-id="23ed3-110">O desempenho pode ser seriamente afetado, pois esse método <xref:System.Windows.Automation.AutomationElement.GetCurrentPattern%2A> chama internamente para cada padrão de controle existente.</span><span class="sxs-lookup"><span data-stu-id="23ed3-110">Performance can be severely affected as this method calls <xref:System.Windows.Automation.AutomationElement.GetCurrentPattern%2A> internally for each existing control pattern.</span></span> <span data-ttu-id="23ed3-111">Se possível, um cliente deve chamar <xref:System.Windows.Automation.AutomationElement.GetCurrentPattern%2A> para os principais padrões de interesse.</span><span class="sxs-lookup"><span data-stu-id="23ed3-111">If possible, a client should call <xref:System.Windows.Automation.AutomationElement.GetCurrentPattern%2A> for the key patterns of interest.</span></span>  
  
### <a name="obtain-a-specific-control-pattern"></a><span data-ttu-id="23ed3-112">Obter um padrão de controle específico</span><span class="sxs-lookup"><span data-stu-id="23ed3-112">Obtain a Specific Control Pattern</span></span>  
  
1. <span data-ttu-id="23ed3-113">Obtenha os <xref:System.Windows.Automation.AutomationElement> padrões de controle cujos quais você está interessado.</span><span class="sxs-lookup"><span data-stu-id="23ed3-113">Get the <xref:System.Windows.Automation.AutomationElement> whose control patterns you are interested in.</span></span>  
  
2. <span data-ttu-id="23ed3-114">Chame <xref:System.Windows.Automation.AutomationElement.GetCurrentPattern%2A> ou<xref:System.Windows.Automation.AutomationElement.TryGetCurrentPattern%2A> para consultar um padrão específico.</span><span class="sxs-lookup"><span data-stu-id="23ed3-114">Call <xref:System.Windows.Automation.AutomationElement.GetCurrentPattern%2A> or <xref:System.Windows.Automation.AutomationElement.TryGetCurrentPattern%2A> to query for a specific pattern.</span></span> <span data-ttu-id="23ed3-115">Esses métodos são semelhantes, mas se o padrão não for encontrado, <xref:System.Windows.Automation.AutomationElement.GetCurrentPattern%2A> o gerará uma exceção <xref:System.Windows.Automation.AutomationElement.TryGetCurrentPattern%2A> e `false`retornará.</span><span class="sxs-lookup"><span data-stu-id="23ed3-115">These methods are similar, but if the pattern is not found, <xref:System.Windows.Automation.AutomationElement.GetCurrentPattern%2A> raises an exception, and <xref:System.Windows.Automation.AutomationElement.TryGetCurrentPattern%2A> returns `false`.</span></span>  
  
## <a name="example"></a><span data-ttu-id="23ed3-116">Exemplo</span><span class="sxs-lookup"><span data-stu-id="23ed3-116">Example</span></span>  
 <span data-ttu-id="23ed3-117">O exemplo a seguir recupera <xref:System.Windows.Automation.AutomationElement> um para um item de lista e obtém <xref:System.Windows.Automation.SelectionItemPattern> um desse elemento.</span><span class="sxs-lookup"><span data-stu-id="23ed3-117">The following example retrieves an <xref:System.Windows.Automation.AutomationElement> for a list item and obtains a <xref:System.Windows.Automation.SelectionItemPattern> from that element.</span></span>  
  
 [!code-csharp[UIAClient_snip#103](../../../samples/snippets/csharp/VS_Snippets_Wpf/UIAClient_snip/CSharp/ClientForm.cs#103)]
 [!code-vb[UIAClient_snip#103](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/UIAClient_snip/VisualBasic/ClientForm.vb#103)]  
  
## <a name="see-also"></a><span data-ttu-id="23ed3-118">Consulte também</span><span class="sxs-lookup"><span data-stu-id="23ed3-118">See also</span></span>

- [<span data-ttu-id="23ed3-119">Padrões de controle de automação de interface do usuário para clientes</span><span class="sxs-lookup"><span data-stu-id="23ed3-119">UI Automation Control Patterns for Clients</span></span>](../../../docs/framework/ui-automation/ui-automation-control-patterns-for-clients.md)
