---
title: Padrões de controle de suporte em um provedor de automação da interface do usuário
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- control patterns, supporting in UI Automation provider
- UI Automation, supporting control patterns in provider
ms.assetid: 0d635c35-ffa8-4dc8-bbc9-12fcd5445776
ms.openlocfilehash: 67f37dfe1fe63f2130646cb227fec855ccc7bf75
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/17/2019
ms.locfileid: "71042597"
---
# <a name="support-control-patterns-in-a-ui-automation-provider"></a><span data-ttu-id="fc7fe-102">Padrões de controle de suporte em um provedor de automação da interface do usuário</span><span class="sxs-lookup"><span data-stu-id="fc7fe-102">Support Control Patterns in a UI Automation Provider</span></span>

> [!NOTE]
> <span data-ttu-id="fc7fe-103">Esta documentação destina-se a desenvolvedores do .NET Framework que querem usar as classes da [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] gerenciadas definidas no namespace <xref:System.Windows.Automation>.</span><span class="sxs-lookup"><span data-stu-id="fc7fe-103">This documentation is intended for .NET Framework developers who want to use the managed [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] classes defined in the <xref:System.Windows.Automation> namespace.</span></span> <span data-ttu-id="fc7fe-104">Para obter as informações mais [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]recentes sobre [o, consulte API de automação do Windows: Automação](https://go.microsoft.com/fwlink/?LinkID=156746)da interface do usuário.</span><span class="sxs-lookup"><span data-stu-id="fc7fe-104">For the latest information about [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], see [Windows Automation API: UI Automation](https://go.microsoft.com/fwlink/?LinkID=156746).</span></span>

<span data-ttu-id="fc7fe-105">Este tópico mostra como implementar um ou mais padrões de controle em um provedor de automação de interface do usuário para que os aplicativos cliente possam manipular controles e obter dados deles.</span><span class="sxs-lookup"><span data-stu-id="fc7fe-105">This topic shows how to implement one or more control patterns on a UI Automation provider so that client applications can manipulate controls and get data from them.</span></span>

## <a name="support-control-patterns"></a><span data-ttu-id="fc7fe-106">Padrões de controle de suporte</span><span class="sxs-lookup"><span data-stu-id="fc7fe-106">Support Control Patterns</span></span>

1. <span data-ttu-id="fc7fe-107">Implemente as interfaces apropriadas para os padrões de controle aos quais o elemento deve dar <xref:System.Windows.Automation.Provider.IInvokeProvider> suporte <xref:System.Windows.Automation.InvokePattern>, como para.</span><span class="sxs-lookup"><span data-stu-id="fc7fe-107">Implement the appropriate interfaces for the control patterns that the element should support, such as <xref:System.Windows.Automation.Provider.IInvokeProvider> for <xref:System.Windows.Automation.InvokePattern>.</span></span>

2. <span data-ttu-id="fc7fe-108">Retornar o objeto que contém a implementação de cada interface de controle em sua implementação de<xref:System.Windows.Automation.Provider.IRawElementProviderSimple.GetPatternProvider%2A?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="fc7fe-108">Return the object containing your implementation of each control interface in your implementation of <xref:System.Windows.Automation.Provider.IRawElementProviderSimple.GetPatternProvider%2A?displayProperty=nameWithType></span></span>

## <a name="example"></a><span data-ttu-id="fc7fe-109">Exemplo</span><span class="sxs-lookup"><span data-stu-id="fc7fe-109">Example</span></span>

<span data-ttu-id="fc7fe-110">O exemplo a seguir mostra uma implementação <xref:System.Windows.Automation.Provider.ISelectionProvider> de para uma caixa de listagem personalizada de seleção única.</span><span class="sxs-lookup"><span data-stu-id="fc7fe-110">The following example shows an implementation of <xref:System.Windows.Automation.Provider.ISelectionProvider> for a single-selection custom list box.</span></span> <span data-ttu-id="fc7fe-111">Ele retorna três propriedades e Obtém o item selecionado no momento.</span><span class="sxs-lookup"><span data-stu-id="fc7fe-111">It returns three properties and gets the currently selected item.</span></span>

[!code-csharp[UIAFragmentProvider_snip#119](../../../samples/snippets/csharp/VS_Snippets_Wpf/UIAFragmentProvider_snip/CSharp/ListPattern.cs#119)]
[!code-vb[UIAFragmentProvider_snip#119](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/UIAFragmentProvider_snip/VisualBasic/ListPattern.vb#119)]

## <a name="example"></a><span data-ttu-id="fc7fe-112">Exemplo</span><span class="sxs-lookup"><span data-stu-id="fc7fe-112">Example</span></span>

<span data-ttu-id="fc7fe-113">O exemplo a seguir mostra uma implementação <xref:System.Windows.Automation.Provider.IRawElementProviderSimple.GetPatternProvider%2A> de que retorna a classe <xref:System.Windows.Automation.Provider.ISelectionProvider>que está implementando.</span><span class="sxs-lookup"><span data-stu-id="fc7fe-113">The following example shows an implementation of <xref:System.Windows.Automation.Provider.IRawElementProviderSimple.GetPatternProvider%2A> that returns the class implementing <xref:System.Windows.Automation.Provider.ISelectionProvider>.</span></span> <span data-ttu-id="fc7fe-114">A maioria dos controles de caixa de listagem também ofereceria suporte a outros padrões, mas neste exemplo`Nothing` uma referência nula (no Microsoft Visual Basic .net) é retornada para todos os outros identificadores de padrão.</span><span class="sxs-lookup"><span data-stu-id="fc7fe-114">Most list box controls would support other patterns as well, but in this example a null reference (`Nothing` in Microsoft Visual Basic .NET) is returned for all other pattern identifiers.</span></span>

[!code-csharp[UIAFragmentProvider_snip#120](../../../samples/snippets/csharp/VS_Snippets_Wpf/UIAFragmentProvider_snip/CSharp/ListFragment.cs#120)]
[!code-vb[UIAFragmentProvider_snip#120](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/UIAFragmentProvider_snip/VisualBasic/ListFragment.vb#120)]

## <a name="see-also"></a><span data-ttu-id="fc7fe-115">Consulte também</span><span class="sxs-lookup"><span data-stu-id="fc7fe-115">See also</span></span>

- [<span data-ttu-id="fc7fe-116">Visão geral dos provedores de automação de interface do usuário</span><span class="sxs-lookup"><span data-stu-id="fc7fe-116">UI Automation Providers Overview</span></span>](ui-automation-providers-overview.md)
- [<span data-ttu-id="fc7fe-117">Implementação de provedor de Automação da Interface do Usuário no lado do servidor</span><span class="sxs-lookup"><span data-stu-id="fc7fe-117">Server-Side UI Automation Provider Implementation</span></span>](server-side-ui-automation-provider-implementation.md)
