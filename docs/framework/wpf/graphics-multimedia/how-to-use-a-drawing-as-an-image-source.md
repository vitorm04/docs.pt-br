---
title: 'Como: Usar um desenho como uma fonte de imagem'
ms.date: 03/30/2017
helpviewer_keywords:
- graphics [WPF], drawings [WPF], as image sources
- image sources [WPF], drawings
- drawings [WPF], as image sources
ms.assetid: dcf71c7b-9e86-4b8e-8e39-0d0ce0389ef4
ms.openlocfilehash: d4b91a6495e1c54400d5fbfe43b6311d908565a7
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59097854"
---
# <a name="how-to-use-a-drawing-as-an-image-source"></a>Como: Usar um desenho como uma fonte de imagem
Este exemplo mostra como usar um <xref:System.Windows.Media.Drawing> como o <xref:System.Windows.Controls.Image.Source%2A> para um <xref:System.Windows.Controls.Image> controle. Para exibir uma <xref:System.Windows.Media.Drawing> com um <xref:System.Windows.Controls.Image> controlar, use um <xref:System.Windows.Media.DrawingImage> como o <xref:System.Windows.Controls.Image> do controle <xref:System.Windows.Controls.Image.Source%2A> e defina a <xref:System.Windows.Media.DrawingImage> do objeto <xref:System.Windows.Media.DrawingImage.Drawing%2A?displayProperty=nameWithType> propriedade para o desenho que você deseja exibir.  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir usa uma <xref:System.Windows.Media.DrawingImage> e uma <xref:System.Windows.Controls.Image> controle para exibir um <xref:System.Windows.Media.GeometryDrawing>. Este exemplo gera a seguinte saída:  
  
 ![Um GeometryDrawing de duas elipses](./media/graphicsmm-geodraw.jpg "graphicsmm_geodraw")  
Uma DrawingImage  
  
 [!code-csharp[DrawingMiscSnippets_snip#DrawingImageExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/DrawingImageExample.cs#drawingimageexamplewholepage)]
 [!code-xaml[DrawingMiscSnippets_snip#DrawingImageExampleWholePage](~/samples/snippets/xaml/VS_Snippets_Wpf/DrawingMiscSnippets_snip/XAML/DrawingImageExample.xaml#drawingimageexamplewholepage)]  
  
## <a name="see-also"></a>Consulte também

- <xref:System.Windows.Freezable.Freeze%2A>
- [Desenhar uma imagem usando ImageDrawing](how-to-draw-an-image-using-imagedrawing.md)
- [Visão geral dos objetos de desenho](drawing-objects-overview.md)
- [Visão geral de objetos congeláveis](../advanced/freezable-objects-overview.md)
- [Atributo PresentationOptions:Freeze](../advanced/presentationoptions-freeze-attribute.md)
