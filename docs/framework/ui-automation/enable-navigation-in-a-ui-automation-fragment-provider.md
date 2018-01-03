---
title: "Permitir navegação em um fragmento por um provedor de automação de interface do usuário"
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
- UI Automation, enabling navigation in provider
- navigation, enabling in UI Automation provider
ms.assetid: 3cb6092a-58c9-4ca0-84a5-0e54d5d00a0d
caps.latest.revision: "16"
author: Xansky
ms.author: mhopkins
manager: markl
ms.workload: dotnet
ms.openlocfilehash: 40e1c1357637678456bcee0fbbeb41ecff2766d7
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="enable-navigation-in-a-ui-automation-fragment-provider"></a><span data-ttu-id="ddf2c-102">Permitir navegação em um fragmento por um provedor de automação de interface do usuário</span><span class="sxs-lookup"><span data-stu-id="ddf2c-102">Enable Navigation in a UI Automation Fragment Provider</span></span>
> [!NOTE]
>  <span data-ttu-id="ddf2c-103">Esta documentação destina-se a desenvolvedores do .NET Framework que querem usar as classes da [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] gerenciadas definidas no namespace <xref:System.Windows.Automation>.</span><span class="sxs-lookup"><span data-stu-id="ddf2c-103">This documentation is intended for .NET Framework developers who want to use the managed [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] classes defined in the <xref:System.Windows.Automation> namespace.</span></span> <span data-ttu-id="ddf2c-104">Para obter as informações mais recentes sobre a [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], consulte [Windows Automation API: UI Automation](http://go.microsoft.com/fwlink/?LinkID=156746) (API de Automação do Windows: Automação da Interface do Usuário).</span><span class="sxs-lookup"><span data-stu-id="ddf2c-104">For the latest information about [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], see [Windows Automation API: UI Automation](http://go.microsoft.com/fwlink/?LinkID=156746).</span></span>  
  
 <span data-ttu-id="ddf2c-105">Este tópico contém código de exemplo que mostra como habilitar a navegação em um provedor de automação de interface do usuário para um elemento que está dentro de um fragmento.</span><span class="sxs-lookup"><span data-stu-id="ddf2c-105">This topic contains example code that shows how to enable navigation in a UI Automation provider for an element that is within a fragment.</span></span>  
  
## <a name="example"></a><span data-ttu-id="ddf2c-106">Exemplo</span><span class="sxs-lookup"><span data-stu-id="ddf2c-106">Example</span></span>  
 <span data-ttu-id="ddf2c-107">O exemplo de código a seguir implementa <xref:System.Windows.Automation.Provider.IRawElementProviderFragment.Navigate%2A> para um item de lista em uma lista.</span><span class="sxs-lookup"><span data-stu-id="ddf2c-107">The following example code implements <xref:System.Windows.Automation.Provider.IRawElementProviderFragment.Navigate%2A> for a list item within a list.</span></span> <span data-ttu-id="ddf2c-108">O elemento pai é o elemento de caixa de listagem e os elementos irmãos são os outros itens na coleção de listas.</span><span class="sxs-lookup"><span data-stu-id="ddf2c-108">The parent element is the list box element, and the sibling elements are other items in the list collection.</span></span> <span data-ttu-id="ddf2c-109">O método retorna `null` (`Nothing` no Visual Basic) para instruções que não são válidas; nesse caso, <xref:System.Windows.Automation.Provider.NavigateDirection.FirstChild> e <xref:System.Windows.Automation.Provider.NavigateDirection.LastChild>, pois o elemento não tem filhos.</span><span class="sxs-lookup"><span data-stu-id="ddf2c-109">The method returns `null` (`Nothing` in Visual Basic) for directions that are not valid; in this case, <xref:System.Windows.Automation.Provider.NavigateDirection.FirstChild> and <xref:System.Windows.Automation.Provider.NavigateDirection.LastChild>, because the element has no children.</span></span>  
  
 [!code-csharp[UIAFragmentProvider_snip#103](../../../samples/snippets/csharp/VS_Snippets_Wpf/UIAFragmentProvider_snip/CSharp/ListItemFragment.cs#103)]
 [!code-vb[UIAFragmentProvider_snip#103](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/UIAFragmentProvider_snip/VisualBasic/ListItemFragment.vb#103)]  
  
## <a name="see-also"></a><span data-ttu-id="ddf2c-110">Consulte também</span><span class="sxs-lookup"><span data-stu-id="ddf2c-110">See Also</span></span>  
 [<span data-ttu-id="ddf2c-111">Visão geral dos provedores de automação de interface do usuário</span><span class="sxs-lookup"><span data-stu-id="ddf2c-111">UI Automation Providers Overview</span></span>](../../../docs/framework/ui-automation/ui-automation-providers-overview.md)  
 [<span data-ttu-id="ddf2c-112">Implementação de provedor de Automação da Interface do Usuário no lado do servidor</span><span class="sxs-lookup"><span data-stu-id="ddf2c-112">Server-Side UI Automation Provider Implementation</span></span>](../../../docs/framework/ui-automation/server-side-ui-automation-provider-implementation.md)
