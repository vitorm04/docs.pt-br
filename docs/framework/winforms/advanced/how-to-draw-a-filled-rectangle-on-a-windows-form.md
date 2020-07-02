---
title: Como desenhar um retângulo preenchido em um formulário do Windows Forms
description: Saiba como desenhar programaticamente um retângulo preenchido em um formulário do Windows. Além disso, saiba como compilar seu código.
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
ms.openlocfilehash: 0ad8ec97000e29b2194a9eda713aa43d5557b44c
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85621633"
---
# <a name="how-to-draw-a-filled-rectangle-on-a-windows-form"></a><span data-ttu-id="26cf1-104">Como desenhar um retângulo preenchido em um formulário do Windows Forms</span><span class="sxs-lookup"><span data-stu-id="26cf1-104">How to: Draw a Filled Rectangle on a Windows Form</span></span>
<span data-ttu-id="26cf1-105">Este exemplo desenha um retângulo preenchido em um formulário.</span><span class="sxs-lookup"><span data-stu-id="26cf1-105">This example draws a filled rectangle on a form.</span></span>  
  
## <a name="example"></a><span data-ttu-id="26cf1-106">Exemplo</span><span class="sxs-lookup"><span data-stu-id="26cf1-106">Example</span></span>  
 [!code-cpp[System.Drawing.ConceptualHowTos#2](~/samples/snippets/cpp/VS_Snippets_Winforms/System.Drawing.ConceptualHowTos/cpp/form1.cpp#2)]
 [!code-csharp[System.Drawing.ConceptualHowTos#2](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.ConceptualHowTos/CS/form1.cs#2)]
 [!code-vb[System.Drawing.ConceptualHowTos#2](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.ConceptualHowTos/VB/form1.vb#2)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="26cf1-107">Compilando o código</span><span class="sxs-lookup"><span data-stu-id="26cf1-107">Compiling the Code</span></span>  
 <span data-ttu-id="26cf1-108">Você não pode chamar esse método no <xref:System.Windows.Forms.Form.Load> manipulador de eventos.</span><span class="sxs-lookup"><span data-stu-id="26cf1-108">You cannot call this method in the <xref:System.Windows.Forms.Form.Load> event handler.</span></span> <span data-ttu-id="26cf1-109">O conteúdo desenhado não será redesenhado se o formulário for redimensionado ou obscurecido por outro formulário.</span><span class="sxs-lookup"><span data-stu-id="26cf1-109">The drawn content will not be redrawn if the form is resized or obscured by another form.</span></span> <span data-ttu-id="26cf1-110">Para tornar seu conteúdo redesenhado automaticamente, você deve substituir o <xref:System.Windows.Forms.Control.OnPaint%2A> método.</span><span class="sxs-lookup"><span data-stu-id="26cf1-110">To make your content automatically repaint, you should override the <xref:System.Windows.Forms.Control.OnPaint%2A> method.</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="26cf1-111">Programação robusta</span><span class="sxs-lookup"><span data-stu-id="26cf1-111">Robust Programming</span></span>  
 <span data-ttu-id="26cf1-112">Você sempre deve chamar <xref:System.IDisposable.Dispose%2A> todos os objetos que consomem recursos do sistema, como <xref:System.Drawing.Brush> <xref:System.Drawing.Graphics> objetos e.</span><span class="sxs-lookup"><span data-stu-id="26cf1-112">You should always call <xref:System.IDisposable.Dispose%2A> on any objects that consume system resources, such as <xref:System.Drawing.Brush> and <xref:System.Drawing.Graphics> objects.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="26cf1-113">Consulte também</span><span class="sxs-lookup"><span data-stu-id="26cf1-113">See also</span></span>

- <xref:System.Drawing.Graphics.FillRectangle%2A>
- <xref:System.Windows.Forms.Control.OnPaint%2A>
- [<span data-ttu-id="26cf1-114">Introdução à Programação de Elementos Gráficos</span><span class="sxs-lookup"><span data-stu-id="26cf1-114">Getting Started with Graphics Programming</span></span>](getting-started-with-graphics-programming.md)
- [<span data-ttu-id="26cf1-115">Elementos gráficos e desenho no Windows Forms</span><span class="sxs-lookup"><span data-stu-id="26cf1-115">Graphics and Drawing in Windows Forms</span></span>](graphics-and-drawing-in-windows-forms.md)
- [<span data-ttu-id="26cf1-116">Uso de uma caneta para desenhar linhas e formas</span><span class="sxs-lookup"><span data-stu-id="26cf1-116">Using a Pen to Draw Lines and Shapes</span></span>](using-a-pen-to-draw-lines-and-shapes.md)
- [<span data-ttu-id="26cf1-117">Pincéis e Formas Preenchidas no GDI+</span><span class="sxs-lookup"><span data-stu-id="26cf1-117">Brushes and Filled Shapes in GDI+</span></span>](brushes-and-filled-shapes-in-gdi.md)
