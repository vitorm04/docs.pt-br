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
ms.openlocfilehash: c68c8c88376cfe7295962264c466030115f2f3db
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79182016"
---
# <a name="user-drawn-controls"></a><span data-ttu-id="e4bca-102">Controles desenhados pelo usuário</span><span class="sxs-lookup"><span data-stu-id="e4bca-102">User-Drawn Controls</span></span>
<span data-ttu-id="e4bca-103">O .NET Framework possibilita que você desenvolva facilmente seus próprios controles.</span><span class="sxs-lookup"><span data-stu-id="e4bca-103">The .NET Framework provides you with the ability to easily develop your own controls.</span></span> <span data-ttu-id="e4bca-104">Você pode criar um controle de usuário, que é um conjunto de controles padrão vinculados por código ou pode criar seu próprio controle desde o início.</span><span class="sxs-lookup"><span data-stu-id="e4bca-104">You can create a user control, which is a set of standard controls bound together by code, or you can design your own control from the ground up.</span></span> <span data-ttu-id="e4bca-105">Você pode até mesmo usar herança para criar um controle que herde de um controle existente e adicionar à sua funcionalidade inerente.</span><span class="sxs-lookup"><span data-stu-id="e4bca-105">You can even use inheritance to create a control that inherits from an existing control and add to its inherent functionality.</span></span> <span data-ttu-id="e4bca-106">Independentemente da abordagem utilizada, o .NET Framework oferece a funcionalidade de desenhar uma interface gráfica personalizada para qualquer controle que você criar.</span><span class="sxs-lookup"><span data-stu-id="e4bca-106">Whatever approach you use, the .NET Framework provides the functionality to draw a custom graphical interface for any control you create.</span></span>  
  
 <span data-ttu-id="e4bca-107">A pintura de um controle é realizada pela <xref:System.Windows.Forms.Control.OnPaint%2A> execução de código no método do controle.</span><span class="sxs-lookup"><span data-stu-id="e4bca-107">Painting of a control is accomplished by the execution of code in the control's <xref:System.Windows.Forms.Control.OnPaint%2A> method.</span></span> <span data-ttu-id="e4bca-108">O único argumento <xref:System.Windows.Forms.Control.OnPaint%2A> do <xref:System.Windows.Forms.PaintEventArgs> método é um objeto que fornece todas as informações e funcionalidades necessárias para renderizar seu controle.</span><span class="sxs-lookup"><span data-stu-id="e4bca-108">The single argument of the <xref:System.Windows.Forms.Control.OnPaint%2A> method is a <xref:System.Windows.Forms.PaintEventArgs> object that provides all of the information and functionality required to render your control.</span></span> <span data-ttu-id="e4bca-109">O <xref:System.Windows.Forms.PaintEventArgs> fornece como propriedades dois objetos principais que serão usados na renderização do seu controle:</span><span class="sxs-lookup"><span data-stu-id="e4bca-109">The <xref:System.Windows.Forms.PaintEventArgs> provides as properties two principal objects that will be used in the rendering of your control:</span></span>  
  
- <span data-ttu-id="e4bca-110"><xref:System.Windows.Forms.PaintEventArgs.ClipRectangle%2A>objeto - o retângulo que representa a parte do controle que será desenhada.</span><span class="sxs-lookup"><span data-stu-id="e4bca-110"><xref:System.Windows.Forms.PaintEventArgs.ClipRectangle%2A> object - the rectangle that represents the part of the control that will be drawn.</span></span> <span data-ttu-id="e4bca-111">Pode ser todo o controle ou parte do controle, dependendo de como o controle é desenhado.</span><span class="sxs-lookup"><span data-stu-id="e4bca-111">This can be the entire control, or part of the control depending on how the control is drawn.</span></span>  
  
