---
title: Como nivelar um demarcador curvo em uma linha
ms.date: 03/30/2017
helpviewer_keywords:
- graphics [Windows Forms], flattening curves into lines
- curves [Windows Forms], flattening
- GraphicsPath object
- paths [Windows Forms], flattening
- drawing [Windows Forms], flattening curves
ms.assetid: e654b8de-25f4-4735-9208-42e4514a589c
ms.openlocfilehash: a3a8467dc5906a88911672316bb0f2ed3607d3a4
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33521197"
---
# <a name="how-to-flatten-a-curved-path-into-a-line"></a>Como nivelar um demarcador curvo em uma linha
Um <xref:System.Drawing.Drawing2D.GraphicsPath> objeto armazena uma sequência de splines de Bézier e linhas. Você pode adicionar vários tipos de curvas (elipses, arcos, splines cardinais) em um caminho, mas cada curva é convertida em um spline de Bézier antes de ser armazenado no caminho. Mesclar um caminho consiste em converter cada spline de Bézier no caminho em uma sequência de linhas retas. A ilustração a seguir mostra um caminho antes e após mesclar.  
  
 ![Linhas retas e curvas](../../../../docs/framework/winforms/advanced/media/aboutgdip02-art32a.gif "AboutGdip02_Art32A")  
  
### <a name="to-flatten-a-path"></a>Para mesclar um caminho  
  
-   chamar o <xref:System.Drawing.Drawing2D.GraphicsPath.Flatten%2A> método de um <xref:System.Drawing.Drawing2D.GraphicsPath> objeto. O <xref:System.Drawing.Drawing2D.GraphicsPath.Flatten%2A> método recebe um argumento de achatamento que especifica a distância máxima entre o caminho mesclado e o caminho original.  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.Drawing.Drawing2D.GraphicsPath?displayProperty=nameWithType>  
 [Linhas, Curvas e Formas](../../../../docs/framework/winforms/advanced/lines-curves-and-shapes.md)  
 [Construindo e desenhando demarcadores](../../../../docs/framework/winforms/advanced/constructing-and-drawing-paths.md)
