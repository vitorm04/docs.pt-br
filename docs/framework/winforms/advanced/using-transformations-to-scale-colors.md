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
ms.openlocfilehash: 6cfe90cef42086672990c45c99961db3d29c3ff3
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33525961"
---
# <a name="using-transformations-to-scale-colors"></a>Usando transformações para ajustar a escala de cores
Uma transformação de dimensionamento multiplica um ou mais dos quatro componentes de cor por um número. As entradas de matriz de cores que representam o dimensionamento são dadas na tabela a seguir.  
  
|Componentes que serão escalados|Entrada de matriz|  
|----------------------------|------------------|  
|Vermelho|[0][0]|  
|Verde|[1][1]|  
|Azul|[2][2]|  
|Alfa|[3][3]|  
  
## <a name="scaling-one-color"></a>Ajustando uma cor  
 O exemplo a seguir constrói um <xref:System.Drawing.Image> objeto do arquivo ColorBars2.bmp. Depois o código escala o componente azul de cada pixel na imagem por um fator de 2. A imagem original é desenhada ao lado da imagem transformada.  
  
 [!code-csharp[System.Drawing.RecoloringImages#41](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.RecoloringImages/CS/Class1.cs#41)]
 [!code-vb[System.Drawing.RecoloringImages#41](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.RecoloringImages/VB/Class1.vb#41)]  
  
 A ilustração a seguir mostra a imagem original à esquerda e a imagem em escala à direita.  
  
 ![Scale Colors](../../../../docs/framework/winforms/advanced/media/colortrans3.png "colortrans3")  
  
 A tabela a seguir lista os vetores de cores para as quatro barras antes e depois do ajuste de azul. Veja que o componente azul na quarta barra de cores foi de 0,8 para 0,6. O motivo é que [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] retém apenas parte fracionária do resultado. Por exemplo, (2)(0,8) = 1,6, e a parte fracionária de 1,6 é 0,6. Reter apenas a parte fracionária assegura que o resultado esteja sempre no intervalo [0, 1].  
  
|Original|Em escala|  
|--------------|------------|  
|(0.4, 0.4, 0.4, 1)|(0.4, 0.4, 0.8, 1)|  
|(0.4, 0.2, 0.2, 1)|(0.4, 0.2, 0.4, 1)|  
|(0.2, 0.4, 0.2, 1)|(0.2, 0.4, 0.4, 1)|  
|(0.4, 0.4, 0.8, 1)|(0.4, 0.4, 0.6, 1)|  
  
## <a name="scaling-multiple-colors"></a>Ajustando de várias cores  
 O exemplo a seguir constrói um <xref:System.Drawing.Image> objeto do arquivo ColorBars2.bmp. Depois, o código escala os componentes vermelho, verde e azul de cada pixel na imagem. Os componentes vermelhos são reduzidos em 25 por cento, os componentes verdes são reduzidos em 35 por cento e os componentes azuis são reduzidos em 50 por cento.  
  
 [!code-csharp[System.Drawing.RecoloringImages#42](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.RecoloringImages/CS/Class1.cs#42)]
 [!code-vb[System.Drawing.RecoloringImages#42](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.RecoloringImages/VB/Class1.vb#42)]  
  
 A ilustração a seguir mostra a imagem original à esquerda e a imagem em escala à direita.  
  
 ![Scale Colors](../../../../docs/framework/winforms/advanced/media/colortrans4.png "colortrans4")  
  
 A tabela a seguir lista os vetores de cor para as quatro barras antes e depois do ajuste de vermelho, verde e azul.  
  
|Original|Em escala|  
|--------------|------------|  
|(0.6, 0.6, 0.6, 1)|(0.45, 0.39, 0.3, 1)|  
|(0, 1, 1, 1)|(0, 0.65, 0.5, 1)|  
|(1, 1, 0, 1)|(0.75, 0.65, 0, 1)|  
|(1, 0, 1, 1)|(0.75, 0, 0.5, 1)|  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.Drawing.Imaging.ColorMatrix>  
 <xref:System.Drawing.Imaging.ImageAttributes>  
 [Elementos Gráficos e Desenho nos Windows Forms](../../../../docs/framework/winforms/advanced/graphics-and-drawing-in-windows-forms.md)  
 [Recolorindo Imagens](../../../../docs/framework/winforms/advanced/recoloring-images.md)
