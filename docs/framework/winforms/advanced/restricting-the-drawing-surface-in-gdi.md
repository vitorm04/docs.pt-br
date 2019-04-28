---
title: Restringindo a superfície de desenho no GDI+
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- GDI+, clipping
- clipping [Windows Forms], using GDI+
- GDI+, restricting drawing surface
ms.assetid: 8b5f71d9-d2f0-4540-9c41-740f90fd4c26
ms.openlocfilehash: d0508166f905b45789ce638b03d0747dd6fa904e
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61672610"
---
# <a name="restricting-the-drawing-surface-in-gdi"></a>Restringindo a superfície de desenho no GDI+
Recorte significa restringir o desenho para um determinado retângulo ou região. A ilustração a seguir mostra a cadeia de caracteres "Hello" recortada para uma região em forma de coração.  
  
 ![Superfície de desenho restrita](./media/aboutgdip02-art30.gif "AboutGdip02_Art30")  
  
## <a name="clipping-with-regions"></a>Recorte com regiões  
 Regiões podem ser construídas de caminhos e os caminhos podem conter os contornos de cadeias de caracteres, então você pode usar texto contornado de corte. A ilustração a seguir mostra um conjunto de elipses concêntricos recortado para o interior de uma cadeia de caracteres de texto.  
  
 ![Superfície de desenho restrita](./media/aboutgdip02-art31.gif "AboutGdip02_Art31")  
  
 Para desenhar com recorte, crie uma <xref:System.Drawing.Graphics> do objeto, defina sua <xref:System.Drawing.Graphics.Clip%2A> propriedade e, em seguida, chamar os métodos de desenho desse mesmo <xref:System.Drawing.Graphics> objeto:  
  
 [!code-csharp[LinesCurvesAndShapes#91](~/samples/snippets/csharp/VS_Snippets_Winforms/LinesCurvesAndShapes/CS/Class1.cs#91)]
 [!code-vb[LinesCurvesAndShapes#91](~/samples/snippets/visualbasic/VS_Snippets_Winforms/LinesCurvesAndShapes/VB/Class1.vb#91)]  
  
## <a name="see-also"></a>Consulte também

- <xref:System.Drawing.Graphics?displayProperty=nameWithType>
- <xref:System.Drawing.Region?displayProperty=nameWithType>
- [Linhas, Curvas e Formas](lines-curves-and-shapes.md)
- [Usando regiões](using-regions.md)
