---
title: Pincéis e formas preenchidas no GDI+
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- brushes [Windows Forms], GDI+
- filled shapes [Windows Forms], GDI+
- shapes [Windows Forms], GDI+
- GDI+, brushes
- GDI+, filled shapes
- gradient brushes
- brushes [Windows Forms], gradient
ms.assetid: e863e2a7-0294-4130-99b6-f1ea3201e7cd
ms.openlocfilehash: 9475518a5f0422e0eac1ec521088071bb4d1c885
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33518985"
---
# <a name="brushes-and-filled-shapes-in-gdi"></a><span data-ttu-id="659a2-102">Pincéis e formas preenchidas no GDI+</span><span class="sxs-lookup"><span data-stu-id="659a2-102">Brushes and Filled Shapes in GDI+</span></span>
<span data-ttu-id="659a2-103">Uma forma fechada, como um retângulo ou uma elipse, é composta por uma estrutura de tópicos e um interior.</span><span class="sxs-lookup"><span data-stu-id="659a2-103">A closed shape, such as a rectangle or an ellipse, consists of an outline and an interior.</span></span> <span data-ttu-id="659a2-104">A estrutura de tópicos é desenhada com uma caneta e o interior é preenchido com um pincel.</span><span class="sxs-lookup"><span data-stu-id="659a2-104">The outline is drawn with a pen and the interior is filled with a brush.</span></span> [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)]<span data-ttu-id="659a2-105"> fornece várias classes de pincel para preencher os interiores das formas fechadas: <xref:System.Drawing.SolidBrush>, <xref:System.Drawing.Drawing2D.HatchBrush>, <xref:System.Drawing.TextureBrush>, <xref:System.Drawing.Drawing2D.LinearGradientBrush>, e <xref:System.Drawing.Drawing2D.PathGradientBrush>.</span><span class="sxs-lookup"><span data-stu-id="659a2-105"> provides several brush classes for filling the interiors of closed shapes: <xref:System.Drawing.SolidBrush>, <xref:System.Drawing.Drawing2D.HatchBrush>, <xref:System.Drawing.TextureBrush>, <xref:System.Drawing.Drawing2D.LinearGradientBrush>, and <xref:System.Drawing.Drawing2D.PathGradientBrush>.</span></span> <span data-ttu-id="659a2-106">Todas essas classes herdam o <xref:System.Drawing.Brush> classe.</span><span class="sxs-lookup"><span data-stu-id="659a2-106">All of these classes inherit from the <xref:System.Drawing.Brush> class.</span></span> <span data-ttu-id="659a2-107">A ilustração a seguir mostra um retângulo preenchido com um pincel sólido e uma elipse preenchida com um pincel de hachura.</span><span class="sxs-lookup"><span data-stu-id="659a2-107">The following illustration shows a rectangle filled with a solid brush and an ellipse filled with a hatch brush.</span></span>  
  
 <span data-ttu-id="659a2-108">![Formas Preenchidas](../../../../docs/framework/winforms/advanced/media/aboutgdip02-art17.gif "Aboutgdip02_art17")</span><span class="sxs-lookup"><span data-stu-id="659a2-108">![Filled Shapes](../../../../docs/framework/winforms/advanced/media/aboutgdip02-art17.gif "Aboutgdip02_art17")</span></span>  
  
