---
title: Como desenhar formas com os controles OvalShape e RectangleShape (Visual Studio)
ms.date: 07/20/2015
ms.prod: .net
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- OvalShape control [Visual Basic]
- shapes, drawing
- RectangleShape control [Visual Basic]
ms.assetid: 0275b4c6-7a13-46c8-90f3-61db308c6b5d
caps.latest.revision: "15"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 53d91d10cc4735bbae521d17d05045cc7ea75fbc
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-draw-shapes-with-the-ovalshape-and-rectangleshape-controls-visual-studio"></a><span data-ttu-id="ee2a4-102">Como desenhar formas com os controles OvalShape e RectangleShape (Visual Studio)</span><span class="sxs-lookup"><span data-stu-id="ee2a4-102">How to: Draw Shapes with the OvalShape and RectangleShape Controls (Visual Studio)</span></span>
<span data-ttu-id="ee2a4-103">Você pode usar o controle <xref:Microsoft.VisualBasic.PowerPacks.OvalShape> para desenhar círculos ou elipses em um formulário ou contêiner, no tempo de design e em tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="ee2a4-103">You can use the <xref:Microsoft.VisualBasic.PowerPacks.OvalShape> control to draw circles or ovals on a form or container, both at design time and at run time.</span></span> <span data-ttu-id="ee2a4-104">Você pode usar o controle <xref:Microsoft.VisualBasic.PowerPacks.RectangleShape> para desenhar quadrados, retângulos ou retângulos com cantos arredondados em um formulário ou contêiner.</span><span class="sxs-lookup"><span data-stu-id="ee2a4-104">You can use the <xref:Microsoft.VisualBasic.PowerPacks.RectangleShape> control to draw squares, rectangles, or rectangles with rounded corners on a form or container.</span></span> <span data-ttu-id="ee2a4-105">Você também pode usar esse controle para desenhar formas em tempo de design e em tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="ee2a4-105">You can also use this control to draw shapes both at design time and at run time.</span></span>  
  
 <span data-ttu-id="ee2a4-106">Você pode personalizar a aparência de uma forma alterando a largura, a cor e o estilo de borda.</span><span class="sxs-lookup"><span data-stu-id="ee2a4-106">You can customize the appearance of a shape by changing the width, color, and style of the border.</span></span> <span data-ttu-id="ee2a4-107">O plano de fundo de uma forma é transparente por padrão. Você pode personalizar o plano de fundo para exibir uma cor sólida, um padrão, um preenchimento gradual (transição de uma cor para outra) ou uma imagem.</span><span class="sxs-lookup"><span data-stu-id="ee2a4-107">The background of a shape is transparent by default; you can customize the background to display a solid color, a pattern, a gradient fill (transitioning from one color to another), or an image.</span></span>  
  
### <a name="to-draw-a-simple-shape-at-design-time"></a><span data-ttu-id="ee2a4-108">Para desenhar uma forma simples em tempo de design</span><span class="sxs-lookup"><span data-stu-id="ee2a4-108">To draw a simple shape at design time</span></span>  
  
1.  <span data-ttu-id="ee2a4-109">Arraste o <xref:Microsoft.VisualBasic.PowerPacks.OvalShape> ou <xref:Microsoft.VisualBasic.PowerPacks.RectangleShape> controlar do **Visual Basic PowerPacks** guia (para instalar, consulte [controles do Visual Basic Power Packs](../../../visual-basic/developing-apps/windows-forms/power-packs-controls.md)) no **caixa de ferramentas** para um controle de formulário ou contêiner.</span><span class="sxs-lookup"><span data-stu-id="ee2a4-109">Drag the <xref:Microsoft.VisualBasic.PowerPacks.OvalShape> or <xref:Microsoft.VisualBasic.PowerPacks.RectangleShape> control from the **Visual Basic PowerPacks** tab (to install, see [Visual Basic Power Packs Controls](../../../visual-basic/developing-apps/windows-forms/power-packs-controls.md))in the **Toolbox** to a form or container control.</span></span>  
  
