---
title: 'Como: Nivelar um demarcador curvo em uma linha'
ms.date: 03/30/2017
helpviewer_keywords:
- graphics [Windows Forms], flattening curves into lines
- curves [Windows Forms], flattening
- GraphicsPath object
- paths [Windows Forms], flattening
- drawing [Windows Forms], flattening curves
ms.assetid: e654b8de-25f4-4735-9208-42e4514a589c
ms.openlocfilehash: d4847124c7af2e0b35d6874f53b85be4891b22df
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/09/2019
ms.locfileid: "57711038"
---
# <a name="how-to-flatten-a-curved-path-into-a-line"></a>Como: Nivelar um demarcador curvo em uma linha
Um <xref:System.Drawing.Drawing2D.GraphicsPath> objeto armazena uma sequência de linhas e splines de Bézier. Você pode adicionar vários tipos de curvas (elipses, arcos, splines cardinais) para um caminho, mas cada curva é convertida em uma spline de Bézier antes de serem armazenado no caminho. Mesclar um caminho consiste em converter cada spline de Bézier no caminho em uma sequência de linhas retas. A ilustração a seguir mostra um caminho de antes e depois do ajuste.  
  
 ![Linhas retas e curvas](./media/aboutgdip02-art32a.gif "AboutGdip02_Art32A")  
  
### <a name="to-flatten-a-path"></a>Para mesclar um caminho  
  
-   Chame o <xref:System.Drawing.Drawing2D.GraphicsPath.Flatten%2A> método de um <xref:System.Drawing.Drawing2D.GraphicsPath> objeto. O <xref:System.Drawing.Drawing2D.GraphicsPath.Flatten%2A> método recebe um argumento de planeza que especifica a distância máxima entre o caminho mesclado e o caminho original.  
  
## <a name="see-also"></a>Consulte também
- <xref:System.Drawing.Drawing2D.GraphicsPath?displayProperty=nameWithType>
- [Linhas, Curvas e Formas](lines-curves-and-shapes.md)
- [Construindo e desenhando demarcadores](constructing-and-drawing-paths.md)
