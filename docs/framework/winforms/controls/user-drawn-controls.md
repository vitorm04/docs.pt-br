---
title: "Controles desenhados pelo usuário"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- custom controls [Windows Forms], user-drawn
- OnPaint method [Windows Forms]
- user-drawn controls [Windows Forms]
ms.assetid: 034af4b5-457f-4160-a937-22891817faa8
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 42f208d10b1c111f98af3c803148590466baddf0
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="user-drawn-controls"></a>Controles desenhados pelo usuário
O .NET Framework possibilita que você desenvolva facilmente seus próprios controles. Você pode criar um controle de usuário, que é um conjunto de controles padrão vinculados por código ou pode criar seu próprio controle desde o início. Você pode até mesmo usar herança para criar um controle que herde de um controle existente e adicionar à sua funcionalidade inerente. Independentemente da abordagem utilizada, o .NET Framework oferece a funcionalidade de desenhar uma interface gráfica personalizada para qualquer controle que você criar.  
  
 Pintura de um controle é realizada pela execução de código do controle <xref:System.Windows.Forms.Control.OnPaint%2A> método. O único argumento de <xref:System.Windows.Forms.Control.OnPaint%2A> método é um <xref:System.Windows.Forms.PaintEventArgs> objeto que fornece todas as informações e a funcionalidade necessária para processar o controle. O <xref:System.Windows.Forms.PaintEventArgs> fornece como propriedades de dois objetos principais que serão usados no processamento de seu controle:  
  
-   <xref:System.Windows.Forms.PaintEventArgs.ClipRectangle%2A>objeto - o retângulo que representa a parte do controle que será desenhado. Pode ser todo o controle ou parte do controle, dependendo de como o controle é desenhado.  
  
-   <xref:System.Drawing.Graphics>objeto - encapsula vários gráficos e orientada a objetos e métodos que fornecem a funcionalidade necessária para desenhar seu controle.  
  
 Para obter mais informações sobre o <xref:System.Drawing.Graphics> objeto e como usá-lo, consulte [como: criar objetos gráficos para desenho](../../../../docs/framework/winforms/advanced/how-to-create-graphics-objects-for-drawing.md).  
  
 O <xref:System.Windows.Forms.Control.OnPaint%2A> evento é acionado sempre que o controle é desenhado ou atualizado na tela e o <xref:System.Windows.Forms.PaintEventArgs.ClipRectangle%2A> objeto representa o retângulo na qual a pintura será realizada. Se todo o controle precisa ser atualizado, o <xref:System.Windows.Forms.PaintEventArgs.ClipRectangle%2A> representa o tamanho de todo o controle. Se apenas parte do controle precisa ser atualizado, no entanto, o <xref:System.Windows.Forms.PaintEventArgs.ClipRectangle%2A> objeto representa apenas a região que precisa ser redesenhada. Um exemplo de um caso assim seria quando um controle foi parcialmente encoberto por outro controle ou formulário na interface do usuário.  
  
 Ao herdar do <xref:System.Windows.Forms.Control> classe, você deve substituir o <xref:System.Windows.Forms.Control.OnPaint%2A> método e fornecem código de processamento de elementos gráficos dentro. Se você quiser fornecer uma interface gráfica personalizada para um controle de usuário ou um controle herdado, você também pode fazer isso, substituindo o <xref:System.Windows.Forms.Control.OnPaint%2A> método. Um exemplo é mostrado abaixo:  
  
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
  
 O exemplo anterior demonstra como renderizar um controle com uma representação gráfica muito simples. Ele chama o <xref:System.Windows.Forms.Control.OnPaint%2A> método da classe base, ele cria um <xref:System.Drawing.Pen> do objeto com o qual desenhar e finalmente desenha uma elipse no retângulo é determinado pelo <xref:System.Windows.Forms.Control.Location%2A> e <xref:System.Windows.Forms.Control.Size%2A> do controle. Embora a maioria dos códigos de renderização será significativamente mais complicado do que isso, este exemplo demonstra o uso do <xref:System.Drawing.Graphics> objeto contido dentro de <xref:System.Windows.Forms.PaintEventArgs> objeto. Observe que, se você estiver herdando de uma classe que já tem uma representação gráfica, como <xref:System.Windows.Forms.UserControl> ou <xref:System.Windows.Forms.Button>e você não deseja incorporar essa representação seu processamento, você não deve chamar sua classe base <xref:System.Windows.Forms.Control.OnPaint%2A> método.  
  
 O código de <xref:System.Windows.Forms.Control.OnPaint%2A> método do controle será executado quando o controle é desenhado primeiro e sempre que ele for atualizado. Para garantir que o controle seja redesenhado sempre que ele for redimensionado, adicione a seguinte linha ao construtor do seu controle:  
  
```vb  
SetStyle(ControlStyles.ResizeRedraw, True)  
```  
  
```csharp  
SetStyle(ControlStyles.ResizeRedraw, true);  
```  
  
> [!NOTE]
>  Use o <xref:System.Windows.Forms.Control.Region%2A?displayProperty=nameWithType> propriedade para implementar um controle não retangulares.  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.Windows.Forms.Control.Region%2A>  
 <xref:System.Windows.Forms.ControlStyles>  
 <xref:System.Drawing.Graphics>  
 <xref:System.Windows.Forms.Control.OnPaint%2A>  
 <xref:System.Windows.Forms.PaintEventArgs>  
 [Como Criar Objetos Gráficos para Desenho](../../../../docs/framework/winforms/advanced/how-to-create-graphics-objects-for-drawing.md)  
 [Controles constituintes](../../../../docs/framework/winforms/controls/constituent-controls.md)  
 [Variedades de Controles Personalizados](../../../../docs/framework/winforms/controls/varieties-of-custom-controls.md)