- <span data-ttu-id="e4bca-112"><xref:System.Drawing.Graphics>objeto - encapsula vários objetos e métodos orientados a gráficos que fornecem a funcionalidade necessária para desenhar seu controle.</span><span class="sxs-lookup"><span data-stu-id="e4bca-112"><xref:System.Drawing.Graphics> object - encapsulates several graphics-oriented objects and methods that provide the functionality necessary to draw your control.</span></span>  
  
 <span data-ttu-id="e4bca-113">Para obter mais <xref:System.Drawing.Graphics> informações sobre o objeto e como usá-lo, consulte [Como: Criar objetos gráficos para desenho](../advanced/how-to-create-graphics-objects-for-drawing.md).</span><span class="sxs-lookup"><span data-stu-id="e4bca-113">For more information on the <xref:System.Drawing.Graphics> object and how to use it, see [How to: Create Graphics Objects for Drawing](../advanced/how-to-create-graphics-objects-for-drawing.md).</span></span>  
  
 <span data-ttu-id="e4bca-114">O <xref:System.Windows.Forms.Control.OnPaint%2A> evento é acionado sempre que o controle é <xref:System.Windows.Forms.PaintEventArgs.ClipRectangle%2A> desenhado ou atualizado na tela, e o objeto representa o retângulo no qual a pintura ocorrerá.</span><span class="sxs-lookup"><span data-stu-id="e4bca-114">The <xref:System.Windows.Forms.Control.OnPaint%2A> event is fired whenever the control is drawn or refreshed on the screen, and the <xref:System.Windows.Forms.PaintEventArgs.ClipRectangle%2A> object represents the rectangle in which painting will take place.</span></span> <span data-ttu-id="e4bca-115">Se todo o controle precisar ser <xref:System.Windows.Forms.PaintEventArgs.ClipRectangle%2A> atualizado, o testamento representará o tamanho de todo o controle.</span><span class="sxs-lookup"><span data-stu-id="e4bca-115">If the entire control needs to be refreshed, the <xref:System.Windows.Forms.PaintEventArgs.ClipRectangle%2A> will represent the size of the entire control.</span></span> <span data-ttu-id="e4bca-116">Se apenas parte do controle precisar ser atualizada, no entanto, o <xref:System.Windows.Forms.PaintEventArgs.ClipRectangle%2A> objeto representará apenas a região que precisa ser redesenhada.</span><span class="sxs-lookup"><span data-stu-id="e4bca-116">If only part of the control needs to be refreshed, however, the <xref:System.Windows.Forms.PaintEventArgs.ClipRectangle%2A> object will represent only the region that needs to be redrawn.</span></span> <span data-ttu-id="e4bca-117">Um exemplo de um caso assim seria quando um controle foi parcialmente encoberto por outro controle ou formulário na interface do usuário.</span><span class="sxs-lookup"><span data-stu-id="e4bca-117">An example of such a case would be when a control was partially obscured by another control or form in the user interface.</span></span>  
  
 <span data-ttu-id="e4bca-118">Ao herdar <xref:System.Windows.Forms.Control> da classe, você <xref:System.Windows.Forms.Control.OnPaint%2A> deve substituir o método e fornecer código de renderização gráfica dentro.</span><span class="sxs-lookup"><span data-stu-id="e4bca-118">When inheriting from the <xref:System.Windows.Forms.Control> class, you must override the <xref:System.Windows.Forms.Control.OnPaint%2A> method and provide graphics-rendering code within.</span></span> <span data-ttu-id="e4bca-119">Se você quiser fornecer uma interface gráfica personalizada para um controle de usuário ou um <xref:System.Windows.Forms.Control.OnPaint%2A> controle herdado, você também pode fazê-lo substituindo o método.</span><span class="sxs-lookup"><span data-stu-id="e4bca-119">If you want to provide a custom graphical interface to a user control or an inherited control, you can also do so by overriding the <xref:System.Windows.Forms.Control.OnPaint%2A> method.</span></span> <span data-ttu-id="e4bca-120">Um exemplo é mostrado abaixo:</span><span class="sxs-lookup"><span data-stu-id="e4bca-120">An example is shown below:</span></span>  
  
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
  
 <span data-ttu-id="e4bca-121">O exemplo anterior demonstra como renderizar um controle com uma representação gráfica muito simples.</span><span class="sxs-lookup"><span data-stu-id="e4bca-121">The preceding example demonstrates how to render a control with a very simple graphical representation.</span></span> <span data-ttu-id="e4bca-122">Ele chama <xref:System.Windows.Forms.Control.OnPaint%2A> o método da classe <xref:System.Drawing.Pen> base, cria um objeto com o qual desenhar, e finalmente <xref:System.Windows.Forms.Control.Location%2A> <xref:System.Windows.Forms.Control.Size%2A> desenha uma elipse no retângulo determinado pelo e do controle.</span><span class="sxs-lookup"><span data-stu-id="e4bca-122">It calls the <xref:System.Windows.Forms.Control.OnPaint%2A> method of the base class, it creates a <xref:System.Drawing.Pen> object with which to draw, and finally draws an ellipse in the rectangle determined by the <xref:System.Windows.Forms.Control.Location%2A> and <xref:System.Windows.Forms.Control.Size%2A> of the control.</span></span> <span data-ttu-id="e4bca-123">Embora a maioria dos códigos de renderização seja significativamente <xref:System.Drawing.Graphics> mais complicado <xref:System.Windows.Forms.PaintEventArgs> do que este, este exemplo demonstra o uso do objeto contido dentro do objeto.</span><span class="sxs-lookup"><span data-stu-id="e4bca-123">Although most rendering code will be significantly more complicated than this, this example demonstrates the use of the <xref:System.Drawing.Graphics> object contained within the <xref:System.Windows.Forms.PaintEventArgs> object.</span></span> <span data-ttu-id="e4bca-124">Observe que se você está herdando de uma classe que <xref:System.Windows.Forms.UserControl> <xref:System.Windows.Forms.Button>já tem uma representação gráfica, como ou , e você não <xref:System.Windows.Forms.Control.OnPaint%2A> deseja incorporar essa representação em sua renderização, você não deve chamar o método da sua classe base.</span><span class="sxs-lookup"><span data-stu-id="e4bca-124">Note that if you are inheriting from a class that already has a graphical representation, such as <xref:System.Windows.Forms.UserControl> or <xref:System.Windows.Forms.Button>, and you do not wish to incorporate that representation into your rendering, you should not call your base class's <xref:System.Windows.Forms.Control.OnPaint%2A> method.</span></span>  
  
 <span data-ttu-id="e4bca-125">O código <xref:System.Windows.Forms.Control.OnPaint%2A> no método do seu controle será executado quando o controle for desenhado pela primeira vez e sempre que for atualizado.</span><span class="sxs-lookup"><span data-stu-id="e4bca-125">The code in the <xref:System.Windows.Forms.Control.OnPaint%2A> method of your control will execute when the control is first drawn, and whenever it is refreshed.</span></span> <span data-ttu-id="e4bca-126">Para garantir que o controle seja redesenhado sempre que ele for redimensionado, adicione a seguinte linha ao construtor do seu controle:</span><span class="sxs-lookup"><span data-stu-id="e4bca-126">To ensure that your control is redrawn every time it is resized, add the following line to the constructor of your control:</span></span>  
  
