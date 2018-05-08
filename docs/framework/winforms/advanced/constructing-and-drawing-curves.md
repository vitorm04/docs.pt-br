---
title: Construindo e desenhando curvas
ms.date: 03/30/2017
helpviewer_keywords:
- drawing [Windows Forms], curves
- examples [Windows Forms], drawing curves
- curves [Windows Forms], drawing
ms.assetid: 76e92623-4130-4644-b867-faca58bdb3a2
ms.openlocfilehash: d9a790060fdf0f0c2a739d99aba1b36cf0323f8b
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="constructing-and-drawing-curves"></a>Construindo e desenhando curvas
O [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] dá suporte a vários tipos de curvas: elipses, arcos, splines cardinais e splines de Bézier. Uma elipse é definida por seu retângulo delimitador; um arco é uma parte de uma elipse definida por um ângulo inicial e um ângulo de flecha. Um spline cardinal é definido por uma matriz de pontos e um parâmetro de tensão – a curva passa suavemente por cada ponto na matriz e o parâmetro de tensão influencia a maneira como a curva se dobra. Um spline de Bézier é definido por dois pontos de extremidade e dois pontos de controle. A curva não passa pelos pontos de controle, mas os pontos de controle influenciam a direção e dobram conforme a curva passa de um ponto de extremidade para o outro.  
  
## <a name="in-this-section"></a>Nesta seção  
 [Como Desenhar Splines Cardinais](../../../../docs/framework/winforms/advanced/how-to-draw-cardinal-splines.md)  
 Descreve splines cardinais e como desenhá-los.  
  
 [Como Desenhar um Único Spline de Bézier](../../../../docs/framework/winforms/advanced/how-to-draw-a-single-bezier-spline.md)  
 Descreve um spline de Bézier e como desenhá-lo.  
  
 [Como Desenhar uma Sequência de Splines de Bézier](../../../../docs/framework/winforms/advanced/how-to-draw-a-sequence-of-bezier-splines.md)  
 Explica como desenhar vários splines de Bézier em sequência.
