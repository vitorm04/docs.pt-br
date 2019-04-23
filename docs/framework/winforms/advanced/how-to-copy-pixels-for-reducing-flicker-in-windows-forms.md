---
title: 'Como: copiar pixels para reduzir a cintilação no Windows Forms'
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
ms.openlocfilehash: e3d1c2b681e98dc7c45467683924dd4022eb377e
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59094028"
---
# <a name="how-to-copy-pixels-for-reducing-flicker-in-windows-forms"></a><span data-ttu-id="8a97e-102">Como: copiar pixels para reduzir a cintilação no Windows Forms</span><span class="sxs-lookup"><span data-stu-id="8a97e-102">How to: Copy Pixels for Reducing Flicker in Windows Forms</span></span>
<span data-ttu-id="8a97e-103">Ao animar um gráfico simples, os usuários podem encontrar cintilação ou outro efeito visual indesejado.</span><span class="sxs-lookup"><span data-stu-id="8a97e-103">When you animate a simple graphic, users can sometimes encounter flicker or other undesirable visual effects.</span></span> <span data-ttu-id="8a97e-104">Uma forma de limitar esse problema é usar um processo de “transferência de bits” no gráfico.</span><span class="sxs-lookup"><span data-stu-id="8a97e-104">One way to limit this problem is to use a "bitblt" process on the graphic.</span></span> <span data-ttu-id="8a97e-105">Transferência de bits é a "transferência de blocos de bit" dos dados de cor de um retângulo de pixels de origem para um retângulo de pixels de destino.</span><span class="sxs-lookup"><span data-stu-id="8a97e-105">Bitblt is the "bit-block transfer" of the color data from an origin rectangle of pixels to a destination rectangle of pixels.</span></span>  
  
 <span data-ttu-id="8a97e-106">Com o Windows Forms, bitblt é feito usando o <xref:System.Drawing.Graphics.CopyFromScreen%2A> método da <xref:System.Drawing.Graphics> classe.</span><span class="sxs-lookup"><span data-stu-id="8a97e-106">With Windows Forms, bitblt is accomplished using the <xref:System.Drawing.Graphics.CopyFromScreen%2A> method of the <xref:System.Drawing.Graphics> class.</span></span> <span data-ttu-id="8a97e-107">Nos parâmetros do método, você especifica a origem e o destino (como pontos), o tamanho da área a ser copiada e o objeto gráfico usado para desenhar a nova forma.</span><span class="sxs-lookup"><span data-stu-id="8a97e-107">In the parameters of the method, you specify the source and destination (as points), the size of the area to be copied, and the graphics object used to draw the new shape.</span></span>  
  
 <span data-ttu-id="8a97e-108">No exemplo a seguir, uma forma é desenhada no formulário em seu <xref:System.Windows.Forms.Control.Paint> manipulador de eventos.</span><span class="sxs-lookup"><span data-stu-id="8a97e-108">In the example below, a shape is drawn on the form in its <xref:System.Windows.Forms.Control.Paint> event handler.</span></span> <span data-ttu-id="8a97e-109">Em seguida, o <xref:System.Drawing.Graphics.CopyFromScreen%2A> método é usado para duplicar a forma.</span><span class="sxs-lookup"><span data-stu-id="8a97e-109">Then, the <xref:System.Drawing.Graphics.CopyFromScreen%2A> method is used to duplicate the shape.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="8a97e-110">Configuração do formulário <xref:System.Windows.Forms.Control.DoubleBuffered%2A> propriedade para `true` fará o código com base em elementos gráficos no <xref:System.Windows.Forms.Control.Paint> evento ser armazenada em buffer duplo.</span><span class="sxs-lookup"><span data-stu-id="8a97e-110">Setting the form's <xref:System.Windows.Forms.Control.DoubleBuffered%2A> property to `true` will make graphics-based code in the <xref:System.Windows.Forms.Control.Paint> event be double-buffered.</span></span> <span data-ttu-id="8a97e-111">Embora isso não terá qualquer ganho de desempenho perceptível ao usar o código a seguir, é algo para ter em mente ao trabalhar com código de manipulação de gráficos mais complexo.</span><span class="sxs-lookup"><span data-stu-id="8a97e-111">While this will not have any discernible performance gains when using the code below, it is something to keep in mind when working with more complex graphics-manipulation code.</span></span>  
  
## <a name="example"></a><span data-ttu-id="8a97e-112">Exemplo</span><span class="sxs-lookup"><span data-stu-id="8a97e-112">Example</span></span>  
  
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
  
## <a name="compiling-the-code"></a><span data-ttu-id="8a97e-113">Compilando o código</span><span class="sxs-lookup"><span data-stu-id="8a97e-113">Compiling the Code</span></span>  
 <span data-ttu-id="8a97e-114">O código acima é executado no formulário de <xref:System.Windows.Forms.Control.Paint> manipulador de eventos, de modo que os gráficos persistem quando o formulário é redesenhado.</span><span class="sxs-lookup"><span data-stu-id="8a97e-114">The code above is run in the form's <xref:System.Windows.Forms.Control.Paint> event handler so that the graphics persist when the form is redrawn.</span></span> <span data-ttu-id="8a97e-115">Como tal, não chame métodos relacionados a elementos gráficos <xref:System.Windows.Forms.Form.Load> manipulador de eventos, porque o conteúdo desenhado não será redesenhado se o formulário for redimensionado ou obscurecido por outro formulário.</span><span class="sxs-lookup"><span data-stu-id="8a97e-115">As such, do not call graphics-related methods in the <xref:System.Windows.Forms.Form.Load> event handler, because the drawn content will not be redrawn if the form is resized or obscured by another form.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8a97e-116">Consulte também</span><span class="sxs-lookup"><span data-stu-id="8a97e-116">See also</span></span>

- <xref:System.Drawing.CopyPixelOperation>
- <xref:System.Drawing.Graphics.FillRectangle%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.Control.OnPaint%2A?displayProperty=nameWithType>
- [<span data-ttu-id="8a97e-117">Elementos Gráficos e Desenho nos Windows Forms</span><span class="sxs-lookup"><span data-stu-id="8a97e-117">Graphics and Drawing in Windows Forms</span></span>](graphics-and-drawing-in-windows-forms.md)
- [<span data-ttu-id="8a97e-118">Usando uma caneta para desenhar linhas e formas</span><span class="sxs-lookup"><span data-stu-id="8a97e-118">Using a Pen to Draw Lines and Shapes</span></span>](using-a-pen-to-draw-lines-and-shapes.md)
