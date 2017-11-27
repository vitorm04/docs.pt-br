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
# <a name="user-drawn-controls"></a><span data-ttu-id="dfa39-102">Controles desenhados pelo usuário</span><span class="sxs-lookup"><span data-stu-id="dfa39-102">User-Drawn Controls</span></span>
<span data-ttu-id="dfa39-103">O .NET Framework possibilita que você desenvolva facilmente seus próprios controles.</span><span class="sxs-lookup"><span data-stu-id="dfa39-103">The .NET Framework provides you with the ability to easily develop your own controls.</span></span> <span data-ttu-id="dfa39-104">Você pode criar um controle de usuário, que é um conjunto de controles padrão vinculados por código ou pode criar seu próprio controle desde o início.</span><span class="sxs-lookup"><span data-stu-id="dfa39-104">You can create a user control, which is a set of standard controls bound together by code, or you can design your own control from the ground up.</span></span> <span data-ttu-id="dfa39-105">Você pode até mesmo usar herança para criar um controle que herde de um controle existente e adicionar à sua funcionalidade inerente.</span><span class="sxs-lookup"><span data-stu-id="dfa39-105">You can even use inheritance to create a control that inherits from an existing control and add to its inherent functionality.</span></span> <span data-ttu-id="dfa39-106">Independentemente da abordagem utilizada, o .NET Framework oferece a funcionalidade de desenhar uma interface gráfica personalizada para qualquer controle que você criar.</span><span class="sxs-lookup"><span data-stu-id="dfa39-106">Whatever approach you use, the .NET Framework provides the functionality to draw a custom graphical interface for any control you create.</span></span>  
  
 <span data-ttu-id="dfa39-107">Pintura de um controle é realizada pela execução de código do controle <xref:System.Windows.Forms.Control.OnPaint%2A> método.</span><span class="sxs-lookup"><span data-stu-id="dfa39-107">Painting of a control is accomplished by the execution of code in the control's <xref:System.Windows.Forms.Control.OnPaint%2A> method.</span></span> <span data-ttu-id="dfa39-108">O único argumento de <xref:System.Windows.Forms.Control.OnPaint%2A> método é um <xref:System.Windows.Forms.PaintEventArgs> objeto que fornece todas as informações e a funcionalidade necessária para processar o controle.</span><span class="sxs-lookup"><span data-stu-id="dfa39-108">The single argument of the <xref:System.Windows.Forms.Control.OnPaint%2A> method is a <xref:System.Windows.Forms.PaintEventArgs> object that provides all of the information and functionality required to render your control.</span></span> <span data-ttu-id="dfa39-109">O <xref:System.Windows.Forms.PaintEventArgs> fornece como propriedades de dois objetos principais que serão usados no processamento de seu controle:</span><span class="sxs-lookup"><span data-stu-id="dfa39-109">The <xref:System.Windows.Forms.PaintEventArgs> provides as properties two principal objects that will be used in the rendering of your control:</span></span>  
  
-   <span data-ttu-id="dfa39-110"><xref:System.Windows.Forms.PaintEventArgs.ClipRectangle%2A>objeto - o retângulo que representa a parte do controle que será desenhado.</span><span class="sxs-lookup"><span data-stu-id="dfa39-110"><xref:System.Windows.Forms.PaintEventArgs.ClipRectangle%2A> object - the rectangle that represents the part of the control that will be drawn.</span></span> <span data-ttu-id="dfa39-111">Pode ser todo o controle ou parte do controle, dependendo de como o controle é desenhado.</span><span class="sxs-lookup"><span data-stu-id="dfa39-111">This can be the entire control, or part of the control depending on how the control is drawn.</span></span>  
  
