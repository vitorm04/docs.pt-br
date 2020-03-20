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
# <a name="overriding-the-onpaint-method"></a><span data-ttu-id="b371f-102">Substituindo o método OnPaint</span><span class="sxs-lookup"><span data-stu-id="b371f-102">Overriding the OnPaint Method</span></span>
<span data-ttu-id="b371f-103">As etapas básicas para sobrepor qualquer evento definido no Quadro .NET são idênticas e são resumidas na lista a seguir.</span><span class="sxs-lookup"><span data-stu-id="b371f-103">The basic steps for overriding any event defined in the .NET Framework are identical and are summarized in the following list.</span></span>  
  
#### <a name="to-override-an-inherited-event"></a><span data-ttu-id="b371f-104">Substituir um evento herdado</span><span class="sxs-lookup"><span data-stu-id="b371f-104">To override an inherited event</span></span>  
  
1. <span data-ttu-id="b371f-105">Substituir o método `On`*EventName* protegido.</span><span class="sxs-lookup"><span data-stu-id="b371f-105">Override the protected `On`*EventName* method.</span></span>  
  
2. <span data-ttu-id="b371f-106">Chame o método `On`*EventName* da classe base do método `On`*EventName* substituído, de modo que delegados registrados recebam o evento.</span><span class="sxs-lookup"><span data-stu-id="b371f-106">Call the `On`*EventName* method of the base class from the overridden `On`*EventName* method, so that registered delegates receive the event.</span></span>  
  
 <span data-ttu-id="b371f-107">O <xref:System.Windows.Forms.Control.Paint> evento é discutido em detalhes aqui porque <xref:System.Windows.Forms.Control.Paint> cada controle do <xref:System.Windows.Forms.Control>Windows Forms deve substituir o evento do que herda .</span><span class="sxs-lookup"><span data-stu-id="b371f-107">The <xref:System.Windows.Forms.Control.Paint> event is discussed in detail here because every Windows Forms control must override the <xref:System.Windows.Forms.Control.Paint> event that it inherits from <xref:System.Windows.Forms.Control>.</span></span> <span data-ttu-id="b371f-108">A <xref:System.Windows.Forms.Control> classe base não sabe como um controle derivado precisa ser desenhado <xref:System.Windows.Forms.Control.OnPaint%2A> e não fornece nenhuma lógica de pintura no método.</span><span class="sxs-lookup"><span data-stu-id="b371f-108">The base <xref:System.Windows.Forms.Control> class does not know how a derived control needs to be drawn and does not provide any painting logic in the <xref:System.Windows.Forms.Control.OnPaint%2A> method.</span></span> <span data-ttu-id="b371f-109">O <xref:System.Windows.Forms.Control.OnPaint%2A> método <xref:System.Windows.Forms.Control> de simplesmente <xref:System.Windows.Forms.Control.Paint> despacha o evento para receptores de eventos registrados.</span><span class="sxs-lookup"><span data-stu-id="b371f-109">The <xref:System.Windows.Forms.Control.OnPaint%2A> method of <xref:System.Windows.Forms.Control> simply dispatches the <xref:System.Windows.Forms.Control.Paint> event to registered event receivers.</span></span>  
  
 <span data-ttu-id="b371f-110">Se você trabalhou através da amostra em [Como: Desenvolver um Controle simples de formulários do Windows,](how-to-develop-a-simple-windows-forms-control.md)você viu um exemplo de substituição do <xref:System.Windows.Forms.Control.OnPaint%2A> método.</span><span class="sxs-lookup"><span data-stu-id="b371f-110">If you worked through the sample in [How to: Develop a Simple Windows Forms Control](how-to-develop-a-simple-windows-forms-control.md), you have seen an example of overriding the <xref:System.Windows.Forms.Control.OnPaint%2A> method.</span></span> <span data-ttu-id="b371f-111">O fragmento de código a seguir é retirado desse exemplo.</span><span class="sxs-lookup"><span data-stu-id="b371f-111">The following code fragment is taken from that sample.</span></span>  
  
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
  
 <span data-ttu-id="b371f-112">A <xref:System.Windows.Forms.PaintEventArgs> classe contém <xref:System.Windows.Forms.Control.Paint> dados para o evento.</span><span class="sxs-lookup"><span data-stu-id="b371f-112">The <xref:System.Windows.Forms.PaintEventArgs> class contains data for the <xref:System.Windows.Forms.Control.Paint> event.</span></span> <span data-ttu-id="b371f-113">Ele tem duas propriedades, conforme mostrado no código a seguir.</span><span class="sxs-lookup"><span data-stu-id="b371f-113">It has two properties, as shown in the following code.</span></span>  
  
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
  
 <span data-ttu-id="b371f-114"><xref:System.Windows.Forms.PaintEventArgs.ClipRectangle%2A>é o retângulo a ser <xref:System.Windows.Forms.PaintEventArgs.Graphics%2A> pintado, e <xref:System.Drawing.Graphics> a propriedade refere-se a um objeto.</span><span class="sxs-lookup"><span data-stu-id="b371f-114"><xref:System.Windows.Forms.PaintEventArgs.ClipRectangle%2A> is the rectangle to be painted, and the <xref:System.Windows.Forms.PaintEventArgs.Graphics%2A> property refers to a <xref:System.Drawing.Graphics> object.</span></span> <span data-ttu-id="b371f-115">As classes <xref:System.Drawing?displayProperty=nameWithType> no namespace são classes gerenciadas que fornecem acesso à funcionalidade do GDI+, a nova biblioteca gráfica do Windows.</span><span class="sxs-lookup"><span data-stu-id="b371f-115">The classes in the <xref:System.Drawing?displayProperty=nameWithType> namespace are managed classes that provide access to the functionality of GDI+, the new Windows graphics library.</span></span> <span data-ttu-id="b371f-116">O <xref:System.Drawing.Graphics> objeto tem métodos para desenhar pontos, cordas, linhas, arcos, elipses e muitas outras formas.</span><span class="sxs-lookup"><span data-stu-id="b371f-116">The <xref:System.Drawing.Graphics> object has methods to draw points, strings, lines, arcs, ellipses, and many other shapes.</span></span>  
  
 <span data-ttu-id="b371f-117">Um controle invoca <xref:System.Windows.Forms.Control.OnPaint%2A> seu método sempre que precisa alterar seu visor visual.</span><span class="sxs-lookup"><span data-stu-id="b371f-117">A control invokes its <xref:System.Windows.Forms.Control.OnPaint%2A> method whenever it needs to change its visual display.</span></span> <span data-ttu-id="b371f-118">Este método, por <xref:System.Windows.Forms.Control.Paint> sua vez, levanta o evento.</span><span class="sxs-lookup"><span data-stu-id="b371f-118">This method in turn raises the <xref:System.Windows.Forms.Control.Paint> event.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b371f-119">Confira também</span><span class="sxs-lookup"><span data-stu-id="b371f-119">See also</span></span>

- [<span data-ttu-id="b371f-120">Eventos</span><span class="sxs-lookup"><span data-stu-id="b371f-120">Events</span></span>](../../../standard/events/index.md)
- [<span data-ttu-id="b371f-121">Renderizando um controle dos Windows Forms</span><span class="sxs-lookup"><span data-stu-id="b371f-121">Rendering a Windows Forms Control</span></span>](rendering-a-windows-forms-control.md)
- [<span data-ttu-id="b371f-122">Definindo um evento</span><span class="sxs-lookup"><span data-stu-id="b371f-122">Defining an Event</span></span>](defining-an-event-in-windows-forms-controls.md)
