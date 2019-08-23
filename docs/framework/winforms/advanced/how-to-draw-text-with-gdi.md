---
title: 'Como: desenhar texto com o GDI'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- GDI [Windows Forms], drawing text [Windows Forms]
- text [Windows Forms], drawing with TextRenderer
- drawing [Windows Forms], text
- Windows Forms, drawing text with GDI
ms.assetid: 2a19fe5d-2ace-451c-94db-01cb1118ef7b
ms.openlocfilehash: 3ed2b5c94e4a38a5873a34e61287c4038cab5cbb
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69956537"
---
# <a name="how-to-draw-text-with-gdi"></a><span data-ttu-id="97231-102">Como: desenhar texto com o GDI</span><span class="sxs-lookup"><span data-stu-id="97231-102">How to: Draw Text with GDI</span></span>
<span data-ttu-id="97231-103">Com o <xref:System.Windows.Forms.TextRenderer.DrawText%2A> método <xref:System.Windows.Forms.TextRenderer> na classe, você pode acessar a funcionalidade GDI para desenhar texto em um formulário ou controle.</span><span class="sxs-lookup"><span data-stu-id="97231-103">With the <xref:System.Windows.Forms.TextRenderer.DrawText%2A> method in the <xref:System.Windows.Forms.TextRenderer> class, you can access GDI functionality for drawing text on a form or control.</span></span> <span data-ttu-id="97231-104">A renderização de texto GDI geralmente oferece melhor desempenho e medição de texto mais precisa do que o GDI+.</span><span class="sxs-lookup"><span data-stu-id="97231-104">GDI text rendering typically offers better performance and more accurate text measuring than GDI+.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="97231-105">Os <xref:System.Windows.Forms.TextRenderer.DrawText%2A> métodos<xref:System.Windows.Forms.TextRenderer> da classe não têm suporte para impressão.</span><span class="sxs-lookup"><span data-stu-id="97231-105">The <xref:System.Windows.Forms.TextRenderer.DrawText%2A> methods of the <xref:System.Windows.Forms.TextRenderer> class are not supported for printing.</span></span> <span data-ttu-id="97231-106">Ao imprimir, sempre use os <xref:System.Drawing.Graphics.DrawString%2A> métodos <xref:System.Drawing.Graphics> da classe.</span><span class="sxs-lookup"><span data-stu-id="97231-106">When printing, always use the <xref:System.Drawing.Graphics.DrawString%2A> methods of the <xref:System.Drawing.Graphics> class.</span></span>  
  
## <a name="example"></a><span data-ttu-id="97231-107">Exemplo</span><span class="sxs-lookup"><span data-stu-id="97231-107">Example</span></span>  
 <span data-ttu-id="97231-108">O exemplo de código a seguir demonstra como desenhar texto em várias linhas dentro de um retângulo <xref:System.Windows.Forms.TextRenderer.DrawText%2A> usando o método.</span><span class="sxs-lookup"><span data-stu-id="97231-108">The following code example demonstrates how to draw text on multiple lines within a rectangle using the <xref:System.Windows.Forms.TextRenderer.DrawText%2A> method.</span></span>  
  
 [!code-csharp[System.Windows.Forms.TextRendererExamples#7](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.TextRendererExamples/CS/Form1.cs#7)]
 [!code-vb[System.Windows.Forms.TextRendererExamples#7](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.TextRendererExamples/VB/Form1.vb#7)]  
  
 <span data-ttu-id="97231-109">Para renderizar o texto <xref:System.Windows.Forms.TextRenderer> com a classe, você <xref:System.Drawing.IDeviceContext>precisa de um, <xref:System.Drawing.Graphics> como um <xref:System.Drawing.Font>e um, um local para desenhar o texto e a cor na qual ele deve ser desenhado.</span><span class="sxs-lookup"><span data-stu-id="97231-109">To render text with the <xref:System.Windows.Forms.TextRenderer> class, you need an <xref:System.Drawing.IDeviceContext>, such as a <xref:System.Drawing.Graphics> and a <xref:System.Drawing.Font>, a location to draw the text, and the color in which it should be drawn.</span></span> <span data-ttu-id="97231-110">Opcionalmente, você pode especificar a formatação do texto usando a <xref:System.Windows.Forms.TextFormatFlags> enumeração.</span><span class="sxs-lookup"><span data-stu-id="97231-110">Optionally, you can specify the text formatting by using the <xref:System.Windows.Forms.TextFormatFlags> enumeration.</span></span>  
  
 <span data-ttu-id="97231-111">Para obter mais informações sobre como <xref:System.Drawing.Graphics>obter um [, consulte Como: Crie objetos gráficos para desenho](how-to-create-graphics-objects-for-drawing.md).</span><span class="sxs-lookup"><span data-stu-id="97231-111">For more information about obtaining a <xref:System.Drawing.Graphics>, see [How to: Create Graphics Objects for Drawing](how-to-create-graphics-objects-for-drawing.md).</span></span> <span data-ttu-id="97231-112">Para obter mais informações sobre como construir <xref:System.Drawing.Font>um, [consulte Como: Construa fontes](how-to-construct-font-families-and-fonts.md)e famílias de fontes.</span><span class="sxs-lookup"><span data-stu-id="97231-112">For more information about constructing a <xref:System.Drawing.Font>, see [How to: Construct Font Families and Fonts](how-to-construct-font-families-and-fonts.md).</span></span>  
  
## <a name="compiling-the-code"></a><span data-ttu-id="97231-113">Compilando o código</span><span class="sxs-lookup"><span data-stu-id="97231-113">Compiling the Code</span></span>  
 <span data-ttu-id="97231-114">O exemplo de código anterior foi projetado para uso com Windows Forms e requer o <xref:System.Windows.Forms.PaintEventArgs> `e`, que é um parâmetro de <xref:System.Windows.Forms.PaintEventHandler>.</span><span class="sxs-lookup"><span data-stu-id="97231-114">The preceding code example is designed for use with Windows Forms, and it requires the <xref:System.Windows.Forms.PaintEventArgs> `e`, which is a parameter of <xref:System.Windows.Forms.PaintEventHandler>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="97231-115">Consulte também</span><span class="sxs-lookup"><span data-stu-id="97231-115">See also</span></span>

- <xref:System.Windows.Forms.TextRenderer>
- <xref:System.Drawing.Font>
- <xref:System.Drawing.Color>
- [<span data-ttu-id="97231-116">Usando fontes e texto</span><span class="sxs-lookup"><span data-stu-id="97231-116">Using Fonts and Text</span></span>](using-fonts-and-text.md)
