---
title: 'Como: criar um gradiente linear'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- linear gradients [Windows Forms], creating
- gradients [Windows Forms], creating linear
- colors [Windows Forms], creating linear gradients
- gradients
ms.assetid: 6c88e1cc-1217-4399-ac12-cb37592b9f01
ms.openlocfilehash: e55d27b454579268658192ae56daa52e0b28bb83
ms.sourcegitcommit: c4e9d05644c9cb89de5ce6002723de107ea2e2c4
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/19/2019
ms.locfileid: "65876068"
---
# <a name="how-to-create-a-linear-gradient"></a><span data-ttu-id="23e31-102">Como: criar um gradiente linear</span><span class="sxs-lookup"><span data-stu-id="23e31-102">How to: Create a Linear Gradient</span></span>
<span data-ttu-id="23e31-103">GDI+ fornece gradientes lineares horizontais, verticais e diagonais.</span><span class="sxs-lookup"><span data-stu-id="23e31-103">GDI+ provides horizontal, vertical, and diagonal linear gradients.</span></span> <span data-ttu-id="23e31-104">Por padrão, a cor em um gradiente linear muda uniformemente.</span><span class="sxs-lookup"><span data-stu-id="23e31-104">By default, the color in a linear gradient changes uniformly.</span></span> <span data-ttu-id="23e31-105">No entanto, você pode personalizar um gradiente linear para que a cor mude de maneira não uniforme.</span><span class="sxs-lookup"><span data-stu-id="23e31-105">However, you can customize a linear gradient so that the color changes in a non-uniform fashion.</span></span>  

> [!NOTE]
> <span data-ttu-id="23e31-106">Os exemplos neste artigo são métodos que são chamados de um controle <xref:System.Windows.Forms.Control.Paint> manipulador de eventos.</span><span class="sxs-lookup"><span data-stu-id="23e31-106">The examples in this article are methods that are called from a control's <xref:System.Windows.Forms.Control.Paint> event handler.</span></span>  

<span data-ttu-id="23e31-107">O exemplo a seguir preenche uma linha, uma elipse e um retângulo com um pincel de gradiente linear horizontal.</span><span class="sxs-lookup"><span data-stu-id="23e31-107">The following example fills a line, an ellipse, and a rectangle with a horizontal linear gradient brush.</span></span>  
  
<span data-ttu-id="23e31-108">O <xref:System.Drawing.Drawing2D.LinearGradientBrush.%23ctor%2A> construtor recebe quatro argumentos: dois pontos e duas cores.</span><span class="sxs-lookup"><span data-stu-id="23e31-108">The <xref:System.Drawing.Drawing2D.LinearGradientBrush.%23ctor%2A> constructor receives four arguments: two points and two colors.</span></span> <span data-ttu-id="23e31-109">O primeiro ponto (0, 10) é associado à primeira cor (vermelho) e o segundo ponto (200, 10) é associado à segunda cor (azul).</span><span class="sxs-lookup"><span data-stu-id="23e31-109">The first point (0, 10) is associated with the first color (red), and the second point (200, 10) is associated with the second color (blue).</span></span> <span data-ttu-id="23e31-110">Como seria de esperar, a linha desenhada de (10, 0) a (200, 10) muda gradualmente de vermelho para azul.</span><span class="sxs-lookup"><span data-stu-id="23e31-110">As you would expect, the line drawn from (0, 10) to (200, 10) changes gradually from red to blue.</span></span>  
  
 <span data-ttu-id="23e31-111">Os 10s nos pontos de (0, 10) e (200, 10) não são importantes.</span><span class="sxs-lookup"><span data-stu-id="23e31-111">The 10s in the points (0, 10) and (200, 10) are not important.</span></span> <span data-ttu-id="23e31-112">O que é importante é que os dois pontos têm a mesma segunda coordenada: a linha que os conecta é horizontal.</span><span class="sxs-lookup"><span data-stu-id="23e31-112">What is important is that the two points have the same second coordinate — the line connecting them is horizontal.</span></span> <span data-ttu-id="23e31-113">A elipse e o retângulo também mudam gradualmente de vermelho para azul conforme a coordenada horizontal vai de 0 a 200.</span><span class="sxs-lookup"><span data-stu-id="23e31-113">The ellipse and the rectangle also change gradually from red to blue as the horizontal coordinate goes from 0 to 200.</span></span>  
  
 <span data-ttu-id="23e31-114">A ilustração a seguir mostra a linha, a elipse e o retângulo.</span><span class="sxs-lookup"><span data-stu-id="23e31-114">The following illustration shows the line, the ellipse, and the rectangle.</span></span> <span data-ttu-id="23e31-115">Observe que o gradiente de cores repete-se à medida que a coordenada horizontal aumenta além de 200.</span><span class="sxs-lookup"><span data-stu-id="23e31-115">Note that the color gradient repeats itself as the horizontal coordinate increases beyond 200.</span></span>  
  
 ![Uma linha, uma elipse e um retângulo preenchido com um gradiente de cores.](./media/how-to-create-a-linear-gradient/gradient-line-ellipse-rectangle.png)  
  
