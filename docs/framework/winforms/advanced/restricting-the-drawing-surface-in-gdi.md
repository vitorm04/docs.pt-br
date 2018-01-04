---
title: "Restringindo a superfície de desenho no GDI+"
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
- GDI+, clipping
- clipping [Windows Forms], using GDI+
- GDI+, restricting drawing surface
ms.assetid: 8b5f71d9-d2f0-4540-9c41-740f90fd4c26
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: b7834c95959972e7264e1caa2cfc21b190341b21
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="restricting-the-drawing-surface-in-gdi"></a>Restringindo a superfície de desenho no GDI+
Recorte envolve restringir o desenho a um determinado retângulo ou região. A ilustração a seguir mostra a cadeia de caracteres "Hello" recortado para uma região em forma de coração.  
  
 ![Superfície de desenho restrita](../../../../docs/framework/winforms/advanced/media/aboutgdip02-art30.gif "AboutGdip02_Art30")  
  
## <a name="clipping-with-regions"></a>Recorte com regiões  
 Regiões podem ser construídas de caminhos e caminhos podem conter os contornos das cadeias de caracteres, então você pode usar o texto com contorno de corte. A ilustração a seguir mostra um conjunto de elipses concêntricas recortado para o interior de uma cadeia de caracteres de texto.  
  
 ![Superfície de desenho restrita](../../../../docs/framework/winforms/advanced/media/aboutgdip02-art31.gif "AboutGdip02_Art31")  
  
 Para desenhar com corte, crie um <xref:System.Drawing.Graphics> do objeto, defina seu <xref:System.Drawing.Graphics.Clip%2A> propriedade e, em seguida, chamar os métodos de desenho do mesmo <xref:System.Drawing.Graphics> objeto:  
  
 [!code-csharp[LinesCurvesAndShapes#91](../../../../samples/snippets/csharp/VS_Snippets_Winforms/LinesCurvesAndShapes/CS/Class1.cs#91)]
 [!code-vb[LinesCurvesAndShapes#91](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/LinesCurvesAndShapes/VB/Class1.vb#91)]  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.Drawing.Graphics?displayProperty=nameWithType>  
 <xref:System.Drawing.Region?displayProperty=nameWithType>  
 [Linhas, Curvas e Formas](../../../../docs/framework/winforms/advanced/lines-curves-and-shapes.md)  
 [Usando regiões](../../../../docs/framework/winforms/advanced/using-regions.md)
