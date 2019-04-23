---
title: Gerenciando o estado de um objeto gráfico
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- graphics [Windows Forms], managing state
- graphics [Windows Forms], clipping
ms.assetid: 6207cad1-7a34-4bd6-bfc1-db823ca7a73e
ms.openlocfilehash: 8fc92bf84def50bed54a054ae634a8a08c8835c2
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59212447"
---
# <a name="managing-the-state-of-a-graphics-object"></a><span data-ttu-id="91404-102">Gerenciando o estado de um objeto gráfico</span><span class="sxs-lookup"><span data-stu-id="91404-102">Managing the State of a Graphics Object</span></span>
<span data-ttu-id="91404-103">O <xref:System.Drawing.Graphics> classe é o cerne da [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)].</span><span class="sxs-lookup"><span data-stu-id="91404-103">The <xref:System.Drawing.Graphics> class is at the heart of [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)].</span></span> <span data-ttu-id="91404-104">Para desenhar qualquer coisa, você deve obter um <xref:System.Drawing.Graphics> do objeto, defina suas propriedades e chamar seus métodos <xref:System.Drawing.Graphics.DrawLine%2A>, <xref:System.Drawing.Graphics.DrawImage%2A>, <xref:System.Drawing.Graphics.DrawString%2A>e assim por diante).</span><span class="sxs-lookup"><span data-stu-id="91404-104">To draw anything, you obtain a <xref:System.Drawing.Graphics> object, set its properties, and call its methods <xref:System.Drawing.Graphics.DrawLine%2A>, <xref:System.Drawing.Graphics.DrawImage%2A>, <xref:System.Drawing.Graphics.DrawString%2A>, and the like).</span></span>  
  
 <span data-ttu-id="91404-105">A exemplo a seguir chama o <xref:System.Drawing.Graphics.DrawRectangle%2A> método de um <xref:System.Drawing.Graphics> objeto.</span><span class="sxs-lookup"><span data-stu-id="91404-105">The following example calls the <xref:System.Drawing.Graphics.DrawRectangle%2A> method of a <xref:System.Drawing.Graphics> object.</span></span> <span data-ttu-id="91404-106">O primeiro argumento passado para o <xref:System.Drawing.Graphics.DrawRectangle%2A> método é um <xref:System.Drawing.Pen> objeto.</span><span class="sxs-lookup"><span data-stu-id="91404-106">The first argument passed to the <xref:System.Drawing.Graphics.DrawRectangle%2A> method is a <xref:System.Drawing.Pen> object.</span></span>  
  
```vb  
Dim graphics As Graphics = e.Graphics  
Dim pen As New Pen(Color.Blue) ' Opaque blue  
graphics.DrawRectangle(pen, 10, 10, 200, 100)  
```  
  
```csharp  
Graphics graphics = e.Graphics;  
Pen pen = new Pen(Color.Blue);  // Opaque blue  
graphics.DrawRectangle(pen, 10, 10, 200, 100);  
```  
  
## <a name="graphics-state"></a><span data-ttu-id="91404-107">Estado gráfico</span><span class="sxs-lookup"><span data-stu-id="91404-107">Graphics State</span></span>  
 <span data-ttu-id="91404-108">Um <xref:System.Drawing.Graphics> objeto mais do que fornecer métodos de desenho, como <xref:System.Drawing.Graphics.DrawLine%2A> e <xref:System.Drawing.Graphics.DrawRectangle%2A>.</span><span class="sxs-lookup"><span data-stu-id="91404-108">A <xref:System.Drawing.Graphics> object does more than provide drawing methods, such as <xref:System.Drawing.Graphics.DrawLine%2A> and <xref:System.Drawing.Graphics.DrawRectangle%2A>.</span></span> <span data-ttu-id="91404-109">Um <xref:System.Drawing.Graphics> objeto também mantém o estado dos gráficos, que pode ser dividido nas seguintes categorias:</span><span class="sxs-lookup"><span data-stu-id="91404-109">A <xref:System.Drawing.Graphics> object also maintains graphics state, which can be divided into the following categories:</span></span>  
  
-   <span data-ttu-id="91404-110">Configurações de qualidade</span><span class="sxs-lookup"><span data-stu-id="91404-110">Quality settings</span></span>  
  
-   <span data-ttu-id="91404-111">Transformações</span><span class="sxs-lookup"><span data-stu-id="91404-111">Transformations</span></span>  
  
-   <span data-ttu-id="91404-112">Área de recorte</span><span class="sxs-lookup"><span data-stu-id="91404-112">Clipping region</span></span>  
  