-   <span data-ttu-id="dfa39-112"><xref:System.Drawing.Graphics>objeto - encapsula vários gráficos e orientada a objetos e métodos que fornecem a funcionalidade necessária para desenhar seu controle.</span><span class="sxs-lookup"><span data-stu-id="dfa39-112"><xref:System.Drawing.Graphics> object - encapsulates several graphics-oriented objects and methods that provide the functionality necessary to draw your control.</span></span>  
  
 <span data-ttu-id="dfa39-113">Para obter mais informações sobre o <xref:System.Drawing.Graphics> objeto e como usá-lo, consulte [como: criar objetos gráficos para desenho](../../../../docs/framework/winforms/advanced/how-to-create-graphics-objects-for-drawing.md).</span><span class="sxs-lookup"><span data-stu-id="dfa39-113">For more information on the <xref:System.Drawing.Graphics> object and how to use it, see [How to: Create Graphics Objects for Drawing](../../../../docs/framework/winforms/advanced/how-to-create-graphics-objects-for-drawing.md).</span></span>  
  
 <span data-ttu-id="dfa39-114">O <xref:System.Windows.Forms.Control.OnPaint%2A> evento é acionado sempre que o controle é desenhado ou atualizado na tela e o <xref:System.Windows.Forms.PaintEventArgs.ClipRectangle%2A> objeto representa o retângulo na qual a pintura será realizada.</span><span class="sxs-lookup"><span data-stu-id="dfa39-114">The <xref:System.Windows.Forms.Control.OnPaint%2A> event is fired whenever the control is drawn or refreshed on the screen, and the <xref:System.Windows.Forms.PaintEventArgs.ClipRectangle%2A> object represents the rectangle in which painting will take place.</span></span> <span data-ttu-id="dfa39-115">Se todo o controle precisa ser atualizado, o <xref:System.Windows.Forms.PaintEventArgs.ClipRectangle%2A> representa o tamanho de todo o controle.</span><span class="sxs-lookup"><span data-stu-id="dfa39-115">If the entire control needs to be refreshed, the <xref:System.Windows.Forms.PaintEventArgs.ClipRectangle%2A> will represent the size of the entire control.</span></span> <span data-ttu-id="dfa39-116">Se apenas parte do controle precisa ser atualizado, no entanto, o <xref:System.Windows.Forms.PaintEventArgs.ClipRectangle%2A> objeto representa apenas a região que precisa ser redesenhada.</span><span class="sxs-lookup"><span data-stu-id="dfa39-116">If only part of the control needs to be refreshed, however, the <xref:System.Windows.Forms.PaintEventArgs.ClipRectangle%2A> object will represent only the region that needs to be redrawn.</span></span> <span data-ttu-id="dfa39-117">Um exemplo de um caso assim seria quando um controle foi parcialmente encoberto por outro controle ou formulário na interface do usuário.</span><span class="sxs-lookup"><span data-stu-id="dfa39-117">An example of such a case would be when a control was partially obscured by another control or form in the user interface.</span></span>  
  
 <span data-ttu-id="dfa39-118">Ao herdar do <xref:System.Windows.Forms.Control> classe, você deve substituir o <xref:System.Windows.Forms.Control.OnPaint%2A> método e fornecem código de processamento de elementos gráficos dentro.</span><span class="sxs-lookup"><span data-stu-id="dfa39-118">When inheriting from the <xref:System.Windows.Forms.Control> class, you must override the <xref:System.Windows.Forms.Control.OnPaint%2A> method and provide graphics-rendering code within.</span></span> <span data-ttu-id="dfa39-119">Se você quiser fornecer uma interface gráfica personalizada para um controle de usuário ou um controle herdado, você também pode fazer isso, substituindo o <xref:System.Windows.Forms.Control.OnPaint%2A> método.</span><span class="sxs-lookup"><span data-stu-id="dfa39-119">If you want to provide a custom graphical interface to a user control or an inherited control, you can also do so by overriding the <xref:System.Windows.Forms.Control.OnPaint%2A> method.</span></span> <span data-ttu-id="dfa39-120">Um exemplo é mostrado abaixo:</span><span class="sxs-lookup"><span data-stu-id="dfa39-120">An example is shown below:</span></span>  
  
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
  
 <span data-ttu-id="dfa39-121">O exemplo anterior demonstra como renderizar um controle com uma representação gráfica muito simples.</span><span class="sxs-lookup"><span data-stu-id="dfa39-121">The preceding example demonstrates how to render a control with a very simple graphical representation.</span></span> <span data-ttu-id="dfa39-122">Ele chama o <xref:System.Windows.Forms.Control.OnPaint%2A> método da classe base, ele cria um <xref:System.Drawing.Pen> do objeto com o qual desenhar e finalmente desenha uma elipse no retângulo é determinado pelo <xref:System.Windows.Forms.Control.Location%2A> e <xref:System.Windows.Forms.Control.Size%2A> do controle.</span><span class="sxs-lookup"><span data-stu-id="dfa39-122">It calls the <xref:System.Windows.Forms.Control.OnPaint%2A> method of the base class, it creates a <xref:System.Drawing.Pen> object with which to draw, and finally draws an ellipse in the rectangle determined by the <xref:System.Windows.Forms.Control.Location%2A> and <xref:System.Windows.Forms.Control.Size%2A> of the control.</span></span> <span data-ttu-id="dfa39-123">Embora a maioria dos códigos de renderização será significativamente mais complicado do que isso, este exemplo demonstra o uso do <xref:System.Drawing.Graphics> objeto contido dentro de <xref:System.Windows.Forms.PaintEventArgs> objeto.</span><span class="sxs-lookup"><span data-stu-id="dfa39-123">Although most rendering code will be significantly more complicated than this, this example demonstrates the use of the <xref:System.Drawing.Graphics> object contained within the <xref:System.Windows.Forms.PaintEventArgs> object.</span></span> <span data-ttu-id="dfa39-124">Observe que, se você estiver herdando de uma classe que já tem uma representação gráfica, como <xref:System.Windows.Forms.UserControl> ou <xref:System.Windows.Forms.Button>e você não deseja incorporar essa representação seu processamento, você não deve chamar sua classe base <xref:System.Windows.Forms.Control.OnPaint%2A> método.</span><span class="sxs-lookup"><span data-stu-id="dfa39-124">Note that if you are inheriting from a class that already has a graphical representation, such as <xref:System.Windows.Forms.UserControl> or <xref:System.Windows.Forms.Button>, and you do not wish to incorporate that representation into your rendering, you should not call your base class's <xref:System.Windows.Forms.Control.OnPaint%2A> method.</span></span>  
  
 <span data-ttu-id="dfa39-125">O código de <xref:System.Windows.Forms.Control.OnPaint%2A> método do controle será executado quando o controle é desenhado primeiro e sempre que ele for atualizado.</span><span class="sxs-lookup"><span data-stu-id="dfa39-125">The code in the <xref:System.Windows.Forms.Control.OnPaint%2A> method of your control will execute when the control is first drawn, and whenever it is refreshed.</span></span> <span data-ttu-id="dfa39-126">Para garantir que o controle seja redesenhado sempre que ele for redimensionado, adicione a seguinte linha ao construtor do seu controle:</span><span class="sxs-lookup"><span data-stu-id="dfa39-126">To ensure that your control is redrawn every time it is resized, add the following line to the constructor of your control:</span></span>  
  
