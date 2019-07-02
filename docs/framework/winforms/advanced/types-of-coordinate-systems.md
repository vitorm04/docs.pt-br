---
title: Tipos de sistemas de coordenadas
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- transformations [Windows Forms], page
- unit of measure
- world coordinate system
- page coordinate system
- page transformation
- device coordinate system
- world transformation
- coordinate systems
- transformations [Windows Forms], world
ms.assetid: c61ff50a-eb1d-4e6c-83cd-f7e9764cfa9f
ms.openlocfilehash: 24079f24bdae5fefd785a20dda9b29a190fb4068
ms.sourcegitcommit: b1cfd260928d464d91e20121f9bdba7611c94d71
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/02/2019
ms.locfileid: "67505254"
---
# <a name="types-of-coordinate-systems"></a><span data-ttu-id="9df90-102">Tipos de sistemas de coordenadas</span><span class="sxs-lookup"><span data-stu-id="9df90-102">Types of Coordinate Systems</span></span>
<span data-ttu-id="9df90-103">GDI+ usa três espaços de coordenadas: mundo, página e dispositivo.</span><span class="sxs-lookup"><span data-stu-id="9df90-103">GDI+ uses three coordinate spaces: world, page, and device.</span></span> <span data-ttu-id="9df90-104">Coordenadas de mundo são as coordenadas usadas para modelar um mundo gráfico específico e são as coordenadas que você passa para métodos no .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="9df90-104">World coordinates are the coordinates used to model a particular graphic world and are the coordinates you pass to methods in the .NET Framework.</span></span> <span data-ttu-id="9df90-105">Coordenadas de página fazem referência ao sistema de coordenadas usado por uma superfície de desenho, como um formulário ou controle.</span><span class="sxs-lookup"><span data-stu-id="9df90-105">Page coordinates refer to the coordinate system used by a drawing surface, such as a form or control.</span></span> <span data-ttu-id="9df90-106">Coordenadas de dispositivo são as coordenadas usadas pelo dispositivo físico em que o desenho está sendo feito, como uma tela ou uma folha de papel.</span><span class="sxs-lookup"><span data-stu-id="9df90-106">Device coordinates are the coordinates used by the physical device being drawn on, such as a screen or sheet of paper.</span></span> <span data-ttu-id="9df90-107">Quando você faz a chamada `myGraphics.DrawLine(myPen, 0, 0, 160, 80)`, os pontos que você passa para o <xref:System.Drawing.Graphics.DrawLine%2A> método —`(0, 0)` e `(160, 80)`— estão no espaço de coordenadas de mundo.</span><span class="sxs-lookup"><span data-stu-id="9df90-107">When you make the call `myGraphics.DrawLine(myPen, 0, 0, 160, 80)`, the points that you pass to the <xref:System.Drawing.Graphics.DrawLine%2A> method—`(0, 0)` and `(160, 80)`—are in the world coordinate space.</span></span> <span data-ttu-id="9df90-108">Antes de GDI+ pode desenhar a linha na tela, as coordenadas passam por uma sequência de transformações.</span><span class="sxs-lookup"><span data-stu-id="9df90-108">Before GDI+ can draw the line on the screen, the coordinates pass through a sequence of transformations.</span></span> <span data-ttu-id="9df90-109">Uma transformação, chamada transformação global, converte coordenadas de mundo em coordenadas de página e outra transformação, chamada transformação de página, converte coordenadas de página em coordenadas de dispositivo.</span><span class="sxs-lookup"><span data-stu-id="9df90-109">One transformation, called the world transformation, converts world coordinates to page coordinates, and another transformation, called the page transformation, converts page coordinates to device coordinates.</span></span>  
  
