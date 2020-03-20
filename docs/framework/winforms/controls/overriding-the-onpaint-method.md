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
ms.openlocfilehash: 863726a6264f01de9f00296b4a64b9fd1bb96765
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79182041"
---
# <a name="overriding-the-onpaint-method"></a>Substituindo o método OnPaint
As etapas básicas para sobrepor qualquer evento definido no Quadro .NET são idênticas e são resumidas na lista a seguir.  
  
#### <a name="to-override-an-inherited-event"></a>Substituir um evento herdado  
  
1. Substituir o método `On`*EventName* protegido.  
  
2. Chame o método `On`*EventName* da classe base do método `On`*EventName* substituído, de modo que delegados registrados recebam o evento.  
  
 O <xref:System.Windows.Forms.Control.Paint> evento é discutido em detalhes aqui porque <xref:System.Windows.Forms.Control.Paint> cada controle do <xref:System.Windows.Forms.Control>Windows Forms deve substituir o evento do que herda . A <xref:System.Windows.Forms.Control> classe base não sabe como um controle derivado precisa ser desenhado <xref:System.Windows.Forms.Control.OnPaint%2A> e não fornece nenhuma lógica de pintura no método. O <xref:System.Windows.Forms.Control.OnPaint%2A> método <xref:System.Windows.Forms.Control> de simplesmente <xref:System.Windows.Forms.Control.Paint> despacha o evento para receptores de eventos registrados.  
  
 Se você trabalhou através da amostra em [Como: Desenvolver um Controle simples de formulários do Windows,](how-to-develop-a-simple-windows-forms-control.md)você viu um exemplo de substituição do <xref:System.Windows.Forms.Control.OnPaint%2A> método. O fragmento de código a seguir é retirado desse exemplo.  
  
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
  
 A <xref:System.Windows.Forms.PaintEventArgs> classe contém <xref:System.Windows.Forms.Control.Paint> dados para o evento. Ele tem duas propriedades, conforme mostrado no código a seguir.  
  
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
  
 <xref:System.Windows.Forms.PaintEventArgs.ClipRectangle%2A>é o retângulo a ser <xref:System.Windows.Forms.PaintEventArgs.Graphics%2A> pintado, e <xref:System.Drawing.Graphics> a propriedade refere-se a um objeto. As classes <xref:System.Drawing?displayProperty=nameWithType> no namespace são classes gerenciadas que fornecem acesso à funcionalidade do GDI+, a nova biblioteca gráfica do Windows. O <xref:System.Drawing.Graphics> objeto tem métodos para desenhar pontos, cordas, linhas, arcos, elipses e muitas outras formas.  
  
 Um controle invoca <xref:System.Windows.Forms.Control.OnPaint%2A> seu método sempre que precisa alterar seu visor visual. Este método, por <xref:System.Windows.Forms.Control.Paint> sua vez, levanta o evento.  
  
## <a name="see-also"></a>Confira também

- [Eventos](../../../standard/events/index.md)
- [Renderizando um controle dos Windows Forms](rendering-a-windows-forms-control.md)
- [Definindo um evento](defining-an-event-in-windows-forms-controls.md)
