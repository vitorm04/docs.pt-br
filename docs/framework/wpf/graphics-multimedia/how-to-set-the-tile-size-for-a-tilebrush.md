---
title: Como definir o tamanho de lado para um TileBrush
ms.date: 03/30/2017
helpviewer_keywords:
- TileBrush [WPF], size of tile properties
- Viewport property of TileBrush [WPF]
ms.assetid: 04f41090-1b46-4e36-832f-d27d28708b8c
ms.openlocfilehash: af7bab59a292549b29dad9b6a7417f22b1b84e48
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79186831"
---
# <a name="how-to-set-the-tile-size-for-a-tilebrush"></a>Como definir o tamanho de lado para um TileBrush

Este exemplo mostra como definir o <xref:System.Windows.Media.TileBrush>tamanho do azulejo para um . Por padrão, <xref:System.Windows.Media.TileBrush> um produz um único ladrilho que preenche completamente a área que você está pintando. Você pode substituir esse comportamento <xref:System.Windows.Media.TileBrush.Viewport%2A> <xref:System.Windows.Media.TileBrush.ViewportUnits%2A> definindo as propriedades e as propriedades.

A <xref:System.Windows.Media.TileBrush.Viewport%2A> propriedade especifica o tamanho <xref:System.Windows.Media.TileBrush>do azulejo para um . Por padrão, o <xref:System.Windows.Media.TileBrush.Viewport%2A> valor do imóvel é relativo ao tamanho da área que está sendo pintada. Para fazer <xref:System.Windows.Media.TileBrush.Viewport%2A> com que a propriedade <xref:System.Windows.Media.TileBrush.ViewportUnits%2A> especifique um tamanho absoluto de telhas, defina a propriedade como <xref:System.Windows.Media.BrushMappingMode.Absolute>.

## <a name="example"></a>Exemplo

O exemplo a <xref:System.Windows.Media.ImageBrush>seguir usa <xref:System.Windows.Media.TileBrush>um tipo de , para pintar um retângulo com telhas. O exemplo define cada ladrilho para 50% por 50% da área de saída (o retângulo). Como resultado, o retângulo é pintado com quatro projeções da imagem.

A ilustração a seguir mostra a saída que o exemplo produz:

![Um retângulo com quatro cerejas demonstrando revestimento com um pincel de imagem.](./media/how-to-set-the-tile-size-for-a-tilebrush/rectangle-tile-image-brush.png)

[!code-csharp[UsingImageBrush_snip#RelativeTileSizeExample](~/samples/snippets/csharp/VS_Snippets_Wpf/UsingImageBrush_snip/CSharp/TileSizeExample.cs#relativetilesizeexample)]

O próximo exemplo <xref:System.Windows.Media.ImageBrush>cria <xref:System.Windows.Media.TileBrush.Viewport%2A> um `0,0,25,25` , <xref:System.Windows.Media.TileBrush.ViewportUnits%2A> <xref:System.Windows.Media.BrushMappingMode.Absolute>define o seu e o seu para , e usa-o para pintar outro retângulo. Como resultado, o pincel produz blocos com uma largura de 25 pixels e uma altura de 25 pixels.

A ilustração a seguir mostra a saída que o exemplo produz:

![Um retângulo com quarenta e oito cerejas demonstrando um TileBrush ladrilho com um Viewport.](./media/how-to-set-the-tile-size-for-a-tilebrush/25-x-25-viewport-tilebrush.png)

[!code-csharp[UsingImageBrush_snip#AbsoluteTileSizeExample](~/samples/snippets/csharp/VS_Snippets_Wpf/UsingImageBrush_snip/CSharp/TileSizeExample.cs#absolutetilesizeexample)]

Os exemplos anteriores fazem parte de um exemplo maior. Para obter a amostra completa, consulte [ImageBrush Sample](https://github.com/Microsoft/WPF-Samples/tree/master/Graphics/ImageBrush).

Embora este exemplo <xref:System.Windows.Media.ImageBrush> use <xref:System.Windows.Media.TileBrush.Viewport%2A> a <xref:System.Windows.Media.TileBrush.ViewportUnits%2A> classe, as propriedades <xref:System.Windows.Media.TileBrush> e as propriedades <xref:System.Windows.Media.DrawingBrush> se <xref:System.Windows.Media.VisualBrush>comportam de forma idêntica para os outros objetos, ou seja, para e . Para obter <xref:System.Windows.Media.ImageBrush> mais informações <xref:System.Windows.Media.TileBrush> sobre e os outros objetos, consulte [Pintura com Imagens, Desenhos e Visuais](painting-with-images-drawings-and-visuals.md).

## <a name="see-also"></a>Confira também

- <xref:System.Windows.Media.TileBrush>
- [Pintando com imagens, desenhos e visuais](painting-with-images-drawings-and-visuals.md)
- [Criar padrões de bloco diferentes com um TileBrush](how-to-create-different-tile-patterns-with-a-tilebrush.md)