```vb  
SetStyle(ControlStyles.ResizeRedraw, True)  
```  
  
```csharp  
SetStyle(ControlStyles.ResizeRedraw, true);  
```  
  
> [!NOTE]
>  <span data-ttu-id="dfa39-127">Use o <xref:System.Windows.Forms.Control.Region%2A?displayProperty=nameWithType> propriedade para implementar um controle não retangulares.</span><span class="sxs-lookup"><span data-stu-id="dfa39-127">Use the <xref:System.Windows.Forms.Control.Region%2A?displayProperty=nameWithType> property to implement a non-rectangular control.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dfa39-128">Consulte também</span><span class="sxs-lookup"><span data-stu-id="dfa39-128">See Also</span></span>  
 <xref:System.Windows.Forms.Control.Region%2A>  
 <xref:System.Windows.Forms.ControlStyles>  
 <xref:System.Drawing.Graphics>  
 <xref:System.Windows.Forms.Control.OnPaint%2A>  
 <xref:System.Windows.Forms.PaintEventArgs>  
 [<span data-ttu-id="dfa39-129">Como Criar Objetos Gráficos para Desenho</span><span class="sxs-lookup"><span data-stu-id="dfa39-129">How to: Create Graphics Objects for Drawing</span></span>](../../../../docs/framework/winforms/advanced/how-to-create-graphics-objects-for-drawing.md)  
 [<span data-ttu-id="dfa39-130">Controles constituintes</span><span class="sxs-lookup"><span data-stu-id="dfa39-130">Constituent Controls</span></span>](../../../../docs/framework/winforms/controls/constituent-controls.md)  
 [<span data-ttu-id="dfa39-131">Variedades de Controles Personalizados</span><span class="sxs-lookup"><span data-stu-id="dfa39-131">Varieties of Custom Controls</span></span>](../../../../docs/framework/winforms/controls/varieties-of-custom-controls.md)
