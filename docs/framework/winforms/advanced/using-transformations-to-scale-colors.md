---
title: Usando transformações para ajustar a escala de cores
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- transformations [Windows Forms], for scaling colors
- colors [Windows Forms], scaling
ms.assetid: df23c887-7fd6-4b15-ad94-e30b5bd4b849
ms.openlocfilehash: 9c8f2392137d04f56096120cec64b60c42c47419
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59107972"
---
# <a name="using-transformations-to-scale-colors"></a><span data-ttu-id="38c58-102">Usando transformações para ajustar a escala de cores</span><span class="sxs-lookup"><span data-stu-id="38c58-102">Using Transformations to Scale Colors</span></span>
<span data-ttu-id="38c58-103">Uma transformação de dimensionamento multiplica um ou mais dos quatro componentes de cor por um número.</span><span class="sxs-lookup"><span data-stu-id="38c58-103">A scaling transformation multiplies one or more of the four color components by a number.</span></span> <span data-ttu-id="38c58-104">As entradas de matriz de cores que representam o dimensionamento são dadas na tabela a seguir.</span><span class="sxs-lookup"><span data-stu-id="38c58-104">The color matrix entries that represent scaling are given in the following table.</span></span>  
  
|<span data-ttu-id="38c58-105">Componentes que serão escalados</span><span class="sxs-lookup"><span data-stu-id="38c58-105">Component to be scaled</span></span>|<span data-ttu-id="38c58-106">Entrada de matriz</span><span class="sxs-lookup"><span data-stu-id="38c58-106">Matrix entry</span></span>|  
|----------------------------|------------------|  
|<span data-ttu-id="38c58-107">Vermelho</span><span class="sxs-lookup"><span data-stu-id="38c58-107">Red</span></span>|<span data-ttu-id="38c58-108">[0][0]</span><span class="sxs-lookup"><span data-stu-id="38c58-108">[0][0]</span></span>|  
|<span data-ttu-id="38c58-109">Verde</span><span class="sxs-lookup"><span data-stu-id="38c58-109">Green</span></span>|<span data-ttu-id="38c58-110">[1][1]</span><span class="sxs-lookup"><span data-stu-id="38c58-110">[1][1]</span></span>|  
|<span data-ttu-id="38c58-111">Azul</span><span class="sxs-lookup"><span data-stu-id="38c58-111">Blue</span></span>|<span data-ttu-id="38c58-112">[2][2]</span><span class="sxs-lookup"><span data-stu-id="38c58-112">[2][2]</span></span>|  
|<span data-ttu-id="38c58-113">Alfa</span><span class="sxs-lookup"><span data-stu-id="38c58-113">Alpha</span></span>|<span data-ttu-id="38c58-114">[3][3]</span><span class="sxs-lookup"><span data-stu-id="38c58-114">[3][3]</span></span>|  
  
