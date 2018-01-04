---
title: Controles constituintes
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
- custom controls [Windows Forms], constituent controls
- constituent controls [Windows Forms]
- user controls [Windows Forms], constituent controls
ms.assetid: 5565e720-198b-4bbd-a2bd-c447ba641798
caps.latest.revision: "16"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 2d03b69c334148313b0cd495fad1b2dfd13df833
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="constituent-controls"></a><span data-ttu-id="6fa4a-102">Controles constituintes</span><span class="sxs-lookup"><span data-stu-id="6fa4a-102">Constituent Controls</span></span>
<span data-ttu-id="6fa4a-103">Os controles que compõem um controle de usuário ou *controles membros* como são denominados, são relativamente inflexíveis quando se trata de renderização de elementos gráficos personalizados.</span><span class="sxs-lookup"><span data-stu-id="6fa4a-103">The controls that make up a user control, or *constituent controls* as they are termed, are relatively inflexible when it comes to custom graphics rendering.</span></span> <span data-ttu-id="6fa4a-104">Todos os controles de Windows Forms lidar com sua próprias renderização por meio de seus próprios <xref:System.Windows.Forms.Control.OnPaint%2A> método.</span><span class="sxs-lookup"><span data-stu-id="6fa4a-104">All Windows Forms controls handle their own rendering through their own <xref:System.Windows.Forms.Control.OnPaint%2A> method.</span></span> <span data-ttu-id="6fa4a-105">Como esse método é protegido, ele não está acessível para o desenvolvedor e, portanto, não pode ser impedido de ser executado quando o controle é pintado.</span><span class="sxs-lookup"><span data-stu-id="6fa4a-105">Because this method is protected, it is not accessible to the developer, and thus cannot be prevented from executing when the control is painted.</span></span> <span data-ttu-id="6fa4a-106">Isso não significa, no entanto, que não é possível adicionar código para afetar a aparência dos controles membros.</span><span class="sxs-lookup"><span data-stu-id="6fa4a-106">This does not mean, however, that you cannot add code to affect the appearance of constituent controls.</span></span> <span data-ttu-id="6fa4a-107">A renderização adicional pode ser realizada adicionando um manipulador de eventos.</span><span class="sxs-lookup"><span data-stu-id="6fa4a-107">Additional rendering can be accomplished by adding an event handler.</span></span> <span data-ttu-id="6fa4a-108">Por exemplo, suponha que você estava criando um <xref:System.Windows.Forms.UserControl> com um botão chamado `MyButton`.</span><span class="sxs-lookup"><span data-stu-id="6fa4a-108">For example, suppose you were authoring a <xref:System.Windows.Forms.UserControl> with a button named `MyButton`.</span></span> <span data-ttu-id="6fa4a-109">Se você quisesse ter renderização adicionais além do que foi fornecido pelo <xref:System.Web.UI.WebControls.Button>, você deve adicionar código ao seu controle de usuário semelhante à seguinte:</span><span class="sxs-lookup"><span data-stu-id="6fa4a-109">If you wished to have additional rendering beyond what was provided by the <xref:System.Web.UI.WebControls.Button>, you would add code to your user control similar to the following:</span></span>  
  
```vb  
Public Sub MyPaint(ByVal sender as Object, e as PaintEventArgs) Handles _  
   MyButton.Paint  
   'Additional rendering code goes here  
End Sub  
```  
  
```csharp  
// Add the event handler to the button's Paint event.  
MyButton.Paint +=   
   new System.Windows.Forms.PaintEventHandler (this.MyPaint);  
// Create the custom painting method.  
protected void MyPaint (object sender,   
System.Windows.Forms.PaintEventArgs e)  
{  
   // Additional rendering code goes here.  
}  
```  
  
