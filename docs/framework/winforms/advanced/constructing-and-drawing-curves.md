---
title: Construindo e desenhando curvas
ms.date: 03/30/2017
helpviewer_keywords:
- drawing [Windows Forms], curves
- examples [Windows Forms], drawing curves
- curves [Windows Forms], drawing
ms.assetid: 76e92623-4130-4644-b867-faca58bdb3a2
ms.openlocfilehash: 4c1b0cc6c6f878569fcf0c392f1b6f9683ec8afc
ms.sourcegitcommit: b1cfd260928d464d91e20121f9bdba7611c94d71
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/02/2019
ms.locfileid: "67506107"
---
# <a name="constructing-and-drawing-curves"></a>Construindo e desenhando curvas
GDI+ dá suporte a vários tipos de curvas: elipses, arcos, splines cardinais e splines de Bézier. Uma elipse é definida por seu retângulo delimitador; um arco é uma parte de uma elipse definida por um ângulo inicial e um ângulo de flecha. Um spline cardinal é definido por uma matriz de pontos e um parâmetro de tensão – a curva passa suavemente por cada ponto na matriz e o parâmetro de tensão influencia a maneira como a curva se dobra. Um spline de Bézier é definido por dois pontos de extremidade e dois pontos de controle. A curva não passa pelos pontos de controle, mas os pontos de controle influenciam a direção e dobram conforme a curva passa de um ponto de extremidade para o outro.  
  
## <a name="in-this-section"></a>Nesta seção  
 [Como: Desenhar splines cardinais](how-to-draw-cardinal-splines.md)  
 Descreve splines cardinais e como desenhá-los.  
  
 [Como: Desenhar um único Spline de Bézier](how-to-draw-a-single-bezier-spline.md)  
 Descreve um spline de Bézier e como desenhá-lo.  
  
 [Como: Desenhar uma sequência de Splines de Bézier](how-to-draw-a-sequence-of-bezier-splines.md)  
 Explica como desenhar vários splines de Bézier em sequência.