2.  <span data-ttu-id="ee2a4-110">Arraste o dimensionamento e mova as alças para dimensionar e posicionar a forma.</span><span class="sxs-lookup"><span data-stu-id="ee2a4-110">Drag the sizing and move handles to size and position the shape.</span></span>  
  
     <span data-ttu-id="ee2a4-111">Você também pode dimensionar e posicionar a forma alterando o `Size` e `Position` propriedades o **propriedades** janela.</span><span class="sxs-lookup"><span data-stu-id="ee2a4-111">You can also size and position the shape by changing the `Size` and `Position` properties in the **Properties** window.</span></span>  
  
     <span data-ttu-id="ee2a4-112">Para criar um retângulo com cantos arredondados, selecione o `CornerRadius` propriedade o **propriedades** janela e defina-o como um valor maior que 0.</span><span class="sxs-lookup"><span data-stu-id="ee2a4-112">To create a rectangle with rounded corners, select the `CornerRadius` property in the **Properties** window and set it to a value that is greater than 0.</span></span>  
  
3.  <span data-ttu-id="ee2a4-113">No **propriedades** janela, opcionalmente, conjunto de propriedades adicionais para alterar a aparência da forma.</span><span class="sxs-lookup"><span data-stu-id="ee2a4-113">In the **Properties** window, optionally set additional properties to change the appearance of the shape.</span></span>  
  
### <a name="to-draw-a-simple-shape-at-run-time"></a><span data-ttu-id="ee2a4-114">Para desenhar uma forma simples em tempo de execução</span><span class="sxs-lookup"><span data-stu-id="ee2a4-114">To draw a simple shape at run time</span></span>  
  
1.  <span data-ttu-id="ee2a4-115">No menu **Projeto**, clique em **Adicionar Referência**.</span><span class="sxs-lookup"><span data-stu-id="ee2a4-115">On the **Project** menu, click **Add Reference**.</span></span>  
  
2.  <span data-ttu-id="ee2a4-116">No **adicionar referência** caixa de diálogo, selecione **Microsoft.VisualBasic.PowerPacks.VS**e, em seguida, clique em **Okey**.</span><span class="sxs-lookup"><span data-stu-id="ee2a4-116">In the **Add Reference** dialog box, select **Microsoft.VisualBasic.PowerPacks.VS**, and then click **OK**.</span></span>  
  
3.  <span data-ttu-id="ee2a4-117">No **Editor de códigos**, adicione um `Imports` ou `using` instrução na parte superior do módulo:</span><span class="sxs-lookup"><span data-stu-id="ee2a4-117">In the **Code Editor**, add an `Imports` or `using` statement at the top of the module:</span></span>  
  
```vb  
Imports Microsoft.VisualBasic.PowerPacks  
```  
  
```csharp  
using Microsoft.VisualBasic.PowerPacks;  
```  
  