## <a name="to-use-horizontal-linear-gradients"></a><span data-ttu-id="23e31-117">Para usar gradientes lineares horizontais</span><span class="sxs-lookup"><span data-stu-id="23e31-117">To use horizontal linear gradients</span></span>  
  
- <span data-ttu-id="23e31-118">Passe o vermelho opaco e o azul opaco como o terceiro e o quarto argumentos, respectivamente.</span><span class="sxs-lookup"><span data-stu-id="23e31-118">Pass in the opaque red and opaque blue as the third and fourth argument, respectively.</span></span>  
  
     [!code-csharp[System.Drawing.UsingaGradientBrush#21](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.UsingaGradientBrush/CS/Class1.cs#21)]
     [!code-vb[System.Drawing.UsingaGradientBrush#21](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.UsingaGradientBrush/VB/Class1.vb#21)]  
  
 <span data-ttu-id="23e31-119">No exemplo anterior, os componentes de cor mudam linearmente conforme você vai de uma coordenada horizontal de 0 para uma coordenada horizontal de 200.</span><span class="sxs-lookup"><span data-stu-id="23e31-119">In the preceding example, the color components change linearly as you move from a horizontal coordinate of 0 to a horizontal coordinate of 200.</span></span> <span data-ttu-id="23e31-120">Por exemplo, um ponto cuja primeira coordenada esteja a meio caminho entre 0 e 200 terá um componente azul a meio caminho entre 0 e 255.</span><span class="sxs-lookup"><span data-stu-id="23e31-120">For example, a point whose first coordinate is halfway between 0 and 200 will have a blue component that is halfway between 0 and 255.</span></span>  
  
 <span data-ttu-id="23e31-121">GDI+ permite que você ajustar a maneira como a cor varia de uma borda de um gradiente para outra.</span><span class="sxs-lookup"><span data-stu-id="23e31-121">GDI+ allows you to adjust the way a color varies from one edge of a gradient to the other.</span></span> <span data-ttu-id="23e31-122">Suponha que você queira criar um pincel de gradiente que mude de preto para vermelho de acordo com a tabela a seguir.</span><span class="sxs-lookup"><span data-stu-id="23e31-122">Suppose you want to create a gradient brush that changes from black to red according to the following table.</span></span>  
  
|<span data-ttu-id="23e31-123">Coordenada horizontal</span><span class="sxs-lookup"><span data-stu-id="23e31-123">Horizontal coordinate</span></span>|<span data-ttu-id="23e31-124">Componentes RGB</span><span class="sxs-lookup"><span data-stu-id="23e31-124">RGB components</span></span>|  
|---------------------------|--------------------|  
|<span data-ttu-id="23e31-125">0</span><span class="sxs-lookup"><span data-stu-id="23e31-125">0</span></span>|<span data-ttu-id="23e31-126">(0, 0, 0)</span><span class="sxs-lookup"><span data-stu-id="23e31-126">(0, 0, 0)</span></span>|  
|<span data-ttu-id="23e31-127">40</span><span class="sxs-lookup"><span data-stu-id="23e31-127">40</span></span>|<span data-ttu-id="23e31-128">(128, 0, 0)</span><span class="sxs-lookup"><span data-stu-id="23e31-128">(128, 0, 0)</span></span>|  
|<span data-ttu-id="23e31-129">200</span><span class="sxs-lookup"><span data-stu-id="23e31-129">200</span></span>|<span data-ttu-id="23e31-130">(255, 0, 0)</span><span class="sxs-lookup"><span data-stu-id="23e31-130">(255, 0, 0)</span></span>|  
  
 <span data-ttu-id="23e31-131">Observe que o componente vermelho está na metade da intensidade quando a coordenada horizontal está a apenas 20% do caminho de 0 a 200.</span><span class="sxs-lookup"><span data-stu-id="23e31-131">Note that the red component is at half intensity when the horizontal coordinate is only 20 percent of the way from 0 to 200.</span></span>  
  
 <span data-ttu-id="23e31-132">O exemplo a seguir define o <xref:System.Drawing.Drawing2D.LinearGradientBrush.Blend%2A?displayProperty=nameWithType> propriedade para associar três intensidades relativas com três posições relativas.</span><span class="sxs-lookup"><span data-stu-id="23e31-132">The following example sets the <xref:System.Drawing.Drawing2D.LinearGradientBrush.Blend%2A?displayProperty=nameWithType> property to associate three relative intensities with three relative positions.</span></span> <span data-ttu-id="23e31-133">Como na tabela anterior, uma intensidade relativa de 0,5 é associada a uma posição relativa de 0,2.</span><span class="sxs-lookup"><span data-stu-id="23e31-133">As in the preceding table, a relative intensity of 0.5 is associated with a relative position of 0.2.</span></span> <span data-ttu-id="23e31-134">O código preenche uma elipse e um retângulo com o pincel de gradiente.</span><span class="sxs-lookup"><span data-stu-id="23e31-134">The code fills an ellipse and a rectangle with the gradient brush.</span></span>  
  
 <span data-ttu-id="23e31-135">A ilustração a seguir mostra o retângulo e elipse resultantes.</span><span class="sxs-lookup"><span data-stu-id="23e31-135">The following illustration shows the resulting ellipse and rectangle.</span></span>  
  
 ![Uma elipse e um retângulo preenchido com um gradiente de cores horizontal.](./media/how-to-create-a-linear-gradient/gradient-ellipse-rectangle.png)  

## <a name="to-customize-linear-gradients"></a><span data-ttu-id="23e31-137">Para personalizar os gradientes lineares</span><span class="sxs-lookup"><span data-stu-id="23e31-137">To customize linear gradients</span></span>  
  
- <span data-ttu-id="23e31-138">Passe o preto opaco e o vermelho opaco como o terceiro e o quarto argumentos, respectivamente.</span><span class="sxs-lookup"><span data-stu-id="23e31-138">Pass in the opaque black and opaque red as the third and fourth argument, respectively.</span></span>  
  
     [!code-csharp[System.Drawing.UsingaGradientBrush#22](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.UsingaGradientBrush/CS/Class1.cs#22)]
     [!code-vb[System.Drawing.UsingaGradientBrush#22](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.UsingaGradientBrush/VB/Class1.vb#22)]  
  
 <span data-ttu-id="23e31-139">Os gradientes nos exemplos anteriores eram horizontais; ou seja, a cor muda gradualmente à medida que você se move ao longo de qualquer linha horizontal.</span><span class="sxs-lookup"><span data-stu-id="23e31-139">The gradients in the preceding examples have been horizontal; that is, the color changes gradually as you move along any horizontal line.</span></span> <span data-ttu-id="23e31-140">Você também pode definir gradientes verticais e gradientes diagonais.</span><span class="sxs-lookup"><span data-stu-id="23e31-140">You can also define vertical gradients and diagonal gradients.</span></span>  
  
 <span data-ttu-id="23e31-141">O exemplo a seguir passa os pontos (0, 0) e (200, 100) para um <xref:System.Drawing.Drawing2D.LinearGradientBrush.%23ctor%2A> construtor.</span><span class="sxs-lookup"><span data-stu-id="23e31-141">The following example passes the points (0, 0) and (200, 100) to a <xref:System.Drawing.Drawing2D.LinearGradientBrush.%23ctor%2A> constructor.</span></span> <span data-ttu-id="23e31-142">A cor azul é associada a (0, 0) e a cor verde é associada a (200, 100).</span><span class="sxs-lookup"><span data-stu-id="23e31-142">The color blue is associated with (0, 0), and the color green is associated with (200, 100).</span></span> <span data-ttu-id="23e31-143">Uma linha (com largura da caneta de 10) e uma elipse são preenchidas com o pincel de gradiente linear.</span><span class="sxs-lookup"><span data-stu-id="23e31-143">A line (with pen width 10) and an ellipse are filled with the linear gradient brush.</span></span>  
  
 <span data-ttu-id="23e31-144">A ilustração a seguir mostra a linha e a elipse.</span><span class="sxs-lookup"><span data-stu-id="23e31-144">The following illustration shows the line and the ellipse.</span></span> <span data-ttu-id="23e31-145">Observe que a cor na elipse muda gradualmente à medida que você se move ao longo de qualquer linha paralela à linha que passa por (0, 0) e (200, 100).</span><span class="sxs-lookup"><span data-stu-id="23e31-145">Note that the color in the ellipse changes gradually as you move along any line that is parallel to the line passing through (0, 0) and (200, 100).</span></span>  
  
 ![Uma linha e uma elipse preenchida com um gradiente de cores diagonal.](./media/how-to-create-a-linear-gradient/gradient-line-ellipse.png)  
  
## <a name="to-create-diagonal-linear-gradients"></a><span data-ttu-id="23e31-147">Para criar gradientes lineares diagonais</span><span class="sxs-lookup"><span data-stu-id="23e31-147">To create diagonal linear gradients</span></span>  
  
- <span data-ttu-id="23e31-148">Passe o azul opaco e o verde opaco como o terceiro e o quarto argumentos, respectivamente.</span><span class="sxs-lookup"><span data-stu-id="23e31-148">Pass in the opaque blue and opaque green as the third and fourth argument, respectively.</span></span>  
  
     [!code-csharp[System.Drawing.UsingaGradientBrush#23](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.UsingaGradientBrush/CS/Class1.cs#23)]
     [!code-vb[System.Drawing.UsingaGradientBrush#23](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.UsingaGradientBrush/VB/Class1.vb#23)]  
  
## <a name="see-also"></a><span data-ttu-id="23e31-149">Consulte também</span><span class="sxs-lookup"><span data-stu-id="23e31-149">See also</span></span>

- [<span data-ttu-id="23e31-150">Usando um Pincel de Gradiente para Preencher Formas</span><span class="sxs-lookup"><span data-stu-id="23e31-150">Using a Gradient Brush to Fill Shapes</span></span>](using-a-gradient-brush-to-fill-shapes.md)
- [<span data-ttu-id="23e31-151">Elementos Gráficos e Desenho nos Windows Forms</span><span class="sxs-lookup"><span data-stu-id="23e31-151">Graphics and Drawing in Windows Forms</span></span>](graphics-and-drawing-in-windows-forms.md)
