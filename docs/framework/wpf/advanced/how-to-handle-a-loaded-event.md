---
title: 'Como: Identificar um evento carregado'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- XAML [WPF], Loaded events
- events [WPF], Loaded
- Loaded events [WPF]
ms.assetid: 0cf8d003-8441-4df4-807a-6db09347e829
ms.openlocfilehash: 187d75c436913140855f4d860eb3b6ad4656f309
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54682937"
---
# <a name="how-to-handle-a-loaded-event"></a><span data-ttu-id="cd976-102">Como: Identificar um evento carregado</span><span class="sxs-lookup"><span data-stu-id="cd976-102">How to: Handle a Loaded Event</span></span>
<span data-ttu-id="cd976-103">Este exemplo mostra como tratar o <xref:System.Windows.FrameworkElement.Loaded?displayProperty=nameWithType> eventos e um cenário apropriado para o tratamento desse evento.</span><span class="sxs-lookup"><span data-stu-id="cd976-103">This example shows how to handle the <xref:System.Windows.FrameworkElement.Loaded?displayProperty=nameWithType> event, and an appropriate scenario for handling that event.</span></span> <span data-ttu-id="cd976-104">O manipulador cria um <xref:System.Windows.Controls.Button> quando a página for carregada.</span><span class="sxs-lookup"><span data-stu-id="cd976-104">The handler  creates a <xref:System.Windows.Controls.Button> when the page loads.</span></span>  
  
## <a name="example"></a><span data-ttu-id="cd976-105">Exemplo</span><span class="sxs-lookup"><span data-stu-id="cd976-105">Example</span></span>  
 <span data-ttu-id="cd976-106">O exemplo a seguir usa [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] junto com um arquivo code-behind.</span><span class="sxs-lookup"><span data-stu-id="cd976-106">The following example uses [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] together with a code-behind file.</span></span>  
  
 [!code-xaml[FELoaded#XAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/FELoaded/CSharp/default.xaml#xaml)]  
  
 [!code-csharp[FELoaded#Handler](../../../../samples/snippets/csharp/VS_Snippets_Wpf/FELoaded/CSharp/default.xaml.cs#handler)]
 [!code-vb[FELoaded#Handler](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/FELoaded/VisualBasic/default.xaml.vb#handler)]  
  
## <a name="see-also"></a><span data-ttu-id="cd976-107">Consulte também</span><span class="sxs-lookup"><span data-stu-id="cd976-107">See also</span></span>
- <xref:System.Windows.FrameworkElement>
- [<span data-ttu-id="cd976-108">Eventos de tempo de vida do objeto</span><span class="sxs-lookup"><span data-stu-id="cd976-108">Object Lifetime Events</span></span>](../../../../docs/framework/wpf/advanced/object-lifetime-events.md)
- [<span data-ttu-id="cd976-109">Visão geral de eventos roteados</span><span class="sxs-lookup"><span data-stu-id="cd976-109">Routed Events Overview</span></span>](../../../../docs/framework/wpf/advanced/routed-events-overview.md)
- [<span data-ttu-id="cd976-110">Tópicos de instruções</span><span class="sxs-lookup"><span data-stu-id="cd976-110">How-to Topics</span></span>](../../../../docs/framework/wpf/advanced/base-elements-how-to-topics.md)
