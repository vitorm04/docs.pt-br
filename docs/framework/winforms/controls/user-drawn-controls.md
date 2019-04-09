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
ms.openlocfilehash: 06513fc44782c78d2d69b82130542949519c0107
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59158438"
---
# <a name="user-drawn-controls"></a><span data-ttu-id="b0c18-102">Controles desenhados pelo usuário</span><span class="sxs-lookup"><span data-stu-id="b0c18-102">User-Drawn Controls</span></span>
<span data-ttu-id="b0c18-103">O .NET Framework possibilita que você desenvolva facilmente seus próprios controles.</span><span class="sxs-lookup"><span data-stu-id="b0c18-103">The .NET Framework provides you with the ability to easily develop your own controls.</span></span> <span data-ttu-id="b0c18-104">Você pode criar um controle de usuário, que é um conjunto de controles padrão vinculados por código ou pode criar seu próprio controle desde o início.</span><span class="sxs-lookup"><span data-stu-id="b0c18-104">You can create a user control, which is a set of standard controls bound together by code, or you can design your own control from the ground up.</span></span> <span data-ttu-id="b0c18-105">Você pode até mesmo usar herança para criar um controle que herde de um controle existente e adicionar à sua funcionalidade inerente.</span><span class="sxs-lookup"><span data-stu-id="b0c18-105">You can even use inheritance to create a control that inherits from an existing control and add to its inherent functionality.</span></span> <span data-ttu-id="b0c18-106">Independentemente da abordagem utilizada, o .NET Framework oferece a funcionalidade de desenhar uma interface gráfica personalizada para qualquer controle que você criar.</span><span class="sxs-lookup"><span data-stu-id="b0c18-106">Whatever approach you use, the .NET Framework provides the functionality to draw a custom graphical interface for any control you create.</span></span>  
  
 <span data-ttu-id="b0c18-107">Pintura de um controle é feita pela execução de código do controle <xref:System.Windows.Forms.Control.OnPaint%2A> método.</span><span class="sxs-lookup"><span data-stu-id="b0c18-107">Painting of a control is accomplished by the execution of code in the control's <xref:System.Windows.Forms.Control.OnPaint%2A> method.</span></span> <span data-ttu-id="b0c18-108">O único argumento de <xref:System.Windows.Forms.Control.OnPaint%2A> método é um <xref:System.Windows.Forms.PaintEventArgs> objeto que fornece todas as informações e a funcionalidade necessária para renderizar o controle.</span><span class="sxs-lookup"><span data-stu-id="b0c18-108">The single argument of the <xref:System.Windows.Forms.Control.OnPaint%2A> method is a <xref:System.Windows.Forms.PaintEventArgs> object that provides all of the information and functionality required to render your control.</span></span> <span data-ttu-id="b0c18-109">O <xref:System.Windows.Forms.PaintEventArgs> fornece como propriedades dois objetos de entidade de segurança que serão usados no processamento de seu controle:</span><span class="sxs-lookup"><span data-stu-id="b0c18-109">The <xref:System.Windows.Forms.PaintEventArgs> provides as properties two principal objects that will be used in the rendering of your control:</span></span>  
  
-   <xref:System.Windows.Forms.PaintEventArgs.ClipRectangle%2A> <span data-ttu-id="b0c18-110">objeto - o retângulo que representa a parte do controle que será desenhada.</span><span class="sxs-lookup"><span data-stu-id="b0c18-110">object - the rectangle that represents the part of the control that will be drawn.</span></span> <span data-ttu-id="b0c18-111">Pode ser todo o controle ou parte do controle, dependendo de como o controle é desenhado.</span><span class="sxs-lookup"><span data-stu-id="b0c18-111">This can be the entire control, or part of the control depending on how the control is drawn.</span></span>  
  