## <a name="transforms-and-coordinate-systems"></a><span data-ttu-id="9df90-110">Transformações e sistemas de coordenadas</span><span class="sxs-lookup"><span data-stu-id="9df90-110">Transforms and Coordinate Systems</span></span>  
 <span data-ttu-id="9df90-111">Suponha que você queira trabalhar com um sistema de coordenadas cuja origem está no corpo da área de cliente em vez do canto superior esquerdo.</span><span class="sxs-lookup"><span data-stu-id="9df90-111">Suppose you want to work with a coordinate system that has its origin in the body of the client area rather than the upper-left corner.</span></span> <span data-ttu-id="9df90-112">Digamos, por exemplo, que você queira que a origem esteja a 100 pixels da borda esquerda da área de cliente e a 50 pixels da parte superior da área de cliente.</span><span class="sxs-lookup"><span data-stu-id="9df90-112">Say, for example, that you want the origin to be 100 pixels from the left edge of the client area and 50 pixels from the top of the client area.</span></span> <span data-ttu-id="9df90-113">A ilustração a seguir mostra esse sistema de coordenadas.</span><span class="sxs-lookup"><span data-stu-id="9df90-113">The following illustration shows such a coordinate system.</span></span>  
  
 <span data-ttu-id="9df90-114">![Sistema de coordenadas](./media/aboutgdip05-art01.gif "AboutGdip05_art01")</span><span class="sxs-lookup"><span data-stu-id="9df90-114">![Coordinate System](./media/aboutgdip05-art01.gif "AboutGdip05_art01")</span></span>  
  
 <span data-ttu-id="9df90-115">Quando faz a chamada `myGraphics.DrawLine(myPen, 0, 0, 160, 80)`, você obtém a linha mostrada na ilustração a seguir.</span><span class="sxs-lookup"><span data-stu-id="9df90-115">When you make the call `myGraphics.DrawLine(myPen, 0, 0, 160, 80)`, you get the line shown in the following illustration.</span></span>  
  
 <span data-ttu-id="9df90-116">![Sistema de coordenadas](./media/aboutgdip05-art02.gif "AboutGdip05_art02")</span><span class="sxs-lookup"><span data-stu-id="9df90-116">![Coordinate System](./media/aboutgdip05-art02.gif "AboutGdip05_art02")</span></span>  
  
 <span data-ttu-id="9df90-117">As coordenadas dos pontos de extremidade da sua linha nos três espaços de coordenadas são as seguintes:</span><span class="sxs-lookup"><span data-stu-id="9df90-117">The coordinates of the endpoints of your line in the three coordinate spaces are as follows:</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="9df90-118">Mundo</span><span class="sxs-lookup"><span data-stu-id="9df90-118">World</span></span>|<span data-ttu-id="9df90-119">(0, 0) a (160, 80)</span><span class="sxs-lookup"><span data-stu-id="9df90-119">(0, 0) to (160, 80)</span></span>|  
