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
ms.openlocfilehash: edef660b2da2f09e0a6edbc0a87f0d1f26eb03da
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69964228"
---
# <a name="how-to-create-and-use-a-canvas"></a><span data-ttu-id="8cc6f-102">Como: Criar e usar uma tela</span><span class="sxs-lookup"><span data-stu-id="8cc6f-102">How to: Create and Use a Canvas</span></span>
<span data-ttu-id="8cc6f-103">Este exemplo mostra como criar e usar uma instância do <xref:System.Windows.Controls.Canvas>.</span><span class="sxs-lookup"><span data-stu-id="8cc6f-103">This example shows how to create and use an instance of <xref:System.Windows.Controls.Canvas>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="8cc6f-104">Exemplo</span><span class="sxs-lookup"><span data-stu-id="8cc6f-104">Example</span></span>  
 <span data-ttu-id="8cc6f-105">O exemplo a seguir posiciona explicitamente <xref:System.Windows.Controls.TextBlock> dois elementos usando os <xref:System.Windows.Controls.Canvas.SetTop%2A> métodos <xref:System.Windows.Controls.Canvas.SetLeft%2A> e de <xref:System.Windows.Controls.Canvas>.</span><span class="sxs-lookup"><span data-stu-id="8cc6f-105">The following example explicitly positions two <xref:System.Windows.Controls.TextBlock> elements by using the <xref:System.Windows.Controls.Canvas.SetTop%2A> and <xref:System.Windows.Controls.Canvas.SetLeft%2A> methods of <xref:System.Windows.Controls.Canvas>.</span></span> <span data-ttu-id="8cc6f-106">O exemplo também atribui uma <xref:System.Windows.Controls.Control.Background%2A> cor de `LightSteelBlue` para o <xref:System.Windows.Controls.Canvas>.</span><span class="sxs-lookup"><span data-stu-id="8cc6f-106">The example also assigns a <xref:System.Windows.Controls.Control.Background%2A> color of `LightSteelBlue` to the <xref:System.Windows.Controls.Canvas>.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="8cc6f-107">Quando você usa [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] para posicionar <xref:System.Windows.Controls.TextBlock> elementos, use <xref:System.Windows.Controls.Canvas.Top%2A> as <xref:System.Windows.Controls.Canvas.Left%2A> Propriedades e.</span><span class="sxs-lookup"><span data-stu-id="8cc6f-107">When you use [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] to position <xref:System.Windows.Controls.TextBlock> elements, use the <xref:System.Windows.Controls.Canvas.Top%2A> and <xref:System.Windows.Controls.Canvas.Left%2A> properties.</span></span>  
  
 [!code-csharp[CanvasCode#1](~/samples/snippets/csharp/VS_Snippets_Wpf/CanvasCode/CSharp/Canvas_Code.cs#1)]
 [!code-vb[CanvasCode#1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/CanvasCode/VisualBasic/canvas_vb.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="8cc6f-108">Consulte também</span><span class="sxs-lookup"><span data-stu-id="8cc6f-108">See also</span></span>

- <xref:System.Windows.Controls.Canvas>
- <xref:System.Windows.Controls.TextBlock>
- <xref:System.Windows.Controls.Canvas.SetTop%2A>
- <xref:System.Windows.Controls.Canvas.SetLeft%2A>
- <xref:System.Windows.Controls.Canvas.Top%2A>
- <xref:System.Windows.Controls.Canvas.Left%2A>
- [<span data-ttu-id="8cc6f-109">Visão geral de painéis</span><span class="sxs-lookup"><span data-stu-id="8cc6f-109">Panels Overview</span></span>](panels-overview.md)
- [<span data-ttu-id="8cc6f-110">Tópicos de instruções</span><span class="sxs-lookup"><span data-stu-id="8cc6f-110">How-to Topics</span></span>](canvas-how-to-topics.md)