-   <xref:System.Drawing.Graphics> <span data-ttu-id="b0c18-112">objeto - encapsula vários gráficos e orientada a objetos e métodos que fornecem a funcionalidade necessária para desenhar o controle.</span><span class="sxs-lookup"><span data-stu-id="b0c18-112">object - encapsulates several graphics-oriented objects and methods that provide the functionality necessary to draw your control.</span></span>  
  
 <span data-ttu-id="b0c18-113">Para obter mais informações sobre o <xref:System.Drawing.Graphics> objeto e como usá-lo, consulte [como: Criar objetos gráficos para desenho](../advanced/how-to-create-graphics-objects-for-drawing.md).</span><span class="sxs-lookup"><span data-stu-id="b0c18-113">For more information on the <xref:System.Drawing.Graphics> object and how to use it, see [How to: Create Graphics Objects for Drawing](../advanced/how-to-create-graphics-objects-for-drawing.md).</span></span>  
  
 <span data-ttu-id="b0c18-114">O <xref:System.Windows.Forms.Control.OnPaint%2A> evento é acionado sempre que o controle é desenhado ou atualizado na tela e o <xref:System.Windows.Forms.PaintEventArgs.ClipRectangle%2A> objeto representa o retângulo no qual será realizada pintura.</span><span class="sxs-lookup"><span data-stu-id="b0c18-114">The <xref:System.Windows.Forms.Control.OnPaint%2A> event is fired whenever the control is drawn or refreshed on the screen, and the <xref:System.Windows.Forms.PaintEventArgs.ClipRectangle%2A> object represents the rectangle in which painting will take place.</span></span> <span data-ttu-id="b0c18-115">Se o controle inteiro precisar ser atualizado, o <xref:System.Windows.Forms.PaintEventArgs.ClipRectangle%2A> representará o tamanho de todo o controle.</span><span class="sxs-lookup"><span data-stu-id="b0c18-115">If the entire control needs to be refreshed, the <xref:System.Windows.Forms.PaintEventArgs.ClipRectangle%2A> will represent the size of the entire control.</span></span> <span data-ttu-id="b0c18-116">Se apenas parte do controle precisa ser atualizado, no entanto, o <xref:System.Windows.Forms.PaintEventArgs.ClipRectangle%2A> objeto representará somente a região que precisa ser redesenhado.</span><span class="sxs-lookup"><span data-stu-id="b0c18-116">If only part of the control needs to be refreshed, however, the <xref:System.Windows.Forms.PaintEventArgs.ClipRectangle%2A> object will represent only the region that needs to be redrawn.</span></span> <span data-ttu-id="b0c18-117">Um exemplo de um caso assim seria quando um controle foi parcialmente encoberto por outro controle ou formulário na interface do usuário.</span><span class="sxs-lookup"><span data-stu-id="b0c18-117">An example of such a case would be when a control was partially obscured by another control or form in the user interface.</span></span>  
  
 <span data-ttu-id="b0c18-118">Ao herdar do <xref:System.Windows.Forms.Control> classe, você deve substituir o <xref:System.Windows.Forms.Control.OnPaint%2A> método e fornecem código de renderização de gráficos dentro.</span><span class="sxs-lookup"><span data-stu-id="b0c18-118">When inheriting from the <xref:System.Windows.Forms.Control> class, you must override the <xref:System.Windows.Forms.Control.OnPaint%2A> method and provide graphics-rendering code within.</span></span> <span data-ttu-id="b0c18-119">Se você quiser fornecer uma interface gráfica personalizada para um controle de usuário ou um controle herdado, você também poderá fazer isso substituindo o <xref:System.Windows.Forms.Control.OnPaint%2A> método.</span><span class="sxs-lookup"><span data-stu-id="b0c18-119">If you want to provide a custom graphical interface to a user control or an inherited control, you can also do so by overriding the <xref:System.Windows.Forms.Control.OnPaint%2A> method.</span></span> <span data-ttu-id="b0c18-120">Um exemplo é mostrado abaixo:</span><span class="sxs-lookup"><span data-stu-id="b0c18-120">An example is shown below:</span></span>  
  
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
  
 <span data-ttu-id="b0c18-121">O exemplo anterior demonstra como renderizar um controle com uma representação gráfica muito simples.</span><span class="sxs-lookup"><span data-stu-id="b0c18-121">The preceding example demonstrates how to render a control with a very simple graphical representation.</span></span> <span data-ttu-id="b0c18-122">Ele chama o <xref:System.Windows.Forms.Control.OnPaint%2A> método da classe base, ele cria um <xref:System.Drawing.Pen> do objeto com o qual desenhar e, por fim, desenha uma elipse no retângulo determinado pelo <xref:System.Windows.Forms.Control.Location%2A> e <xref:System.Windows.Forms.Control.Size%2A> do controle.</span><span class="sxs-lookup"><span data-stu-id="b0c18-122">It calls the <xref:System.Windows.Forms.Control.OnPaint%2A> method of the base class, it creates a <xref:System.Drawing.Pen> object with which to draw, and finally draws an ellipse in the rectangle determined by the <xref:System.Windows.Forms.Control.Location%2A> and <xref:System.Windows.Forms.Control.Size%2A> of the control.</span></span> <span data-ttu-id="b0c18-123">Embora a maioria dos códigos de renderização vá ser significativamente mais complicada do que isso, este exemplo demonstra o uso do <xref:System.Drawing.Graphics> objeto contido dentro de <xref:System.Windows.Forms.PaintEventArgs> objeto.</span><span class="sxs-lookup"><span data-stu-id="b0c18-123">Although most rendering code will be significantly more complicated than this, this example demonstrates the use of the <xref:System.Drawing.Graphics> object contained within the <xref:System.Windows.Forms.PaintEventArgs> object.</span></span> <span data-ttu-id="b0c18-124">Observe que, se você estiver herdando de uma classe que já tem uma representação gráfica, como <xref:System.Windows.Forms.UserControl> ou <xref:System.Windows.Forms.Button>e você não quiser incorporar essa representação à sua renderização, você não deve chamar sua classe base <xref:System.Windows.Forms.Control.OnPaint%2A> método.</span><span class="sxs-lookup"><span data-stu-id="b0c18-124">Note that if you are inheriting from a class that already has a graphical representation, such as <xref:System.Windows.Forms.UserControl> or <xref:System.Windows.Forms.Button>, and you do not wish to incorporate that representation into your rendering, you should not call your base class's <xref:System.Windows.Forms.Control.OnPaint%2A> method.</span></span>  
  
 <span data-ttu-id="b0c18-125">O código a <xref:System.Windows.Forms.Control.OnPaint%2A> método do seu controle será executado quando o controle é desenhado pela primeira vez e sempre que ele for atualizado.</span><span class="sxs-lookup"><span data-stu-id="b0c18-125">The code in the <xref:System.Windows.Forms.Control.OnPaint%2A> method of your control will execute when the control is first drawn, and whenever it is refreshed.</span></span> <span data-ttu-id="b0c18-126">Para garantir que o controle seja redesenhado sempre que ele for redimensionado, adicione a seguinte linha ao construtor do seu controle:</span><span class="sxs-lookup"><span data-stu-id="b0c18-126">To ensure that your control is redrawn every time it is resized, add the following line to the constructor of your control:</span></span>  
  
