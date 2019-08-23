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
ms.openlocfilehash: 5a18539153c64a5059d8079f6e245115b026bb91
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69950144"
---
# <a name="how-to-copy-pixels-for-reducing-flicker-in-windows-forms"></a>Como: copiar pixels para reduzir a cintilação no Windows Forms
Ao animar um gráfico simples, os usuários podem encontrar cintilação ou outro efeito visual indesejado. Uma forma de limitar esse problema é usar um processo de “transferência de bits” no gráfico. Transferência de bits é a "transferência de blocos de bit" dos dados de cor de um retângulo de pixels de origem para um retângulo de pixels de destino.  
  
 Com Windows Forms, BitBlt é realizado usando o <xref:System.Drawing.Graphics.CopyFromScreen%2A> método <xref:System.Drawing.Graphics> da classe. Nos parâmetros do método, você especifica a origem e o destino (como pontos), o tamanho da área a ser copiada e o objeto gráfico usado para desenhar a nova forma.  
  
 No exemplo a seguir, uma forma é desenhada no formulário em <xref:System.Windows.Forms.Control.Paint> seu manipulador de eventos. Em seguida, <xref:System.Drawing.Graphics.CopyFromScreen%2A> o método é usado para duplicar a forma.  
  
> [!NOTE]
> Definir a propriedade do <xref:System.Windows.Forms.Control.DoubleBuffered%2A> formulário como `true` fará com que o código baseado em gráficos <xref:System.Windows.Forms.Control.Paint> no evento seja armazenado em buffer duplo. Embora isso não tenha nenhum ganho de desempenho de discerníveis ao usar o código abaixo, é algo a ter em mente ao trabalhar com um código de manipulação de gráficos mais complexo.  
  
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
 O código acima é executado no manipulador de eventos <xref:System.Windows.Forms.Control.Paint> do formulário para que os elementos gráficos persistam quando o formulário é redesenhado. Como tal, não chame métodos relacionados a gráficos no <xref:System.Windows.Forms.Form.Load> manipulador de eventos, pois o conteúdo desenhado não será redesenhado se o formulário for redimensionado ou obscurecido por outro formulário.  
  
## <a name="see-also"></a>Consulte também

- <xref:System.Drawing.CopyPixelOperation>
- <xref:System.Drawing.Graphics.FillRectangle%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.Control.OnPaint%2A?displayProperty=nameWithType>
- [Elementos Gráficos e Desenho nos Windows Forms](graphics-and-drawing-in-windows-forms.md)
- [Usando uma caneta para desenhar linhas e formas](using-a-pen-to-draw-lines-and-shapes.md)