|<span data-ttu-id="9df90-120">Página</span><span class="sxs-lookup"><span data-stu-id="9df90-120">Page</span></span>|<span data-ttu-id="9df90-121">(100, 50) a (260, 130)</span><span class="sxs-lookup"><span data-stu-id="9df90-121">(100, 50) to (260, 130)</span></span>|  
|<span data-ttu-id="9df90-122">Dispositivo</span><span class="sxs-lookup"><span data-stu-id="9df90-122">Device</span></span>|<span data-ttu-id="9df90-123">(100, 50) a (260, 130)</span><span class="sxs-lookup"><span data-stu-id="9df90-123">(100, 50) to (260, 130)</span></span>|  
  
 <span data-ttu-id="9df90-124">Observe que o espaço de coordenadas de página tem sua origem no canto superior esquerdo da área de cliente; sempre será esse o caso.</span><span class="sxs-lookup"><span data-stu-id="9df90-124">Note that the page coordinate space has its origin at the upper-left corner of the client area; this will always be the case.</span></span> <span data-ttu-id="9df90-125">Observe também que, como a unidade de medida é o pixel, as coordenadas do dispositivo são as mesmas que as coordenadas da página.</span><span class="sxs-lookup"><span data-stu-id="9df90-125">Also note that because the unit of measure is the pixel, the device coordinates are the same as the page coordinates.</span></span> <span data-ttu-id="9df90-126">Se você definir a unidade de medida como algo diferente de pixels (por exemplo, polegadas), as coordenadas do dispositivo serão diferentes das coordenadas da página.</span><span class="sxs-lookup"><span data-stu-id="9df90-126">If you set the unit of measure to something other than pixels (for example, inches), then the device coordinates will be different from the page coordinates.</span></span>  
  
 <span data-ttu-id="9df90-127">A transformação global, que mapeia coordenadas de mundo para coordenadas de página, é mantida na <xref:System.Drawing.Graphics.Transform%2A> propriedade do <xref:System.Drawing.Graphics> classe.</span><span class="sxs-lookup"><span data-stu-id="9df90-127">The world transformation, which maps world coordinates to page coordinates, is held in the <xref:System.Drawing.Graphics.Transform%2A> property of the <xref:System.Drawing.Graphics> class.</span></span> <span data-ttu-id="9df90-128">No exemplo anterior, a transformação global é uma translação de 100 unidades na direção x e 50 unidades na direção y.</span><span class="sxs-lookup"><span data-stu-id="9df90-128">In the preceding example, the world transformation is a translation 100 units in the x direction and 50 units in the y direction.</span></span> <span data-ttu-id="9df90-129">O exemplo a seguir define a transformação global de um <xref:System.Drawing.Graphics> do objeto e, em seguida, usa que <xref:System.Drawing.Graphics> objeto para desenhar a linha mostrada na figura anterior:</span><span class="sxs-lookup"><span data-stu-id="9df90-129">The following example sets the world transformation of a <xref:System.Drawing.Graphics> object and then uses that <xref:System.Drawing.Graphics> object to draw the line shown in the preceding figure:</span></span>  
  
 [!code-csharp[System.Drawing.CoordinateSystems#31](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.CoordinateSystems/CS/Class1.cs#31)]
 [!code-vb[System.Drawing.CoordinateSystems#31](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.CoordinateSystems/VB/Class1.vb#31)]  
  
 <span data-ttu-id="9df90-130">A transformação de página mapeia as coordenadas da página para coordenadas do dispositivo.</span><span class="sxs-lookup"><span data-stu-id="9df90-130">The page transformation maps page coordinates to device coordinates.</span></span> <span data-ttu-id="9df90-131">O <xref:System.Drawing.Graphics> classe fornece a <xref:System.Drawing.Graphics.PageUnit%2A> e <xref:System.Drawing.Graphics.PageScale%2A> propriedades para manipular a transformação de página.</span><span class="sxs-lookup"><span data-stu-id="9df90-131">The <xref:System.Drawing.Graphics> class provides the <xref:System.Drawing.Graphics.PageUnit%2A> and <xref:System.Drawing.Graphics.PageScale%2A> properties for manipulating the page transformation.</span></span> <span data-ttu-id="9df90-132">O <xref:System.Drawing.Graphics> classe também fornece duas propriedades somente leitura, <xref:System.Drawing.Graphics.DpiX%2A> e <xref:System.Drawing.Graphics.DpiY%2A>, para examinar os pontos horizontais e verticais por polegada do dispositivo de vídeo.</span><span class="sxs-lookup"><span data-stu-id="9df90-132">The <xref:System.Drawing.Graphics> class also provides two read-only properties, <xref:System.Drawing.Graphics.DpiX%2A> and <xref:System.Drawing.Graphics.DpiY%2A>, for examining the horizontal and vertical dots per inch of the display device.</span></span>  
  
 <span data-ttu-id="9df90-133">Você pode usar o <xref:System.Drawing.Graphics.PageUnit%2A> propriedade do <xref:System.Drawing.Graphics> classe para especificar uma unidade de medida diferente do pixel.</span><span class="sxs-lookup"><span data-stu-id="9df90-133">You can use the <xref:System.Drawing.Graphics.PageUnit%2A> property of the <xref:System.Drawing.Graphics> class to specify a unit of measure other than the pixel.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="9df90-134">Não é possível definir a <xref:System.Drawing.Graphics.PageUnit%2A> propriedade para <xref:System.Drawing.GraphicsUnit.World>, pois isso não é uma unidade física e causará uma exceção.</span><span class="sxs-lookup"><span data-stu-id="9df90-134">You cannot set the <xref:System.Drawing.Graphics.PageUnit%2A> property to <xref:System.Drawing.GraphicsUnit.World>, as this is not a physical unit and will cause an exception.</span></span>  
  
 <span data-ttu-id="9df90-135">O exemplo a seguir desenha uma linha de (0, 0) para (2, 1), no qual o ponto (2, 1) está 2 polegadas à direita e 1 polegada abaixo do ponto (0, 0):</span><span class="sxs-lookup"><span data-stu-id="9df90-135">The following example draws a line from (0, 0) to (2, 1), where the point (2, 1) is 2 inches to the right and 1 inch down from the point (0, 0):</span></span>  
  
 [!code-csharp[System.Drawing.CoordinateSystems#32](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.CoordinateSystems/CS/Class1.cs#32)]
 [!code-vb[System.Drawing.CoordinateSystems#32](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.CoordinateSystems/VB/Class1.vb#32)]  
  
> [!NOTE]
>  <span data-ttu-id="9df90-136">Se você não especificar uma largura de caneta ao construir a caneta, o exemplo anterior desenhará uma linha com uma polegada de largura.</span><span class="sxs-lookup"><span data-stu-id="9df90-136">If you don't specify a pen width when you construct your pen, the preceding example will draw a line that is one inch wide.</span></span> <span data-ttu-id="9df90-137">Você pode especificar a largura da caneta no segundo argumento para o <xref:System.Drawing.Pen> construtor:</span><span class="sxs-lookup"><span data-stu-id="9df90-137">You can specify the pen width in the second argument to the <xref:System.Drawing.Pen> constructor:</span></span>  
  
 [!code-csharp[System.Drawing.CoordinateSystems#33](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.CoordinateSystems/CS/Class1.cs#33)]
 [!code-vb[System.Drawing.CoordinateSystems#33](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.CoordinateSystems/VB/Class1.vb#33)]  
  
 <span data-ttu-id="9df90-138">Se supusermos que o dispositivo de vídeo tem 96 pontos por polegada na direção horizontal e 96 pontos por polegada na direção vertical, os pontos de extremidade da linha no exemplo anterior terão as seguintes coordenadas nos três espaços de coordenadas:</span><span class="sxs-lookup"><span data-stu-id="9df90-138">If we assume that the display device has 96 dots per inch in the horizontal direction and 96 dots per inch in the vertical direction, the endpoints of the line in the preceding example have the following coordinates in the three coordinate spaces:</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="9df90-139">Mundo</span><span class="sxs-lookup"><span data-stu-id="9df90-139">World</span></span>|<span data-ttu-id="9df90-140">(0, 0) a (2, 1)</span><span class="sxs-lookup"><span data-stu-id="9df90-140">(0, 0) to (2, 1)</span></span>|  
|<span data-ttu-id="9df90-141">Página</span><span class="sxs-lookup"><span data-stu-id="9df90-141">Page</span></span>|<span data-ttu-id="9df90-142">(0, 0) a (2, 1)</span><span class="sxs-lookup"><span data-stu-id="9df90-142">(0, 0) to (2, 1)</span></span>|  
|<span data-ttu-id="9df90-143">Dispositivo</span><span class="sxs-lookup"><span data-stu-id="9df90-143">Device</span></span>|<span data-ttu-id="9df90-144">(0, 0) a (192, 96)</span><span class="sxs-lookup"><span data-stu-id="9df90-144">(0, 0, to (192, 96)</span></span>|  
  
 <span data-ttu-id="9df90-145">Observe que, como a origem do espaço de coordenadas de mundo está no canto superior esquerdo da área de cliente, as coordenadas de página serão as mesmas que as coordenadas de mundo.</span><span class="sxs-lookup"><span data-stu-id="9df90-145">Note that because the origin of the world coordinate space is at the upper-left corner of the client area, the page coordinates are the same as the world coordinates.</span></span>  
  
 <span data-ttu-id="9df90-146">É possível combinar as transformações global e de página para obter uma variedade de resultados.</span><span class="sxs-lookup"><span data-stu-id="9df90-146">You can combine the world and page transformations to achieve a variety of effects.</span></span> <span data-ttu-id="9df90-147">Por exemplo, suponha que você queira usar polegadas como a unidade de medida e queira que a origem se seu sistema de coordenadas esteja a 2 polegadas da borda esquerda da área de cliente e a 1/2 polegada da parte superior da área de cliente.</span><span class="sxs-lookup"><span data-stu-id="9df90-147">For example, suppose you want to use inches as the unit of measure and you want the origin of your coordinate system to be 2 inches from the left edge of the client area and 1/2 inch from the top of the client area.</span></span> <span data-ttu-id="9df90-148">O exemplo a seguir define as transformações global e de página de um <xref:System.Drawing.Graphics> de objeto e, em seguida, desenha uma linha de (0, 0) para (2, 1):</span><span class="sxs-lookup"><span data-stu-id="9df90-148">The following example sets the world and page transformations of a <xref:System.Drawing.Graphics> object and then draws a line from (0, 0) to (2, 1):</span></span>  
  
 [!code-csharp[System.Drawing.CoordinateSystems#34](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.CoordinateSystems/CS/Class1.cs#34)]
 [!code-vb[System.Drawing.CoordinateSystems#34](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.CoordinateSystems/VB/Class1.vb#34)]  
  
 <span data-ttu-id="9df90-149">A ilustração a seguir mostra a linha e o sistema de coordenadas.</span><span class="sxs-lookup"><span data-stu-id="9df90-149">The following illustration shows the line and coordinate system.</span></span>  
  
 <span data-ttu-id="9df90-150">![Sistema de coordenadas](./media/aboutgdip05-art03.gif "AboutGdip05_art03")</span><span class="sxs-lookup"><span data-stu-id="9df90-150">![Coordinate System](./media/aboutgdip05-art03.gif "AboutGdip05_art03")</span></span>  
  
 <span data-ttu-id="9df90-151">Se supusermos que o dispositivo de vídeo tem 96 pontos por polegada na direção horizontal e 96 pontos por polegada na direção vertical, os pontos de extremidade da linha no exemplo anterior terão as seguintes coordenadas nos três espaços de coordenadas:</span><span class="sxs-lookup"><span data-stu-id="9df90-151">If we assume that the display device has 96 dots per inch in the horizontal direction and 96 dots per inch in the vertical direction, the endpoints of the line in the preceding example have the following coordinates in the three coordinate spaces:</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="9df90-152">Mundo</span><span class="sxs-lookup"><span data-stu-id="9df90-152">World</span></span>|<span data-ttu-id="9df90-153">(0, 0) a (2, 1)</span><span class="sxs-lookup"><span data-stu-id="9df90-153">(0, 0) to (2, 1)</span></span>|  
|<span data-ttu-id="9df90-154">Página</span><span class="sxs-lookup"><span data-stu-id="9df90-154">Page</span></span>|<span data-ttu-id="9df90-155">(2, 0.5) a (4, 1.5)</span><span class="sxs-lookup"><span data-stu-id="9df90-155">(2, 0.5) to (4, 1.5)</span></span>|  
|<span data-ttu-id="9df90-156">Dispositivo</span><span class="sxs-lookup"><span data-stu-id="9df90-156">Device</span></span>|<span data-ttu-id="9df90-157">(192, 48) a (384, 144)</span><span class="sxs-lookup"><span data-stu-id="9df90-157">(192, 48) to (384, 144)</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="9df90-158">Consulte também</span><span class="sxs-lookup"><span data-stu-id="9df90-158">See also</span></span>

- [<span data-ttu-id="9df90-159">Sistemas de Coordenadas e Transformações</span><span class="sxs-lookup"><span data-stu-id="9df90-159">Coordinate Systems and Transformations</span></span>](coordinate-systems-and-transformations.md)
- [<span data-ttu-id="9df90-160">Representação Matricial de Transformações</span><span class="sxs-lookup"><span data-stu-id="9df90-160">Matrix Representation of Transformations</span></span>](matrix-representation-of-transformations.md)