```vb  
SetStyle(ControlStyles.ResizeRedraw, True)  
```  
  
```csharp  
SetStyle(ControlStyles.ResizeRedraw, true);  
```  
  
> [!NOTE]
>  <span data-ttu-id="b0c18-127">Use o <xref:System.Windows.Forms.Control.Region%2A?displayProperty=nameWithType> propriedade para implementar um controle não retangular.</span><span class="sxs-lookup"><span data-stu-id="b0c18-127">Use the <xref:System.Windows.Forms.Control.Region%2A?displayProperty=nameWithType> property to implement a non-rectangular control.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b0c18-128">Consulte também</span><span class="sxs-lookup"><span data-stu-id="b0c18-128">See also</span></span>

- <xref:System.Windows.Forms.Control.Region%2A>
- <xref:System.Windows.Forms.ControlStyles>
- <xref:System.Drawing.Graphics>
- <xref:System.Windows.Forms.Control.OnPaint%2A>
- <xref:System.Windows.Forms.PaintEventArgs>
- [<span data-ttu-id="b0c18-129">Como: criar objetos gráficos para desenho</span><span class="sxs-lookup"><span data-stu-id="b0c18-129">How to: Create Graphics Objects for Drawing</span></span>](../advanced/how-to-create-graphics-objects-for-drawing.md)
- [<span data-ttu-id="b0c18-130">Controles constituintes</span><span class="sxs-lookup"><span data-stu-id="b0c18-130">Constituent Controls</span></span>](constituent-controls.md)
- [<span data-ttu-id="b0c18-131">Variedades de controles personalizados</span><span class="sxs-lookup"><span data-stu-id="b0c18-131">Varieties of Custom Controls</span></span>](varieties-of-custom-controls.md)