## <a name="solid-brushes"></a><span data-ttu-id="659a2-109">Pincéis Sólidos</span><span class="sxs-lookup"><span data-stu-id="659a2-109">Solid Brushes</span></span>  
 <span data-ttu-id="659a2-110">Para preencher uma forma fechada, você precisa de uma ocorrência da <xref:System.Drawing.Graphics> classe e um <xref:System.Drawing.Brush>.</span><span class="sxs-lookup"><span data-stu-id="659a2-110">To fill a closed shape, you need an instance of the <xref:System.Drawing.Graphics> class and a <xref:System.Drawing.Brush>.</span></span> <span data-ttu-id="659a2-111">A instância do <xref:System.Drawing.Graphics> classe fornece métodos, como <xref:System.Drawing.Graphics.FillRectangle%2A> e <xref:System.Drawing.Graphics.FillEllipse%2A>e o <xref:System.Drawing.Brush> armazena atributos de preenchimento, como cor e o padrão.</span><span class="sxs-lookup"><span data-stu-id="659a2-111">The instance of the <xref:System.Drawing.Graphics> class provides methods, such as <xref:System.Drawing.Graphics.FillRectangle%2A> and <xref:System.Drawing.Graphics.FillEllipse%2A>, and the <xref:System.Drawing.Brush> stores attributes of the fill, such as color and pattern.</span></span> <span data-ttu-id="659a2-112">O <xref:System.Drawing.Brush> é passado como um dos argumentos para o método de preenchimento.</span><span class="sxs-lookup"><span data-stu-id="659a2-112">The <xref:System.Drawing.Brush> is passed as one of the arguments to the fill method.</span></span> <span data-ttu-id="659a2-113">O exemplo de código a seguir mostra como preencher uma elipse com uma cor vermelha sólida.</span><span class="sxs-lookup"><span data-stu-id="659a2-113">The following code example shows how to fill an ellipse with a solid red color.</span></span>  
  
 [!code-csharp[LinesCurvesAndShapes#121](../../../../samples/snippets/csharp/VS_Snippets_Winforms/LinesCurvesAndShapes/CS/Class1.cs#121)]
 [!code-vb[LinesCurvesAndShapes#121](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/LinesCurvesAndShapes/VB/Class1.vb#121)]  
  
> [!NOTE]
>  <span data-ttu-id="659a2-114">No exemplo anterior, o pincel é do tipo <xref:System.Drawing.SolidBrush>, que herda de <xref:System.Drawing.Brush>.</span><span class="sxs-lookup"><span data-stu-id="659a2-114">In the preceding example, the brush is of type <xref:System.Drawing.SolidBrush>, which inherits from <xref:System.Drawing.Brush>.</span></span>  
  
## <a name="hatch-brushes"></a><span data-ttu-id="659a2-115">Pincéis de Hachura</span><span class="sxs-lookup"><span data-stu-id="659a2-115">Hatch Brushes</span></span>  
 <span data-ttu-id="659a2-116">Ao preencher uma forma com um pincel de hachura, é necessário especificar uma cor de primeiro plano, uma cor da tela de fundo e um estilo de hachura.</span><span class="sxs-lookup"><span data-stu-id="659a2-116">When you fill a shape with a hatch brush, you specify a foreground color, a background color, and a hatch style.</span></span> <span data-ttu-id="659a2-117">A cor de primeiro plano é a cor da hachura.</span><span class="sxs-lookup"><span data-stu-id="659a2-117">The foreground color is the color of the hatching.</span></span>  
  
 [!code-csharp[LinesCurvesAndShapes#122](../../../../samples/snippets/csharp/VS_Snippets_Winforms/LinesCurvesAndShapes/CS/Class1.cs#122)]
 [!code-vb[LinesCurvesAndShapes#122](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/LinesCurvesAndShapes/VB/Class1.vb#122)]  
  
 [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)]<span data-ttu-id="659a2-118"> fornece a mais de 50 estilos de hachura; os três estilos mostrados na ilustração a seguir são <xref:System.Drawing.Drawing2D.HatchStyle.Horizontal>, <xref:System.Drawing.Drawing2D.HatchStyle.ForwardDiagonal>, e <xref:System.Drawing.Drawing2D.HatchStyle.Cross>.</span><span class="sxs-lookup"><span data-stu-id="659a2-118"> provides more than 50 hatch styles; the three styles shown in the following illustration are <xref:System.Drawing.Drawing2D.HatchStyle.Horizontal>, <xref:System.Drawing.Drawing2D.HatchStyle.ForwardDiagonal>, and <xref:System.Drawing.Drawing2D.HatchStyle.Cross>.</span></span>  
  
 <span data-ttu-id="659a2-119">![Formas Preenchidas](../../../../docs/framework/winforms/advanced/media/aboutgdip02-art18.gif "Aboutgdip02_art18")</span><span class="sxs-lookup"><span data-stu-id="659a2-119">![Filled Shapes](../../../../docs/framework/winforms/advanced/media/aboutgdip02-art18.gif "Aboutgdip02_art18")</span></span>  
  
## <a name="texture-brushes"></a><span data-ttu-id="659a2-120">Pincéis de Textura</span><span class="sxs-lookup"><span data-stu-id="659a2-120">Texture Brushes</span></span>  
 <span data-ttu-id="659a2-121">Com um pincel de textura, é possível preencher uma forma com um padrão armazenado em um bitmap.</span><span class="sxs-lookup"><span data-stu-id="659a2-121">With a texture brush, you can fill a shape with a pattern stored in a bitmap.</span></span> <span data-ttu-id="659a2-122">Por exemplo, suponha que a imagem a seguir está armazenada em um arquivo de disco chamado `MyTexture.bmp`.</span><span class="sxs-lookup"><span data-stu-id="659a2-122">For example, suppose the following picture is stored in a disk file named `MyTexture.bmp`.</span></span>  
  
 <span data-ttu-id="659a2-123">![Forma Preenchida](../../../../docs/framework/winforms/advanced/media/aboutgdip02-art19.gif "Aboutgdip02_Art19")</span><span class="sxs-lookup"><span data-stu-id="659a2-123">![Filled Shape](../../../../docs/framework/winforms/advanced/media/aboutgdip02-art19.gif "Aboutgdip02_Art19")</span></span>  
  
 <span data-ttu-id="659a2-124">O exemplo de código a seguir mostra como preencher uma elipse repetindo a imagem armazenada em `MyTexture.bmp`.</span><span class="sxs-lookup"><span data-stu-id="659a2-124">The following code example shows how to fill an ellipse by repeating the picture stored in `MyTexture.bmp`.</span></span>  
  
 [!code-csharp[LinesCurvesAndShapes#123](../../../../samples/snippets/csharp/VS_Snippets_Winforms/LinesCurvesAndShapes/CS/Class1.cs#123)]
 [!code-vb[LinesCurvesAndShapes#123](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/LinesCurvesAndShapes/VB/Class1.vb#123)]  
  
 <span data-ttu-id="659a2-125">A ilustração a seguir mostra a elipse preenchida.</span><span class="sxs-lookup"><span data-stu-id="659a2-125">The following illustration shows the filled ellipse.</span></span>  
  
 <span data-ttu-id="659a2-126">![Forma Preenchida](../../../../docs/framework/winforms/advanced/media/aboutgdip02-art20.gif "AboutGdip02_Art20")</span><span class="sxs-lookup"><span data-stu-id="659a2-126">![Filled Shape](../../../../docs/framework/winforms/advanced/media/aboutgdip02-art20.gif "AboutGdip02_Art20")</span></span>  
  
## <a name="gradient-brushes"></a><span data-ttu-id="659a2-127">Pincéis de Gradiente</span><span class="sxs-lookup"><span data-stu-id="659a2-127">Gradient Brushes</span></span>  
 [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)]<span data-ttu-id="659a2-128"> oferece dois tipos de pincéis de gradiente: linear e de caminho.</span><span class="sxs-lookup"><span data-stu-id="659a2-128"> provides two kinds of gradient brushes: linear and path.</span></span> <span data-ttu-id="659a2-129">É possível usar um pincel de gradiente linear para preencher uma forma com uma cor que muda gradualmente à medida que a forma é movida horizontal, vertical ou diagonalmente.</span><span class="sxs-lookup"><span data-stu-id="659a2-129">You can use a linear gradient brush to fill a shape with color that changes gradually as you move across the shape horizontally, vertically, or diagonally.</span></span> <span data-ttu-id="659a2-130">O exemplo de código a seguir mostra como preencher uma elipse com um pincel de gradiente horizontal que muda de azul para verde ao mover da borda esquerda para a borda direita da elipse.</span><span class="sxs-lookup"><span data-stu-id="659a2-130">The following code example shows how to fill an ellipse with a horizontal gradient brush that changes from blue to green as you move from the left edge of the ellipse to the right edge.</span></span>  
  
 [!code-csharp[LinesCurvesAndShapes#124](../../../../samples/snippets/csharp/VS_Snippets_Winforms/LinesCurvesAndShapes/CS/Class1.cs#124)]
 [!code-vb[LinesCurvesAndShapes#124](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/LinesCurvesAndShapes/VB/Class1.vb#124)]  
  
 <span data-ttu-id="659a2-131">A ilustração a seguir mostra a elipse preenchida.</span><span class="sxs-lookup"><span data-stu-id="659a2-131">The following illustration shows the filled ellipse.</span></span>  
  
 <span data-ttu-id="659a2-132">![Forma Preenchida](../../../../docs/framework/winforms/advanced/media/aboutgdip02-art21.gif "AboutGdip02_Art21")</span><span class="sxs-lookup"><span data-stu-id="659a2-132">![Filled Shape](../../../../docs/framework/winforms/advanced/media/aboutgdip02-art21.gif "AboutGdip02_Art21")</span></span>  
  
 <span data-ttu-id="659a2-133">Um pincel de gradiente de caminho pode ser configurado para alterar a cor ao mover do centro de uma forma para a borda.</span><span class="sxs-lookup"><span data-stu-id="659a2-133">A path gradient brush can be configured to change color as you move from the center of a shape toward the edge.</span></span>  
  
 <span data-ttu-id="659a2-134">![Forma Preenchida](../../../../docs/framework/winforms/advanced/media/aboutgdip02-art22.gif "AboutGdip02_Art22")</span><span class="sxs-lookup"><span data-stu-id="659a2-134">![Filled Shape](../../../../docs/framework/winforms/advanced/media/aboutgdip02-art22.gif "AboutGdip02_Art22")</span></span>  
  
 <span data-ttu-id="659a2-135">Pincéis de gradiente de caminho são bastante flexíveis.</span><span class="sxs-lookup"><span data-stu-id="659a2-135">Path gradient brushes are quite flexible.</span></span> <span data-ttu-id="659a2-136">O pincel de gradiente usado para preencher o triângulo nas seguintes ilustrações altera gradualmente de vermelho no centro para cada uma das três cores diferentes nos vértices.</span><span class="sxs-lookup"><span data-stu-id="659a2-136">The gradient brush used to fill the triangle in the following illustration changes gradually from red at the center to each of three different colors at the vertices.</span></span>  
  
 <span data-ttu-id="659a2-137">![Forma Preenchida](../../../../docs/framework/winforms/advanced/media/aboutgdip02-art23.gif "AboutGdip02_Art23")</span><span class="sxs-lookup"><span data-stu-id="659a2-137">![Filled Shape](../../../../docs/framework/winforms/advanced/media/aboutgdip02-art23.gif "AboutGdip02_Art23")</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="659a2-138">Consulte também</span><span class="sxs-lookup"><span data-stu-id="659a2-138">See Also</span></span>  
 <xref:System.Drawing.SolidBrush?displayProperty=nameWithType>  
 <xref:System.Drawing.Drawing2D.HatchBrush?displayProperty=nameWithType>  
 <xref:System.Drawing.TextureBrush?displayProperty=nameWithType>  
 <xref:System.Drawing.Drawing2D.LinearGradientBrush?displayProperty=nameWithType>  
 [<span data-ttu-id="659a2-139">Linhas, Curvas e Formas</span><span class="sxs-lookup"><span data-stu-id="659a2-139">Lines, Curves, and Shapes</span></span>](../../../../docs/framework/winforms/advanced/lines-curves-and-shapes.md)  
 [<span data-ttu-id="659a2-140">Como Desenhar um Retângulo Preenchido em um Formulário dos Windows Forms</span><span class="sxs-lookup"><span data-stu-id="659a2-140">How to: Draw a Filled Rectangle on a Windows Form</span></span>](../../../../docs/framework/winforms/advanced/how-to-draw-a-filled-rectangle-on-a-windows-form.md)  
 [<span data-ttu-id="659a2-141">Como Desenhar uma Elipse Preenchida em um Formulário dos Windows Forms</span><span class="sxs-lookup"><span data-stu-id="659a2-141">How to: Draw a Filled Ellipse on a Windows Form</span></span>](../../../../docs/framework/winforms/advanced/how-to-draw-a-filled-ellipse-on-a-windows-form.md)
