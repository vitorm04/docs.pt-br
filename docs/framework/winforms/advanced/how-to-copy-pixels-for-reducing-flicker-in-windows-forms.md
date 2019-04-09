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
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59094028"
---
# <a name="how-to-copy-pixels-for-reducing-flicker-in-windows-forms"></a>Como: copiar pixels para reduzir a cintilação no Windows Forms
Ao animar um gráfico simples, os usuários podem encontrar cintilação ou outro efeito visual indesejado. Uma forma de limitar esse problema é usar um processo de “transferência de bits” no gráfico. Transferência de bits é a "transferência de blocos de bit" dos dados de cor de um retângulo de pixels de origem para um retângulo de pixels de destino.  
  
 Com o Windows Forms, bitblt é feito usando o <xref:System.Drawing.Graphics.CopyFromScreen%2A> método da <xref:System.Drawing.Graphics> classe. Nos parâmetros do método, você especifica a origem e o destino (como pontos), o tamanho da área a ser copiada e o objeto gráfico usado para desenhar a nova forma.  
  
 No exemplo a seguir, uma forma é desenhada no formulário em seu <xref:System.Windows.Forms.Control.Paint> manipulador de eventos. Em seguida, o <xref:System.Drawing.Graphics.CopyFromScreen%2A> método é usado para duplicar a forma.  
  
> [!NOTE]
>  Configuração do formulário <xref:System.Windows.Forms.Control.DoubleBuffered%2A> propriedade para `true` fará o código com base em elementos gráficos no <xref:System.Windows.Forms.Control.Paint> evento ser armazenada em buffer duplo. Embora isso não terá qualquer ganho de desempenho perceptível ao usar o código a seguir, é algo para ter em mente ao trabalhar com código de manipulação de gráficos mais complexo.  
  
## <a name="example"></a>Exemplo  
  
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
  
## <a name="compiling-the-code"></a>Compilando o código  
 O código acima é executado no formulário de <xref:System.Windows.Forms.Control.Paint> manipulador de eventos, de modo que os gráficos persistem quando o formulário é redesenhado. Como tal, não chame métodos relacionados a elementos gráficos <xref:System.Windows.Forms.Form.Load> manipulador de eventos, porque o conteúdo desenhado não será redesenhado se o formulário for redimensionado ou obscurecido por outro formulário.  
  
## <a name="see-also"></a>Consulte também

- <xref:System.Drawing.CopyPixelOperation>
- <xref:System.Drawing.Graphics.FillRectangle%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.Control.OnPaint%2A?displayProperty=nameWithType>
- [Elementos gráficos e desenho no Windows Forms](graphics-and-drawing-in-windows-forms.md)
- [Usando uma caneta para desenhar linhas e formas](using-a-pen-to-draw-lines-and-shapes.md)
