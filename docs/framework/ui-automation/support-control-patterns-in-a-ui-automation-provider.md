---
title: "Padrões de controle de suporte em um provedor de automação da interface do usuário"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-bcl
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- control patterns, supporting in UI Automation provider
- UI Automation, supporting control patterns in provider
ms.assetid: 0d635c35-ffa8-4dc8-bbc9-12fcd5445776
caps.latest.revision: "13"
author: Xansky
ms.author: mhopkins
manager: markl
ms.openlocfilehash: d427c4e3957dd620659f6f5097f4c16caf290d72
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="support-control-patterns-in-a-ui-automation-provider"></a><span data-ttu-id="fa532-102">Padrões de controle de suporte em um provedor de automação da interface do usuário</span><span class="sxs-lookup"><span data-stu-id="fa532-102">Support Control Patterns in a UI Automation Provider</span></span>
> [!NOTE]
>  <span data-ttu-id="fa532-103">Esta documentação destina-se a desenvolvedores do .NET Framework que querem usar as classes da [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] gerenciadas definidas no namespace <xref:System.Windows.Automation>.</span><span class="sxs-lookup"><span data-stu-id="fa532-103">This documentation is intended for .NET Framework developers who want to use the managed [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] classes defined in the <xref:System.Windows.Automation> namespace.</span></span> <span data-ttu-id="fa532-104">Para obter as informações mais recentes sobre a [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], consulte [Windows Automation API: UI Automation](http://go.microsoft.com/fwlink/?LinkID=156746) (API de Automação do Windows: Automação da Interface do Usuário).</span><span class="sxs-lookup"><span data-stu-id="fa532-104">For the latest information about [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], see [Windows Automation API: UI Automation](http://go.microsoft.com/fwlink/?LinkID=156746).</span></span>  
  
 <span data-ttu-id="fa532-105">Este tópico mostra como implementar um ou mais padrões de controle em um provedor de automação de interface do usuário para que os aplicativos cliente possam manipular os controles e obter dados deles.</span><span class="sxs-lookup"><span data-stu-id="fa532-105">This topic shows how to implement one or more control patterns on a UI Automation provider so that client applications can manipulate controls and get data from them.</span></span>  
  
### <a name="support-control-patterns"></a><span data-ttu-id="fa532-106">Suporte a padrões de controle</span><span class="sxs-lookup"><span data-stu-id="fa532-106">Support Control Patterns</span></span>  
  
1.  <span data-ttu-id="fa532-107">Implemente as interfaces apropriadas para os padrões de controle que o elemento deve suportar, como <xref:System.Windows.Automation.Provider.IInvokeProvider> para <xref:System.Windows.Automation.InvokePattern>.</span><span class="sxs-lookup"><span data-stu-id="fa532-107">Implement the appropriate interfaces for the control patterns that the element should support, such as <xref:System.Windows.Automation.Provider.IInvokeProvider> for <xref:System.Windows.Automation.InvokePattern>.</span></span>  
  
2.  <span data-ttu-id="fa532-108">Retornar o objeto que contém a implementação de cada interface de controle na sua implementação de<xref:System.Windows.Automation.Provider.IRawElementProviderSimple.GetPatternProvider%2A?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="fa532-108">Return the object containing your implementation of each control interface in your implementation of <xref:System.Windows.Automation.Provider.IRawElementProviderSimple.GetPatternProvider%2A?displayProperty=nameWithType></span></span>  
  
## <a name="example"></a><span data-ttu-id="fa532-109">Exemplo</span><span class="sxs-lookup"><span data-stu-id="fa532-109">Example</span></span>  
 <span data-ttu-id="fa532-110">O exemplo a seguir mostra uma implementação de <xref:System.Windows.Automation.Provider.ISelectionProvider> para uma caixa de listagem de seleção única personalizado.</span><span class="sxs-lookup"><span data-stu-id="fa532-110">The following example shows an implementation of <xref:System.Windows.Automation.Provider.ISelectionProvider> for a single-selection custom list box.</span></span> <span data-ttu-id="fa532-111">Ela retorna três propriedades e obtém o item atualmente selecionado.</span><span class="sxs-lookup"><span data-stu-id="fa532-111">It returns three properties and gets the currently selected item.</span></span>  
  
 [!code-csharp[UIAFragmentProvider_snip#119](../../../samples/snippets/csharp/VS_Snippets_Wpf/UIAFragmentProvider_snip/CSharp/ListPattern.cs#119)]
 [!code-vb[UIAFragmentProvider_snip#119](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/UIAFragmentProvider_snip/VisualBasic/ListPattern.vb#119)]  
  
## <a name="example"></a><span data-ttu-id="fa532-112">Exemplo</span><span class="sxs-lookup"><span data-stu-id="fa532-112">Example</span></span>  
 <span data-ttu-id="fa532-113">O exemplo a seguir mostra uma implementação de <xref:System.Windows.Automation.Provider.IRawElementProviderSimple.GetPatternProvider%2A> que retorna a classe que implementa <xref:System.Windows.Automation.Provider.ISelectionProvider>.</span><span class="sxs-lookup"><span data-stu-id="fa532-113">The following example shows an implementation of <xref:System.Windows.Automation.Provider.IRawElementProviderSimple.GetPatternProvider%2A> that returns the class implementing <xref:System.Windows.Automation.Provider.ISelectionProvider>.</span></span> <span data-ttu-id="fa532-114">A maioria dos controles de caixa de lista suportaria outros padrões também, mas nesse exemplo uma referência nula (`Nothing` em [!INCLUDE[TLA#tla_visualbnet](../../../includes/tlasharptla-visualbnet-md.md)]) é retornado para todos os outros identificadores de padrão.</span><span class="sxs-lookup"><span data-stu-id="fa532-114">Most list box controls would support other patterns as well, but in this example a null reference (`Nothing` in [!INCLUDE[TLA#tla_visualbnet](../../../includes/tlasharptla-visualbnet-md.md)]) is returned for all other pattern identifiers.</span></span>  
  
 [!code-csharp[UIAFragmentProvider_snip#120](../../../samples/snippets/csharp/VS_Snippets_Wpf/UIAFragmentProvider_snip/CSharp/ListFragment.cs#120)]
 [!code-vb[UIAFragmentProvider_snip#120](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/UIAFragmentProvider_snip/VisualBasic/ListFragment.vb#120)]  
  
## <a name="see-also"></a><span data-ttu-id="fa532-115">Consulte também</span><span class="sxs-lookup"><span data-stu-id="fa532-115">See Also</span></span>  
 [<span data-ttu-id="fa532-116">Visão geral dos provedores de automação de interface do usuário</span><span class="sxs-lookup"><span data-stu-id="fa532-116">UI Automation Providers Overview</span></span>](../../../docs/framework/ui-automation/ui-automation-providers-overview.md)  
 [<span data-ttu-id="fa532-117">Implementação de provedor de Automação da Interface do Usuário no lado do servidor</span><span class="sxs-lookup"><span data-stu-id="fa532-117">Server-Side UI Automation Provider Implementation</span></span>](../../../docs/framework/ui-automation/server-side-ui-automation-provider-implementation.md)
