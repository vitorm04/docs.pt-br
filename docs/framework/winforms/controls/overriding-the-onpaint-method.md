---
title: Substituindo o método OnPaint
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Paint event [Windows Forms], handling in Windows Forms custom control
- OnPaint method [Windows Forms], overriding in Windows Forms custom controls
ms.assetid: e9ca2723-0107-4540-bb21-4f5ffb4a9906
ms.openlocfilehash: baf4e6cb3b2a40b1b792ae12e78cb9f878a738ff
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59124300"
---
# <a name="overriding-the-onpaint-method"></a>Substituindo o método OnPaint
As etapas básicas para a substituição de qualquer evento definido no [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] são idênticas e são resumidas na lista a seguir.  
  
#### <a name="to-override-an-inherited-event"></a>Substituir um evento herdado  
  
1.  Substituir o método `On`*EventName* protegido.  
  
2.  Chame o método `On`*EventName* da classe base do método `On`*EventName* substituído, de modo que delegados registrados recebam o evento.  
  
 O <xref:System.Windows.Forms.Control.Paint> evento é discutido em detalhes aqui porque todos os controles Windows Forms devem substituir o <xref:System.Windows.Forms.Control.Paint> eventos que herda de <xref:System.Windows.Forms.Control>. A base <xref:System.Windows.Forms.Control> classe não sabe como um controle derivado deve ser desenhado e não fornece qualquer lógica de pintura no <xref:System.Windows.Forms.Control.OnPaint%2A> método. O <xref:System.Windows.Forms.Control.OnPaint%2A> método de <xref:System.Windows.Forms.Control> simplesmente despacha o <xref:System.Windows.Forms.Control.Paint> evento para receptores de evento registrados.  
  
 Se você trabalhou com o exemplo em [como: Desenvolver um controle simples dos Windows Forms](how-to-develop-a-simple-windows-forms-control.md), você viu um exemplo de substituição a <xref:System.Windows.Forms.Control.OnPaint%2A> método. O fragmento de código a seguir é retirado desse exemplo.  
  
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
public class FirstControl : Control {  
   public FirstControl() {}  
   protected override void OnPaint(PaintEventArgs e) {  
      // Call the OnPaint method of the base class.  
      base.OnPaint(e);  
      // Call methods of the System.Drawing.Graphics object.  
      e.Graphics.DrawString(Text, Font, new SolidBrush(ForeColor), ClientRectangle);  
   }   
}   
```  
  
 O <xref:System.Windows.Forms.PaintEventArgs> classe contém dados para o <xref:System.Windows.Forms.Control.Paint> eventos. Ele tem duas propriedades, conforme mostrado no código a seguir.  
  
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
  
 <xref:System.Windows.Forms.PaintEventArgs.ClipRectangle%2A> é o retângulo a ser pintado e o <xref:System.Windows.Forms.PaintEventArgs.Graphics%2A> propriedade se refere a um <xref:System.Drawing.Graphics> objeto. As classes de <xref:System.Drawing?displayProperty=nameWithType> namespace são gerenciados classes que fornecem acesso à funcionalidade de [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)], a nova biblioteca de gráficos do Windows. O <xref:System.Drawing.Graphics> objeto tem métodos para desenhar pontos, cadeias de caracteres, linhas, arcos, elipses e muitas outras formas.  
  
 Um controle chama seu <xref:System.Windows.Forms.Control.OnPaint%2A> método sempre que precisar alterar sua exibição visual. Esse método por sua vez dispara o <xref:System.Windows.Forms.Control.Paint> eventos.  
  
## <a name="see-also"></a>Consulte também

- [Eventos](../../../standard/events/index.md)
- [Renderizando um controle dos Windows Forms](rendering-a-windows-forms-control.md)
- [Definir um evento](defining-an-event-in-windows-forms-controls.md)
