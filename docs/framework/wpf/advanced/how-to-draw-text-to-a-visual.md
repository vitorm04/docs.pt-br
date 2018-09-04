---
title: Como desenhar texto em um visual
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- typography [WPF], drawing text to visuals
- visuals [WPF], drawing text to
- text [WPF], drawing to visuals
- drawing [WPF], text to visuals
ms.assetid: fee4003c-e8a6-46ec-babd-2c7f4231a101
ms.openlocfilehash: bc7a4f989137ec2b021d27a6e112ff1aebd99d07
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/04/2018
ms.locfileid: "43523237"
---
# <a name="how-to-draw-text-to-a-visual"></a><span data-ttu-id="fc057-102">Como desenhar texto em um visual</span><span class="sxs-lookup"><span data-stu-id="fc057-102">How to: Draw Text to a Visual</span></span>
<span data-ttu-id="fc057-103">O exemplo a seguir mostra como desenhar texto para um <xref:System.Windows.Media.DrawingVisual> usando um <xref:System.Windows.Media.DrawingContext> objeto.</span><span class="sxs-lookup"><span data-stu-id="fc057-103">The following example shows how to draw text to a <xref:System.Windows.Media.DrawingVisual> using a <xref:System.Windows.Media.DrawingContext> object.</span></span> <span data-ttu-id="fc057-104">Um contexto de desenho é retornado ao chamar o <xref:System.Windows.Media.DrawingVisual.RenderOpen%2A> método de um <xref:System.Windows.Media.DrawingVisual> objeto.</span><span class="sxs-lookup"><span data-stu-id="fc057-104">A drawing context is returned by calling the <xref:System.Windows.Media.DrawingVisual.RenderOpen%2A> method of a <xref:System.Windows.Media.DrawingVisual> object.</span></span> <span data-ttu-id="fc057-105">Você pode desenhar texto e elementos gráficos em um contexto de desenho.</span><span class="sxs-lookup"><span data-stu-id="fc057-105">You can draw graphics and text into a drawing context.</span></span>  
  
 <span data-ttu-id="fc057-106">Para desenhar texto em um contexto de desenho, use o <xref:System.Windows.Media.DrawingContext.DrawText%2A> método de um <xref:System.Windows.Media.DrawingContext> objeto.</span><span class="sxs-lookup"><span data-stu-id="fc057-106">To draw text into the drawing context, use the <xref:System.Windows.Media.DrawingContext.DrawText%2A> method of a <xref:System.Windows.Media.DrawingContext> object.</span></span> <span data-ttu-id="fc057-107">Quando tiver terminado de desenhar conteúdo no contexto de desenho, chame o <xref:System.Windows.Media.DrawingContext.Close%2A> método para fechar o contexto de desenho e persistir o conteúdo.</span><span class="sxs-lookup"><span data-stu-id="fc057-107">When you are finished drawing content into the drawing context, call the <xref:System.Windows.Media.DrawingContext.Close%2A> method to close the drawing context and persist the content.</span></span>  
  
## <a name="example"></a><span data-ttu-id="fc057-108">Exemplo</span><span class="sxs-lookup"><span data-stu-id="fc057-108">Example</span></span>  
 [!code-csharp[DrawingVisualSample#110](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DrawingVisualSample/CSharp/Window1.xaml.cs#110)]
 [!code-vb[DrawingVisualSample#110](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DrawingVisualSample/visualbasic/window1.xaml.vb#110)]  
  
> [!NOTE]
>  <span data-ttu-id="fc057-109">Para o exemplo de código completo do qual o exemplo de código anterior foi extraído, consulte [Exemplo de teste de clique usando DrawingVisuals](https://go.microsoft.com/fwlink/?LinkID=159994).</span><span class="sxs-lookup"><span data-stu-id="fc057-109">For the complete code sample from which the preceding code example was extracted, see [Hit Test Using DrawingVisuals Sample](https://go.microsoft.com/fwlink/?LinkID=159994).</span></span>
