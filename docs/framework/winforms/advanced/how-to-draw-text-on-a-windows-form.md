---
title: 'Como: desenhar texto em um formulário do Windows'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- forms [Windows Forms], drawing text
- text [Windows Forms], drawing
ms.assetid: 5d2447a9-21a1-4adc-b954-5516f2bb9b2c
ms.openlocfilehash: ae7749deedba03f0a63bb74099d071d5da4fe27e
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62004075"
---
# <a name="how-to-draw-text-on-a-windows-form"></a><span data-ttu-id="b1c69-102">Como: desenhar texto em um formulário do Windows</span><span class="sxs-lookup"><span data-stu-id="b1c69-102">How to: Draw Text on a Windows Form</span></span>
<span data-ttu-id="b1c69-103">O exemplo de código a seguir mostra como usar o <xref:System.Drawing.Graphics.DrawString%2A> método da <xref:System.Drawing.Graphics> para desenhar texto em um formulário.</span><span class="sxs-lookup"><span data-stu-id="b1c69-103">The following code example shows how to use the <xref:System.Drawing.Graphics.DrawString%2A> method of the <xref:System.Drawing.Graphics> to draw text on a form.</span></span> <span data-ttu-id="b1c69-104">Como alternativa, você pode usar <xref:System.Windows.Forms.TextRenderer> para desenhar texto em um formulário.</span><span class="sxs-lookup"><span data-stu-id="b1c69-104">Alternatively, you can use <xref:System.Windows.Forms.TextRenderer> for drawing text on a form.</span></span> <span data-ttu-id="b1c69-105">Para obter mais informações, confira [Como: Desenhar texto com GDI](how-to-draw-text-with-gdi.md).</span><span class="sxs-lookup"><span data-stu-id="b1c69-105">For more information, see [How to: Draw Text with GDI](how-to-draw-text-with-gdi.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="b1c69-106">Exemplo</span><span class="sxs-lookup"><span data-stu-id="b1c69-106">Example</span></span>  
 [!code-cpp[System.Drawing.ConceptualHowTos#7](~/samples/snippets/cpp/VS_Snippets_Winforms/System.Drawing.ConceptualHowTos/cpp/form1.cpp#7)]
 [!code-csharp[System.Drawing.ConceptualHowTos#7](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.ConceptualHowTos/CS/form1.cs#7)]
 [!code-vb[System.Drawing.ConceptualHowTos#7](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.ConceptualHowTos/VB/form1.vb#7)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="b1c69-107">Compilando o código</span><span class="sxs-lookup"><span data-stu-id="b1c69-107">Compiling the Code</span></span>  
 <span data-ttu-id="b1c69-108">Você não pode chamar o <xref:System.Drawing.Graphics.DrawString%2A> método no <xref:System.Windows.Forms.Form.Load> manipulador de eventos.</span><span class="sxs-lookup"><span data-stu-id="b1c69-108">You cannot call the <xref:System.Drawing.Graphics.DrawString%2A> method in the <xref:System.Windows.Forms.Form.Load> event handler.</span></span> <span data-ttu-id="b1c69-109">O conteúdo desenhado não será redesenhado se o formulário for redimensionado ou obscurecido por outro formulário.</span><span class="sxs-lookup"><span data-stu-id="b1c69-109">The drawn content will not be redrawn if the form is resized or obscured by another form.</span></span> <span data-ttu-id="b1c69-110">Para tornar seu conteúdo redesenhar automaticamente, você deve substituir o <xref:System.Windows.Forms.Control.OnPaint%2A> método.</span><span class="sxs-lookup"><span data-stu-id="b1c69-110">To make your content automatically repaint, you should override the <xref:System.Windows.Forms.Control.OnPaint%2A> method.</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="b1c69-111">Programação robusta</span><span class="sxs-lookup"><span data-stu-id="b1c69-111">Robust Programming</span></span>  
 <span data-ttu-id="b1c69-112">As seguintes condições podem causar uma exceção:</span><span class="sxs-lookup"><span data-stu-id="b1c69-112">The following conditions may cause an exception:</span></span>  
  
- <span data-ttu-id="b1c69-113">A fonte Arial não está instalada.</span><span class="sxs-lookup"><span data-stu-id="b1c69-113">The Arial font is not installed.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b1c69-114">Consulte também</span><span class="sxs-lookup"><span data-stu-id="b1c69-114">See also</span></span>

- <xref:System.Drawing.Graphics.DrawString%2A>
- <xref:System.Windows.Forms.TextRenderer.DrawText%2A>
- <xref:System.Drawing.StringFormat.FormatFlags%2A>
- <xref:System.Drawing.StringFormatFlags>
- <xref:System.Windows.Forms.TextFormatFlags>
- <xref:System.Windows.Forms.Control.OnPaint%2A>
- [<span data-ttu-id="b1c69-115">Introdução à Programação de Elementos Gráficos</span><span class="sxs-lookup"><span data-stu-id="b1c69-115">Getting Started with Graphics Programming</span></span>](getting-started-with-graphics-programming.md)
- [<span data-ttu-id="b1c69-116">Como: Desenhar texto com GDI</span><span class="sxs-lookup"><span data-stu-id="b1c69-116">How to: Draw Text with GDI</span></span>](how-to-draw-text-with-gdi.md)
