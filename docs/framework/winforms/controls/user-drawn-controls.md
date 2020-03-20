---
title: Controles desenhados pelo usuário
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- custom controls [Windows Forms], user-drawn
- OnPaint method [Windows Forms]
- user-drawn controls [Windows Forms]
ms.assetid: 034af4b5-457f-4160-a937-22891817faa8
ms.openlocfilehash: c68c8c88376cfe7295962264c466030115f2f3db
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79182016"
---
# <a name="user-drawn-controls"></a>Controles desenhados pelo usuário
O .NET Framework possibilita que você desenvolva facilmente seus próprios controles. Você pode criar um controle de usuário, que é um conjunto de controles padrão vinculados por código ou pode criar seu próprio controle desde o início. Você pode até mesmo usar herança para criar um controle que herde de um controle existente e adicionar à sua funcionalidade inerente. Independentemente da abordagem utilizada, o .NET Framework oferece a funcionalidade de desenhar uma interface gráfica personalizada para qualquer controle que você criar.  
  
 A pintura de um controle é realizada pela <xref:System.Windows.Forms.Control.OnPaint%2A> execução de código no método do controle. O único argumento <xref:System.Windows.Forms.Control.OnPaint%2A> do <xref:System.Windows.Forms.PaintEventArgs> método é um objeto que fornece todas as informações e funcionalidades necessárias para renderizar seu controle. O <xref:System.Windows.Forms.PaintEventArgs> fornece como propriedades dois objetos principais que serão usados na renderização do seu controle:  
  
- <xref:System.Windows.Forms.PaintEventArgs.ClipRectangle%2A>objeto - o retângulo que representa a parte do controle que será desenhada. Pode ser todo o controle ou parte do controle, dependendo de como o controle é desenhado.  
  
- <xref:System.Drawing.Graphics>objeto - encapsula vários objetos e métodos orientados a gráficos que fornecem a funcionalidade necessária para desenhar seu controle.  
  
 Para obter mais <xref:System.Drawing.Graphics> informações sobre o objeto e como usá-lo, consulte [Como: Criar objetos gráficos para desenho](../advanced/how-to-create-graphics-objects-for-drawing.md).  
  
 O <xref:System.Windows.Forms.Control.OnPaint%2A> evento é acionado sempre que o controle é <xref:System.Windows.Forms.PaintEventArgs.ClipRectangle%2A> desenhado ou atualizado na tela, e o objeto representa o retângulo no qual a pintura ocorrerá. Se todo o controle precisar ser <xref:System.Windows.Forms.PaintEventArgs.ClipRectangle%2A> atualizado, o testamento representará o tamanho de todo o controle. Se apenas parte do controle precisar ser atualizada, no entanto, o <xref:System.Windows.Forms.PaintEventArgs.ClipRectangle%2A> objeto representará apenas a região que precisa ser redesenhada. Um exemplo de um caso assim seria quando um controle foi parcialmente encoberto por outro controle ou formulário na interface do usuário.  
  
 Ao herdar <xref:System.Windows.Forms.Control> da classe, você <xref:System.Windows.Forms.Control.OnPaint%2A> deve substituir o método e fornecer código de renderização gráfica dentro. Se você quiser fornecer uma interface gráfica personalizada para um controle de usuário ou um <xref:System.Windows.Forms.Control.OnPaint%2A> controle herdado, você também pode fazê-lo substituindo o método. Um exemplo é mostrado abaixo:  
  
```vb  
Protected Overrides Sub OnPaint(ByVal e As PaintEventArgs)  
   ' Call the OnPaint method of the base class.  
   MyBase.OnPaint(e)  
  
   ' Declare and instantiate a drawing pen.  
   Using myPen As System.Drawing.Pen = New System.Drawing.Pen(Color.Aqua)  
      ' Draw an aqua rectangle in the rectangle represented by the control.  
      e.Graphics.DrawRectangle(myPen, New Rectangle(Me.Location, Me.Size))  
   End Using
End Sub  
```  
  
```csharp  
protected override void OnPaint(PaintEventArgs e)  
{  
   // Call the OnPaint method of the base class.  
   base.OnPaint(e);  
  
   // Declare and instantiate a new pen.  
   using (System.Drawing.Pen myPen = new System.Drawing.Pen(Color.Aqua))  
   {
      // Draw an aqua rectangle in the rectangle represented by the control.  
      e.Graphics.DrawRectangle(myPen, new Rectangle(this.Location,
         this.Size));  
   }
}  
```  
  
 O exemplo anterior demonstra como renderizar um controle com uma representação gráfica muito simples. Ele chama <xref:System.Windows.Forms.Control.OnPaint%2A> o método da classe <xref:System.Drawing.Pen> base, cria um objeto com o qual desenhar, e finalmente <xref:System.Windows.Forms.Control.Location%2A> <xref:System.Windows.Forms.Control.Size%2A> desenha uma elipse no retângulo determinado pelo e do controle. Embora a maioria dos códigos de renderização seja significativamente <xref:System.Drawing.Graphics> mais complicado <xref:System.Windows.Forms.PaintEventArgs> do que este, este exemplo demonstra o uso do objeto contido dentro do objeto. Observe que se você está herdando de uma classe que <xref:System.Windows.Forms.UserControl> <xref:System.Windows.Forms.Button>já tem uma representação gráfica, como ou , e você não <xref:System.Windows.Forms.Control.OnPaint%2A> deseja incorporar essa representação em sua renderização, você não deve chamar o método da sua classe base.  
  
 O código <xref:System.Windows.Forms.Control.OnPaint%2A> no método do seu controle será executado quando o controle for desenhado pela primeira vez e sempre que for atualizado. Para garantir que o controle seja redesenhado sempre que ele for redimensionado, adicione a seguinte linha ao construtor do seu controle:  
  
```vb  
SetStyle(ControlStyles.ResizeRedraw, True)  
```  
  
```csharp  
SetStyle(ControlStyles.ResizeRedraw, true);  
```  
  
> [!NOTE]
> Use <xref:System.Windows.Forms.Control.Region%2A?displayProperty=nameWithType> a propriedade para implementar um controle não retangular.  
  
## <a name="see-also"></a>Confira também

- <xref:System.Windows.Forms.Control.Region%2A>
- <xref:System.Windows.Forms.ControlStyles>
- <xref:System.Drawing.Graphics>
- <xref:System.Windows.Forms.Control.OnPaint%2A>
- <xref:System.Windows.Forms.PaintEventArgs>
- [Como Criar Objetos Gráficos para Desenho](../advanced/how-to-create-graphics-objects-for-drawing.md)
- [Controles constituintes](constituent-controls.md)
- [Variedades de Controles Personalizados](varieties-of-custom-controls.md)
