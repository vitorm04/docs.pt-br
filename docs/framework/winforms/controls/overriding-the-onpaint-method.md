---
title: "Substituindo o método OnPaint"
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
- Paint event [Windows Forms], handling in Windows Forms custom control
- OnPaint method [Windows Forms], overriding in Windows Forms custom controls
ms.assetid: e9ca2723-0107-4540-bb21-4f5ffb4a9906
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 7d9012d1a31eeaf50560b6166d32ac58662c5aa4
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="overriding-the-onpaint-method"></a>Substituindo o método OnPaint
As etapas básicas para a substituição de qualquer evento definido no [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] são idênticas e são resumidas na lista a seguir.  
  
#### <a name="to-override-an-inherited-event"></a>Substituir um evento herdado  
  
1.  Substituir o método `On`*EventName* protegido.  
  
2.  Chame o método `On`*EventName* da classe base do método `On`*EventName* substituído, de modo que delegados registrados recebam o evento.  
  
 O <xref:System.Windows.Forms.Control.Paint> evento é abordado em detalhes aqui porque todos os controles de formulários do Windows devem substituir o <xref:System.Windows.Forms.Control.Paint> evento que ele herda de <xref:System.Windows.Forms.Control>. A base de <xref:System.Windows.Forms.Control> classe não sabe como um controle derivado deve ser desenhado e não fornece qualquer lógica de pintura no <xref:System.Windows.Forms.Control.OnPaint%2A> método. O <xref:System.Windows.Forms.Control.OnPaint%2A> método <xref:System.Windows.Forms.Control> simplesmente despacha o <xref:System.Windows.Forms.Control.Paint> evento em receptores de evento registrado.  
  
 Se você trabalhou por meio do exemplo em [como: desenvolver um controle de Windows Forms simples](../../../../docs/framework/winforms/controls/how-to-develop-a-simple-windows-forms-control.md), você viu um exemplo de substituição de <xref:System.Windows.Forms.Control.OnPaint%2A> método. O fragmento de código a seguir é retirado desse exemplo.  
  
```vb  
Public Class FirstControl  
   Inherits Control  
  
   Public Sub New()  
   End Sub  
  
   Protected Overrides Sub OnPaint(e As PaintEventArgs)  
      ' Call the OnPaint method of the base class.  
      MyBase.OnPaint(e)  
      ' Call methods of the System.Drawing.Graphics object.  
      e.Graphics.DrawString(Text, Font, New SolidBrush(ForeColor), RectangleF.op_Implicit(ClientRectangle))  
   End Sub  
End Class   
```  
  
```csharp  
public class FirstControl : Control{  
   public FirstControl() {}  
   protected override void OnPaint(PaintEventArgs e) {  
      // Call the OnPaint method of the base class.  
      base.OnPaint(e);  
      // Call methods of the System.Drawing.Graphics object.  
      e.Graphics.DrawString(Text, Font, new SolidBrush(ForeColor), ClientRectangle);  
   }   
}   
```  
  
 O <xref:System.Windows.Forms.PaintEventArgs> classe contém dados para o <xref:System.Windows.Forms.Control.Paint> evento. Ele tem duas propriedades, conforme mostrado no código a seguir.  
  
```vb  
Public Class PaintEventArgs  
   Inherits EventArgs  
   ...  
   Public ReadOnly Property ClipRectangle() As System.Drawing.Rectangle  
      ...  
   End Property  
  
   Public ReadOnly Property Graphics() As System.Drawing.Graphics  
      ...  
   End Property   
   ...  
End Class  
```  
  
```csharp  
public class PaintEventArgs : EventArgs {  
...  
    public System.Drawing.Rectangle ClipRectangle {}  
    public System.Drawing.Graphics Graphics {}  
...  
}  
```  
  
 <xref:System.Windows.Forms.PaintEventArgs.ClipRectangle%2A>é o retângulo de pintura e o <xref:System.Windows.Forms.PaintEventArgs.Graphics%2A> propriedade se refere a um <xref:System.Drawing.Graphics> objeto. As classes de <xref:System.Drawing?displayProperty=nameWithType> namespace são gerenciados classes que fornecem acesso à funcionalidade de [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)], a nova biblioteca de elementos gráficos do Windows. O <xref:System.Drawing.Graphics> objeto tem métodos para desenhar pontos, cadeias de caracteres, linhas, arcos, elipses e muitas outras formas.  
  
 Invoca um controle de seu <xref:System.Windows.Forms.Control.OnPaint%2A> método sempre que precisar alterar sua exibição visual. Esse método por sua vez dispara o <xref:System.Windows.Forms.Control.Paint> evento.  
  
## <a name="see-also"></a>Consulte também  
 [Eventos](../../../../docs/standard/events/index.md)  
 [Renderizando um controle dos Windows Forms](../../../../docs/framework/winforms/controls/rendering-a-windows-forms-control.md)  
 [Definindo um evento](../../../../docs/framework/winforms/controls/defining-an-event-in-windows-forms-controls.md)
