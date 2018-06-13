---
title: Como usar o modo de composição para controlar a combinação alfa
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- alpha blending [Windows Forms], compositing
- colors [Windows Forms], blending
- colors [Windows Forms], controlling transparency
ms.assetid: f331df2d-b395-4b0a-95be-24fec8c9bbb5
ms.openlocfilehash: 55c6db1029c6823652ac29fca46f6f8dc4ec40d0
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33526996"
---
# <a name="how-to-use-compositing-mode-to-control-alpha-blending"></a><span data-ttu-id="831d9-102">Como usar o modo de composição para controlar a combinação alfa</span><span class="sxs-lookup"><span data-stu-id="831d9-102">How to: Use Compositing Mode to Control Alpha Blending</span></span>
<span data-ttu-id="831d9-103">Pode haver ocasiões em que é útil criar um bitmap fora da tela com as seguintes características:</span><span class="sxs-lookup"><span data-stu-id="831d9-103">There may be times when you want to create an off-screen bitmap that has the following characteristics:</span></span>  
  
-   <span data-ttu-id="831d9-104">Cores com valores alfabéticos inferiores a 255.</span><span class="sxs-lookup"><span data-stu-id="831d9-104">Colors have alpha values that are less than 255.</span></span>  
  
-   <span data-ttu-id="831d9-105">As cores não têm combinação alfa umas com as outras ao criar o bitmap.</span><span class="sxs-lookup"><span data-stu-id="831d9-105">Colors are not alpha blended with each other as you create the bitmap.</span></span>  
  
