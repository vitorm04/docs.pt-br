---
title: 'Como: desenhar uma elipse preenchida em um formulário do Windows'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
f1_keywords:
- Graphics.FillEllipse
helpviewer_keywords:
- ellipses [Windows Forms], drawing
- circles [Windows Forms], drawing
- circular shapes
- drawing [Windows Forms], ellipses
- shapes [Windows Forms], drawing
- forms [Windows Forms], drawing ellipses
ms.assetid: 781db806-950d-4c5b-b022-493f7fd0c4a8
ms.openlocfilehash: 2e7be3f2c4c710bb24568dd2e70f6f5cc4706c63
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59170989"
---
# <a name="how-to-draw-a-filled-ellipse-on-a-windows-form"></a><span data-ttu-id="bee75-102">Como: desenhar uma elipse preenchida em um formulário do Windows</span><span class="sxs-lookup"><span data-stu-id="bee75-102">How to: Draw a Filled Ellipse on a Windows Form</span></span>
<span data-ttu-id="bee75-103">Este exemplo desenha uma elipse preenchida em um formulário.</span><span class="sxs-lookup"><span data-stu-id="bee75-103">This example draws a filled ellipse on a form.</span></span>  
  
## <a name="example"></a><span data-ttu-id="bee75-104">Exemplo</span><span class="sxs-lookup"><span data-stu-id="bee75-104">Example</span></span>  
 [!code-cpp[System.Drawing.ConceptualHowTos#1](~/samples/snippets/cpp/VS_Snippets_Winforms/System.Drawing.ConceptualHowTos/cpp/form1.cpp#1)]
 [!code-csharp[System.Drawing.ConceptualHowTos#1](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.ConceptualHowTos/CS/form1.cs#1)]
 [!code-vb[System.Drawing.ConceptualHowTos#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.ConceptualHowTos/VB/form1.vb#1)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="bee75-105">Compilando o código</span><span class="sxs-lookup"><span data-stu-id="bee75-105">Compiling the Code</span></span>  
 <span data-ttu-id="bee75-106">Não é possível chamar esse método <xref:System.Windows.Forms.Form.Load> manipulador de eventos.</span><span class="sxs-lookup"><span data-stu-id="bee75-106">You cannot call this method in the <xref:System.Windows.Forms.Form.Load> event handler.</span></span> <span data-ttu-id="bee75-107">O conteúdo desenhado não será redesenhado se o formulário for redimensionado ou obscurecido por outro formulário.</span><span class="sxs-lookup"><span data-stu-id="bee75-107">The drawn content will not be redrawn if the form is resized or obscured by another form.</span></span> <span data-ttu-id="bee75-108">Para tornar seu conteúdo redesenhar automaticamente, você deve substituir o <xref:System.Windows.Forms.Control.OnPaint%2A> método.</span><span class="sxs-lookup"><span data-stu-id="bee75-108">To make your content automatically repaint, you should override the <xref:System.Windows.Forms.Control.OnPaint%2A> method.</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="bee75-109">Programação robusta</span><span class="sxs-lookup"><span data-stu-id="bee75-109">Robust Programming</span></span>  
 <span data-ttu-id="bee75-110">Você sempre deve chamar <xref:System.IDisposable.Dispose%2A> em todos os objetos que consomem recursos do sistema, como <xref:System.Drawing.Brush> e <xref:System.Drawing.Graphics> objetos.</span><span class="sxs-lookup"><span data-stu-id="bee75-110">You should always call <xref:System.IDisposable.Dispose%2A> on any objects that consume system resources, such as <xref:System.Drawing.Brush> and <xref:System.Drawing.Graphics> objects.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bee75-111">Consulte também</span><span class="sxs-lookup"><span data-stu-id="bee75-111">See also</span></span>

- [<span data-ttu-id="bee75-112">Elementos gráficos e desenho no Windows Forms</span><span class="sxs-lookup"><span data-stu-id="bee75-112">Graphics and Drawing in Windows Forms</span></span>](graphics-and-drawing-in-windows-forms.md)
- [<span data-ttu-id="bee75-113">Introdução à programação de elementos gráficos</span><span class="sxs-lookup"><span data-stu-id="bee75-113">Getting Started with Graphics Programming</span></span>](getting-started-with-graphics-programming.md)
- [<span data-ttu-id="bee75-114">Combinação alfa em linhas e preenchimentos</span><span class="sxs-lookup"><span data-stu-id="bee75-114">Alpha Blending Lines and Fills</span></span>](alpha-blending-lines-and-fills.md)
- [<span data-ttu-id="bee75-115">Usando um pincel para preencher formas</span><span class="sxs-lookup"><span data-stu-id="bee75-115">Using a Brush to Fill Shapes</span></span>](using-a-brush-to-fill-shapes.md)
