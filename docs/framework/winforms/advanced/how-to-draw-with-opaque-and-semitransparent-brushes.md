---
title: Como desenhar com pincéis opacos e semitransparentes
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- semi-transparent shapes [Windows Forms], drawing
- transparency [Windows Forms], semi-transparent shapes
- alpha blending [Windows Forms], brush
- brushes [Windows Forms], using semi-transparent
ms.assetid: a4f6f6b8-3bc8-440a-84af-d62ef0f8ff40
ms.openlocfilehash: 1e48bbd563f6377380848949325962b568fa432c
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79142401"
---
# <a name="how-to-draw-with-opaque-and-semitransparent-brushes"></a><span data-ttu-id="0e745-102">Como desenhar com pincéis opacos e semitransparentes</span><span class="sxs-lookup"><span data-stu-id="0e745-102">How to: Draw with Opaque and Semitransparent Brushes</span></span>
<span data-ttu-id="0e745-103">Quando você preenche uma forma, <xref:System.Drawing.Brush> você deve passar um objeto <xref:System.Drawing.Graphics> para um dos métodos de preenchimento da classe.</span><span class="sxs-lookup"><span data-stu-id="0e745-103">When you fill a shape, you must pass a <xref:System.Drawing.Brush> object to one of the fill methods of the <xref:System.Drawing.Graphics> class.</span></span> <span data-ttu-id="0e745-104">O único parâmetro <xref:System.Drawing.SolidBrush.%23ctor%2A> do construtor <xref:System.Drawing.Color> é um objeto.</span><span class="sxs-lookup"><span data-stu-id="0e745-104">The one parameter of the <xref:System.Drawing.SolidBrush.%23ctor%2A> constructor is a <xref:System.Drawing.Color> object.</span></span> <span data-ttu-id="0e745-105">Para preencher uma forma opaca, defina o componente alfa da cor como 255.</span><span class="sxs-lookup"><span data-stu-id="0e745-105">To fill an opaque shape, set the alpha component of the color to 255.</span></span> <span data-ttu-id="0e745-106">Para preencher uma forma semitransparente, defina o componente alfa para qualquer valor de 1 a 254.</span><span class="sxs-lookup"><span data-stu-id="0e745-106">To fill a semitransparent shape, set the alpha component to any value from 1 through 254.</span></span>  
  
 <span data-ttu-id="0e745-107">Ao preencher uma forma semitransparente, a cor da forma é combinada com as cores da tela de fundo.</span><span class="sxs-lookup"><span data-stu-id="0e745-107">When you fill a semitransparent shape, the color of the shape is blended with the colors of the background.</span></span> <span data-ttu-id="0e745-108">O componente alfa especifica como as cores da tela de fundo e da forma são misturadas; valores alfa próximos a 0 colocam mais peso nas cores da tela de fundo e valores alfabéticos próximos 255 colocam mais peso na cor da forma.</span><span class="sxs-lookup"><span data-stu-id="0e745-108">The alpha component specifies how the shape and background colors are mixed; alpha values near 0 place more weight on the background colors, and alpha values near 255 place more weight on the shape color.</span></span>  
  
## <a name="example"></a><span data-ttu-id="0e745-109">Exemplo</span><span class="sxs-lookup"><span data-stu-id="0e745-109">Example</span></span>  
 <span data-ttu-id="0e745-110">O exemplo a seguir desenha um bitmap e, em seguida, preenche três elipses que sobrepõem o bitmap.</span><span class="sxs-lookup"><span data-stu-id="0e745-110">The following example draws a bitmap and then fills three ellipses that overlap the bitmap.</span></span> <span data-ttu-id="0e745-111">A primeira elipse usa um componente alfa de 255, portanto, é opaca.</span><span class="sxs-lookup"><span data-stu-id="0e745-111">The first ellipse uses an alpha component of 255, so it is opaque.</span></span> <span data-ttu-id="0e745-112">As segunda e terceira elipses usam um componente alfa de 128, para que sejam semitransparentes; É possível ver a imagem da tela de fundo pelas elipses.</span><span class="sxs-lookup"><span data-stu-id="0e745-112">The second and third ellipses use an alpha component of 128, so they are semitransparent; you can see the background image through the ellipses.</span></span> <span data-ttu-id="0e745-113">A chamada que <xref:System.Drawing.Graphics.CompositingQuality%2A> define a propriedade faz com que a mistura para a terceira elipse seja feita em conjunto com a correção gama.</span><span class="sxs-lookup"><span data-stu-id="0e745-113">The call that sets the <xref:System.Drawing.Graphics.CompositingQuality%2A> property causes the blending for the third ellipse to be done in conjunction with gamma correction.</span></span>  

 [!code-csharp[System.Drawing.AlphaBlending#31](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.AlphaBlending/CS/Class1.cs#31)]
 [!code-vb[System.Drawing.AlphaBlending#31](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.AlphaBlending/VB/Class1.vb#31)]  

 <span data-ttu-id="0e745-114">A ilustração a seguir mostra a saída do seguinte código:</span><span class="sxs-lookup"><span data-stu-id="0e745-114">The following illustration shows the output of the following code:</span></span>
  
 ![Ilustração que mostra saída opaca e semitransparente.](./media/how-to-draw-with-opaque-and-semitransparent-brushes/compositingquality-ellipse-semitransparent.png)  
  
## <a name="compiling-the-code"></a><span data-ttu-id="0e745-116">Compilando o código</span><span class="sxs-lookup"><span data-stu-id="0e745-116">Compiling the Code</span></span>  
 <span data-ttu-id="0e745-117">O exemplo anterior foi projetado para ser <xref:System.Windows.Forms.PaintEventArgs> `e`usado com formulários <xref:System.Windows.Forms.PaintEventHandler>do Windows, e requer , que é um parâmetro de .</span><span class="sxs-lookup"><span data-stu-id="0e745-117">The preceding example is designed for use with Windows Forms, and it requires <xref:System.Windows.Forms.PaintEventArgs> `e`, which is a parameter of <xref:System.Windows.Forms.PaintEventHandler>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0e745-118">Confira também</span><span class="sxs-lookup"><span data-stu-id="0e745-118">See also</span></span>

- [<span data-ttu-id="0e745-119">Elementos gráficos e desenho no Windows Forms</span><span class="sxs-lookup"><span data-stu-id="0e745-119">Graphics and Drawing in Windows Forms</span></span>](graphics-and-drawing-in-windows-forms.md)
- [<span data-ttu-id="0e745-120">Combinação Alfa em Linhas e Preenchimentos</span><span class="sxs-lookup"><span data-stu-id="0e745-120">Alpha Blending Lines and Fills</span></span>](alpha-blending-lines-and-fills.md)
- [<span data-ttu-id="0e745-121">Como dar ao controle um plano de fundo transparente</span><span class="sxs-lookup"><span data-stu-id="0e745-121">How to: Give Your Control a Transparent Background</span></span>](../controls/how-to-give-your-control-a-transparent-background.md)
- [<span data-ttu-id="0e745-122">Como desenhar linhas opacas e semitransparentes</span><span class="sxs-lookup"><span data-stu-id="0e745-122">How to: Draw Opaque and Semitransparent Lines</span></span>](how-to-draw-opaque-and-semitransparent-lines.md)
