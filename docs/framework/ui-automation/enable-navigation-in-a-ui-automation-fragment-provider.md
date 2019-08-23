---
title: Permitir navegação em um fragmento por um provedor de automação de interface do usuário
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- UI Automation, enabling navigation in provider
- navigation, enabling in UI Automation provider
ms.assetid: 3cb6092a-58c9-4ca0-84a5-0e54d5d00a0d
ms.openlocfilehash: 6410a0f8a991f1dc21a298972182ec630723f627
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69932604"
---
# <a name="enable-navigation-in-a-ui-automation-fragment-provider"></a><span data-ttu-id="7699a-102">Permitir navegação em um fragmento por um provedor de automação de interface do usuário</span><span class="sxs-lookup"><span data-stu-id="7699a-102">Enable Navigation in a UI Automation Fragment Provider</span></span>
> [!NOTE]
> <span data-ttu-id="7699a-103">Esta documentação destina-se a desenvolvedores do .NET Framework que querem usar as classes da [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] gerenciadas definidas no namespace <xref:System.Windows.Automation>.</span><span class="sxs-lookup"><span data-stu-id="7699a-103">This documentation is intended for .NET Framework developers who want to use the managed [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] classes defined in the <xref:System.Windows.Automation> namespace.</span></span> <span data-ttu-id="7699a-104">Para obter as informações mais [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]recentes sobre [o, consulte API de automação do Windows: Automação](https://go.microsoft.com/fwlink/?LinkID=156746)da interface do usuário.</span><span class="sxs-lookup"><span data-stu-id="7699a-104">For the latest information about [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], see [Windows Automation API: UI Automation](https://go.microsoft.com/fwlink/?LinkID=156746).</span></span>  
  
 <span data-ttu-id="7699a-105">Este tópico contém um código de exemplo que mostra como habilitar a navegação em um provedor de automação de interface do usuário para um elemento que está dentro de um fragmento.</span><span class="sxs-lookup"><span data-stu-id="7699a-105">This topic contains example code that shows how to enable navigation in a UI Automation provider for an element that is within a fragment.</span></span>  
  
## <a name="example"></a><span data-ttu-id="7699a-106">Exemplo</span><span class="sxs-lookup"><span data-stu-id="7699a-106">Example</span></span>  
 <span data-ttu-id="7699a-107">O código de exemplo a <xref:System.Windows.Automation.Provider.IRawElementProviderFragment.Navigate%2A> seguir implementa para um item de lista em uma lista.</span><span class="sxs-lookup"><span data-stu-id="7699a-107">The following example code implements <xref:System.Windows.Automation.Provider.IRawElementProviderFragment.Navigate%2A> for a list item within a list.</span></span> <span data-ttu-id="7699a-108">O elemento pai é o elemento da caixa de listagem e os elementos irmãos são outros itens na coleção de listas.</span><span class="sxs-lookup"><span data-stu-id="7699a-108">The parent element is the list box element, and the sibling elements are other items in the list collection.</span></span> <span data-ttu-id="7699a-109">O método retorna `null` (`Nothing` em Visual Basic) para direções que não são válidas; nesse caso, <xref:System.Windows.Automation.Provider.NavigateDirection.FirstChild> e <xref:System.Windows.Automation.Provider.NavigateDirection.LastChild>, porque o elemento não tem filhos.</span><span class="sxs-lookup"><span data-stu-id="7699a-109">The method returns `null` (`Nothing` in Visual Basic) for directions that are not valid; in this case, <xref:System.Windows.Automation.Provider.NavigateDirection.FirstChild> and <xref:System.Windows.Automation.Provider.NavigateDirection.LastChild>, because the element has no children.</span></span>  
  
 [!code-csharp[UIAFragmentProvider_snip#103](../../../samples/snippets/csharp/VS_Snippets_Wpf/UIAFragmentProvider_snip/CSharp/ListItemFragment.cs#103)]
 [!code-vb[UIAFragmentProvider_snip#103](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/UIAFragmentProvider_snip/VisualBasic/ListItemFragment.vb#103)]  
  
## <a name="see-also"></a><span data-ttu-id="7699a-110">Consulte também</span><span class="sxs-lookup"><span data-stu-id="7699a-110">See also</span></span>

- [<span data-ttu-id="7699a-111">Visão geral dos provedores de automação de interface do usuário</span><span class="sxs-lookup"><span data-stu-id="7699a-111">UI Automation Providers Overview</span></span>](../../../docs/framework/ui-automation/ui-automation-providers-overview.md)
- [<span data-ttu-id="7699a-112">Implementação de provedor de Automação da Interface do Usuário no lado do servidor</span><span class="sxs-lookup"><span data-stu-id="7699a-112">Server-Side UI Automation Provider Implementation</span></span>](../../../docs/framework/ui-automation/server-side-ui-automation-provider-implementation.md)
