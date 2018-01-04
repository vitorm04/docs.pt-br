---
title: "Por que a ordem das transformações é importante"
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
helpviewer_keywords: transformations [Windows Forms], order signficance
ms.assetid: 37d5f9dc-a5cf-4475-aa5d-34d714e808a9
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: cd3363a1afb8658ed3bb27359259cb752464507d
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="why-transformation-order-is-significant"></a>Por que a ordem das transformações é importante
Um único <xref:System.Drawing.Drawing2D.Matrix> objeto pode armazenar uma única transformação ou uma sequência de transformações. Essa última é chamada de transformação composta. A matriz de uma transformação composta é obtida pela multiplicação das matrizes de transformações individuais.  
  
## <a name="composite-transform-examples"></a>Exemplos de transformação composta  
 Em uma transformação composta, a ordem das transformações individuais é importante. Por exemplo, girar, ajustar a escala e mover terá um resultado diferente de mover, girar e ajustar a escala. No [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)], transformações compostas são criadas da esquerda para a direita. Se S, R e T forem matrizes de escala, rotação e translação, respectivamente, o produto SRT (nesta ordem) será a matriz da transformação composta que primeiro ajusta a escala, em seguida girará e finalmente fará a translação. A matriz produzida pelo produto SRT será diferente da matriz produzida pelo produto TRS.  
  
 Um motivo de a ordem ser importante é que transformações, como rotação e colocação em escala, são feitas em relação a origem do sistema de coordenadas. Dimensionamento de um objeto que é centralizado na origem produz um resultado diferente de dimensionamento de um objeto que foi movido para fora da origem. Da mesma forma, girar um objeto centralizado na origem produz um resultado diferente de girar um objeto movido para fora da origem.  
  
 O exemplo a seguir combina colocação em escala, rotação e translação (nessa ordem) para formar uma transformação composta. O argumento <xref:System.Drawing.Drawing2D.MatrixOrder.Append> passado para o <xref:System.Drawing.Graphics.RotateTransform%2A> método indica que a rotação seguirá o dimensionamento. Da mesma forma, o argumento <xref:System.Drawing.Drawing2D.MatrixOrder.Append> passado para o <xref:System.Drawing.Graphics.TranslateTransform%2A> método indica que a conversão seguirão a rotação. <xref:System.Drawing.Drawing2D.MatrixOrder.Append>e <xref:System.Drawing.Drawing2D.MatrixOrder.Prepend> são membros de <xref:System.Drawing.Drawing2D.MatrixOrder> enumeração.  
  
 [!code-csharp[System.Drawing.MiscLegacyTopics#21](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.MiscLegacyTopics/CS/Class1.cs#21)]
 [!code-vb[System.Drawing.MiscLegacyTopics#21](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.MiscLegacyTopics/VB/Class1.vb#21)]  
  
 O exemplo a seguir faz com que o mesmo método chame como o exemplo anterior, mas a ordem das chamadas é invertida. A ordem resultante das operações é mover, girar e ajustar a escala, o que produz um resultado muito diferente de ajustar a escala, girar e mover.  
  
 [!code-csharp[System.Drawing.MiscLegacyTopics#22](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.MiscLegacyTopics/CS/Class1.cs#22)]
 [!code-vb[System.Drawing.MiscLegacyTopics#22](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.MiscLegacyTopics/VB/Class1.vb#22)]  
  
 Uma maneira de inverter a ordem das transformações individuais em uma transformação composta é inverter a ordem de uma sequência de chamadas de método. Outra maneira de controlar a ordem das operações é alterar o argumento de ordem de matriz. O exemplo a seguir é o mesmo que o exemplo anterior, exceto que <xref:System.Drawing.Drawing2D.MatrixOrder.Append> foi alterado para <xref:System.Drawing.Drawing2D.MatrixOrder.Prepend>. A multiplicação de matriz é feita na ordem SRT, em que S, R e T são matrizes para ajustar escala, girar e mover, respectivamente. A ordem da transformação composta é ajustar escala, girar e mover.  
  
 [!code-csharp[System.Drawing.MiscLegacyTopics#23](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.MiscLegacyTopics/CS/Class1.cs#23)]
 [!code-vb[System.Drawing.MiscLegacyTopics#23](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.MiscLegacyTopics/VB/Class1.vb#23)]  
  
 O resultado do exemplo imediatamente anterior é o mesmo que o resultado do primeiro exemplo neste tópico. Isso ocorre porque invertemos a ordem das chamadas de método e a ordem de multiplicação da matriz.  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.Drawing.Drawing2D.Matrix>  
 [Sistemas de Coordenadas e Transformações](../../../../docs/framework/winforms/advanced/coordinate-systems-and-transformations.md)  
 [Usando Transformações no GDI+ Gerenciado](../../../../docs/framework/winforms/advanced/using-transformations-in-managed-gdi.md)
