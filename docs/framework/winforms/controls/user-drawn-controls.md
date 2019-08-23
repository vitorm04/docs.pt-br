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
ms.openlocfilehash: 50036f5bef323368b4970a080ca7a70cf94252d6
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69966480"
---
# <a name="user-drawn-controls"></a>Controles desenhados pelo usuário
O .NET Framework possibilita que você desenvolva facilmente seus próprios controles. Você pode criar um controle de usuário, que é um conjunto de controles padrão vinculados por código ou pode criar seu próprio controle desde o início. Você pode até mesmo usar herança para criar um controle que herde de um controle existente e adicionar à sua funcionalidade inerente. Independentemente da abordagem utilizada, o .NET Framework oferece a funcionalidade de desenhar uma interface gráfica personalizada para qualquer controle que você criar.  
  
 A pintura de um controle é realizada pela execução do código no método do <xref:System.Windows.Forms.Control.OnPaint%2A> controle. O argumento único do <xref:System.Windows.Forms.Control.OnPaint%2A> método é um <xref:System.Windows.Forms.PaintEventArgs> objeto que fornece todas as informações e funcionalidades necessárias para processar seu controle. O <xref:System.Windows.Forms.PaintEventArgs> fornece como propriedades dois objetos principais que serão usados na renderização do seu controle:  
  
- <xref:System.Windows.Forms.PaintEventArgs.ClipRectangle%2A>objeto-o retângulo que representa a parte do controle que será desenhado. Pode ser todo o controle ou parte do controle, dependendo de como o controle é desenhado.  
  
- <xref:System.Drawing.Graphics>objeto – encapsula vários objetos e métodos orientados a gráficos que fornecem a funcionalidade necessária para desenhar seu controle.  
  
 Para obter mais informações sobre <xref:System.Drawing.Graphics> o objeto e como usá-lo, [consulte Como: Crie objetos gráficos para desenho](../advanced/how-to-create-graphics-objects-for-drawing.md).  
  
 O <xref:System.Windows.Forms.Control.OnPaint%2A> evento é acionado sempre que o controle é desenhado ou atualizado na tela, e o <xref:System.Windows.Forms.PaintEventArgs.ClipRectangle%2A> objeto representa o retângulo no qual ocorrerá a pintura. Se o controle inteiro precisar ser atualizado, o <xref:System.Windows.Forms.PaintEventArgs.ClipRectangle%2A> irá representar o tamanho do controle inteiro. No entanto, se apenas parte do controle precisar ser atualizada, o <xref:System.Windows.Forms.PaintEventArgs.ClipRectangle%2A> objeto representará apenas a região que precisa ser redesenhada. Um exemplo de um caso assim seria quando um controle foi parcialmente encoberto por outro controle ou formulário na interface do usuário.  
  
 Ao herdar da <xref:System.Windows.Forms.Control> classe, você deve substituir o método <xref:System.Windows.Forms.Control.OnPaint%2A> e fornecer o código de renderização de gráficos no. Se você quiser fornecer uma interface gráfica personalizada para um controle de usuário ou um controle herdado, também poderá fazer isso substituindo o <xref:System.Windows.Forms.Control.OnPaint%2A> método. Um exemplo é mostrado abaixo:  
  
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
  
 O exemplo anterior demonstra como renderizar um controle com uma representação gráfica muito simples. Ele chama o <xref:System.Windows.Forms.Control.OnPaint%2A> método da classe base, ele cria um <xref:System.Drawing.Pen> objeto com o qual desenhar e, por fim, desenha uma elipse no retângulo determinado pelo <xref:System.Windows.Forms.Control.Location%2A> e <xref:System.Windows.Forms.Control.Size%2A> do controle. Embora a maior parte do código de renderização seja significativamente mais complicada do que isso, este exemplo demonstra <xref:System.Drawing.Graphics> o uso do objeto <xref:System.Windows.Forms.PaintEventArgs> contido no objeto. Observe que se você estiver herdando de uma classe que já tem uma representação gráfica, como <xref:System.Windows.Forms.UserControl> ou <xref:System.Windows.Forms.Button>, e não quiser incorporar essa representação à renderização, você não deve <xref:System.Windows.Forms.Control.OnPaint%2A> chamar a classe base forma.  
  
 O código no <xref:System.Windows.Forms.Control.OnPaint%2A> método do seu controle será executado quando o controle for desenhado primeiro e sempre que for atualizado. Para garantir que o controle seja redesenhado sempre que ele for redimensionado, adicione a seguinte linha ao construtor do seu controle:  
  
```vb  
SetStyle(ControlStyles.ResizeRedraw, True)  
```  
  
```csharp  
SetStyle(ControlStyles.ResizeRedraw, true);  
```  
  
> [!NOTE]
> Use a <xref:System.Windows.Forms.Control.Region%2A?displayProperty=nameWithType> propriedade para implementar um controle não retangular.  
  
## <a name="see-also"></a>Consulte também

- <xref:System.Windows.Forms.Control.Region%2A>
- <xref:System.Windows.Forms.ControlStyles>
- <xref:System.Drawing.Graphics>
- <xref:System.Windows.Forms.Control.OnPaint%2A>
- <xref:System.Windows.Forms.PaintEventArgs>
- [Como: Criar objetos gráficos para desenho](../advanced/how-to-create-graphics-objects-for-drawing.md)
- [Controles constituintes](constituent-controls.md)
- [Variedades de controles personalizados](varieties-of-custom-controls.md)
