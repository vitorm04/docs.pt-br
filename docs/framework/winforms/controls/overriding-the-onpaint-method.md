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
# <a name="overriding-the-onpaint-method"></a><span data-ttu-id="a70bb-102">Substituindo o método OnPaint</span><span class="sxs-lookup"><span data-stu-id="a70bb-102">Overriding the OnPaint Method</span></span>
<span data-ttu-id="a70bb-103">As etapas básicas para a substituição de qualquer evento definido no [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] são idênticas e são resumidas na lista a seguir.</span><span class="sxs-lookup"><span data-stu-id="a70bb-103">The basic steps for overriding any event defined in the [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] are identical and are summarized in the following list.</span></span>  
  
#### <a name="to-override-an-inherited-event"></a><span data-ttu-id="a70bb-104">Substituir um evento herdado</span><span class="sxs-lookup"><span data-stu-id="a70bb-104">To override an inherited event</span></span>  
  
1.  <span data-ttu-id="a70bb-105">Substituir o método `On`*EventName* protegido.</span><span class="sxs-lookup"><span data-stu-id="a70bb-105">Override the protected `On`*EventName* method.</span></span>  
  
2.  <span data-ttu-id="a70bb-106">Chame o método `On`*EventName* da classe base do método `On`*EventName* substituído, de modo que delegados registrados recebam o evento.</span><span class="sxs-lookup"><span data-stu-id="a70bb-106">Call the `On`*EventName* method of the base class from the overridden `On`*EventName* method, so that registered delegates receive the event.</span></span>  
  
 <span data-ttu-id="a70bb-107">O <xref:System.Windows.Forms.Control.Paint> evento é abordado em detalhes aqui porque todos os controles de formulários do Windows devem substituir o <xref:System.Windows.Forms.Control.Paint> evento que ele herda de <xref:System.Windows.Forms.Control>.</span><span class="sxs-lookup"><span data-stu-id="a70bb-107">The <xref:System.Windows.Forms.Control.Paint> event is discussed in detail here because every Windows Forms control must override the <xref:System.Windows.Forms.Control.Paint> event that it inherits from <xref:System.Windows.Forms.Control>.</span></span> <span data-ttu-id="a70bb-108">A base de <xref:System.Windows.Forms.Control> classe não sabe como um controle derivado deve ser desenhado e não fornece qualquer lógica de pintura no <xref:System.Windows.Forms.Control.OnPaint%2A> método.</span><span class="sxs-lookup"><span data-stu-id="a70bb-108">The base <xref:System.Windows.Forms.Control> class does not know how a derived control needs to be drawn and does not provide any painting logic in the <xref:System.Windows.Forms.Control.OnPaint%2A> method.</span></span> <span data-ttu-id="a70bb-109">O <xref:System.Windows.Forms.Control.OnPaint%2A> método <xref:System.Windows.Forms.Control> simplesmente despacha o <xref:System.Windows.Forms.Control.Paint> evento em receptores de evento registrado.</span><span class="sxs-lookup"><span data-stu-id="a70bb-109">The <xref:System.Windows.Forms.Control.OnPaint%2A> method of <xref:System.Windows.Forms.Control> simply dispatches the <xref:System.Windows.Forms.Control.Paint> event to registered event receivers.</span></span>  
  
 <span data-ttu-id="a70bb-110">Se você trabalhou por meio do exemplo em [como: desenvolver um controle de Windows Forms simples](../../../../docs/framework/winforms/controls/how-to-develop-a-simple-windows-forms-control.md), você viu um exemplo de substituição de <xref:System.Windows.Forms.Control.OnPaint%2A> método.</span><span class="sxs-lookup"><span data-stu-id="a70bb-110">If you worked through the sample in [How to: Develop a Simple Windows Forms Control](../../../../docs/framework/winforms/controls/how-to-develop-a-simple-windows-forms-control.md), you have seen an example of overriding the <xref:System.Windows.Forms.Control.OnPaint%2A> method.</span></span> <span data-ttu-id="a70bb-111">O fragmento de código a seguir é retirado desse exemplo.</span><span class="sxs-lookup"><span data-stu-id="a70bb-111">The following code fragment is taken from that sample.</span></span>  
  
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
  
 <span data-ttu-id="a70bb-112">O <xref:System.Windows.Forms.PaintEventArgs> classe contém dados para o <xref:System.Windows.Forms.Control.Paint> evento.</span><span class="sxs-lookup"><span data-stu-id="a70bb-112">The <xref:System.Windows.Forms.PaintEventArgs> class contains data for the <xref:System.Windows.Forms.Control.Paint> event.</span></span> <span data-ttu-id="a70bb-113">Ele tem duas propriedades, conforme mostrado no código a seguir.</span><span class="sxs-lookup"><span data-stu-id="a70bb-113">It has two properties, as shown in the following code.</span></span>  
  
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
  
 <span data-ttu-id="a70bb-114"><xref:System.Windows.Forms.PaintEventArgs.ClipRectangle%2A>é o retângulo de pintura e o <xref:System.Windows.Forms.PaintEventArgs.Graphics%2A> propriedade se refere a um <xref:System.Drawing.Graphics> objeto.</span><span class="sxs-lookup"><span data-stu-id="a70bb-114"><xref:System.Windows.Forms.PaintEventArgs.ClipRectangle%2A> is the rectangle to be painted, and the <xref:System.Windows.Forms.PaintEventArgs.Graphics%2A> property refers to a <xref:System.Drawing.Graphics> object.</span></span> <span data-ttu-id="a70bb-115">As classes de <xref:System.Drawing?displayProperty=nameWithType> namespace são gerenciados classes que fornecem acesso à funcionalidade de [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)], a nova biblioteca de elementos gráficos do Windows.</span><span class="sxs-lookup"><span data-stu-id="a70bb-115">The classes in the <xref:System.Drawing?displayProperty=nameWithType> namespace are managed classes that provide access to the functionality of [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)], the new Windows graphics library.</span></span> <span data-ttu-id="a70bb-116">O <xref:System.Drawing.Graphics> objeto tem métodos para desenhar pontos, cadeias de caracteres, linhas, arcos, elipses e muitas outras formas.</span><span class="sxs-lookup"><span data-stu-id="a70bb-116">The <xref:System.Drawing.Graphics> object has methods to draw points, strings, lines, arcs, ellipses, and many other shapes.</span></span>  
  
 <span data-ttu-id="a70bb-117">Invoca um controle de seu <xref:System.Windows.Forms.Control.OnPaint%2A> método sempre que precisar alterar sua exibição visual.</span><span class="sxs-lookup"><span data-stu-id="a70bb-117">A control invokes its <xref:System.Windows.Forms.Control.OnPaint%2A> method whenever it needs to change its visual display.</span></span> <span data-ttu-id="a70bb-118">Esse método por sua vez dispara o <xref:System.Windows.Forms.Control.Paint> evento.</span><span class="sxs-lookup"><span data-stu-id="a70bb-118">This method in turn raises the <xref:System.Windows.Forms.Control.Paint> event.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a70bb-119">Consulte também</span><span class="sxs-lookup"><span data-stu-id="a70bb-119">See Also</span></span>  
 [<span data-ttu-id="a70bb-120">Eventos</span><span class="sxs-lookup"><span data-stu-id="a70bb-120">Events</span></span>](../../../../docs/standard/events/index.md)  
 [<span data-ttu-id="a70bb-121">Renderizando um controle dos Windows Forms</span><span class="sxs-lookup"><span data-stu-id="a70bb-121">Rendering a Windows Forms Control</span></span>](../../../../docs/framework/winforms/controls/rendering-a-windows-forms-control.md)  
 [<span data-ttu-id="a70bb-122">Definindo um evento</span><span class="sxs-lookup"><span data-stu-id="a70bb-122">Defining an Event</span></span>](../../../../docs/framework/winforms/controls/defining-an-event-in-windows-forms-controls.md)
