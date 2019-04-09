---
title: 'Como: Manipular um evento carregado'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- XAML [WPF], Loaded events
- events [WPF], Loaded
- Loaded events [WPF]
ms.assetid: 0cf8d003-8441-4df4-807a-6db09347e829
ms.openlocfilehash: b8cd2f5e9d848cebb712e7b4930ca39efe48ecc0
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59122545"
---
# <a name="how-to-handle-a-loaded-event"></a><span data-ttu-id="f1cc9-102">Como: Manipular um evento carregado</span><span class="sxs-lookup"><span data-stu-id="f1cc9-102">How to: Handle a Loaded Event</span></span>
<span data-ttu-id="f1cc9-103">Este exemplo mostra como tratar o <xref:System.Windows.FrameworkElement.Loaded?displayProperty=nameWithType> eventos e um cenário apropriado para o tratamento desse evento.</span><span class="sxs-lookup"><span data-stu-id="f1cc9-103">This example shows how to handle the <xref:System.Windows.FrameworkElement.Loaded?displayProperty=nameWithType> event, and an appropriate scenario for handling that event.</span></span> <span data-ttu-id="f1cc9-104">O manipulador cria um <xref:System.Windows.Controls.Button> quando a página for carregada.</span><span class="sxs-lookup"><span data-stu-id="f1cc9-104">The handler  creates a <xref:System.Windows.Controls.Button> when the page loads.</span></span>  
  
## <a name="example"></a><span data-ttu-id="f1cc9-105">Exemplo</span><span class="sxs-lookup"><span data-stu-id="f1cc9-105">Example</span></span>  
 <span data-ttu-id="f1cc9-106">O exemplo a seguir usa [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] junto com um arquivo code-behind.</span><span class="sxs-lookup"><span data-stu-id="f1cc9-106">The following example uses [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] together with a code-behind file.</span></span>  
  
 [!code-xaml[FELoaded#XAML](~/samples/snippets/csharp/VS_Snippets_Wpf/FELoaded/CSharp/default.xaml#xaml)]  
  
 [!code-csharp[FELoaded#Handler](~/samples/snippets/csharp/VS_Snippets_Wpf/FELoaded/CSharp/default.xaml.cs#handler)]
 [!code-vb[FELoaded#Handler](~/samples/snippets/visualbasic/VS_Snippets_Wpf/FELoaded/VisualBasic/default.xaml.vb#handler)]  
  
## <a name="see-also"></a><span data-ttu-id="f1cc9-107">Consulte também</span><span class="sxs-lookup"><span data-stu-id="f1cc9-107">See also</span></span>

- <xref:System.Windows.FrameworkElement>
- [<span data-ttu-id="f1cc9-108">Eventos de tempo de vida do objeto</span><span class="sxs-lookup"><span data-stu-id="f1cc9-108">Object Lifetime Events</span></span>](object-lifetime-events.md)
- [<span data-ttu-id="f1cc9-109">Visão geral de eventos roteados</span><span class="sxs-lookup"><span data-stu-id="f1cc9-109">Routed Events Overview</span></span>](routed-events-overview.md)
- [<span data-ttu-id="f1cc9-110">Tópicos explicativos </span><span class="sxs-lookup"><span data-stu-id="f1cc9-110">How-to Topics</span></span>](base-elements-how-to-topics.md)
