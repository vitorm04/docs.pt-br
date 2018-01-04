---
title: "Suavização com linhas e curvas"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- antialiasing
- antialiasing [Windows Forms], smoothing modes
- GDI+, antialiasing
ms.assetid: 810da1a4-c136-4abf-88df-68e49efdd8d4
caps.latest.revision: "16"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: b8552f185a93b688555dbcfab3da9d28d9bfde6d
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="antialiasing-with-lines-and-curves"></a><span data-ttu-id="fe5c3-102">Suavização com linhas e curvas</span><span class="sxs-lookup"><span data-stu-id="fe5c3-102">Antialiasing with Lines and Curves</span></span>
<span data-ttu-id="fe5c3-103">Ao usar [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] para desenhar uma linha, você deverá fornecer o ponto inicial e final da linha, mas não será necessário fornecer todas as informações sobre os pixels individuais nela.</span><span class="sxs-lookup"><span data-stu-id="fe5c3-103">When you use [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] to draw a line, you provide the starting point and ending point of the line, but you do not have to provide any information about the individual pixels on the line.</span></span> [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)]<span data-ttu-id="fe5c3-104"> funciona junto com o software de driver de vídeo para determinar quais pixels serão ativados para mostrar a linha em um dispositivo de vídeo específico.</span><span class="sxs-lookup"><span data-stu-id="fe5c3-104"> works in conjunction with the display driver software to determine which pixels will be turned on to show the line on a particular display device.</span></span>  
  
## <a name="aliasing"></a><span data-ttu-id="fe5c3-105">Serrilhado</span><span class="sxs-lookup"><span data-stu-id="fe5c3-105">Aliasing</span></span>  
 <span data-ttu-id="fe5c3-106">Considere a linha reta vermelha que vai do ponto (4, 2) até o ponto (16, 10).</span><span class="sxs-lookup"><span data-stu-id="fe5c3-106">Consider the straight red line that goes from the point (4, 2) to the point (16, 10).</span></span> <span data-ttu-id="fe5c3-107">Suponha que o sistema de coordenadas tem sua origem no canto superior esquerdo e que a unidade de medida é o pixel.</span><span class="sxs-lookup"><span data-stu-id="fe5c3-107">Assume the coordinate system has its origin in the upper-left corner and that the unit of measure is the pixel.</span></span> <span data-ttu-id="fe5c3-108">Suponha também que o eixo X aponta para a direita e o eixo Y aponta para baixo.</span><span class="sxs-lookup"><span data-stu-id="fe5c3-108">Also assume that the x-axis points to the right and the y-axis points down.</span></span> <span data-ttu-id="fe5c3-109">A ilustração a seguir mostra uma exibição ampliada da linha vermelha desenhada em uma tela de fundo multicolorida.</span><span class="sxs-lookup"><span data-stu-id="fe5c3-109">The following illustration shows an enlarged view of the red line drawn on a multicolored background.</span></span>  
  
 <span data-ttu-id="fe5c3-110">![Linha, sem suavização](../../../../docs/framework/winforms/advanced/media/aboutgdip02-art33.gif "AboutGdip02_Art33")</span><span class="sxs-lookup"><span data-stu-id="fe5c3-110">![Line, no antialiasing](../../../../docs/framework/winforms/advanced/media/aboutgdip02-art33.gif "AboutGdip02_Art33")</span></span>  
  
 <span data-ttu-id="fe5c3-111">Os pixels vermelhos usados para renderizar a linha são opacos.</span><span class="sxs-lookup"><span data-stu-id="fe5c3-111">The red pixels used to render the line are opaque.</span></span> <span data-ttu-id="fe5c3-112">Não existem pixels parcialmente transparentes na linha.</span><span class="sxs-lookup"><span data-stu-id="fe5c3-112">There are no partially transparent pixels in the line.</span></span> <span data-ttu-id="fe5c3-113">Esse tipo de processamento de linha dá a esta uma aparência denteada, fazendo com que se pareça com uma escada.</span><span class="sxs-lookup"><span data-stu-id="fe5c3-113">This type of line rendering gives the line a jagged appearance, and the line looks somewhat like a staircase.</span></span> <span data-ttu-id="fe5c3-114">Essa técnica de representar uma linha com uma escada é chamada de serrilhado; a escada é um alias para a linha teórica.</span><span class="sxs-lookup"><span data-stu-id="fe5c3-114">This technique of representing a line with a staircase is called aliasing; the staircase is an alias for the theoretical line.</span></span>  
  
