---
title: Controles constituintes
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- custom controls [Windows Forms], constituent controls
- constituent controls [Windows Forms]
- user controls [Windows Forms], constituent controls
ms.assetid: 5565e720-198b-4bbd-a2bd-c447ba641798
ms.openlocfilehash: 522a1012fc7bdd54860b0538064ee073f7a761f7
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69918423"
---
# <a name="constituent-controls"></a><span data-ttu-id="889c2-102">Controles constituintes</span><span class="sxs-lookup"><span data-stu-id="889c2-102">Constituent Controls</span></span>
<span data-ttu-id="889c2-103">Os controles que compõem um controle de usuário ou *controles membros* como são denominados, são relativamente inflexíveis quando se trata de renderização de elementos gráficos personalizados.</span><span class="sxs-lookup"><span data-stu-id="889c2-103">The controls that make up a user control, or *constituent controls* as they are termed, are relatively inflexible when it comes to custom graphics rendering.</span></span> <span data-ttu-id="889c2-104">Todos os controles de Windows Forms manipulam sua própria renderização <xref:System.Windows.Forms.Control.OnPaint%2A> por meio de seu próprio método.</span><span class="sxs-lookup"><span data-stu-id="889c2-104">All Windows Forms controls handle their own rendering through their own <xref:System.Windows.Forms.Control.OnPaint%2A> method.</span></span> <span data-ttu-id="889c2-105">Como esse método é protegido, ele não está acessível para o desenvolvedor e, portanto, não pode ser impedido de ser executado quando o controle é pintado.</span><span class="sxs-lookup"><span data-stu-id="889c2-105">Because this method is protected, it is not accessible to the developer, and thus cannot be prevented from executing when the control is painted.</span></span> <span data-ttu-id="889c2-106">Isso não significa, no entanto, que não é possível adicionar código para afetar a aparência dos controles membros.</span><span class="sxs-lookup"><span data-stu-id="889c2-106">This does not mean, however, that you cannot add code to affect the appearance of constituent controls.</span></span> <span data-ttu-id="889c2-107">A renderização adicional pode ser realizada adicionando um manipulador de eventos.</span><span class="sxs-lookup"><span data-stu-id="889c2-107">Additional rendering can be accomplished by adding an event handler.</span></span> <span data-ttu-id="889c2-108">Por exemplo, suponha que você estivesse criando um <xref:System.Windows.Forms.UserControl> com um botão chamado `MyButton`.</span><span class="sxs-lookup"><span data-stu-id="889c2-108">For example, suppose you were authoring a <xref:System.Windows.Forms.UserControl> with a button named `MyButton`.</span></span> <span data-ttu-id="889c2-109">Se desejar ter renderização adicional além do que foi fornecido pelo <xref:System.Web.UI.WebControls.Button>, você adicionaria código ao seu controle de usuário semelhante ao seguinte:</span><span class="sxs-lookup"><span data-stu-id="889c2-109">If you wished to have additional rendering beyond what was provided by the <xref:System.Web.UI.WebControls.Button>, you would add code to your user control similar to the following:</span></span>  
  
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
> <span data-ttu-id="889c2-110">Alguns controles de Windows Forms, <xref:System.Windows.Forms.TextBox>como, são pintados diretamente pelo Windows.</span><span class="sxs-lookup"><span data-stu-id="889c2-110">Some Windows Forms controls, such as <xref:System.Windows.Forms.TextBox>, are painted directly by Windows.</span></span> <span data-ttu-id="889c2-111">Nesses casos, o <xref:System.Windows.Forms.Control.OnPaint%2A> método nunca é chamado e, portanto, o exemplo acima nunca será chamado.</span><span class="sxs-lookup"><span data-stu-id="889c2-111">In these instances, the <xref:System.Windows.Forms.Control.OnPaint%2A> method is never called, and thus the above example will never be called.</span></span>  
  
 <span data-ttu-id="889c2-112">Isso cria um método que é executado sempre que o evento `MyButton.Paint` é executado, conferindo, assim, uma representação gráfica adicional ao controle.</span><span class="sxs-lookup"><span data-stu-id="889c2-112">This creates a method that executes every time the `MyButton.Paint` event executes, thereby adding additional graphical representation to your control.</span></span> <span data-ttu-id="889c2-113">Observe que isso não impede a execução de `MyButton.OnPaint` e, portanto, toda pintura normalmente executada por um botão será realizada além da sua pintura personalizada.</span><span class="sxs-lookup"><span data-stu-id="889c2-113">Note that this does not prevent the execution of `MyButton.OnPaint`, and thus all of the painting usually performed by a button will still be performed in addition to your custom painting.</span></span> <span data-ttu-id="889c2-114">Para obter detalhes sobre a tecnologia GDI+ e a renderização personalizada, consulte [Criando imagens gráficas com GDI+](../advanced/how-to-create-graphics-objects-for-drawing.md).</span><span class="sxs-lookup"><span data-stu-id="889c2-114">For details about GDI+ technology and custom rendering, see the [Creating Graphical Images with GDI+](../advanced/how-to-create-graphics-objects-for-drawing.md).</span></span> <span data-ttu-id="889c2-115">Se desejar ter uma representação exclusiva do seu controle, a melhor opção será criar um controle herdado e escrever código de renderização personalizada para ele.</span><span class="sxs-lookup"><span data-stu-id="889c2-115">If you wish to have a unique representation of your control, your best course of action is to create an inherited control, and to write custom rendering code for it.</span></span> <span data-ttu-id="889c2-116">Para ver mais detalhes, consulte [Controles desenhados pelo usuário](user-drawn-controls.md).</span><span class="sxs-lookup"><span data-stu-id="889c2-116">For details, see [User-Drawn Controls](user-drawn-controls.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="889c2-117">Consulte também</span><span class="sxs-lookup"><span data-stu-id="889c2-117">See also</span></span>

- <xref:System.Windows.Forms.UserControl>
- <xref:System.Windows.Forms.Control.OnPaint%2A>
- [<span data-ttu-id="889c2-118">Controles desenhados pelo usuário</span><span class="sxs-lookup"><span data-stu-id="889c2-118">User-Drawn Controls</span></span>](user-drawn-controls.md)
- [<span data-ttu-id="889c2-119">Como: Criar objetos gráficos para desenho</span><span class="sxs-lookup"><span data-stu-id="889c2-119">How to: Create Graphics Objects for Drawing</span></span>](../advanced/how-to-create-graphics-objects-for-drawing.md)
- [<span data-ttu-id="889c2-120">Variedades de controles personalizados</span><span class="sxs-lookup"><span data-stu-id="889c2-120">Varieties of Custom Controls</span></span>](varieties-of-custom-controls.md)
