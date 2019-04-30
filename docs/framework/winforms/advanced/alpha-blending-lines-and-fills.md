---
title: Combinação alfa em linhas e preenchimentos
ms.date: 03/30/2017
helpviewer_keywords:
- lines [Windows Forms], adding transparency
- examples [Windows Forms], alpha blending
- alpha blending [Windows Forms], using with lines
- alpha blending
- lines [Windows Forms], alpha blending
- fills [Windows Forms], alpha blending
- alpha blending [Windows Forms], using with fills
- shapes [Windows Forms], adding transparency
ms.assetid: 5440f48c-3ac9-44c3-b170-c1c110bdbab8
ms.openlocfilehash: 7a8286fb741effaf668b87e90da04f79d1490de2
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61960934"
---
# <a name="alpha-blending-lines-and-fills"></a>Combinação alfa em linhas e preenchimentos
No [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)], uma cor é um valor de 32 bits com 8 bits cada para alfa, vermelho, verde e azul. O valor alfa indica a transparência da cor – a extensão a qual a cor é combinada com a cor da tela de fundo. Os valores alfa variam de 0 a 255, em que 0 representa uma cor totalmente transparente e 255 representa uma cor totalmente opaca.  
  
 A combinação alfa é uma combinação de pixel por pixel da fonte e dos dados de cor da tela de fundo. Cada um dos três componentes (vermelho, verde, azul) de uma cor de origem é combinado com o componente correspondente da cor da tela de fundo de acordo com a seguinte fórmula:  
  
 displayColor = sourceColor × alfa / 255 + backgroundColor × (255 – alfa) / 255  
  
 Por exemplo, suponha que o componente vermelho da cor da fonte é 150 e o componente vermelho da cor da tela de fundo é 100. Se o valor alfa for 200, o componente vermelho da cor resultante será calculado da seguinte maneira:  
  
 150 × 200 / 255 + 100 × (255 – 200) / 255 = 139  
  
## <a name="in-this-section"></a>Nesta seção  
 [Como: Desenhar linhas opacas e semitransparentes](how-to-draw-opaque-and-semitransparent-lines.md)  
 Mostra como desenhar linhas com combinação alfa.  
  
 [Como: Desenhar com pincéis opacos e semitransparentes](how-to-draw-with-opaque-and-semitransparent-brushes.md)  
 Explica como fazer a combinação alfa com pincéis.  
  
 [Como: Use o modo de composição para controlar a combinação alfa](how-to-use-compositing-mode-to-control-alpha-blending.md)  
 Descreve como controlar a combinação alfa usando <xref:System.Drawing.Drawing2D.CompositingMode>.  
  
 [Como: Use uma matriz de cores para definir valores alfa em imagens](how-to-use-a-color-matrix-to-set-alpha-values-in-images.md)  
 Explica como usar um <xref:System.Drawing.Imaging.ColorMatrix> objeto para controlar a combinação alfa.
