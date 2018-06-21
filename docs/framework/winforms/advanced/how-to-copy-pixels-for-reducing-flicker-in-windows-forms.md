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
# <a name="how-to-copy-pixels-for-reducing-flicker-in-windows-forms"></a>Como copiar pixels para reduzir a cintilação no Windows Forms
Ao animar um gráfico simples, os usuários podem encontrar cintilação ou outro efeito visual indesejado. Uma forma de limitar esse problema é usar um processo de “transferência de bits” no gráfico. Transferência de bits é a "transferência de blocos de bit" dos dados de cor de um retângulo de pixels de origem para um retângulo de pixels de destino.  
  
 Com o Windows Forms, bitblt é realizada usando o <xref:System.Drawing.Graphics.CopyFromScreen%2A> método o <xref:System.Drawing.Graphics> classe. Nos parâmetros do método, você especifica a origem e o destino (como pontos), o tamanho da área a ser copiada e o objeto gráfico usado para desenhar a nova forma.  
  
 No exemplo a seguir, uma forma será desenhada no formulário no seu <xref:System.Windows.Forms.Control.Paint> manipulador de eventos. Em seguida, o <xref:System.Drawing.Graphics.CopyFromScreen%2A> método é usado para duplicar a forma.  
  
> [!NOTE]
>  Configuração do formulário <xref:System.Windows.Forms.Control.DoubleBuffered%2A> propriedade `true` fará o código de elementos gráficos no <xref:System.Windows.Forms.Control.Paint> evento ser armazenada em buffer duplo. Embora isso não terá nenhum ganho de desempenho perceptível ao usar o código a seguir, é algo para ter em mente ao trabalhar com o código de manipulação de gráficos mais complexo.  
  
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
 O código acima é executado do formulário <xref:System.Windows.Forms.Control.Paint> manipulador de eventos para que os elementos gráficos persistem quando o formulário é redesenhado. Como tal, não chamar métodos relacionados a elementos gráficos no <xref:System.Windows.Forms.Form.Load> manipulador de eventos, porque o conteúdo desenhado não será redesenhado se o formulário é redimensionado ou obscurecido por outra forma.  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.Drawing.CopyPixelOperation>  
 <xref:System.Drawing.Graphics.FillRectangle%2A?displayProperty=nameWithType>  
 <xref:System.Windows.Forms.Control.OnPaint%2A?displayProperty=nameWithType>  
 [Elementos Gráficos e Desenho nos Windows Forms](../../../../docs/framework/winforms/advanced/graphics-and-drawing-in-windows-forms.md)  
 [Usando uma caneta para desenhar linhas e formas](../../../../docs/framework/winforms/advanced/using-a-pen-to-draw-lines-and-shapes.md)
