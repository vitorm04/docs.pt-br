---
title: "Combinação alfa em linhas e preenchimentos"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- lines [Windows Forms], adding transparency
- examples [Windows Forms], alpha blending
- alpha blending [Windows Forms], using with lines
- alpha blending
- lines [Windows Forms], alpha blending
- fills [Windows Forms], alpha blending
- alpha blending [Windows Forms], using with fills
- shapes [Windows Forms], adding transparency
ms.assetid: 5440f48c-3ac9-44c3-b170-c1c110bdbab8
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 2a46efeccf9ab343ca0da07fad07138bd72e4e44
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="alpha-blending-lines-and-fills"></a><span data-ttu-id="0582c-102">Combinação alfa em linhas e preenchimentos</span><span class="sxs-lookup"><span data-stu-id="0582c-102">Alpha Blending Lines and Fills</span></span>
<span data-ttu-id="0582c-103">No [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)], uma cor é um valor de 32 bits com 8 bits cada para alfa, vermelho, verde e azul.</span><span class="sxs-lookup"><span data-stu-id="0582c-103">In [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)], a color is a 32-bit value with 8 bits each for alpha, red, green, and blue.</span></span> <span data-ttu-id="0582c-104">O valor alfa indica a transparência da cor – a extensão a qual a cor é combinada com a cor da tela de fundo.</span><span class="sxs-lookup"><span data-stu-id="0582c-104">The alpha value indicates the transparency of the color — the extent to which the color is blended with the background color.</span></span> <span data-ttu-id="0582c-105">Os valores alfa variam de 0 a 255, em que 0 representa uma cor totalmente transparente e 255 representa uma cor totalmente opaca.</span><span class="sxs-lookup"><span data-stu-id="0582c-105">Alpha values range from 0 through 255, where 0 represents a fully transparent color, and 255 represents a fully opaque color.</span></span>  
  
 <span data-ttu-id="0582c-106">A combinação alfa é uma combinação de pixel por pixel da fonte e dos dados de cor da tela de fundo.</span><span class="sxs-lookup"><span data-stu-id="0582c-106">Alpha blending is a pixel-by-pixel blending of source and background color data.</span></span> <span data-ttu-id="0582c-107">Cada um dos três componentes (vermelho, verde, azul) de uma cor de origem é combinado com o componente correspondente da cor da tela de fundo de acordo com a seguinte fórmula:</span><span class="sxs-lookup"><span data-stu-id="0582c-107">Each of the three components (red, green, blue) of a given source color is blended with the corresponding component of the background color according to the following formula:</span></span>  
  
 <span data-ttu-id="0582c-108">displayColor = sourceColor × alfa / 255 + backgroundColor × (255 – alfa) / 255</span><span class="sxs-lookup"><span data-stu-id="0582c-108">displayColor = sourceColor × alpha / 255 + backgroundColor × (255 – alpha) / 255</span></span>  
  
 <span data-ttu-id="0582c-109">Por exemplo, suponha que o componente vermelho da cor da fonte é 150 e o componente vermelho da cor da tela de fundo é 100.</span><span class="sxs-lookup"><span data-stu-id="0582c-109">For example, suppose the red component of the source color is 150 and the red component of the background color is 100.</span></span> <span data-ttu-id="0582c-110">Se o valor alfa for 200, o componente vermelho da cor resultante será calculado da seguinte maneira:</span><span class="sxs-lookup"><span data-stu-id="0582c-110">If the alpha value is 200, the red component of the resultant color is calculated as follows:</span></span>  
  
 <span data-ttu-id="0582c-111">150 × 200 / 255 + 100 × (255 – 200) / 255 = 139</span><span class="sxs-lookup"><span data-stu-id="0582c-111">150 × 200 / 255 + 100 × (255 – 200) / 255 = 139</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="0582c-112">Nesta seção</span><span class="sxs-lookup"><span data-stu-id="0582c-112">In This Section</span></span>  
 [<span data-ttu-id="0582c-113">Como Desenhar Linhas Opacas e Semitransparentes</span><span class="sxs-lookup"><span data-stu-id="0582c-113">How to: Draw Opaque and Semitransparent Lines</span></span>](../../../../docs/framework/winforms/advanced/how-to-draw-opaque-and-semitransparent-lines.md)  
 <span data-ttu-id="0582c-114">Mostra como desenhar linhas com combinação alfa.</span><span class="sxs-lookup"><span data-stu-id="0582c-114">Shows how to draw alpha-blended lines.</span></span>  
  
 [<span data-ttu-id="0582c-115">Como Desenhar com Pincéis Opacos e Semitransparentes</span><span class="sxs-lookup"><span data-stu-id="0582c-115">How to: Draw with Opaque and Semitransparent Brushes</span></span>](../../../../docs/framework/winforms/advanced/how-to-draw-with-opaque-and-semitransparent-brushes.md)  
 <span data-ttu-id="0582c-116">Explica como fazer a combinação alfa com pincéis.</span><span class="sxs-lookup"><span data-stu-id="0582c-116">Explains how to alpha-blend with brushes.</span></span>  
  
 [<span data-ttu-id="0582c-117">Como Usar o Modo de Composição para Controlar a Combinação Alfa</span><span class="sxs-lookup"><span data-stu-id="0582c-117">How to: Use Compositing Mode to Control Alpha Blending</span></span>](../../../../docs/framework/winforms/advanced/how-to-use-compositing-mode-to-control-alpha-blending.md)  
 <span data-ttu-id="0582c-118">Descreve como controlar a combinação alfa usando <xref:System.Drawing.Drawing2D.CompositingMode>.</span><span class="sxs-lookup"><span data-stu-id="0582c-118">Describes how to control alpha blending using <xref:System.Drawing.Drawing2D.CompositingMode>.</span></span>  
  
 [<span data-ttu-id="0582c-119">Como Usar uma Matriz de Cores para Definir Valores Alfa em Imagens</span><span class="sxs-lookup"><span data-stu-id="0582c-119">How to: Use a Color Matrix to Set Alpha Values in Images</span></span>](../../../../docs/framework/winforms/advanced/how-to-use-a-color-matrix-to-set-alpha-values-in-images.md)  
 <span data-ttu-id="0582c-120">Explica como usar um <xref:System.Drawing.Imaging.ColorMatrix> objeto para controlar a combinação alfa.</span><span class="sxs-lookup"><span data-stu-id="0582c-120">Explains how to use a <xref:System.Drawing.Imaging.ColorMatrix> object to control alpha blending.</span></span>