### <a name="quality-settings"></a><span data-ttu-id="91404-113">Configurações de Qualidade</span><span class="sxs-lookup"><span data-stu-id="91404-113">Quality Settings</span></span>  
 <span data-ttu-id="91404-114">Um <xref:System.Drawing.Graphics> objeto tem várias propriedades que influenciam a qualidade dos itens que são desenhadas.</span><span class="sxs-lookup"><span data-stu-id="91404-114">A <xref:System.Drawing.Graphics> object has several properties that influence the quality of the items that are drawn.</span></span> <span data-ttu-id="91404-115">Por exemplo, você pode definir o <xref:System.Drawing.Graphics.TextRenderingHint%2A> propriedade para especificar o tipo de suavização (se houver) aplicado ao texto.</span><span class="sxs-lookup"><span data-stu-id="91404-115">For example, you can set the <xref:System.Drawing.Graphics.TextRenderingHint%2A> property to specify the type of antialiasing (if any) applied to text.</span></span> <span data-ttu-id="91404-116">Outras propriedades que influenciam a qualidade são <xref:System.Drawing.Graphics.SmoothingMode%2A>, <xref:System.Drawing.Graphics.CompositingMode%2A>, <xref:System.Drawing.Graphics.CompositingQuality%2A>, e <xref:System.Drawing.Graphics.InterpolationMode%2A>.</span><span class="sxs-lookup"><span data-stu-id="91404-116">Other properties that influence quality are <xref:System.Drawing.Graphics.SmoothingMode%2A>, <xref:System.Drawing.Graphics.CompositingMode%2A>, <xref:System.Drawing.Graphics.CompositingQuality%2A>, and <xref:System.Drawing.Graphics.InterpolationMode%2A>.</span></span>  
  
 <span data-ttu-id="91404-117">O exemplo a seguir desenha duas elipses, uma com o modo de suavização definido como <xref:System.Drawing.Drawing2D.SmoothingMode.AntiAlias> e outra com o modo de suavização definido como <xref:System.Drawing.Drawing2D.SmoothingMode.HighSpeed>:</span><span class="sxs-lookup"><span data-stu-id="91404-117">The following example draws two ellipses, one with the smoothing mode set to <xref:System.Drawing.Drawing2D.SmoothingMode.AntiAlias> and one with the smoothing mode set to <xref:System.Drawing.Drawing2D.SmoothingMode.HighSpeed>:</span></span>  
  
```vb  
Dim graphics As Graphics = e.Graphics  
Dim pen As New Pen(Color.Blue)  
  
graphics.SmoothingMode = SmoothingMode.AntiAlias  
graphics.DrawEllipse(pen, 0, 0, 200, 100)  
graphics.SmoothingMode = SmoothingMode.HighSpeed  
graphics.DrawEllipse(pen, 0, 150, 200, 100)  
```  
  
```csharp  
Graphics graphics = e.Graphics;  
Pen pen = new Pen(Color.Blue);  
  
graphics.SmoothingMode = SmoothingMode.AntiAlias;  
graphics.DrawEllipse(pen, 0, 0, 200, 100);  
graphics.SmoothingMode = SmoothingMode.HighSpeed;  
graphics.DrawEllipse(pen, 0, 150, 200, 100);  
```  
  
