---
title: Usando a transformação global
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- graphics [Windows Forms], world transformation
- world transformation [Windows Forms], examples
ms.assetid: 1e717711-1361-448e-aa49-0f3ec43110c9
ms.openlocfilehash: 6a029e17096222d7ed80dea16f91b83a813039f8
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33523677"
---
# <a name="using-the-world-transformation"></a>Usando a transformação global
A transformação global é uma propriedade do <xref:System.Drawing.Graphics> classe. Os números que especifique a transformação global são armazenados em um <xref:System.Drawing.Drawing2D.Matrix> objeto que representa uma matriz 3 x 3. O <xref:System.Drawing.Drawing2D.Matrix> e <xref:System.Drawing.Graphics> classes têm vários métodos para definir os números na matriz de transformação do mundo.  
  
## <a name="different-types-of-transformations"></a>Tipos diferentes de transformações  
 No exemplo a seguir, o code first cria um retângulo de 50×50 e o localiza na origem (0, 0). A origem está localizada no canto superior esquerdo da área de cliente.  
  
 [!code-csharp[System.Drawing.MiscLegacyTopics#11](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.MiscLegacyTopics/CS/Class1.cs#11)]
 [!code-vb[System.Drawing.MiscLegacyTopics#11](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.MiscLegacyTopics/VB/Class1.vb#11)]  
  
 O código a seguir aplica uma transformação de escala que expande o retângulo por um fator de 1,75 na direção x e encolhe o retângulo por um fator de 0,5 na direção y:  
  
 [!code-csharp[System.Drawing.MiscLegacyTopics#12](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.MiscLegacyTopics/CS/Class1.cs#12)]
 [!code-vb[System.Drawing.MiscLegacyTopics#12](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.MiscLegacyTopics/VB/Class1.vb#12)]  
  
 O resultado é um retângulo que é maior na direção x e menor na direção y que o original.  
  
 Para girar o retângulo em vez de dimensioná-lo, use o seguinte código:  
  
 [!code-csharp[System.Drawing.MiscLegacyTopics#13](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.MiscLegacyTopics/CS/Class1.cs#13)]
 [!code-vb[System.Drawing.MiscLegacyTopics#13](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.MiscLegacyTopics/VB/Class1.vb#13)]  
  
 Para converter o retângulo, use o seguinte código:  
  
 [!code-csharp[System.Drawing.MiscLegacyTopics#14](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.MiscLegacyTopics/CS/Class1.cs#14)]
 [!code-vb[System.Drawing.MiscLegacyTopics#14](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.MiscLegacyTopics/VB/Class1.vb#14)]  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.Drawing.Drawing2D.Matrix>  
 [Sistemas de Coordenadas e Transformações](../../../../docs/framework/winforms/advanced/coordinate-systems-and-transformations.md)  
 [Usando Transformações no GDI+ Gerenciado](../../../../docs/framework/winforms/advanced/using-transformations-in-managed-gdi.md)
