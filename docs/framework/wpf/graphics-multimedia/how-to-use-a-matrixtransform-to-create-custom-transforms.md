---
title: 'Como: Usar um MatrixTransform para criar transformações personalizadas'
ms.date: 03/30/2017
helpviewer_keywords:
- graphics [WPF], custom Transforms
ms.assetid: 919381ca-989f-47cf-86b4-1094060236e4
ms.openlocfilehash: aeccb961db539d4cc6dea75fb487fba06e59d6de
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59182306"
---
# <a name="how-to-use-a-matrixtransform-to-create-custom-transforms"></a>Como: Usar um MatrixTransform para criar transformações personalizadas
Este exemplo mostra como usar um <xref:System.Windows.Media.MatrixTransform> para mover (translação) a posição, ampliar e distorção de um <xref:System.Windows.Controls.Button>.  
  
> [!NOTE]
>  Use o <xref:System.Windows.Media.MatrixTransform> classe para criar transformações personalizadas que não são fornecidas pelo <xref:System.Windows.Media.RotateTransform>, <xref:System.Windows.Media.SkewTransform>, <xref:System.Windows.Media.ScaleTransform>, ou <xref:System.Windows.Media.TranslateTransform> classes.  
  
## <a name="example"></a>Exemplo  
 [!code-xaml[Transforms_snip#MatrixTransform](~/samples/snippets/csharp/VS_Snippets_Wpf/Transforms_snip/CS/MatrixTransformExample.xaml#matrixtransform)]  
  
## <a name="see-also"></a>Consulte também

- <xref:System.Windows.Media.MatrixTransform>
- <xref:System.Windows.Media.Transform>
- [Visão geral de transformações](transforms-overview.md)
- [Tópicos de instruções](transformations-how-to-topics.md)
- [Visão geral de formas e desenho básico no WPF](shapes-and-basic-drawing-in-wpf-overview.md)
