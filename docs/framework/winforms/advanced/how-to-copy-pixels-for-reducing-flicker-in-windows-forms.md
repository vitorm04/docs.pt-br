---
title: Como copiar pixels para reduzir a cintilação no Windows Forms
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- bitblt
- graphics [Windows Forms], copying
- flicker [Windows Forms], reducing in Windows Forms
- graphics [Windows Forms], reducing flicker
- pixels [Windows Forms], copying
- flicker
- bit-block transfer
ms.assetid: 33b76910-13a3-4521-be98-5c097341ae3b
ms.openlocfilehash: dc5f05ff4ea9f3c2b828cbe37860e1bd241fc604
ms.sourcegitcommit: 3d42e1d73e21c35c540dd4adbea23efcbe1b8b0a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/20/2018
ms.locfileid: "36270429"
---
# <a name="how-to-copy-pixels-for-reducing-flicker-in-windows-forms"></a><span data-ttu-id="507be-102">Como copiar pixels para reduzir a cintilação no Windows Forms</span><span class="sxs-lookup"><span data-stu-id="507be-102">How to: Copy Pixels for Reducing Flicker in Windows Forms</span></span>
<span data-ttu-id="507be-103">Ao animar um gráfico simples, os usuários podem encontrar cintilação ou outro efeito visual indesejado.</span><span class="sxs-lookup"><span data-stu-id="507be-103">When you animate a simple graphic, users can sometimes encounter flicker or other undesirable visual effects.</span></span> <span data-ttu-id="507be-104">Uma forma de limitar esse problema é usar um processo de “transferência de bits” no gráfico.</span><span class="sxs-lookup"><span data-stu-id="507be-104">One way to limit this problem is to use a "bitblt" process on the graphic.</span></span> <span data-ttu-id="507be-105">Transferência de bits é a "transferência de blocos de bit" dos dados de cor de um retângulo de pixels de origem para um retângulo de pixels de destino.</span><span class="sxs-lookup"><span data-stu-id="507be-105">Bitblt is the "bit-block transfer" of the color data from an origin rectangle of pixels to a destination rectangle of pixels.</span></span>  
  
 <span data-ttu-id="507be-106">Com o Windows Forms, bitblt é realizada usando o <xref:System.Drawing.Graphics.CopyFromScreen%2A> método o <xref:System.Drawing.Graphics> classe.</span><span class="sxs-lookup"><span data-stu-id="507be-106">With Windows Forms, bitblt is accomplished using the <xref:System.Drawing.Graphics.CopyFromScreen%2A> method of the <xref:System.Drawing.Graphics> class.</span></span> <span data-ttu-id="507be-107">Nos parâmetros do método, você especifica a origem e o destino (como pontos), o tamanho da área a ser copiada e o objeto gráfico usado para desenhar a nova forma.</span><span class="sxs-lookup"><span data-stu-id="507be-107">In the parameters of the method, you specify the source and destination (as points), the size of the area to be copied, and the graphics object used to draw the new shape.</span></span>  
  
 <span data-ttu-id="507be-108">No exemplo a seguir, uma forma será desenhada no formulário no seu <xref:System.Windows.Forms.Control.Paint> manipulador de eventos.</span><span class="sxs-lookup"><span data-stu-id="507be-108">In the example below, a shape is drawn on the form in its <xref:System.Windows.Forms.Control.Paint> event handler.</span></span> <span data-ttu-id="507be-109">Em seguida, o <xref:System.Drawing.Graphics.CopyFromScreen%2A> método é usado para duplicar a forma.</span><span class="sxs-lookup"><span data-stu-id="507be-109">Then, the <xref:System.Drawing.Graphics.CopyFromScreen%2A> method is used to duplicate the shape.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="507be-110">Configuração do formulário <xref:System.Windows.Forms.Control.DoubleBuffered%2A> propriedade `true` fará o código de elementos gráficos no <xref:System.Windows.Forms.Control.Paint> evento ser armazenada em buffer duplo.</span><span class="sxs-lookup"><span data-stu-id="507be-110">Setting the form's <xref:System.Windows.Forms.Control.DoubleBuffered%2A> property to `true` will make graphics-based code in the <xref:System.Windows.Forms.Control.Paint> event be double-buffered.</span></span> <span data-ttu-id="507be-111">Embora isso não terá nenhum ganho de desempenho perceptível ao usar o código a seguir, é algo para ter em mente ao trabalhar com o código de manipulação de gráficos mais complexo.</span><span class="sxs-lookup"><span data-stu-id="507be-111">While this will not have any discernible performance gains when using the code below, it is something to keep in mind when working with more complex graphics-manipulation code.</span></span>  
  
