---
title: Como desenhar uma linha
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- drawing [WPF], lines
- graphics [WPF], lines
- lines [WPF], drawing
ms.assetid: 0513ee01-6b27-4bb3-85f3-3a3e6710d80e
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 88d667e8654f72226dc609a14aec650effe2d5c8
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-draw-a-line"></a><span data-ttu-id="116f1-102">Como desenhar uma linha</span><span class="sxs-lookup"><span data-stu-id="116f1-102">How to: Draw a Line</span></span>
<span data-ttu-id="116f1-103">Este exemplo mostra como desenhar linhas usando o <xref:System.Windows.Shapes.Line> elemento.</span><span class="sxs-lookup"><span data-stu-id="116f1-103">This example shows you how to draw lines by using the <xref:System.Windows.Shapes.Line> element.</span></span>  
  
 <span data-ttu-id="116f1-104">Para desenhar uma linha, crie um <xref:System.Windows.Shapes.Line> elemento.</span><span class="sxs-lookup"><span data-stu-id="116f1-104">To draw a line, create a <xref:System.Windows.Shapes.Line> element.</span></span> <span data-ttu-id="116f1-105">Use seu <xref:System.Windows.Shapes.Line.X1%2A> e <xref:System.Windows.Shapes.Line.Y1%2A> propriedades para definir seu ponto inicial; e use seu <xref:System.Windows.Shapes.Line.X2%2A> e <xref:System.Windows.Shapes.Line.Y2%2A> propriedades para definir seu ponto de extremidade.</span><span class="sxs-lookup"><span data-stu-id="116f1-105">Use its <xref:System.Windows.Shapes.Line.X1%2A> and <xref:System.Windows.Shapes.Line.Y1%2A> properties to set its start point; and use its <xref:System.Windows.Shapes.Line.X2%2A> and <xref:System.Windows.Shapes.Line.Y2%2A> properties to set its end point.</span></span> <span data-ttu-id="116f1-106">Finalmente, defina seu <xref:System.Windows.Shapes.Shape.Stroke%2A> e <xref:System.Windows.Shapes.Shape.StrokeThickness%2A> porque uma linha sem um traço é invisível.</span><span class="sxs-lookup"><span data-stu-id="116f1-106">Finally, set its <xref:System.Windows.Shapes.Shape.Stroke%2A> and <xref:System.Windows.Shapes.Shape.StrokeThickness%2A> because a line without a stroke is invisible.</span></span>  
  
 <span data-ttu-id="116f1-107">Definindo o <xref:System.Windows.Shapes.Shape.Fill%2A> elemento para uma linha não tem nenhum efeito, porque uma linha não possui interior.</span><span class="sxs-lookup"><span data-stu-id="116f1-107">Setting the <xref:System.Windows.Shapes.Shape.Fill%2A> element for a line has no effect, because a line has no interior.</span></span>  
  
 <span data-ttu-id="116f1-108">O exemplo a seguir desenha três linhas dentro de um <xref:System.Windows.Controls.Canvas> elemento.</span><span class="sxs-lookup"><span data-stu-id="116f1-108">The following example draws three lines inside a <xref:System.Windows.Controls.Canvas> element.</span></span>  
  
## <a name="example"></a><span data-ttu-id="116f1-109">Exemplo</span><span class="sxs-lookup"><span data-stu-id="116f1-109">Example</span></span>  
 [!code-xaml[drawingwithshapeelements#LineExample1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DrawingWithShapeElements/CS/lineexample.xaml#lineexample1)]  
  
 <span data-ttu-id="116f1-110">Este exemplo faz parte de um exemplo maior; para ver o exemplo completo, consulte o [Exemplo de elementos de forma](http://go.microsoft.com/fwlink/?LinkID=160037).</span><span class="sxs-lookup"><span data-stu-id="116f1-110">This example is part of a larger sample; for the complete sample, see [Shape Elements Sample](http://go.microsoft.com/fwlink/?LinkID=160037).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="116f1-111">Consulte também</span><span class="sxs-lookup"><span data-stu-id="116f1-111">See Also</span></span>  
 <xref:System.Windows.Shapes.Line>  
 [<span data-ttu-id="116f1-112">Exemplo de elementos de forma</span><span class="sxs-lookup"><span data-stu-id="116f1-112">Shape Elements Sample</span></span>](http://go.microsoft.com/fwlink/?LinkID=160037)