## <a name="antialiasing"></a><span data-ttu-id="fe5c3-115">Suavização</span><span class="sxs-lookup"><span data-stu-id="fe5c3-115">Antialiasing</span></span>  
 <span data-ttu-id="fe5c3-116">Uma técnica mais sofisticada para renderizar uma linha envolve o uso de pixels parcialmente transparentes junto com pixels opacos.</span><span class="sxs-lookup"><span data-stu-id="fe5c3-116">A more sophisticated technique for rendering a line involves using partially transparent pixels along with opaque pixels.</span></span> <span data-ttu-id="fe5c3-117">Pixels são definidas como vermelho puro ou como uma mistura de vermelho e a cor da tela de fundo, dependendo da sua proximidade da linha.</span><span class="sxs-lookup"><span data-stu-id="fe5c3-117">Pixels are set to pure red, or to some blend of red and the background color, depending on how close they are to the line.</span></span> <span data-ttu-id="fe5c3-118">Esse tipo de renderização é chamado de suavização e resulta em uma linha que o olho humano percebe como mais suave.</span><span class="sxs-lookup"><span data-stu-id="fe5c3-118">This type of rendering is called antialiasing and results in a line that the human eye perceives as more smooth.</span></span> <span data-ttu-id="fe5c3-119">A ilustração a seguir mostra como determinados pixels são mesclados com a tela de fundo para produzir uma linha suavizada.</span><span class="sxs-lookup"><span data-stu-id="fe5c3-119">The following illustration shows how certain pixels are blended with the background to produce an antialiased line.</span></span>  
  
 <span data-ttu-id="fe5c3-120">![Suavizando uma linha](../../../../docs/framework/winforms/advanced/media/aboutgdip02-art34.gif "AboutGdip02_Art34")</span><span class="sxs-lookup"><span data-stu-id="fe5c3-120">![Antialiasing a Line](../../../../docs/framework/winforms/advanced/media/aboutgdip02-art34.gif "AboutGdip02_Art34")</span></span>  
  
 <span data-ttu-id="fe5c3-121">A suavização, também chamada de antialiasing, também pode ser aplicada a curvas.</span><span class="sxs-lookup"><span data-stu-id="fe5c3-121">Antialiasing, also called smoothing, can also be applied to curves.</span></span> <span data-ttu-id="fe5c3-122">A ilustração a seguir mostra uma exibição ampliada de uma elipse suavizada.</span><span class="sxs-lookup"><span data-stu-id="fe5c3-122">The following illustration shows an enlarged view of a smoothed ellipse.</span></span>  
  
 <span data-ttu-id="fe5c3-123">![Suavização de curvas](../../../../docs/framework/winforms/advanced/media/aboutgdip02-art35.gif "AboutGdip02_Art35")</span><span class="sxs-lookup"><span data-stu-id="fe5c3-123">![Antialiasing Curves](../../../../docs/framework/winforms/advanced/media/aboutgdip02-art35.gif "AboutGdip02_Art35")</span></span>  
  
 <span data-ttu-id="fe5c3-124">A ilustração a seguir mostra a mesma elipse em seu tamanho real, uma vez sem suavização e outra com suavização.</span><span class="sxs-lookup"><span data-stu-id="fe5c3-124">The following illustration shows the same ellipse in its actual size, once without antialiasing and once with antialiasing.</span></span>  
  
 <span data-ttu-id="fe5c3-125">![Exemplo de suavização](../../../../docs/framework/winforms/advanced/media/aboutgdip02-art36.gif "AboutGdip02_Art36")</span><span class="sxs-lookup"><span data-stu-id="fe5c3-125">![Antialiasing example](../../../../docs/framework/winforms/advanced/media/aboutgdip02-art36.gif "AboutGdip02_Art36")</span></span>  
  
 <span data-ttu-id="fe5c3-126">Para desenhar linhas e curvas que usam suavização, crie uma instância do <xref:System.Drawing.Graphics> de classe e defina seu <xref:System.Drawing.Graphics.SmoothingMode%2A> propriedade <xref:System.Drawing.Drawing2D.SmoothingMode.AntiAlias> ou <xref:System.Drawing.Drawing2D.SmoothingMode.HighQuality>.</span><span class="sxs-lookup"><span data-stu-id="fe5c3-126">To draw lines and curves that use antialiasing, create an instance of the <xref:System.Drawing.Graphics> class and set its <xref:System.Drawing.Graphics.SmoothingMode%2A> property to <xref:System.Drawing.Drawing2D.SmoothingMode.AntiAlias> or <xref:System.Drawing.Drawing2D.SmoothingMode.HighQuality>.</span></span> <span data-ttu-id="fe5c3-127">Em seguida, chame um dos métodos de desenho do mesmo <xref:System.Drawing.Graphics> classe.</span><span class="sxs-lookup"><span data-stu-id="fe5c3-127">Then call one of the drawing methods of that same <xref:System.Drawing.Graphics> class.</span></span>  
  
 [!code-csharp[LinesCurvesAndShapes#81](../../../../samples/snippets/csharp/VS_Snippets_Winforms/LinesCurvesAndShapes/CS/Class1.cs#81)]
 [!code-vb[LinesCurvesAndShapes#81](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/LinesCurvesAndShapes/VB/Class1.vb#81)]  
  
## <a name="see-also"></a><span data-ttu-id="fe5c3-128">Consulte também</span><span class="sxs-lookup"><span data-stu-id="fe5c3-128">See Also</span></span>  
 <xref:System.Drawing.Drawing2D.SmoothingMode?displayProperty=nameWithType>  
 [<span data-ttu-id="fe5c3-129">Linhas, Curvas e Formas</span><span class="sxs-lookup"><span data-stu-id="fe5c3-129">Lines, Curves, and Shapes</span></span>](../../../../docs/framework/winforms/advanced/lines-curves-and-shapes.md)  
 [<span data-ttu-id="fe5c3-130">Como usar suavização com texto</span><span class="sxs-lookup"><span data-stu-id="fe5c3-130">How to: Use Antialiasing with Text</span></span>](../../../../docs/framework/winforms/advanced/how-to-use-antialiasing-with-text.md)
