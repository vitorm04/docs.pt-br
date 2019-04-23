---
title: 'Como: Criar e usar uma tela'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- controls [WPF], Canvas
- Canvas control [WPF], creating
- Canvas control [WPF], using
ms.assetid: 420b9487-9a15-477c-9489-a22a4dec7779
ms.openlocfilehash: 33b98024699a88f56d27b7e5ab8d5216c906e7ec
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59190763"
---
# <a name="how-to-create-and-use-a-canvas"></a><span data-ttu-id="5b2e0-102">Como: Criar e usar uma tela</span><span class="sxs-lookup"><span data-stu-id="5b2e0-102">How to: Create and Use a Canvas</span></span>
<span data-ttu-id="5b2e0-103">Este exemplo mostra como criar e usar uma instância de <xref:System.Windows.Controls.Canvas>.</span><span class="sxs-lookup"><span data-stu-id="5b2e0-103">This example shows how to create and use an instance of <xref:System.Windows.Controls.Canvas>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="5b2e0-104">Exemplo</span><span class="sxs-lookup"><span data-stu-id="5b2e0-104">Example</span></span>  
 <span data-ttu-id="5b2e0-105">O exemplo a seguir explicitamente posiciona duas <xref:System.Windows.Controls.TextBlock> elementos usando o <xref:System.Windows.Controls.Canvas.SetTop%2A> e <xref:System.Windows.Controls.Canvas.SetLeft%2A> métodos de <xref:System.Windows.Controls.Canvas>.</span><span class="sxs-lookup"><span data-stu-id="5b2e0-105">The following example explicitly positions two <xref:System.Windows.Controls.TextBlock> elements by using the <xref:System.Windows.Controls.Canvas.SetTop%2A> and <xref:System.Windows.Controls.Canvas.SetLeft%2A> methods of <xref:System.Windows.Controls.Canvas>.</span></span> <span data-ttu-id="5b2e0-106">O exemplo também atribui uma <xref:System.Windows.Controls.Control.Background%2A> cor dos `LightSteelBlue` para o <xref:System.Windows.Controls.Canvas>.</span><span class="sxs-lookup"><span data-stu-id="5b2e0-106">The example also assigns a <xref:System.Windows.Controls.Control.Background%2A> color of `LightSteelBlue` to the <xref:System.Windows.Controls.Canvas>.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="5b2e0-107">Quando você usa [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] posição <xref:System.Windows.Controls.TextBlock> elementos, use o <xref:System.Windows.Controls.Canvas.Top%2A> e <xref:System.Windows.Controls.Canvas.Left%2A> propriedades.</span><span class="sxs-lookup"><span data-stu-id="5b2e0-107">When you use [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] to position <xref:System.Windows.Controls.TextBlock> elements, use the <xref:System.Windows.Controls.Canvas.Top%2A> and <xref:System.Windows.Controls.Canvas.Left%2A> properties.</span></span>  
  
 [!code-csharp[CanvasCode#1](~/samples/snippets/csharp/VS_Snippets_Wpf/CanvasCode/CSharp/Canvas_Code.cs#1)]
 [!code-vb[CanvasCode#1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/CanvasCode/VisualBasic/canvas_vb.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="5b2e0-108">Consulte também</span><span class="sxs-lookup"><span data-stu-id="5b2e0-108">See also</span></span>

- <xref:System.Windows.Controls.Canvas>
- <xref:System.Windows.Controls.TextBlock>
- <xref:System.Windows.Controls.Canvas.SetTop%2A>
- <xref:System.Windows.Controls.Canvas.SetLeft%2A>
- <xref:System.Windows.Controls.Canvas.Top%2A>
- <xref:System.Windows.Controls.Canvas.Left%2A>
- [<span data-ttu-id="5b2e0-109">Visão geral de painéis</span><span class="sxs-lookup"><span data-stu-id="5b2e0-109">Panels Overview</span></span>](panels-overview.md)
- [<span data-ttu-id="5b2e0-110">Tópicos de instruções</span><span class="sxs-lookup"><span data-stu-id="5b2e0-110">How-to Topics</span></span>](canvas-how-to-topics.md)