> [!NOTE]
>  <span data-ttu-id="6fa4a-110">Controles de alguns formulários do Windows, como <xref:System.Windows.Forms.TextBox>, são pintadas diretamente pelo Windows.</span><span class="sxs-lookup"><span data-stu-id="6fa4a-110">Some Windows Forms controls, such as <xref:System.Windows.Forms.TextBox>, are painted directly by Windows.</span></span> <span data-ttu-id="6fa4a-111">Nesses casos, o <xref:System.Windows.Forms.Control.OnPaint%2A> nunca é chamado de método e, portanto, o exemplo acima nunca será chamado.</span><span class="sxs-lookup"><span data-stu-id="6fa4a-111">In these instances, the <xref:System.Windows.Forms.Control.OnPaint%2A> method is never called, and thus the above example will never be called.</span></span>  
  
 <span data-ttu-id="6fa4a-112">Isso cria um método que é executado sempre que o evento `MyButton.Paint` é executado, conferindo, assim, uma representação gráfica adicional ao controle.</span><span class="sxs-lookup"><span data-stu-id="6fa4a-112">This creates a method that executes every time the `MyButton.Paint` event executes, thereby adding additional graphical representation to your control.</span></span> <span data-ttu-id="6fa4a-113">Observe que isso não impede a execução de `MyButton.OnPaint` e, portanto, toda pintura normalmente executada por um botão será realizada além da sua pintura personalizada.</span><span class="sxs-lookup"><span data-stu-id="6fa4a-113">Note that this does not prevent the execution of `MyButton.OnPaint`, and thus all of the painting usually performed by a button will still be performed in addition to your custom painting.</span></span> <span data-ttu-id="6fa4a-114">Para obter detalhes sobre a tecnologia GDI+ e a renderização personalizada, consulte [Criando imagens gráficas com GDI+](../../../../docs/framework/winforms/advanced/how-to-create-graphics-objects-for-drawing.md).</span><span class="sxs-lookup"><span data-stu-id="6fa4a-114">For details about GDI+ technology and custom rendering, see the [Creating Graphical Images with GDI+](../../../../docs/framework/winforms/advanced/how-to-create-graphics-objects-for-drawing.md).</span></span> <span data-ttu-id="6fa4a-115">Se desejar ter uma representação exclusiva do seu controle, a melhor opção será criar um controle herdado e escrever código de renderização personalizada para ele.</span><span class="sxs-lookup"><span data-stu-id="6fa4a-115">If you wish to have a unique representation of your control, your best course of action is to create an inherited control, and to write custom rendering code for it.</span></span> <span data-ttu-id="6fa4a-116">Para ver mais detalhes, consulte [Controles desenhados pelo usuário](../../../../docs/framework/winforms/controls/user-drawn-controls.md).</span><span class="sxs-lookup"><span data-stu-id="6fa4a-116">For details, see [User-Drawn Controls](../../../../docs/framework/winforms/controls/user-drawn-controls.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6fa4a-117">Consulte também</span><span class="sxs-lookup"><span data-stu-id="6fa4a-117">See Also</span></span>  
 <xref:System.Windows.Forms.UserControl>  
 <xref:System.Windows.Forms.Control.OnPaint%2A>  
 [<span data-ttu-id="6fa4a-118">Controles desenhados pelo usuário</span><span class="sxs-lookup"><span data-stu-id="6fa4a-118">User-Drawn Controls</span></span>](../../../../docs/framework/winforms/controls/user-drawn-controls.md)  
 [<span data-ttu-id="6fa4a-119">Como Criar Objetos Gráficos para Desenho</span><span class="sxs-lookup"><span data-stu-id="6fa4a-119">How to: Create Graphics Objects for Drawing</span></span>](../../../../docs/framework/winforms/advanced/how-to-create-graphics-objects-for-drawing.md)  
 [<span data-ttu-id="6fa4a-120">Variedades de controles personalizados</span><span class="sxs-lookup"><span data-stu-id="6fa4a-120">Varieties of Custom Controls</span></span>](../../../../docs/framework/winforms/controls/varieties-of-custom-controls.md)
