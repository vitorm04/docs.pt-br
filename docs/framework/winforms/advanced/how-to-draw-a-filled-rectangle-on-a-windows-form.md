---
title: 'Como: Desenhar um retângulo preenchido em um formulário do Windows'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
f1_keywords:
- Graphics.FillRectangle
helpviewer_keywords:
- drawing [Windows Forms], rectangles
- rectangles [Windows Forms], drawing
- drawing rectangles
ms.assetid: d656a93c-987d-4809-aafd-493fe17450f0
ms.openlocfilehash: 53fab93f47c16257b5ab2e336b43c6133a31d509
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/09/2019
ms.locfileid: "57716888"
---
# <a name="how-to-draw-a-filled-rectangle-on-a-windows-form"></a><span data-ttu-id="44743-102">Como: Desenhar um retângulo preenchido em um formulário do Windows</span><span class="sxs-lookup"><span data-stu-id="44743-102">How to: Draw a Filled Rectangle on a Windows Form</span></span>
<span data-ttu-id="44743-103">Este exemplo desenha um retângulo preenchido em um formulário.</span><span class="sxs-lookup"><span data-stu-id="44743-103">This example draws a filled rectangle on a form.</span></span>  
  
## <a name="example"></a><span data-ttu-id="44743-104">Exemplo</span><span class="sxs-lookup"><span data-stu-id="44743-104">Example</span></span>  
 [!code-cpp[System.Drawing.ConceptualHowTos#2](~/samples/snippets/cpp/VS_Snippets_Winforms/System.Drawing.ConceptualHowTos/cpp/form1.cpp#2)]
 [!code-csharp[System.Drawing.ConceptualHowTos#2](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.ConceptualHowTos/CS/form1.cs#2)]
 [!code-vb[System.Drawing.ConceptualHowTos#2](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.ConceptualHowTos/VB/form1.vb#2)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="44743-105">Compilando o código</span><span class="sxs-lookup"><span data-stu-id="44743-105">Compiling the Code</span></span>  
 <span data-ttu-id="44743-106">Não é possível chamar esse método <xref:System.Windows.Forms.Form.Load> manipulador de eventos.</span><span class="sxs-lookup"><span data-stu-id="44743-106">You cannot call this method in the <xref:System.Windows.Forms.Form.Load> event handler.</span></span> <span data-ttu-id="44743-107">O conteúdo desenhado não será redesenhado se o formulário for redimensionado ou obscurecido por outro formulário.</span><span class="sxs-lookup"><span data-stu-id="44743-107">The drawn content will not be redrawn if the form is resized or obscured by another form.</span></span> <span data-ttu-id="44743-108">Para tornar seu conteúdo redesenhar automaticamente, você deve substituir o <xref:System.Windows.Forms.Control.OnPaint%2A> método.</span><span class="sxs-lookup"><span data-stu-id="44743-108">To make your content automatically repaint, you should override the <xref:System.Windows.Forms.Control.OnPaint%2A> method.</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="44743-109">Programação robusta</span><span class="sxs-lookup"><span data-stu-id="44743-109">Robust Programming</span></span>  
 <span data-ttu-id="44743-110">Você sempre deve chamar <xref:System.IDisposable.Dispose%2A> em todos os objetos que consomem recursos do sistema, como <xref:System.Drawing.Brush> e <xref:System.Drawing.Graphics> objetos.</span><span class="sxs-lookup"><span data-stu-id="44743-110">You should always call <xref:System.IDisposable.Dispose%2A> on any objects that consume system resources, such as <xref:System.Drawing.Brush> and <xref:System.Drawing.Graphics> objects.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="44743-111">Consulte também</span><span class="sxs-lookup"><span data-stu-id="44743-111">See also</span></span>
- <xref:System.Drawing.Graphics.FillRectangle%2A>
- <xref:System.Windows.Forms.Control.OnPaint%2A>
- [<span data-ttu-id="44743-112">Introdução à Programação de Elementos Gráficos</span><span class="sxs-lookup"><span data-stu-id="44743-112">Getting Started with Graphics Programming</span></span>](getting-started-with-graphics-programming.md)
- [<span data-ttu-id="44743-113">Elementos Gráficos e Desenho nos Windows Forms</span><span class="sxs-lookup"><span data-stu-id="44743-113">Graphics and Drawing in Windows Forms</span></span>](graphics-and-drawing-in-windows-forms.md)
- [<span data-ttu-id="44743-114">Usando uma caneta para desenhar linhas e formas</span><span class="sxs-lookup"><span data-stu-id="44743-114">Using a Pen to Draw Lines and Shapes</span></span>](using-a-pen-to-draw-lines-and-shapes.md)
- [<span data-ttu-id="44743-115">Pincéis e Formas Preenchidas no GDI+</span><span class="sxs-lookup"><span data-stu-id="44743-115">Brushes and Filled Shapes in GDI+</span></span>](brushes-and-filled-shapes-in-gdi.md)