-   <span data-ttu-id="831d9-106">Ao exibir o bitmap terminado, as cores no bitmap são combinadas em alfo com as cores da tela de fundo no dispositivo de vídeo.</span><span class="sxs-lookup"><span data-stu-id="831d9-106">When you display the finished bitmap, colors in the bitmap are alpha blended with the background colors on the display device.</span></span>  
  
 <span data-ttu-id="831d9-107">Para criar esse bitmap, construir um espaço em branco <xref:System.Drawing.Bitmap> de objeto e, em seguida, criar um <xref:System.Drawing.Graphics> objeto com base no que bitmap.</span><span class="sxs-lookup"><span data-stu-id="831d9-107">To create such a bitmap, construct a blank <xref:System.Drawing.Bitmap> object, and then construct a <xref:System.Drawing.Graphics> object based on that bitmap.</span></span> <span data-ttu-id="831d9-108">Definir o modo de composição do <xref:System.Drawing.Graphics> do objeto para <xref:System.Drawing.Drawing2D.CompositingMode.SourceCopy?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="831d9-108">Set the compositing mode of the <xref:System.Drawing.Graphics> object to <xref:System.Drawing.Drawing2D.CompositingMode.SourceCopy?displayProperty=nameWithType>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="831d9-109">Exemplo</span><span class="sxs-lookup"><span data-stu-id="831d9-109">Example</span></span>  
 <span data-ttu-id="831d9-110">O exemplo a seguir cria um <xref:System.Drawing.Graphics> objeto com base em um <xref:System.Drawing.Bitmap> objeto.</span><span class="sxs-lookup"><span data-stu-id="831d9-110">The following example creates a <xref:System.Drawing.Graphics> object based on a <xref:System.Drawing.Bitmap> object.</span></span> <span data-ttu-id="831d9-111">O código usa o <xref:System.Drawing.Graphics> objeto juntamente com dois pincéis semitransparentes (alfa = 160) para pintar o bitmap.</span><span class="sxs-lookup"><span data-stu-id="831d9-111">The code uses the <xref:System.Drawing.Graphics> object along with two semitransparent brushes (alpha = 160) to paint on the bitmap.</span></span> <span data-ttu-id="831d9-112">O código preenche uma elipse vermelha e uma elipse verde usando os pincéis semitransparentes.</span><span class="sxs-lookup"><span data-stu-id="831d9-112">The code fills a red ellipse and a green ellipse using the semitransparent brushes.</span></span> <span data-ttu-id="831d9-113">Elipse verde se sobrepõe a elipse vermelha, mas não verde é combinado com o red porque o modo de composição do <xref:System.Drawing.Graphics> objeto é definido como <xref:System.Drawing.Drawing2D.CompositingMode.SourceCopy>.</span><span class="sxs-lookup"><span data-stu-id="831d9-113">The green ellipse overlaps the red ellipse, but the green is not blended with the red because the compositing mode of the <xref:System.Drawing.Graphics> object is set to <xref:System.Drawing.Drawing2D.CompositingMode.SourceCopy>.</span></span>  
  
 <span data-ttu-id="831d9-114">O código desenha o bitmap na tela duas vezes: uma vez em uma tela de fundo branca e uma vez em uma tela de fundo multicolorida.</span><span class="sxs-lookup"><span data-stu-id="831d9-114">The code draws the bitmap on the screen twice: once on a white background and once on a multicolored background.</span></span> <span data-ttu-id="831d9-115">Os pixels no bitmap que fazem parte das duas elipses têm um componente alfa de 160, de forma que as elipses são mescladas com as cores da tela de fundo na tela.</span><span class="sxs-lookup"><span data-stu-id="831d9-115">The pixels in the bitmap that are part of the two ellipses have an alpha component of 160, so the ellipses are blended with the background colors on the screen.</span></span>  
  
 <span data-ttu-id="831d9-116">A ilustração a seguir mostra a saída do código de exemplo.</span><span class="sxs-lookup"><span data-stu-id="831d9-116">The following illustration shows the output of the code example.</span></span> <span data-ttu-id="831d9-117">Observe que as elipses são mescladas com a tela de fundo, mas elas não são mescladas uma com a outra.</span><span class="sxs-lookup"><span data-stu-id="831d9-117">Note that the ellipses are blended with the background, but they are not blended with each other.</span></span>  
  
 <span data-ttu-id="831d9-118">![Cópia de origem](../../../../docs/framework/winforms/advanced/media/sourcecopy.png "sourcecopy")</span><span class="sxs-lookup"><span data-stu-id="831d9-118">![Source Copy](../../../../docs/framework/winforms/advanced/media/sourcecopy.png "sourcecopy")</span></span>  
  
 <span data-ttu-id="831d9-119">O exemplo de código contém esta instrução:</span><span class="sxs-lookup"><span data-stu-id="831d9-119">The code example contains this statement:</span></span>  
  
 [!code-csharp[System.Drawing.AlphaBlending#41](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.AlphaBlending/CS/Class1.cs#41)]
 [!code-vb[System.Drawing.AlphaBlending#41](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.AlphaBlending/VB/Class1.vb#41)]  
  
 <span data-ttu-id="831d9-120">Se desejar que as elipses sejam mescladas entre si e com a tela de fundo, altere essa instrução para o seguinte:</span><span class="sxs-lookup"><span data-stu-id="831d9-120">If you want the ellipses to be blended with each other as well as with the background, change that statement to the following:</span></span>  
  
 [!code-csharp[System.Drawing.AlphaBlending#42](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.AlphaBlending/CS/Class1.cs#42)]
 [!code-vb[System.Drawing.AlphaBlending#42](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.AlphaBlending/VB/Class1.vb#42)]  
  
 <span data-ttu-id="831d9-121">A ilustração a seguir mostra a saída do código revisado.</span><span class="sxs-lookup"><span data-stu-id="831d9-121">The following illustration shows the output of the revised code.</span></span>  
  
 <span data-ttu-id="831d9-122">![Origem sobre](../../../../docs/framework/winforms/advanced/media/sourceover.png "sourceover")</span><span class="sxs-lookup"><span data-stu-id="831d9-122">![Source Over](../../../../docs/framework/winforms/advanced/media/sourceover.png "sourceover")</span></span>  
  
 [!code-csharp[System.Drawing.AlphaBlending#43](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.AlphaBlending/CS/Class1.cs#43)]
 [!code-vb[System.Drawing.AlphaBlending#43](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.AlphaBlending/VB/Class1.vb#43)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="831d9-123">Compilando o código</span><span class="sxs-lookup"><span data-stu-id="831d9-123">Compiling the Code</span></span>  
 <span data-ttu-id="831d9-124">O exemplo anterior é projetado para uso com o Windows Forms e requer <xref:System.Windows.Forms.PaintEventArgs> `e`, que é um parâmetro de <xref:System.Windows.Forms.PaintEventHandler>.</span><span class="sxs-lookup"><span data-stu-id="831d9-124">The preceding example is designed for use with Windows Forms, and it requires <xref:System.Windows.Forms.PaintEventArgs>`e`, which is a parameter of <xref:System.Windows.Forms.PaintEventHandler>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="831d9-125">Consulte também</span><span class="sxs-lookup"><span data-stu-id="831d9-125">See Also</span></span>  
 <xref:System.Drawing.Color.FromArgb%2A>  
 [<span data-ttu-id="831d9-126">Combinação Alfa em Linhas e Preenchimentos</span><span class="sxs-lookup"><span data-stu-id="831d9-126">Alpha Blending Lines and Fills</span></span>](../../../../docs/framework/winforms/advanced/alpha-blending-lines-and-fills.md)