### <a name="transformations"></a><span data-ttu-id="91404-118">Transformações</span><span class="sxs-lookup"><span data-stu-id="91404-118">Transformations</span></span>  
 <span data-ttu-id="91404-119">Um <xref:System.Drawing.Graphics> objeto mantém duas transformações (global e página) que são aplicadas a todos os itens desenhados por esse <xref:System.Drawing.Graphics> objeto.</span><span class="sxs-lookup"><span data-stu-id="91404-119">A <xref:System.Drawing.Graphics> object maintains two transformations (world and page) that are applied to all items drawn by that <xref:System.Drawing.Graphics> object.</span></span> <span data-ttu-id="91404-120">Qualquer transformação afim pode ser armazenada na transformação global.</span><span class="sxs-lookup"><span data-stu-id="91404-120">Any affine transformation can be stored in the world transformation.</span></span> <span data-ttu-id="91404-121">Transformações afins incluem colocação em escala, rotação, reflexão, distorção e translação.</span><span class="sxs-lookup"><span data-stu-id="91404-121">Affine transformations include scaling, rotating, reflecting, skewing, and translating.</span></span> <span data-ttu-id="91404-122">A transformação de página pode ser usada para colocação em escala e para alterar unidades (por exemplo, pixels em polegadas).</span><span class="sxs-lookup"><span data-stu-id="91404-122">The page transformation can be used for scaling and for changing units (for example, pixels to inches).</span></span> <span data-ttu-id="91404-123">Para obter mais informações, consulte [Sistemas de Coordenadas e Transformações](coordinate-systems-and-transformations.md).</span><span class="sxs-lookup"><span data-stu-id="91404-123">For more information, see [Coordinate Systems and Transformations](coordinate-systems-and-transformations.md).</span></span>  
  
 <span data-ttu-id="91404-124">O exemplo a seguir define as transformações global e de página de um <xref:System.Drawing.Graphics> objeto.</span><span class="sxs-lookup"><span data-stu-id="91404-124">The following example sets the world and page transformations of a <xref:System.Drawing.Graphics> object.</span></span> <span data-ttu-id="91404-125">A transformação global é definida com uma rotação de 30 graus.</span><span class="sxs-lookup"><span data-stu-id="91404-125">The world transformation is set to a 30-degree rotation.</span></span> <span data-ttu-id="91404-126">A transformação de página é definida para que as coordenadas passadas para o segundo <xref:System.Drawing.Graphics.DrawEllipse%2A> serão tratadas como milímetros em vez de pixels.</span><span class="sxs-lookup"><span data-stu-id="91404-126">The page transformation is set so that the coordinates passed to the second <xref:System.Drawing.Graphics.DrawEllipse%2A> will be treated as millimeters instead of pixels.</span></span> <span data-ttu-id="91404-127">O código faz duas chamadas idênticas para o <xref:System.Drawing.Graphics.DrawEllipse%2A> método.</span><span class="sxs-lookup"><span data-stu-id="91404-127">The code makes two identical calls to the <xref:System.Drawing.Graphics.DrawEllipse%2A> method.</span></span> <span data-ttu-id="91404-128">A transformação global é aplicada ao primeiro <xref:System.Drawing.Graphics.DrawEllipse%2A> de chamada e as duas transformações (global e página) são aplicadas à segunda <xref:System.Drawing.Graphics.DrawEllipse%2A> chamar.</span><span class="sxs-lookup"><span data-stu-id="91404-128">The world transformation is applied to the first <xref:System.Drawing.Graphics.DrawEllipse%2A> call, and both transformations (world and page) are applied to the second <xref:System.Drawing.Graphics.DrawEllipse%2A> call.</span></span>  
  
```vb  
Dim graphics As Graphics = e.Graphics  
Dim pen As New Pen(Color.Red)  
  
graphics.ResetTransform()  
graphics.RotateTransform(30) ' world transformation  
graphics.DrawEllipse(pen, 0, 0, 100, 50)  
graphics.PageUnit = GraphicsUnit.Millimeter ' page transformation  
graphics.DrawEllipse(pen, 0, 0, 100, 50)  
```  
  
```csharp  
Graphics graphics = e.Graphics;  
Pen pen = new Pen(Color.Red);   
  
graphics.ResetTransform();  
graphics.RotateTransform(30);                    // world transformation  
graphics.DrawEllipse(pen, 0, 0, 100, 50);  
graphics.PageUnit = GraphicsUnit.Millimeter;     // page transformation  
graphics.DrawEllipse(pen, 0, 0, 100, 50);  
```  
  
 <span data-ttu-id="91404-129">A ilustração a seguir mostra as duas elipses.</span><span class="sxs-lookup"><span data-stu-id="91404-129">The following illustration shows the two ellipses.</span></span> <span data-ttu-id="91404-130">Observe que a rotação de 30 graus é sobre a origem do sistema de coordenadas (canto superior esquerdo da área de cliente), e não sobre os centros das elipses.</span><span class="sxs-lookup"><span data-stu-id="91404-130">Note that the 30-degree rotation is about the origin of the coordinate system (upper-left corner of the client area), not about the centers of the ellipses.</span></span> <span data-ttu-id="91404-131">Observe também que a largura da caneta de 1 significa 1 pixel para a primeira elipse e 1 milímetro para a segunda elipse.</span><span class="sxs-lookup"><span data-stu-id="91404-131">Also note that the pen width of 1 means 1 pixel for the first ellipse and 1 millimeter for the second ellipse.</span></span>  
  
 ![Ilustração que mostra duas elipses: largura de rotação e caneta.](./media/managing-the-state-of-a-graphics-object/set-rotation-pen-width-drawellipse-method.png)  
  