```vb  
SetStyle(ControlStyles.ResizeRedraw, True)  
```  
  
```csharp  
SetStyle(ControlStyles.ResizeRedraw, true);  
```  
  
> [!NOTE]
> <span data-ttu-id="e4bca-127">Use <xref:System.Windows.Forms.Control.Region%2A?displayProperty=nameWithType> a propriedade para implementar um controle não retangular.</span><span class="sxs-lookup"><span data-stu-id="e4bca-127">Use the <xref:System.Windows.Forms.Control.Region%2A?displayProperty=nameWithType> property to implement a non-rectangular control.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e4bca-128">Confira também</span><span class="sxs-lookup"><span data-stu-id="e4bca-128">See also</span></span>

- <xref:System.Windows.Forms.Control.Region%2A>
- <xref:System.Windows.Forms.ControlStyles>
- <xref:System.Drawing.Graphics>
- <xref:System.Windows.Forms.Control.OnPaint%2A>
- <xref:System.Windows.Forms.PaintEventArgs>
- [<span data-ttu-id="e4bca-129">Como Criar Objetos Gráficos para Desenho</span><span class="sxs-lookup"><span data-stu-id="e4bca-129">How to: Create Graphics Objects for Drawing</span></span>](../advanced/how-to-create-graphics-objects-for-drawing.md)
- [<span data-ttu-id="e4bca-130">Controles constituintes</span><span class="sxs-lookup"><span data-stu-id="e4bca-130">Constituent Controls</span></span>](constituent-controls.md)
- [<span data-ttu-id="e4bca-131">Variedades de Controles Personalizados</span><span class="sxs-lookup"><span data-stu-id="e4bca-131">Varieties of Custom Controls</span></span>](varieties-of-custom-controls.md)
