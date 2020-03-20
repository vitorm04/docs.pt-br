---
title: 'Como: Copiar pixels para reduzir flicker'
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
ms.openlocfilehash: a25295532d7123d92bcacc6828d3e8cfcc839d6e
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79182580"
---
# <a name="how-to-copy-pixels-for-reducing-flicker-in-windows-forms"></a><span data-ttu-id="9076a-102">Como copiar pixels para reduzir a cintilação no Windows Forms</span><span class="sxs-lookup"><span data-stu-id="9076a-102">How to: Copy Pixels for Reducing Flicker in Windows Forms</span></span>
<span data-ttu-id="9076a-103">Ao animar um gráfico simples, os usuários podem encontrar cintilação ou outro efeito visual indesejado.</span><span class="sxs-lookup"><span data-stu-id="9076a-103">When you animate a simple graphic, users can sometimes encounter flicker or other undesirable visual effects.</span></span> <span data-ttu-id="9076a-104">Uma forma de limitar esse problema é usar um processo de “transferência de bits” no gráfico.</span><span class="sxs-lookup"><span data-stu-id="9076a-104">One way to limit this problem is to use a "bitblt" process on the graphic.</span></span> <span data-ttu-id="9076a-105">Transferência de bits é a "transferência de blocos de bit" dos dados de cor de um retângulo de pixels de origem para um retângulo de pixels de destino.</span><span class="sxs-lookup"><span data-stu-id="9076a-105">Bitblt is the "bit-block transfer" of the color data from an origin rectangle of pixels to a destination rectangle of pixels.</span></span>  
  
 <span data-ttu-id="9076a-106">Com o Windows Forms, o <xref:System.Drawing.Graphics.CopyFromScreen%2A> bitblt <xref:System.Drawing.Graphics> é realizado usando o método da classe.</span><span class="sxs-lookup"><span data-stu-id="9076a-106">With Windows Forms, bitblt is accomplished using the <xref:System.Drawing.Graphics.CopyFromScreen%2A> method of the <xref:System.Drawing.Graphics> class.</span></span> <span data-ttu-id="9076a-107">Nos parâmetros do método, você especifica a origem e o destino (como pontos), o tamanho da área a ser copiada e o objeto gráfico usado para desenhar a nova forma.</span><span class="sxs-lookup"><span data-stu-id="9076a-107">In the parameters of the method, you specify the source and destination (as points), the size of the area to be copied, and the graphics object used to draw the new shape.</span></span>  
  
 <span data-ttu-id="9076a-108">No exemplo abaixo, uma forma é desenhada <xref:System.Windows.Forms.Control.Paint> no formulário em seu manipulador de eventos.</span><span class="sxs-lookup"><span data-stu-id="9076a-108">In the example below, a shape is drawn on the form in its <xref:System.Windows.Forms.Control.Paint> event handler.</span></span> <span data-ttu-id="9076a-109">Em seguida, o <xref:System.Drawing.Graphics.CopyFromScreen%2A> método é usado para duplicar a forma.</span><span class="sxs-lookup"><span data-stu-id="9076a-109">Then, the <xref:System.Drawing.Graphics.CopyFromScreen%2A> method is used to duplicate the shape.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="9076a-110">Definir a propriedade <xref:System.Windows.Forms.Control.DoubleBuffered%2A> do `true` formulário para fazer com <xref:System.Windows.Forms.Control.Paint> que o código baseado em gráficos no evento seja duplamente tamponado.</span><span class="sxs-lookup"><span data-stu-id="9076a-110">Setting the form's <xref:System.Windows.Forms.Control.DoubleBuffered%2A> property to `true` will make graphics-based code in the <xref:System.Windows.Forms.Control.Paint> event be double-buffered.</span></span> <span data-ttu-id="9076a-111">Embora isso não tenha ganhos de desempenho perceptíveis ao usar o código abaixo, é algo a ter em mente ao trabalhar com código de manipulação gráfica mais complexo.</span><span class="sxs-lookup"><span data-stu-id="9076a-111">While this will not have any discernible performance gains when using the code below, it is something to keep in mind when working with more complex graphics-manipulation code.</span></span>  
  
## <a name="example"></a><span data-ttu-id="9076a-112">Exemplo</span><span class="sxs-lookup"><span data-stu-id="9076a-112">Example</span></span>  
  
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
  
## <a name="compiling-the-code"></a><span data-ttu-id="9076a-113">Compilando o código</span><span class="sxs-lookup"><span data-stu-id="9076a-113">Compiling the Code</span></span>  
 <span data-ttu-id="9076a-114">O código acima é executado <xref:System.Windows.Forms.Control.Paint> no manipulador de eventos do formulário para que os gráficos persistam quando o formulário é redesenhado.</span><span class="sxs-lookup"><span data-stu-id="9076a-114">The code above is run in the form's <xref:System.Windows.Forms.Control.Paint> event handler so that the graphics persist when the form is redrawn.</span></span> <span data-ttu-id="9076a-115">Como tal, não chame métodos relacionados <xref:System.Windows.Forms.Form.Load> a gráficos no manipulador de eventos, pois o conteúdo sorteado não será redesenhado se o formulário for redimensionado ou obscurecido por outro formulário.</span><span class="sxs-lookup"><span data-stu-id="9076a-115">As such, do not call graphics-related methods in the <xref:System.Windows.Forms.Form.Load> event handler, because the drawn content will not be redrawn if the form is resized or obscured by another form.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9076a-116">Confira também</span><span class="sxs-lookup"><span data-stu-id="9076a-116">See also</span></span>

- <xref:System.Drawing.CopyPixelOperation>
- <xref:System.Drawing.Graphics.FillRectangle%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.Control.OnPaint%2A?displayProperty=nameWithType>
- [<span data-ttu-id="9076a-117">Elementos gráficos e desenho no Windows Forms</span><span class="sxs-lookup"><span data-stu-id="9076a-117">Graphics and Drawing in Windows Forms</span></span>](graphics-and-drawing-in-windows-forms.md)
- [<span data-ttu-id="9076a-118">Usando uma caneta para desenhar linhas e formas</span><span class="sxs-lookup"><span data-stu-id="9076a-118">Using a Pen to Draw Lines and Shapes</span></span>](using-a-pen-to-draw-lines-and-shapes.md)
