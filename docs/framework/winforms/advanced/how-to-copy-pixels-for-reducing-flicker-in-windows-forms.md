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
# <a name="how-to-copy-pixels-for-reducing-flicker-in-windows-forms"></a>Como copiar pixels para reduzir a cintilação no Windows Forms
Ao animar um gráfico simples, os usuários podem encontrar cintilação ou outro efeito visual indesejado. Uma forma de limitar esse problema é usar um processo de “transferência de bits” no gráfico. Transferência de bits é a "transferência de blocos de bit" dos dados de cor de um retângulo de pixels de origem para um retângulo de pixels de destino.  
  
 Com o Windows Forms, o <xref:System.Drawing.Graphics.CopyFromScreen%2A> bitblt <xref:System.Drawing.Graphics> é realizado usando o método da classe. Nos parâmetros do método, você especifica a origem e o destino (como pontos), o tamanho da área a ser copiada e o objeto gráfico usado para desenhar a nova forma.  
  
 No exemplo abaixo, uma forma é desenhada <xref:System.Windows.Forms.Control.Paint> no formulário em seu manipulador de eventos. Em seguida, o <xref:System.Drawing.Graphics.CopyFromScreen%2A> método é usado para duplicar a forma.  
  
> [!NOTE]
> Definir a propriedade <xref:System.Windows.Forms.Control.DoubleBuffered%2A> do `true` formulário para fazer com <xref:System.Windows.Forms.Control.Paint> que o código baseado em gráficos no evento seja duplamente tamponado. Embora isso não tenha ganhos de desempenho perceptíveis ao usar o código abaixo, é algo a ter em mente ao trabalhar com código de manipulação gráfica mais complexo.  
  
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
 O código acima é executado <xref:System.Windows.Forms.Control.Paint> no manipulador de eventos do formulário para que os gráficos persistam quando o formulário é redesenhado. Como tal, não chame métodos relacionados <xref:System.Windows.Forms.Form.Load> a gráficos no manipulador de eventos, pois o conteúdo sorteado não será redesenhado se o formulário for redimensionado ou obscurecido por outro formulário.  
  
## <a name="see-also"></a>Confira também

- <xref:System.Drawing.CopyPixelOperation>
- <xref:System.Drawing.Graphics.FillRectangle%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.Control.OnPaint%2A?displayProperty=nameWithType>
- [Elementos gráficos e desenho no Windows Forms](graphics-and-drawing-in-windows-forms.md)
- [Usando uma caneta para desenhar linhas e formas](using-a-pen-to-draw-lines-and-shapes.md)
