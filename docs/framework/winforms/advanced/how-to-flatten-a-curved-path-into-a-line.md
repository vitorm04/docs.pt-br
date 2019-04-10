---
title: 'Como: nivelar um caminho curvo em uma linha'
ms.date: 03/30/2017
helpviewer_keywords:
- graphics [Windows Forms], flattening curves into lines
- curves [Windows Forms], flattening
- GraphicsPath object
- paths [Windows Forms], flattening
- drawing [Windows Forms], flattening curves
ms.assetid: e654b8de-25f4-4735-9208-42e4514a589c
ms.openlocfilehash: a151b4244e14d3704fd5fa1c55de92211981232f
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59215151"
---
# <a name="how-to-flatten-a-curved-path-into-a-line"></a>Como: nivelar um caminho curvo em uma linha
Um <xref:System.Drawing.Drawing2D.GraphicsPath> objeto armazena uma sequência de linhas e splines de Bézier. Você pode adicionar vários tipos de curvas (elipses, arcos, splines cardinais) para um caminho, mas cada curva é convertida em uma spline de Bézier antes de serem armazenado no caminho. Mesclar um caminho consiste em converter cada spline de Bézier no caminho em uma sequência de linhas retas. A ilustração a seguir mostra um caminho de antes e depois do ajuste.  
  
 ![Linhas retas e curvas](./media/aboutgdip02-art32a.gif "AboutGdip02_Art32A")  
  
### <a name="to-flatten-a-path"></a>Para mesclar um caminho  
  
-   Chame o <xref:System.Drawing.Drawing2D.GraphicsPath.Flatten%2A> método de um <xref:System.Drawing.Drawing2D.GraphicsPath> objeto. O <xref:System.Drawing.Drawing2D.GraphicsPath.Flatten%2A> método recebe um argumento de planeza que especifica a distância máxima entre o caminho mesclado e o caminho original.  
  
## <a name="see-also"></a>Consulte também

- <xref:System.Drawing.Drawing2D.GraphicsPath?displayProperty=nameWithType>
- [Linhas, curvas e formas](lines-curves-and-shapes.md)
- [Construindo e desenhando demarcadores](constructing-and-drawing-paths.md)
