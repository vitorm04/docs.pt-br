---
title: 'Como: Usar um MatrixTransform para criar transformações personalizadas'
ms.date: 03/30/2017
helpviewer_keywords:
- graphics [WPF], custom Transforms
ms.assetid: 919381ca-989f-47cf-86b4-1094060236e4
ms.openlocfilehash: 1971d5fe9422c5138f140517e6fd4c9f9b2cf48b
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69913911"
---
# <a name="how-to-use-a-matrixtransform-to-create-custom-transforms"></a>Como: Usar um MatrixTransform para criar transformações personalizadas
Este exemplo mostra como usar um <xref:System.Windows.Media.MatrixTransform> para converter (mover) a posição, a ampliação e a distorção de um. <xref:System.Windows.Controls.Button>  
  
> [!NOTE]
> Use a <xref:System.Windows.Media.MatrixTransform> classe para criar transformações personalizadas que não são fornecidas <xref:System.Windows.Media.RotateTransform>pelas classes, <xref:System.Windows.Media.SkewTransform> <xref:System.Windows.Media.ScaleTransform>, ou <xref:System.Windows.Media.TranslateTransform> .  
  
## <a name="example"></a>Exemplo  
 [!code-xaml[Transforms_snip#MatrixTransform](~/samples/snippets/csharp/VS_Snippets_Wpf/Transforms_snip/CS/MatrixTransformExample.xaml#matrixtransform)]  
  
## <a name="see-also"></a>Consulte também

- <xref:System.Windows.Media.MatrixTransform>
- <xref:System.Windows.Media.Transform>
- [Visão geral de transformações](transforms-overview.md)
- [Tópicos de instruções](transformations-how-to-topics.md)
- [Visão geral de formas e desenho básico no WPF](shapes-and-basic-drawing-in-wpf-overview.md)