## <a name="example"></a><span data-ttu-id="507be-112">Exemplo</span><span class="sxs-lookup"><span data-stu-id="507be-112">Example</span></span>  
  
```vb  
Private Sub Form1_Paint(ByVal sender As Object, ByVal e As _  
    System.Windows.Forms.PaintEventArgs) Handles MyBase.Paint  
    ' Draw a circle with a bar on top.  
        e.Graphics.FillEllipse(Brushes.DarkBlue, New Rectangle _  
             (10, 10, 60, 60))  
        e.Graphics.FillRectangle(Brushes.Khaki, New Rectangle _  
             (20, 30, 60, 10))  
    ' Copy the graphic to a new location.  
        e.Graphics.CopyFromScreen(New Point(10, 10), New Point _  
             (100, 100), New Size(70, 70))  
End Sub  
```  
  
```csharp  
private void Form1_Paint(System.Object sender,  
    System.Windows.Forms.PaintEventArgs e)  
        {  
        e.Graphics.FillEllipse(Brushes.DarkBlue, new  
            Rectangle(10,10,60,60));  
        e.Graphics.FillRectangle(Brushes.Khaki, new  
            Rectangle(20,30,60,10));  
        e.Graphics.CopyFromScreen(new Point(10, 10), new Point(100, 100),   
            new Size(70, 70));  
}  
```  
  
## <a name="compiling-the-code"></a><span data-ttu-id="507be-113">Compilando o código</span><span class="sxs-lookup"><span data-stu-id="507be-113">Compiling the Code</span></span>  
 <span data-ttu-id="507be-114">O código acima é executado do formulário <xref:System.Windows.Forms.Control.Paint> manipulador de eventos para que os elementos gráficos persistem quando o formulário é redesenhado.</span><span class="sxs-lookup"><span data-stu-id="507be-114">The code above is run in the form's <xref:System.Windows.Forms.Control.Paint> event handler so that the graphics persist when the form is redrawn.</span></span> <span data-ttu-id="507be-115">Como tal, não chamar métodos relacionados a elementos gráficos no <xref:System.Windows.Forms.Form.Load> manipulador de eventos, porque o conteúdo desenhado não será redesenhado se o formulário é redimensionado ou obscurecido por outra forma.</span><span class="sxs-lookup"><span data-stu-id="507be-115">As such, do not call graphics-related methods in the <xref:System.Windows.Forms.Form.Load> event handler, because the drawn content will not be redrawn if the form is resized or obscured by another form.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="507be-116">Consulte também</span><span class="sxs-lookup"><span data-stu-id="507be-116">See Also</span></span>  
 <xref:System.Drawing.CopyPixelOperation>  
 <xref:System.Drawing.Graphics.FillRectangle%2A?displayProperty=nameWithType>  
 <xref:System.Windows.Forms.Control.OnPaint%2A?displayProperty=nameWithType>  
 [<span data-ttu-id="507be-117">Elementos Gráficos e Desenho nos Windows Forms</span><span class="sxs-lookup"><span data-stu-id="507be-117">Graphics and Drawing in Windows Forms</span></span>](../../../../docs/framework/winforms/advanced/graphics-and-drawing-in-windows-forms.md)  
 [<span data-ttu-id="507be-118">Usando uma caneta para desenhar linhas e formas</span><span class="sxs-lookup"><span data-stu-id="507be-118">Using a Pen to Draw Lines and Shapes</span></span>](../../../../docs/framework/winforms/advanced/using-a-pen-to-draw-lines-and-shapes.md)