## <a name="scaling-one-color"></a><span data-ttu-id="38c58-115">Ajustando uma cor</span><span class="sxs-lookup"><span data-stu-id="38c58-115">Scaling One Color</span></span>  
 <span data-ttu-id="38c58-116">O exemplo a seguir constrói um <xref:System.Drawing.Image> objeto do arquivo ColorBars2.bmp.</span><span class="sxs-lookup"><span data-stu-id="38c58-116">The following example constructs an <xref:System.Drawing.Image> object from the file ColorBars2.bmp.</span></span> <span data-ttu-id="38c58-117">Depois o código escala o componente azul de cada pixel na imagem por um fator de 2.</span><span class="sxs-lookup"><span data-stu-id="38c58-117">Then the code scales the blue component of each pixel in the image by a factor of 2.</span></span> <span data-ttu-id="38c58-118">A imagem original é desenhada ao lado da imagem transformada.</span><span class="sxs-lookup"><span data-stu-id="38c58-118">The original image is drawn alongside the transformed image.</span></span>  
  
 [!code-csharp[System.Drawing.RecoloringImages#41](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.RecoloringImages/CS/Class1.cs#41)]
 [!code-vb[System.Drawing.RecoloringImages#41](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.RecoloringImages/VB/Class1.vb#41)]  
  
 <span data-ttu-id="38c58-119">A ilustração a seguir mostra a imagem original à esquerda e a imagem dimensionada à direita:</span><span class="sxs-lookup"><span data-stu-id="38c58-119">The following illustration shows the original image on the left and the scaled image on the right:</span></span>  
  
 ![Captura de tela que compara as cores em escala e originais.](./media/using-transformations-to-scale-colors/four-bar-scale-one-color.png)  
  
 <span data-ttu-id="38c58-121">A tabela a seguir lista os vetores de cores para as quatro barras antes e depois do ajuste de azul.</span><span class="sxs-lookup"><span data-stu-id="38c58-121">The following table lists the color vectors for the four bars before and after the blue scaling.</span></span> <span data-ttu-id="38c58-122">Veja que o componente azul na quarta barra de cores foi de 0,8 para 0,6.</span><span class="sxs-lookup"><span data-stu-id="38c58-122">Note that the blue component in the fourth color bar went from 0.8 to 0.6.</span></span> <span data-ttu-id="38c58-123">O motivo é que [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] retém apenas parte fracionária do resultado.</span><span class="sxs-lookup"><span data-stu-id="38c58-123">That is because [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] retains only the fractional part of the result.</span></span> <span data-ttu-id="38c58-124">Por exemplo, (2)(0,8) = 1,6, e a parte fracionária de 1,6 é 0,6.</span><span class="sxs-lookup"><span data-stu-id="38c58-124">For example, (2)(0.8) = 1.6, and the fractional part of 1.6 is 0.6.</span></span> <span data-ttu-id="38c58-125">Reter apenas a parte fracionária assegura que o resultado esteja sempre no intervalo [0, 1].</span><span class="sxs-lookup"><span data-stu-id="38c58-125">Retaining only the fractional part ensures that the result is always in the interval [0, 1].</span></span>  
  
|<span data-ttu-id="38c58-126">Original</span><span class="sxs-lookup"><span data-stu-id="38c58-126">Original</span></span>|<span data-ttu-id="38c58-127">Em escala</span><span class="sxs-lookup"><span data-stu-id="38c58-127">Scaled</span></span>|  
|--------------|------------|  
|<span data-ttu-id="38c58-128">(0.4, 0.4, 0.4, 1)</span><span class="sxs-lookup"><span data-stu-id="38c58-128">(0.4, 0.4, 0.4, 1)</span></span>|<span data-ttu-id="38c58-129">(0.4, 0.4, 0.8, 1)</span><span class="sxs-lookup"><span data-stu-id="38c58-129">(0.4, 0.4, 0.8, 1)</span></span>|  
|<span data-ttu-id="38c58-130">(0.4, 0.2, 0.2, 1)</span><span class="sxs-lookup"><span data-stu-id="38c58-130">(0.4, 0.2, 0.2, 1)</span></span>|<span data-ttu-id="38c58-131">(0.4, 0.2, 0.4, 1)</span><span class="sxs-lookup"><span data-stu-id="38c58-131">(0.4, 0.2, 0.4, 1)</span></span>|  
|<span data-ttu-id="38c58-132">(0.2, 0.4, 0.2, 1)</span><span class="sxs-lookup"><span data-stu-id="38c58-132">(0.2, 0.4, 0.2, 1)</span></span>|<span data-ttu-id="38c58-133">(0.2, 0.4, 0.4, 1)</span><span class="sxs-lookup"><span data-stu-id="38c58-133">(0.2, 0.4, 0.4, 1)</span></span>|  
|<span data-ttu-id="38c58-134">(0.4, 0.4, 0.8, 1)</span><span class="sxs-lookup"><span data-stu-id="38c58-134">(0.4, 0.4, 0.8, 1)</span></span>|<span data-ttu-id="38c58-135">(0.4, 0.4, 0.6, 1)</span><span class="sxs-lookup"><span data-stu-id="38c58-135">(0.4, 0.4, 0.6, 1)</span></span>|  
  
## <a name="scaling-multiple-colors"></a><span data-ttu-id="38c58-136">Ajustando de várias cores</span><span class="sxs-lookup"><span data-stu-id="38c58-136">Scaling Multiple Colors</span></span>  
 <span data-ttu-id="38c58-137">O exemplo a seguir constrói um <xref:System.Drawing.Image> objeto do arquivo ColorBars2.bmp.</span><span class="sxs-lookup"><span data-stu-id="38c58-137">The following example constructs an <xref:System.Drawing.Image> object from the file ColorBars2.bmp.</span></span> <span data-ttu-id="38c58-138">Depois, o código escala os componentes vermelho, verde e azul de cada pixel na imagem.</span><span class="sxs-lookup"><span data-stu-id="38c58-138">Then the code scales the red, green, and blue components of each pixel in the image.</span></span> <span data-ttu-id="38c58-139">Os componentes vermelhos são reduzidos em 25 por cento, os componentes verdes são reduzidos em 35 por cento e os componentes azuis são reduzidos em 50 por cento.</span><span class="sxs-lookup"><span data-stu-id="38c58-139">The red components are scaled down 25 percent, the green components are scaled down 35 percent, and the blue components are scaled down 50 percent.</span></span>  
  
 [!code-csharp[System.Drawing.RecoloringImages#42](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.RecoloringImages/CS/Class1.cs#42)]
 [!code-vb[System.Drawing.RecoloringImages#42](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.RecoloringImages/VB/Class1.vb#42)]  
  
 <span data-ttu-id="38c58-140">A ilustração a seguir mostra a imagem original à esquerda e a imagem dimensionada à direita:</span><span class="sxs-lookup"><span data-stu-id="38c58-140">The following illustration shows the original image on the left and the scaled image on the right:</span></span>  
  
 ![Captura de tela que compara as cores em escala e originais.](./media/using-transformations-to-scale-colors/four-bar-scale-multiple-colors.png)  
  
 <span data-ttu-id="38c58-142">A tabela a seguir lista os vetores de cor para as quatro barras antes e depois do ajuste de vermelho, verde e azul.</span><span class="sxs-lookup"><span data-stu-id="38c58-142">The following table lists the color vectors for the four bars before and after the red, green and blue scaling.</span></span>  
  
|<span data-ttu-id="38c58-143">Original</span><span class="sxs-lookup"><span data-stu-id="38c58-143">Original</span></span>|<span data-ttu-id="38c58-144">Em escala</span><span class="sxs-lookup"><span data-stu-id="38c58-144">Scaled</span></span>|  
|--------------|------------|  
|<span data-ttu-id="38c58-145">(0.6, 0.6, 0.6, 1)</span><span class="sxs-lookup"><span data-stu-id="38c58-145">(0.6, 0.6, 0.6, 1)</span></span>|<span data-ttu-id="38c58-146">(0.45, 0.39, 0.3, 1)</span><span class="sxs-lookup"><span data-stu-id="38c58-146">(0.45, 0.39, 0.3, 1)</span></span>|  
|<span data-ttu-id="38c58-147">(0, 1, 1, 1)</span><span class="sxs-lookup"><span data-stu-id="38c58-147">(0, 1, 1, 1)</span></span>|<span data-ttu-id="38c58-148">(0, 0.65, 0.5, 1)</span><span class="sxs-lookup"><span data-stu-id="38c58-148">(0, 0.65, 0.5, 1)</span></span>|  
|<span data-ttu-id="38c58-149">(1, 1, 0, 1)</span><span class="sxs-lookup"><span data-stu-id="38c58-149">(1, 1, 0, 1)</span></span>|<span data-ttu-id="38c58-150">(0.75, 0.65, 0, 1)</span><span class="sxs-lookup"><span data-stu-id="38c58-150">(0.75, 0.65, 0, 1)</span></span>|  
|<span data-ttu-id="38c58-151">(1, 0, 1, 1)</span><span class="sxs-lookup"><span data-stu-id="38c58-151">(1, 0, 1, 1)</span></span>|<span data-ttu-id="38c58-152">(0.75, 0, 0.5, 1)</span><span class="sxs-lookup"><span data-stu-id="38c58-152">(0.75, 0, 0.5, 1)</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="38c58-153">Consulte também</span><span class="sxs-lookup"><span data-stu-id="38c58-153">See also</span></span>

- <xref:System.Drawing.Imaging.ColorMatrix>
- <xref:System.Drawing.Imaging.ImageAttributes>
- [<span data-ttu-id="38c58-154">Elementos gráficos e desenho no Windows Forms</span><span class="sxs-lookup"><span data-stu-id="38c58-154">Graphics and Drawing in Windows Forms</span></span>](graphics-and-drawing-in-windows-forms.md)
- [<span data-ttu-id="38c58-155">Recolorindo imagens</span><span class="sxs-lookup"><span data-stu-id="38c58-155">Recoloring Images</span></span>](recoloring-images.md)
