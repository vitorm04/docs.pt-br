---
title: 'Como: Desenhar uma imagem usando ImageDrawing'
ms.date: 03/30/2017
helpviewer_keywords:
- drawing [WPF], images
- graphics [WPF], drawing images
- images [WPF], drawing
ms.assetid: df28ab41-25fb-4ab3-b51d-7f695b24f55e
ms.openlocfilehash: 9a9a7ee32104e44997e6eaada09edaac2b1d610e
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/05/2019
ms.locfileid: "57355580"
---
# <a name="how-to-draw-an-image-using-imagedrawing"></a>Como: Desenhar uma imagem usando ImageDrawing
Este exemplo mostra como usar um <xref:System.Windows.Media.ImageDrawing> para desenhar uma imagem. Uma <xref:System.Windows.Media.ImageDrawing> permite que você exiba uma <xref:System.Windows.Media.ImageSource> com um <xref:System.Windows.Media.DrawingBrush>, <xref:System.Windows.Media.DrawingImage>, ou <xref:System.Windows.Media.Visual>. Para desenhar uma imagem, você cria um <xref:System.Windows.Media.ImageDrawing> e defina sua <xref:System.Windows.Media.ImageDrawing.ImageSource%2A?displayProperty=nameWithType> e <xref:System.Windows.Media.ImageDrawing.Rect%2A?displayProperty=nameWithType> propriedades. O <xref:System.Windows.Media.ImageDrawing.ImageSource%2A?displayProperty=nameWithType> propriedade especifica a imagem a ser desenhada e o <xref:System.Windows.Media.ImageDrawing.Rect%2A?displayProperty=nameWithType> propriedade especifica a posição e tamanho de cada imagem.  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir cria um desenho composto usando quatro <xref:System.Windows.Media.ImageDrawing> objetos. Este exemplo produz a imagem a seguir:  
  
 ![Vários objetos DrawingImage](./media/graphicsmm-imagedrawingexample.jpg "graphicsmm_ImageDrawingExample")  
Quatro objetos ImageDrawing  
  
 [!code-csharp[DrawingMiscSnippets_snip#ImageDrawingExample](~/samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/ImageDrawingExample.cs#imagedrawingexample)]
 [!code-xaml[DrawingMiscSnippets_snip#ImageDrawingExample](~/samples/snippets/xaml/VS_Snippets_Wpf/DrawingMiscSnippets_snip/XAML/ImageDrawingExample.xaml#imagedrawingexample)]  
  
 Para obter um exemplo que mostra uma maneira simples para exibir uma imagem sem usar <xref:System.Windows.Media.ImageDrawing>, consulte [usar o elemento Image](../controls/how-to-use-the-image-element.md).  
  
## <a name="see-also"></a>Consulte também
- <xref:System.Windows.Freezable.Freeze%2A>
- <xref:System.Windows.Controls.Image>
- [Visão geral dos objetos de desenho](drawing-objects-overview.md)
- [Visão geral de objetos congeláveis](../advanced/freezable-objects-overview.md)
- [Atributo PresentationOptions:Freeze](../advanced/presentationoptions-freeze-attribute.md)