4.  <span data-ttu-id="ee2a4-118">Adicione o seguinte código em um procedimento do `Event`:</span><span class="sxs-lookup"><span data-stu-id="ee2a4-118">Add the following code in an `Event` procedure:</span></span>  
  
     [!code-csharp[VbPowerpacksShape#1](../../../visual-basic/developing-apps/windows-forms/codesnippet/CSharp/how-to-draw-shapes-with-the-ovalshape-and-rectangleshape-controls_1.cs)]
     [!code-vb[VbPowerpacksShape#1](../../../visual-basic/developing-apps/windows-forms/codesnippet/VisualBasic/how-to-draw-shapes-with-the-ovalshape-and-rectangleshape-controls_1.vb)]  
  
## <a name="customizing-shapes"></a><span data-ttu-id="ee2a4-119">Personalizando Formas</span><span class="sxs-lookup"><span data-stu-id="ee2a4-119">Customizing Shapes</span></span>  
 <span data-ttu-id="ee2a4-120">Ao usar as configurações padrão, os controles <xref:Microsoft.VisualBasic.PowerPacks.OvalShape> e <xref:Microsoft.VisualBasic.PowerPacks.RectangleShape> são exibidos com uma borda preta sólida que é um pixel mais amplo e um plano de fundo transparente.</span><span class="sxs-lookup"><span data-stu-id="ee2a4-120">When you use the default settings, the <xref:Microsoft.VisualBasic.PowerPacks.OvalShape> and <xref:Microsoft.VisualBasic.PowerPacks.RectangleShape> controls are displayed with a solid black border that is one pixel wide and a transparent background.</span></span> <span data-ttu-id="ee2a4-121">Você pode alterar a largura, o estilo e a cor da borda definindo as propriedades.</span><span class="sxs-lookup"><span data-stu-id="ee2a4-121">You can change the width, style, and color of the border by setting properties.</span></span> <span data-ttu-id="ee2a4-122">As propriedades adicionais permitem que você altere o plano de fundo de uma forma para uma cor sólida, um padrão, um preenchimento gradual ou uma imagem.</span><span class="sxs-lookup"><span data-stu-id="ee2a4-122">Additional properties enable you to change the background of a shape to a solid color, a pattern, a gradient fill, or an image.</span></span>  
  
 <span data-ttu-id="ee2a4-123">Antes de alterar o plano de fundo de uma forma, você deve saber como diversas propriedades interagem.</span><span class="sxs-lookup"><span data-stu-id="ee2a4-123">Before you change the background of a shape, you should know how several of the properties interact.</span></span>  
  
-   <span data-ttu-id="ee2a4-124">A configuração de propriedade <xref:Microsoft.VisualBasic.PowerPacks.SimpleShape.BackColor%2A> não tem efeito, a menos que a propriedade <xref:Microsoft.VisualBasic.PowerPacks.SimpleShape.BackStyle%2A> esteja definida como <xref:Microsoft.VisualBasic.PowerPacks.BackStyle.Opaque>.</span><span class="sxs-lookup"><span data-stu-id="ee2a4-124">The <xref:Microsoft.VisualBasic.PowerPacks.SimpleShape.BackColor%2A> property setting has no effect unless the <xref:Microsoft.VisualBasic.PowerPacks.SimpleShape.BackStyle%2A> property is set to <xref:Microsoft.VisualBasic.PowerPacks.BackStyle.Opaque>.</span></span>  
  
-   <span data-ttu-id="ee2a4-125">Se a propriedade <xref:Microsoft.VisualBasic.PowerPacks.SimpleShape.FillStyle%2A> for definida como <xref:Microsoft.VisualBasic.PowerPacks.FillStyle.Solid>, o <xref:Microsoft.VisualBasic.PowerPacks.SimpleShape.FillColor%2A> substitui o <xref:Microsoft.VisualBasic.PowerPacks.SimpleShape.BackColor%2A>.</span><span class="sxs-lookup"><span data-stu-id="ee2a4-125">If the <xref:Microsoft.VisualBasic.PowerPacks.SimpleShape.FillStyle%2A> property is set to <xref:Microsoft.VisualBasic.PowerPacks.FillStyle.Solid>, the <xref:Microsoft.VisualBasic.PowerPacks.SimpleShape.FillColor%2A> overrides the <xref:Microsoft.VisualBasic.PowerPacks.SimpleShape.BackColor%2A>.</span></span>  
  
-   <span data-ttu-id="ee2a4-126">Se a propriedade <xref:Microsoft.VisualBasic.PowerPacks.SimpleShape.FillStyle%2A> for definida como um valor padrão, como <xref:Microsoft.VisualBasic.PowerPacks.FillStyle.Horizontal> ou <xref:Microsoft.VisualBasic.PowerPacks.FillStyle.Vertical>, o padrão será exibido no <xref:Microsoft.VisualBasic.PowerPacks.SimpleShape.FillColor%2A>.</span><span class="sxs-lookup"><span data-stu-id="ee2a4-126">If the <xref:Microsoft.VisualBasic.PowerPacks.SimpleShape.FillStyle%2A> property is set to a pattern value such as <xref:Microsoft.VisualBasic.PowerPacks.FillStyle.Horizontal> or <xref:Microsoft.VisualBasic.PowerPacks.FillStyle.Vertical>, the pattern will be displayed in the <xref:Microsoft.VisualBasic.PowerPacks.SimpleShape.FillColor%2A>.</span></span> <span data-ttu-id="ee2a4-127">O plano de fundo será exibido no <xref:Microsoft.VisualBasic.PowerPacks.SimpleShape.BackColor%2A>, desde que a propriedade <xref:Microsoft.VisualBasic.PowerPacks.SimpleShape.BackStyle%2A> seja definida como <xref:Microsoft.VisualBasic.PowerPacks.BackStyle.Opaque>.</span><span class="sxs-lookup"><span data-stu-id="ee2a4-127">The background will be displayed in the <xref:Microsoft.VisualBasic.PowerPacks.SimpleShape.BackColor%2A>, provided that the <xref:Microsoft.VisualBasic.PowerPacks.SimpleShape.BackStyle%2A> property is set to <xref:Microsoft.VisualBasic.PowerPacks.BackStyle.Opaque>.</span></span>  
  
-   <span data-ttu-id="ee2a4-128">Para exibir um preenchimento gradual, a propriedade <xref:Microsoft.VisualBasic.PowerPacks.SimpleShape.FillStyle%2A> deve estar configurada como <xref:Microsoft.VisualBasic.PowerPacks.FillStyle.Solid> e a propriedade <xref:Microsoft.VisualBasic.PowerPacks.SimpleShape.FillGradientStyle%2A> deve ser configurada com um valor diferente de <xref:Microsoft.VisualBasic.PowerPacks.FillGradientStyle.None>.</span><span class="sxs-lookup"><span data-stu-id="ee2a4-128">In order to display a gradient fill, the <xref:Microsoft.VisualBasic.PowerPacks.SimpleShape.FillStyle%2A> property must be set to <xref:Microsoft.VisualBasic.PowerPacks.FillStyle.Solid> and the <xref:Microsoft.VisualBasic.PowerPacks.SimpleShape.FillGradientStyle%2A> property must be set to a value other than <xref:Microsoft.VisualBasic.PowerPacks.FillGradientStyle.None>.</span></span>  
  
-   <span data-ttu-id="ee2a4-129">Configurando a propriedade <xref:Microsoft.VisualBasic.PowerPacks.SimpleShape.BackgroundImage%2A> para uma imagem substitui todas as outras configurações de plano de fundo.</span><span class="sxs-lookup"><span data-stu-id="ee2a4-129">Setting the <xref:Microsoft.VisualBasic.PowerPacks.SimpleShape.BackgroundImage%2A> property to an image overrides all other background settings.</span></span>  
  
#### <a name="to-draw-a-circle-that-has-a-custom-border"></a><span data-ttu-id="ee2a4-130">Para desenhar um círculo com uma borda personalizada</span><span class="sxs-lookup"><span data-stu-id="ee2a4-130">To draw a circle that has a custom border</span></span>  
  
1.  <span data-ttu-id="ee2a4-131">Arraste o `OvalShape` controlar do **Visual Basic PowerPacks** guia o **caixa de ferramentas** a um controle de formulário ou contêiner.</span><span class="sxs-lookup"><span data-stu-id="ee2a4-131">Drag the `OvalShape` control from the **Visual Basic PowerPacks** tab in the **Toolbox** to a form or container control.</span></span>  
  
2.  <span data-ttu-id="ee2a4-132">No **propriedades** janela, no `Size` propriedade, definida `Height` e `Width` para igualar valores.</span><span class="sxs-lookup"><span data-stu-id="ee2a4-132">In the **Properties** window, in the `Size` property, set `Height` and `Width` to equal values.</span></span>  
  
3.  <span data-ttu-id="ee2a4-133">Defina a propriedade `BorderColor` com a cor desejada.</span><span class="sxs-lookup"><span data-stu-id="ee2a4-133">Set the `BorderColor` property to the color that you want.</span></span>  
  
4.  <span data-ttu-id="ee2a4-134">Defina a propriedade `BorderStyle` como qualquer valor diferente de `Solid`.</span><span class="sxs-lookup"><span data-stu-id="ee2a4-134">Set the `BorderStyle` property to any value other than `Solid`.</span></span>  
  
5.  <span data-ttu-id="ee2a4-135">Defina o `BorderWidth` para o tamanho desejado, em pixels.</span><span class="sxs-lookup"><span data-stu-id="ee2a4-135">Set the `BorderWidth` to the size that you want, in pixels.</span></span>  
  
#### <a name="to-draw-a-circle-that-has-a-solid-fill"></a><span data-ttu-id="ee2a4-136">Para desenhar um círculo que tenha um preenchimento sólido</span><span class="sxs-lookup"><span data-stu-id="ee2a4-136">To draw a circle that has a solid fill</span></span>  
  
1.  <span data-ttu-id="ee2a4-137">Arraste o `OvalShape` controlar do **Visual Basic PowerPacks** guia o **caixa de ferramentas** a um controle de formulário ou contêiner.</span><span class="sxs-lookup"><span data-stu-id="ee2a4-137">Drag the `OvalShape` control from the **Visual Basic PowerPacks** tab in the **Toolbox** to a form or container control.</span></span>  
  
2.  <span data-ttu-id="ee2a4-138">No **propriedades** janela, no `Size` propriedade, definida `Height` e `Width` para igualar valores.</span><span class="sxs-lookup"><span data-stu-id="ee2a4-138">In the **Properties** window, in the `Size` property, set `Height` and `Width` to equal values.</span></span>  
  
3.  <span data-ttu-id="ee2a4-139">Defina a propriedade `BackColor` com a cor desejada.</span><span class="sxs-lookup"><span data-stu-id="ee2a4-139">Set the `BackColor` property to the color that you want.</span></span>  
  
4.  <span data-ttu-id="ee2a4-140">Defina a propriedade `BackStyle` como `Opaque`.</span><span class="sxs-lookup"><span data-stu-id="ee2a4-140">Set the `BackStyle` property to `Opaque`.</span></span>  
  
#### <a name="to-draw-a-circle-that-has-a-patterned-fill"></a><span data-ttu-id="ee2a4-141">Para desenhar um círculo que tenha um preenchimento padronizado</span><span class="sxs-lookup"><span data-stu-id="ee2a4-141">To draw a circle that has a patterned fill</span></span>  
  
1.  <span data-ttu-id="ee2a4-142">Arraste o `OvalShape` controlar do **Visual Basic PowerPacks** guia o **caixa de ferramentas** a um controle de formulário ou contêiner.</span><span class="sxs-lookup"><span data-stu-id="ee2a4-142">Drag the `OvalShape` control from the **Visual Basic PowerPacks** tab in the **Toolbox** to a form or container control.</span></span>  
  
2.  <span data-ttu-id="ee2a4-143">No **propriedades** janela, no `Size` propriedade, definida `Height` e `Width` para igualar valores.</span><span class="sxs-lookup"><span data-stu-id="ee2a4-143">In the **Properties** window, in the `Size` property, set `Height` and `Width` to equal values.</span></span>  
  
3.  <span data-ttu-id="ee2a4-144">Defina a propriedade `BackColor` com a cor desejada para o plano de fundo.</span><span class="sxs-lookup"><span data-stu-id="ee2a4-144">Set the `BackColor` property to the color that you want for the background.</span></span>  
  
4.  <span data-ttu-id="ee2a4-145">Defina a propriedade `BackStyle` como `Opaque`.</span><span class="sxs-lookup"><span data-stu-id="ee2a4-145">Set the `BackStyle` property to `Opaque`.</span></span>  
  
5.  <span data-ttu-id="ee2a4-146">Defina a propriedade `FillColor` com a cor desejada para o padrão.</span><span class="sxs-lookup"><span data-stu-id="ee2a4-146">Set the `FillColor` property to the color that you want for the pattern.</span></span>  
  
6.  <span data-ttu-id="ee2a4-147">Defina a propriedade `FillStyle` como qualquer valor diferente de `Transparent` ou `Solid`.</span><span class="sxs-lookup"><span data-stu-id="ee2a4-147">Set the `FillStyle` property to any value other than `Transparent` or `Solid`.</span></span>  
  
#### <a name="to-draw-a-circle-that-has-a-gradient-fill"></a><span data-ttu-id="ee2a4-148">Para desenhar um círculo que tenha um preenchimento gradual</span><span class="sxs-lookup"><span data-stu-id="ee2a4-148">To draw a circle that has a gradient fill</span></span>  
  
1.  <span data-ttu-id="ee2a4-149">Arraste o `OvalShape` controlar do **Visual Basic PowerPacks** guia o **caixa de ferramentas** a um controle de formulário ou contêiner.</span><span class="sxs-lookup"><span data-stu-id="ee2a4-149">Drag the `OvalShape` control from the **Visual Basic PowerPacks** tab in the **Toolbox** to a form or container control.</span></span>  
  
2.  <span data-ttu-id="ee2a4-150">No **propriedades** janela, no `Size` propriedade, definida `Height` e `Width` para igualar valores.</span><span class="sxs-lookup"><span data-stu-id="ee2a4-150">In the **Properties** window, in the `Size` property, set `Height` and `Width` to equal values.</span></span>  
  
3.  <span data-ttu-id="ee2a4-151">Defina a propriedade `FillColor` com a cor desejada para a cor inicial.</span><span class="sxs-lookup"><span data-stu-id="ee2a4-151">Set the `FillColor` property to the color that you want for the starting color.</span></span>  
  
4.  <span data-ttu-id="ee2a4-152">Defina a propriedade `FillGradientColor` com a cor desejada para a cor final.</span><span class="sxs-lookup"><span data-stu-id="ee2a4-152">Set the `FillGradientColor` property to the color that you want for the ending color.</span></span>  
  
5.  <span data-ttu-id="ee2a4-153">Defina a propriedade `FillGradientStyle` como um valor diferente de `None`.</span><span class="sxs-lookup"><span data-stu-id="ee2a4-153">Set the `FillGradientStyle` property to a value other than `None`.</span></span>  
  
#### <a name="to-draw-a-circle-that-is-filled-with-an-image"></a><span data-ttu-id="ee2a4-154">Para desenhar um círculo preenchido com uma imagem</span><span class="sxs-lookup"><span data-stu-id="ee2a4-154">To draw a circle that is filled with an image</span></span>  
  
1.  <span data-ttu-id="ee2a4-155">Arraste o `OvalShape` controlar do **Visual Basic PowerPacks** guia o **caixa de ferramentas** a um controle de formulário ou contêiner.</span><span class="sxs-lookup"><span data-stu-id="ee2a4-155">Drag the `OvalShape` control from the **Visual Basic PowerPacks** tab in the **Toolbox** to a form or container control.</span></span>  
  
2.  <span data-ttu-id="ee2a4-156">No **propriedades** janela, no `Size` propriedade, definida `Height` e `Width` para igualar valores.</span><span class="sxs-lookup"><span data-stu-id="ee2a4-156">In the **Properties** window, in the `Size` property, set `Height` and `Width` to equal values.</span></span>  
  
3.  <span data-ttu-id="ee2a4-157">Selecione o `BackgroundImage` propriedade e clique no **reticências** botão (…).</span><span class="sxs-lookup"><span data-stu-id="ee2a4-157">Select the `BackgroundImage` property and click the **ellipsis** button (...).</span></span>  
  
4.  <span data-ttu-id="ee2a4-158">No **selecionar recurso** caixa de diálogo, selecione uma imagem a ser exibida.</span><span class="sxs-lookup"><span data-stu-id="ee2a4-158">In the **Select Resource** dialog box, select an image to display.</span></span> <span data-ttu-id="ee2a4-159">Se nenhum recurso de imagem estiver listado, clique em **importação** para navegar até o local de uma imagem.</span><span class="sxs-lookup"><span data-stu-id="ee2a4-159">If no image resources are listed, click **Import** to browse to the location of an image.</span></span>  
  
5.  <span data-ttu-id="ee2a4-160">Clique em **Okey** para inserir a imagem.</span><span class="sxs-lookup"><span data-stu-id="ee2a4-160">Click **OK** to insert the image.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ee2a4-161">Consulte também</span><span class="sxs-lookup"><span data-stu-id="ee2a4-161">See Also</span></span>  
 <xref:Microsoft.VisualBasic.PowerPacks.OvalShape>  
 <xref:Microsoft.VisualBasic.PowerPacks.RectangleShape>  
 [<span data-ttu-id="ee2a4-162">Introdução aos controles de linha e forma</span><span class="sxs-lookup"><span data-stu-id="ee2a4-162">Introduction to the Line and Shape Controls</span></span>](../../../visual-basic/developing-apps/windows-forms/introduction-to-the-line-and-shape-controls-visual-studio.md)  
 [<span data-ttu-id="ee2a4-163">Como desenhar linhas com o controle LineShape</span><span class="sxs-lookup"><span data-stu-id="ee2a4-163">How to: Draw Lines with the LineShape Control</span></span>](../../../visual-basic/developing-apps/windows-forms/how-to-draw-lines-with-the-lineshape-control-visual-studio.md)