### <a name="clipping-region"></a><span data-ttu-id="91404-133">Área de recorte</span><span class="sxs-lookup"><span data-stu-id="91404-133">Clipping Region</span></span>  
 <span data-ttu-id="91404-134">Um <xref:System.Drawing.Graphics> objeto mantém uma região de recorte que se aplica a todos os itens desenhados por esse <xref:System.Drawing.Graphics> objeto.</span><span class="sxs-lookup"><span data-stu-id="91404-134">A <xref:System.Drawing.Graphics> object maintains a clipping region that applies to all items drawn by that <xref:System.Drawing.Graphics> object.</span></span> <span data-ttu-id="91404-135">Você pode definir a região de recorte chamando o <xref:System.Drawing.Graphics.SetClip%2A> método.</span><span class="sxs-lookup"><span data-stu-id="91404-135">You can set the clipping region by calling the <xref:System.Drawing.Graphics.SetClip%2A> method.</span></span>  
  
 <span data-ttu-id="91404-136">O exemplo a seguir cria uma região em forma de mais (+), formando a união de dois retângulos.</span><span class="sxs-lookup"><span data-stu-id="91404-136">The following example creates a plus-shaped region by forming the union of two rectangles.</span></span> <span data-ttu-id="91404-137">Essa área é designada como a região de recorte de um <xref:System.Drawing.Graphics> objeto.</span><span class="sxs-lookup"><span data-stu-id="91404-137">That region is designated as the clipping region of a <xref:System.Drawing.Graphics> object.</span></span> <span data-ttu-id="91404-138">Em seguida, o código desenha duas linhas restritas ao interior da área de recorte.</span><span class="sxs-lookup"><span data-stu-id="91404-138">Then the code draws two lines that are restricted to the interior of the clipping region.</span></span>  
  
```vb  
Dim graphics As Graphics = e.Graphics  
  
' Opaque red, width 5  
Dim pen As New Pen(Color.Red, 5)  
  
' Opaque aqua  
Dim brush As New SolidBrush(Color.FromArgb(255, 180, 255, 255))  
  
' Create a plus-shaped region by forming the union of two rectangles.  
Dim [region] As New [Region](New Rectangle(50, 0, 50, 150))  
[region].Union(New Rectangle(0, 50, 150, 50))  
graphics.FillRegion(brush, [region])  
  
' Set the clipping region.  
graphics.SetClip([region], CombineMode.Replace)  
  
' Draw two clipped lines.  
graphics.DrawLine(pen, 0, 30, 150, 160)  
graphics.DrawLine(pen, 40, 20, 190, 150)  
```  
  
```csharp  
Graphics graphics = e.Graphics;  
  
// Opaque red, width 5  
Pen pen = new Pen(Color.Red, 5);    
  
// Opaque aqua  
SolidBrush brush = new SolidBrush(Color.FromArgb(255, 180, 255, 255));    
  
// Create a plus-shaped region by forming the union of two rectangles.  
Region region = new Region(new Rectangle(50, 0, 50, 150));  
region.Union(new Rectangle(0, 50, 150, 50));  
graphics.FillRegion(brush, region);  
  
// Set the clipping region.  
graphics.SetClip(region, CombineMode.Replace);  
  
// Draw two clipped lines.  
graphics.DrawLine(pen, 0, 30, 150, 160);  
graphics.DrawLine(pen, 40, 20, 190, 150);  
```  
  
 <span data-ttu-id="91404-139">A ilustração a seguir mostra as linhas recortadas:</span><span class="sxs-lookup"><span data-stu-id="91404-139">The following illustration shows the clipped lines:</span></span>  
  
 ![Diagrama que mostra a região de recorte limitada.](./media/managing-the-state-of-a-graphics-object/set-clipping-region-setclip-method.png)  
  
## <a name="see-also"></a><span data-ttu-id="91404-141">Consulte também</span><span class="sxs-lookup"><span data-stu-id="91404-141">See also</span></span>

- [<span data-ttu-id="91404-142">Elementos Gráficos e Desenho nos Windows Forms</span><span class="sxs-lookup"><span data-stu-id="91404-142">Graphics and Drawing in Windows Forms</span></span>](graphics-and-drawing-in-windows-forms.md)
- [<span data-ttu-id="91404-143">Usando Contêineres de Elementos Gráficos Aninhados</span><span class="sxs-lookup"><span data-stu-id="91404-143">Using Nested Graphics Containers</span></span>](using-nested-graphics-containers.md)
