---
title: Como definir o tamanho de lado para um TileBrush
ms.date: 03/30/2017
helpviewer_keywords:
- TileBrush [WPF], size of tilepropertys
- Viewport property of TileBrush [WPF]
ms.assetid: 04f41090-1b46-4e36-832f-d27d28708b8c
ms.openlocfilehash: 16f0a4b3a5c9b9075126ba6d8f19d65169f70921
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33561742"
---
# <a name="how-to-set-the-tile-size-for-a-tilebrush"></a>Como definir o tamanho de lado para um TileBrush
Este exemplo mostra como definir o tamanho de bloco para um <xref:System.Windows.Media.TileBrush>. Por padrão, um <xref:System.Windows.Media.TileBrush> produz um único bloco que preenche completamente a área que você estiver pintando. Você pode substituir esse comportamento, definindo a <xref:System.Windows.Media.TileBrush.Viewport%2A> e <xref:System.Windows.Media.TileBrush.ViewportUnits%2A> propriedades.  
  
 O <xref:System.Windows.Media.TileBrush.Viewport%2A> propriedade especifica o tamanho de bloco para um <xref:System.Windows.Media.TileBrush>. Por padrão, o valor de <xref:System.Windows.Media.TileBrush.Viewport%2A> propriedade é relativo ao tamanho da área que está sendo pintada. Para fazer o <xref:System.Windows.Media.TileBrush.Viewport%2A> propriedade especificar um tamanho de bloco absoluto, definir o <xref:System.Windows.Media.TileBrush.ViewportUnits%2A> propriedade <xref:System.Windows.Media.BrushMappingMode.Absolute>.  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir usa uma <xref:System.Windows.Media.ImageBrush>, um tipo de <xref:System.Windows.Media.TileBrush>, para desenhar um retângulo com blocos. O exemplo define cada bloco para 50% por 50% da área de saída (o retângulo). Como resultado, o retângulo é pintado com quatro projeções da imagem.  
  
 A ilustração a seguir mostra a saída que esse exemplo produz.
  
 ![Exemplo de agrupamento lado a lado com um pincel de imagem](../../../../docs/framework/wpf/graphics-multimedia/media/0.png "0")  
  
 [!code-csharp[UsingImageBrush_snip#RelativeTileSizeExample](../../../../samples/snippets/csharp/VS_Snippets_Wpf/UsingImageBrush_snip/CSharp/TileSizeExample.cs#relativetilesizeexample)]  
  
 O exemplo a seguir cria um <xref:System.Windows.Media.ImageBrush>, define seu <xref:System.Windows.Media.TileBrush.Viewport%2A> para `0,0,25,25` e sua <xref:System.Windows.Media.TileBrush.ViewportUnits%2A> para <xref:System.Windows.Media.BrushMappingMode.Absolute>e o utiliza para pintar outro retângulo. Como resultado, o pincel produz blocos com uma largura de 25 pixels e uma altura de 25 pixels.  
  
 A ilustração a seguir mostra a saída que esse exemplo produz.  
  
 ![Um TileBrush organizado lado a lado com um Viewport de 0,0,0,25,0,25](../../../../docs/framework/wpf/graphics-multimedia/media/25x25viewport.png "25x25viewport")  
  
 [!code-csharp[UsingImageBrush_snip#AbsoluteTileSizeExample](../../../../samples/snippets/csharp/VS_Snippets_Wpf/UsingImageBrush_snip/CSharp/TileSizeExample.cs#absolutetilesizeexample)]  
  
 Os exemplos anteriores fazem parte de um exemplo maior. Para o exemplo completo, consulte [ImageBrush exemplo](http://go.microsoft.com/fwlink/?LinkID=160005).  
  
 Embora este exemplo usa o <xref:System.Windows.Media.ImageBrush> classe, o <xref:System.Windows.Media.TileBrush.Viewport%2A> e <xref:System.Windows.Media.TileBrush.ViewportUnits%2A> propriedades se comportam de forma idêntica para os outros <xref:System.Windows.Media.TileBrush> objetos, ou seja, para <xref:System.Windows.Media.DrawingBrush> e <xref:System.Windows.Media.VisualBrush>. Para obter mais informações sobre <xref:System.Windows.Media.ImageBrush> e outros <xref:System.Windows.Media.TileBrush> objetos, consulte [pintura com imagens, desenhos e visuais](../../../../docs/framework/wpf/graphics-multimedia/painting-with-images-drawings-and-visuals.md).  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.Windows.Media.TileBrush>  
 [Pintando com imagens, desenhos e visuais](../../../../docs/framework/wpf/graphics-multimedia/painting-with-images-drawings-and-visuals.md)  
 [Criar padrões de bloco diferentes com um TileBrush](../../../../docs/framework/wpf/graphics-multimedia/how-to-create-different-tile-patterns-with-a-tilebrush.md)
