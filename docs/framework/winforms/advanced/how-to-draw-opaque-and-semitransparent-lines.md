---
title: 'Como: Desenhar linhas opacas e semitransparentes'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- drawing [Windows Forms], lines
- transparency [Windows Forms], lines
- lines [Windows Forms], drawing alpha blended
- alpha blending [Windows Forms], drawing lines
ms.assetid: 8f2508af-f495-4223-b5cc-646cbbb520eb
ms.openlocfilehash: 6076ebf6cb75aa4fdb5cf5798b642597d8f84c80
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54559041"
---
# <a name="how-to-draw-opaque-and-semitransparent-lines"></a><span data-ttu-id="47cd0-102">Como: Desenhar linhas opacas e semitransparentes</span><span class="sxs-lookup"><span data-stu-id="47cd0-102">How to: Draw Opaque and Semitransparent Lines</span></span>
<span data-ttu-id="47cd0-103">Quando você desenha uma linha, você deve passar uma <xref:System.Drawing.Pen> do objeto para o <xref:System.Drawing.Graphics.DrawLine%2A> método da <xref:System.Drawing.Graphics> classe.</span><span class="sxs-lookup"><span data-stu-id="47cd0-103">When you draw a line, you must pass a <xref:System.Drawing.Pen> object to the <xref:System.Drawing.Graphics.DrawLine%2A> method of the <xref:System.Drawing.Graphics> class.</span></span> <span data-ttu-id="47cd0-104">Um dos parâmetros do <xref:System.Drawing.Pen.%23ctor%2A> construtor é um <xref:System.Drawing.Color> objeto.</span><span class="sxs-lookup"><span data-stu-id="47cd0-104">One of the parameters of the <xref:System.Drawing.Pen.%23ctor%2A> constructor is a <xref:System.Drawing.Color> object.</span></span> <span data-ttu-id="47cd0-105">Para desenhar uma linha opaca, defina o componente alfa da cor como 255.</span><span class="sxs-lookup"><span data-stu-id="47cd0-105">To draw an opaque line, set the alpha component of the color to 255.</span></span> <span data-ttu-id="47cd0-106">Para desenhar uma linha semitransparente, defina o componente alfa para qualquer valor de 1 a 254.</span><span class="sxs-lookup"><span data-stu-id="47cd0-106">To draw a semitransparent line, set the alpha component to any value from 1 through 254.</span></span>  
  
 <span data-ttu-id="47cd0-107">Ao desenhar uma linha semitransparente em uma tela de fundo, a cor da linha é combinada com as cores da tela de fundo.</span><span class="sxs-lookup"><span data-stu-id="47cd0-107">When you draw a semitransparent line over a background, the color of the line is blended with the colors of the background.</span></span> <span data-ttu-id="47cd0-108">O componente alfa especifica como as cores da tela de fundo e da linha são misturadas; valores alfa próximos a 0 colocam mais peso nas cores da tela de fundo e valores alfa próximos a 255 colocam mais peso na cor da linha.</span><span class="sxs-lookup"><span data-stu-id="47cd0-108">The alpha component specifies how the line and background colors are mixed; alpha values near 0 place more weight on the background colors, and alpha values near 255 place more weight on the line color.</span></span>  
  
## <a name="example"></a><span data-ttu-id="47cd0-109">Exemplo</span><span class="sxs-lookup"><span data-stu-id="47cd0-109">Example</span></span>  
 <span data-ttu-id="47cd0-110">O exemplo a seguir desenha um bitmap e, em seguida, desenha três linhas que usam o bitmap como tela de fundo.</span><span class="sxs-lookup"><span data-stu-id="47cd0-110">The following example draws a bitmap and then draws three lines that use the bitmap as a background.</span></span> <span data-ttu-id="47cd0-111">A primeira linha usa um componente alfa de 255, portanto, é opaca.</span><span class="sxs-lookup"><span data-stu-id="47cd0-111">The first line uses an alpha component of 255, so it is opaque.</span></span> <span data-ttu-id="47cd0-112">As segunda e terceira linhas usam um componente alfa de 128, para que sejam semitransparentes. É possível ver a imagem da tela de fundo pelas linhas.</span><span class="sxs-lookup"><span data-stu-id="47cd0-112">The second and third lines use an alpha component of 128, so they are semitransparent; you can see the background image through the lines.</span></span> <span data-ttu-id="47cd0-113">A instrução que define o <xref:System.Drawing.Graphics.CompositingQuality%2A> propriedade faz com que a mesclagem da terceira linha a ser feito em conjunto com a correção gama.</span><span class="sxs-lookup"><span data-stu-id="47cd0-113">The statement that sets the <xref:System.Drawing.Graphics.CompositingQuality%2A> property causes the blending for the third line to be done in conjunction with gamma correction.</span></span>  
  
 <span data-ttu-id="47cd0-114">A seguinte ilustração mostra a saída do código a seguir.</span><span class="sxs-lookup"><span data-stu-id="47cd0-114">The following illustration shows the output of the following code.</span></span>  
  
 <span data-ttu-id="47cd0-115">![Opacas e semitransparentes](../../../../docs/framework/winforms/advanced/media/compqualline.png "compqualline")</span><span class="sxs-lookup"><span data-stu-id="47cd0-115">![Opaque and Semitransparent](../../../../docs/framework/winforms/advanced/media/compqualline.png "compqualline")</span></span>  
  
 [!code-csharp[System.Drawing.AlphaBlending#11](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.AlphaBlending/CS/Class1.cs#11)]
 [!code-vb[System.Drawing.AlphaBlending#11](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.AlphaBlending/VB/Class1.vb#11)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="47cd0-116">Compilando o código</span><span class="sxs-lookup"><span data-stu-id="47cd0-116">Compiling the Code</span></span>  
 <span data-ttu-id="47cd0-117">O exemplo anterior foi projetado para uso com o Windows Forms e requer <xref:System.Windows.Forms.PaintEventArgs> `e`, que é um parâmetro do <xref:System.Windows.Forms.Control.Paint> manipulador de eventos.</span><span class="sxs-lookup"><span data-stu-id="47cd0-117">The preceding example is designed for use with Windows Forms, and it requires <xref:System.Windows.Forms.PaintEventArgs>`e`, which is a parameter of the <xref:System.Windows.Forms.Control.Paint> event handler.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="47cd0-118">Consulte também</span><span class="sxs-lookup"><span data-stu-id="47cd0-118">See also</span></span>
- [<span data-ttu-id="47cd0-119">Combinação Alfa em Linhas e Preenchimentos</span><span class="sxs-lookup"><span data-stu-id="47cd0-119">Alpha Blending Lines and Fills</span></span>](../../../../docs/framework/winforms/advanced/alpha-blending-lines-and-fills.md)
- [<span data-ttu-id="47cd0-120">Como: Dar ao controle uma tela de fundo transparente</span><span class="sxs-lookup"><span data-stu-id="47cd0-120">How to: Give Your Control a Transparent Background</span></span>](../../../../docs/framework/winforms/controls/how-to-give-your-control-a-transparent-background.md)
- [<span data-ttu-id="47cd0-121">Como: Desenhar com pincéis opacos e semitransparentes</span><span class="sxs-lookup"><span data-stu-id="47cd0-121">How to: Draw with Opaque and Semitransparent Brushes</span></span>](../../../../docs/framework/winforms/advanced/how-to-draw-with-opaque-and-semitransparent-brushes.md)
